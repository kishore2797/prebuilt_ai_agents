# RAG — Implementation Notes

## 1. What is RAG?

**Retrieval-Augmented Generation** — retrieve relevant documents at query time and inject them into the LLM prompt. Grounds output in real, current, private data.

```
User Query → Retrieve relevant chunks → Inject into prompt → LLM generates answer
```

**Evolution path (90% of use cases):**
```
Naive RAG → Hybrid RAG → Advanced RAG → Agentic RAG
(prototype)  (better recall) (better precision) (complex tasks)
```

---

## 2. Basic RAG Pipeline

### Step 1 — Load & Chunk Documents

```python
from langchain_community.document_loaders import PyPDFLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter

loader = PyPDFLoader("document.pdf")
docs = loader.load()

splitter = RecursiveCharacterTextSplitter(chunk_size=512, chunk_overlap=64)
chunks = splitter.split_documents(docs)
```

### Step 2 — Embed & Store

```python
from langchain_openai import OpenAIEmbeddings
from langchain_community.vectorstores import Chroma

embeddings = OpenAIEmbeddings()
vectorstore = Chroma.from_documents(chunks, embeddings, persist_directory="./chroma_db")
```

### Step 3 — Retrieve & Generate

```python
from langchain_openai import ChatOpenAI
from langchain.chains import RetrievalQA

retriever = vectorstore.as_retriever(search_kwargs={"k": 4})
llm = ChatOpenAI(model="gpt-4o-mini")

qa_chain = RetrievalQA.from_chain_type(llm=llm, retriever=retriever)
result = qa_chain.invoke({"query": "What is the return policy?"})
print(result["result"])
```

---

## 3. Chunking Strategies

| Strategy | Split By | `chunk_size` | `chunk_overlap` | Best For |
|---|---|---|---|---|
| **Fixed-size** | Token/char count | 256–1024 | 10–20% of size | General-purpose, fast prototyping |
| **Sentence-level** | Sentence boundary | N sentences | 1 sentence | QA over policies, contracts |
| **Paragraph-level** | `\n\n` | 1–2 paras | 1 para | Legal docs, manuals |
| **Recursive (default)** | `\n\n` → `\n` → `.` → ` ` | 512 | 64 | Best general default |
| **Semantic** | Topic shift (cosine drop) | Variable | None | Mixed-topic documents |
| **Parent-child** | Small+large pair | 128 child / 512 parent | N/A | Precise retrieval + full context |
| **Structural** | Headings/sections | Section | Section heading | Markdown, structured PDFs |
| **Page index** | PDF page | 1 page | None | PDFs needing page citations |
| **Token-aware** | Token count (tiktoken) | 400 | 50 | Prevents embedding truncation |

### Why overlap matters

```
# Without overlap — boundary context is lost
Chunk 1: "Employee is entitled to 20 days annual leave."
Chunk 2: "This does not include sick leave or public holidays."

# With overlap — boundary appears in both chunks
Chunk 1: "...entitled to 20 days annual leave. This does not include sick leave..."
Chunk 2: "...annual leave. This does not include sick leave or public holidays."
```

### Overlap trade-offs

| Overlap | Pros | Cons |
|---|---|---|
| 0% | Smallest index | Loses boundary context |
| 10–15% | Balanced | Slight redundancy |
| 20–25% | Good for dense text | Larger index |
| 50%+ | Max coverage | 2× storage |

### Semantic chunking (LangChain)

```python
from langchain_experimental.text_splitter import SemanticChunker
from langchain_openai import OpenAIEmbeddings

splitter = SemanticChunker(OpenAIEmbeddings(), breakpoint_threshold_type="percentile")
chunks = splitter.split_text(text)
```

### Parent-child retrieval (LangChain)

```python
from langchain.retrievers import ParentDocumentRetriever
from langchain.storage import InMemoryStore

child_splitter = RecursiveCharacterTextSplitter(chunk_size=128)
parent_splitter = RecursiveCharacterTextSplitter(chunk_size=512)
store = InMemoryStore()

retriever = ParentDocumentRetriever(
    vectorstore=vectorstore, docstore=store,
    child_splitter=child_splitter, parent_splitter=parent_splitter
)
retriever.add_documents(docs)
```

---

## 4. Retrieval Methods

| Method | Semantic | Exact Match | Speed | Best Use |
|---|---|---|---|---|
| **Dense (Vector)** | ✅ | ❌ | Fast | General QA |
| **Sparse (BM25)** | ❌ | ✅ | Very Fast | Keyword / ID search |
| **Hybrid** | ✅ | ✅ | Medium | Production default |
| **Re-ranking** | ✅ | ✅ | Slow | High-accuracy |
| **HyDE / Multi-vector** | ✅ | ❌ | Medium | Short/ambiguous queries |
| **Contextual Compression** | ✅ | ✅ | Slow | Long documents |
| **Metadata Filtered** | ✅ | ✅ | Fast | Scoped/multi-tenant |

### Hybrid retrieval (Dense + BM25)

```python
from langchain.retrievers import BM25Retriever, EnsembleRetriever

bm25 = BM25Retriever.from_documents(chunks, k=4)
dense = vectorstore.as_retriever(search_kwargs={"k": 4})

hybrid = EnsembleRetriever(retrievers=[bm25, dense], weights=[0.4, 0.6])
```

### Re-ranking

```python
from langchain.retrievers import ContextualCompressionRetriever
from langchain_cohere import CohereRerank

compressor = CohereRerank(model="rerank-english-v3.0", top_n=3)
reranking_retriever = ContextualCompressionRetriever(
    base_compressor=compressor, base_retriever=hybrid
)
```

### HyDE — Hypothetical Document Embeddings

```python
from langchain.chains import HypotheticalDocumentEmbedder

hyde_embeddings = HypotheticalDocumentEmbedder.from_llm(llm, embeddings, "web_search")
hyde_store = Chroma.from_documents(chunks, hyde_embeddings)
```

### Front-matter injection

Always inject document metadata (title, author, year) regardless of retrieval score to prevent hallucinated citations:

```python
front_matter = "Title: Deep Learning | Authors: Goodfellow et al. | Year: 2016\n\n"
context = front_matter + "\n\n".join([doc.page_content for doc in retrieved_docs])
```

---

## 5. Full Pipeline

```
Raw Document
    ↓
[Chunking] — Recursive / Semantic / Parent-child
    ↓
[Embedding] — OpenAI Ada / BGE / E5 / local
    ↓
[Vector Store] — Chroma / FAISS / Pinecone / Qdrant
    ↓
[Retrieval] — Hybrid (Dense + BM25) + Metadata filter
    ↓
[Post-Retrieval] — Re-ranking + Contextual compression
    ↓
[LLM Generation] — GPT-4o / Claude / local
```

---

## 6. RAG Types — Quick Reference

| Type | When to Use |
|---|---|
| **Naive RAG** | Prototyping; single-fact queries |
| **Hybrid RAG** | Production default; both semantic + exact needed |
| **Advanced RAG** | Re-ranking + query rewriting for precision |
| **Corrective RAG (CRAG)** | Retrieved docs might be wrong; fallback to web |
| **Self-RAG** | Model evaluates its own retrieval quality |
| **Agentic RAG** | LLM decides when/what to retrieve dynamically |
| **Graph RAG** | Entity-rich domains; multi-hop reasoning |
| **PageIndex** | Long PDFs; vectorless reasoning-based retrieval (98.7% on FinanceBench) |

---

## 7. Key Packages

```
langchain langchain-community langchain-openai langchain-experimental
chromadb faiss-cpu rank-bm25 pypdf
cohere tiktoken spacy
```

---

*Last updated: February 2026*
