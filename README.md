# 🧠 AI Agents & RAG — Learning Notes

> Personal notes from my learning journey into AI Agents, RAG systems, retrieval methods, and chunking strategies.
> Updated continuously as I go deeper.

## 📚 Table of Contents

1. [Agent Frameworks & Tools](#1-agent-frameworks--tools)
2. [GitHub Repositories & Resources](#2-github-repositories--resources)
3. [Repository Assessments](#3-repository-assessments)
4. [Learning Path](#4-learning-path)
5. [RAG — Types & Decision Framework](#5-rag--types--decision-framework)
6. [RAG — Advanced & Experimental Variants](#6-rag--advanced--experimental-variants)
7. [Retrieval Methods](#7-retrieval-methods)
8. [Chunking & Chunk Overlap Strategies](#8-chunking--chunk-overlap-strategies)

---

## 1. Agent Frameworks & Tools

### Production-Ready Frameworks

| Framework | Language | Key Features | Best For |
|-----------|----------|--------------|----------|
| **LangChain** | Python | Memory, chains, agents, tools, RAG | General-purpose agent + RAG pipelines |
| **LangGraph** | Python | Stateful agent workflows, cycles | Complex multi-step agent flows |
| **CrewAI** | Python | Multi-agent collaboration, roles | Team-based task workflows |
| **Microsoft AutoGen** | Python | Multi-agent conversations | Group problem-solving, debate agents |
| **MetaGPT** | Python | Software development agents | Coding, architecture planning |
| **Phidata** | Python | Structured agents, type-safe | Production agents with validation |

### Experimental / Emerging

| Framework | Novelty | Status |
|-----------|---------|--------|
| **OpenAI Swarm** | Lightweight multi-agent handoffs | Experimental |
| **AutoGPT** | Autonomous long-horizon task execution | Community |
| **AgentOps** | Agent monitoring & tracing | Early access |

---

### Development & Observability Tools

| Tool | Purpose |
|------|---------|
| **LangSmith** | Tracing, evaluation, debugging for LangChain |
| **AgentOps** | Monitor agent behavior, session replays |
| **Weights & Biases** | Experiment tracking |
| **CometML** | Agent performance monitoring |

### Deployment Tools

| Tool | Purpose |
|------|---------|
| **FastAPI** | Build REST APIs for agents |
| **Streamlit / Gradio** | Quick agent UIs for demos |
| **Docker** | Containerize agents for portability |
| **Kubernetes** | Scale agent deployments |

---

### Benchmarks & Evaluation

| Benchmark | What It Measures |
|-----------|-----------------|
| **GAIA** | General AI assistant capability |
| **AgentBench** | Multi-domain agent performance |
| **EvalAI** | Open evaluation platform |
| **ai-agent-benchmark-compendium** | 50+ tests across reasoning, tool use, safety |

**Key Metrics to Track:**
- **Task Completion Rate** — Did the agent finish the job?
- **Tool Usage Efficiency** — Did it use the right tool at the right time?
- **Reasoning Quality** — Was the chain of thought logical?
- **Safety & Compliance** — Did it stay within defined boundaries?

---

### Essential Papers

| Paper | Why It Matters |
|-------|---------------|
| **ReAct** | Combines reasoning + acting in one loop — foundation of most agent designs |
| **Toolformer** | LLM learns to call APIs on its own |
| **Self-RAG** | Model decides when to retrieve, critiques its own outputs |
| **HyDE** | Generate a hypothetical answer first, then use it to retrieve real docs |
| **GraphRAG (Microsoft)** | Community-based knowledge graph retrieval |

---

## 2. GitHub Repositories & Resources

### Agent Frameworks

| Repository | What It Is | Best For |
|------------|-----------|----------|
| [HKUDS/ClawWork](https://github.com/HKUDS/ClawWork) | Multi-modal agent framework — text, images, audio | Complex reasoning + tool integration |
| [olly-styles/WorkBench](https://github.com/olly-styles/WorkBench) | Visual agent builder, drag-and-drop, debugging | Learning, prototyping, demos |
| [microsoft/autogen](https://github.com/microsoft/autogen) | Multi-agent conversation framework | Group problem-solving, autonomous workflows |
| [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | Stateful agent workflow graphs | Production agents with persistence |
| [openai/swarm](https://github.com/openai/swarm) | Lightweight multi-agent handoffs | Fast, minimal agent orchestration |
| [phidata/phidata](https://github.com/phidata/phidata) | Structured agents with type safety | Production-grade validated agents |

### Evaluation & Benchmarking

| Repository | What It Is |
|------------|-----------|
| [philschmid/ai-agent-benchmark-compendium](https://github.com/philschmid/ai-agent-benchmark-compendium) | 50+ benchmark tests — reasoning, tool use, safety, efficiency |
| [topics/agent-evaluation](https://github.com/topics/agent-evaluation) | Hub aggregating evaluation frameworks, datasets, papers |
| [reworkd/bananalyzer](https://github.com/reworkd/bananalyzer) | Agent behavior analysis — decision trees, bottleneck detection |

### Curated Collections

| Repository | What It Is |
|------------|-----------|
| [ashishpatel26/500-AI-Agents-Projects](https://github.com/ashishpatel26/500-AI-Agents-Projects) | 500+ agent projects — conversational, automation, creative, research |
| [slavakurilyak/awesome-ai-agents](https://github.com/slavakurilyak/awesome-ai-agents) | Curated awesome list — frameworks, tools, papers, guides |

---

## 3. Repository Assessments

Quick reference for choosing what to use and when.

| Repository | Learning | Production | Security | Best For |
|------------|----------|------------|----------|----------|
| `ClawWork` | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 🛡️ Medium | Multi-modal agents, enterprise |
| `WorkBench` | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | 🛡️ Medium | Visual learning, prototyping |
| `bananalyzer` | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 🛡️ High | Production monitoring, QA |
| `benchmark-compendium` | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 🛡️ High | Pre-deployment validation |
| `agent-evaluation` | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | 🛡️ High | Research, tool selection |
| `500-AI-Agents-Projects` | ⭐⭐⭐⭐⭐ | ⭐⭐ | 🛡️ Low | Learning by example |
| `awesome-ai-agents` | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 🛡️ Medium | Overview, stack planning |

### When to Use What

- **Starting out** → `awesome-ai-agents` + `500-AI-Agents-Projects` + `WorkBench`
- **Building production** → `ClawWork` or `LangGraph` + `benchmark-compendium` + `bananalyzer`
- **Evaluating/researching** → `benchmark-compendium` + `agent-evaluation`
- **Security-sensitive** → `bananalyzer` (read-only), `benchmark-compendium` (no external deps)

### Security Notes

Before using any repo in production:
1. Review license compatibility
2. Audit dependencies (`pip audit`, `npm audit`)
3. Test in a sandboxed/containerized environment first
4. Restrict network access from agent containers
5. Never hardcode API keys — use environment variables

---

## 4. Learning Path

### 🌱 Stage 1 — Foundations (Month 1–3)
- Understand what agents are: LLM + memory + tools + planning loop
- Read **ReAct paper** — the core loop behind most agent frameworks
- Build a basic agent with LangChain (simple QA + tool use)
- Explore `awesome-ai-agents` and `500-AI-Agents-Projects` for patterns

### 🚀 Stage 2 — RAG & Retrieval (Month 3–6)
- Build a simple RAG pipeline: chunk → embed → store → retrieve → generate
- Understand chunking strategies and overlap (see Section 8)
- Understand dense vs sparse vs hybrid retrieval (see Section 7)
- Experiment with `ParentDocumentRetriever`, `EnsembleRetriever`, re-ranking

### 🏗️ Stage 3 — Production Patterns (Month 6–12)
- Move to `LangGraph` for stateful, multi-step agent workflows
- Add metadata filtering, self-query retrieval
- Implement monitoring with `LangSmith` or `AgentOps`
- Run `benchmark-compendium` before any production deployment
- Use `bananalyzer` to detect behavior drift

### 🧠 Stage 4 — Advanced (12+ months)
- Build multi-agent systems (CrewAI, AutoGen)
- Implement Agentic RAG — agent decides when and what to retrieve
- Explore GraphRAG for entity-rich domains
- Contribute to open-source agent frameworks

---

## 5. RAG — Types & Decision Framework

### What is RAG?

**Retrieval-Augmented Generation** — instead of relying solely on the LLM's training data, you retrieve relevant documents at query time and inject them into the prompt. This grounds the output in real, current, private data.

```
User Query
    ↓
Retrieve relevant chunks from knowledge base
    ↓
Inject chunks into LLM prompt as context
    ↓
LLM generates grounded answer
```

---

### RAG Types by Retrieval Strategy

| Type | What It Does |
|------|-------------|
| **Naive RAG** | Basic pipeline: chunk → embed → retrieve top-K → generate |
| **Advanced RAG** | Adds query rewriting, re-ranking, hybrid search before/after retrieval |
| **Modular RAG** | Swappable modules — retriever, reranker, generator can be changed independently |

### RAG Types by Retrieval Granularity

| Type | Granularity |
|------|------------|
| **Chunk-based RAG** | Fixed or semantic text chunks |
| **Sentence-level RAG** | Finer granularity for precision |
| **Document-level RAG** | Full document retrieval |

### RAG Types by Index/Search

| Type | How It Retrieves |
|------|-----------------|
| **Dense RAG** | Vector similarity search (embeddings) |
| **Sparse RAG** | Keyword-based (BM25, TF-IDF) |
| **Hybrid RAG** | Combines dense + sparse |

### RAG Types by Architecture

| Type | Behavior |
|------|---------|
| **Single-hop RAG** | One retrieval step per query |
| **Multi-hop RAG** | Iterative retrieval; each step informs the next |
| **Agentic RAG** | LLM agent decides when and what to retrieve |
| **Self-RAG** | Model critiques its own retrieval and output using special tokens |
| **Corrective RAG (CRAG)** | Evaluates retrieved docs; falls back to web search if low quality |
| **Graph RAG** | Retrieves from a knowledge graph, not a flat vector store |

### RAG Types by Knowledge Source

| Type | Source |
|------|--------|
| **Local RAG** | Private/local document stores |
| **Web RAG** | Real-time web retrieval |
| **Structured RAG** | Databases/tables via Text-to-SQL |
| **Multimodal RAG** | Images, audio, video alongside text |

---

### Decision Framework — Which RAG to Use

**Step 1 — How complex is your query?**
- Single-fact questions → Naive or Advanced RAG
- Multi-step reasoning → Multi-hop RAG
- Dynamic, unpredictable queries → Agentic RAG

**Step 2 — What's your data source?**
- Private docs/files → Local RAG (dense or hybrid)
- Real-time info needed → Web RAG
- Structured DB/tables → Structured RAG (Text-to-SQL)
- Entities with relationships → Graph RAG
- Images + text → Multimodal RAG

**Step 3 — How critical is retrieval quality?**
- Good enough, fast → Naive RAG
- Need accuracy → Advanced RAG (re-ranking + query rewriting)
- Retrieved docs might be wrong → Corrective RAG (CRAG)
- Model should self-evaluate → Self-RAG

**Step 4 — Constraints?**

| Constraint | Recommendation |
|---|---|
| Low latency | Naive RAG, Dense RAG |
| Fast prototype | Naive → Advanced RAG |
| Keyword + semantic both matter | Hybrid RAG |
| High accuracy, production | Advanced or Modular RAG |
| Complex autonomous tasks | Agentic RAG |

### Evolution Path (90% of use cases follow this)

```
Naive RAG  →  Hybrid RAG  →  Advanced RAG  →  Agentic RAG
(prototype)   (better recall) (better precision) (complex tasks)
```

> Start simple. Measure where it fails. Add complexity only where needed.

---

## 6. RAG — Advanced & Experimental Variants

### Known & Production-Viable Variants

#### Hybrid Multilingual RAG
RAG across multiple languages using cross-lingual embeddings (mBERT, LaBSE). Query in one language retrieves docs in another. **In active use.**

#### HiRAG / HiFi-RAG
Hierarchical RAG — chunks at multiple granularity levels (sentence → paragraph → section), retrieves at the appropriate level. HiFi = high-fidelity, minimal noise retrieval.

#### Bidirectional RAG
Forward retrieval (query → docs) + backward verification (docs → does this support the answer?). Used for answer verification.

#### Graph-RAG / Graph-01
Microsoft's GraphRAG — community-based knowledge graph retrieval. Graph-01 = specific variant using graph traversal for multi-hop reasoning.

#### Mega-RAG
Scaling RAG to millions of docs using ANN indexes (FAISS, ScaNN). For large-scale corpora.

---

### Research / Emerging Variants

#### Classic RAG (Baseline)
```
User Query → Vector Embedding → Similarity Search → Top-K Docs → LLM
```
Use cases: Enterprise QA, knowledge base chat, documentation search.

---

#### Mindscape-Aware RAG
**Focus:** Personalized retrieval using user mental models and long-term context.

Retrieval adapts based on: user history, behavioral patterns, goals, skill level, emotional tone.
```
User Query → User State Model (Profile + Memory) → Adaptive Retrieval → LLM
```
Use cases: AI tutors, personalized assistants, advisory AI. **Maturity: Research**

---

#### Hypergraph Memory RAG
**Focus:** Multi-entity relational retrieval using hypergraphs.

- Graph: Node → Edge → Node (pairwise)
- Hypergraph: One relation connects **multiple nodes simultaneously**

```
Documents → Entity Extraction → Hypergraph Construction → Query Traversal → Relevant Subgraph → LLM
```
Use cases: Multi-hop reasoning, surveillance intelligence, complex BI. **Maturity: Advanced but implementable**

---

#### QuCo-RAG (Query-Context Optimization RAG)
**Focus:** Intelligent query rewriting + context compression.
```
User Query → Query Rewriter (LLM) → Multi-Step Retrieval → Context Reranking/Compression → LLM
```
Benefits: Better long-document QA, reduced hallucination, improved precision. **Maturity: Production-ready**

---

#### Affordance RAG
**Focus:** Retrieve not just knowledge but actionable capabilities — combines knowledge retrieval + tool selection + API invocation.
```
User Intent → Retrieve Knowledge → Retrieve Available Tools → LLM + Tool Execution
```
Use cases: DevOps copilots, AI workflow agents, autonomous assistants. **Maturity: Production-ready (with tool calling)**

---

#### SignRAG
**Focus:** Retrieval for sign-language and gesture-based systems.
```
Sign Video → Pose + Gesture Encoder → Embedding Search → Retrieve Similar Sequences → Multimodal LLM
```
Use cases: Accessibility systems, real-time sign translation. **Maturity: Research**

---

#### TV-RAG (Temporal-Visual RAG)
**Focus:** Time-aware video retrieval — retrieve video segments instead of static docs.
```
Video Input → Frame Sampling + Temporal Encoding → Segment Embeddings → Similarity Search → LLM
```
Use cases: CCTV analysis, forensic search, sports analytics. **Maturity: Emerging**

---

#### RAGPart (Partial Context RAG)
**Focus:** Pass only the most relevant parts of retrieved documents to reduce token cost.
```
Retrieve Documents → Fine-Grained Chunk Scoring → Select High-Importance Segments → LLM
```
Benefits: Lower token cost, faster inference, better signal-to-noise. **Maturity: Production-ready**

---

#### RAGMask
**Focus:** Token-level masking of irrelevant content instead of trimming chunks.
```
Original:      Full paragraph
After Masking: Important sections visible, rest masked → LLM
```
Benefits: Better attention control, reduced distraction. **Maturity: Research (requires model-level integration)**

---

### Evolution Overview

| Variant | Focus | Maturity |
|---------|-------|----------|
| Classic RAG | Vector similarity | Production |
| Hybrid Multilingual RAG | Cross-language retrieval | Production |
| HiRAG / HiFi-RAG | Hierarchical granularity | Production |
| Bidirectional RAG | Answer verification | Production |
| Graph-RAG | Entity/relationship retrieval | Production |
| QuCo-RAG | Query optimization | Production |
| Affordance RAG | Tool + knowledge retrieval | Production |
| RAGPart | Context efficiency | Production |
| Mindscape-Aware RAG | Personalization | Advanced |
| Hypergraph Memory RAG | Multi-entity reasoning | Advanced |
| TV-RAG | Video + temporal | Emerging |
| SignRAG | Gesture retrieval | Research |
| RAGMask | Token-level filtering | Research |

### Key Insight

> Most advanced RAG systems in 2026 combine: **Hybrid Retrieval** + **Query Rewriting** + **Context Compression** + **Tool-Augmented Agents** + **Multimodal Embeddings**.
> The real advantage isn't the name — it's combining the right retrieval strategy for the domain.

---

## 7. Retrieval Methods

Retrieval is the core of any RAG system. The method determines what gets found, how fast, and how accurate the context fed to the LLM is.

---

### 1. Dense Retrieval (Vector Search)

**How it works:** Documents and queries are encoded into dense vectors using an embedding model. Retrieval is done via cosine similarity or dot product between the query vector and stored document vectors.

**Pipeline:**
```
Query
  ↓
Embedding Model (e.g., text-embedding-ada-002, BGE, E5)
  ↓
Query Vector
  ↓
Approximate Nearest Neighbor Search (ANN)
  ↓
Top-K Most Similar Chunks
```

**Index Types:**
| Index | Algorithm | Trade-off |
|---|---|---|
| FAISS Flat | Exact brute-force | Slowest, most accurate |
| FAISS IVF | Inverted file index | Fast, slight accuracy drop |
| HNSW | Hierarchical Navigable Small World | Very fast, high recall |
| ScaNN | Google's ANN | Best for large-scale |

**Best for:** Semantic similarity, paraphrase matching, conceptual queries
**Weakness:** Poor on exact keyword matches (e.g., product codes, IDs, names)

---

### 2. Sparse Retrieval (Keyword Search)

**How it works:** Documents are indexed using term frequency statistics. Retrieval scores documents based on term overlap between query and document.

**Algorithms:**
| Algorithm | Description |
|---|---|
| **BM25** | Best Match 25 — gold standard sparse retriever; scores by TF-IDF with length normalization |
| **TF-IDF** | Term Frequency–Inverse Document Frequency; classic IR baseline |
| **SPLADE** | Sparse Learned Encoder; learned sparse representations via transformer |
| **BM25+** | BM25 variant with lower-bounded term frequency weighting |

**Pipeline:**
```
Query
  ↓
Tokenize + Stem / Lemmatize
  ↓
Term Matching against Inverted Index
  ↓
BM25 Score per Document
  ↓
Top-K Documents
```

**Best for:** Exact keyword matches, named entities, product codes, rare terms
**Weakness:** Misses semantic synonyms (e.g., "car" vs "automobile")

---

### 3. Hybrid Retrieval (Dense + Sparse)

**How it works:** Runs both dense and sparse retrieval independently, then merges results using a fusion algorithm.

**Fusion Methods:**

**Reciprocal Rank Fusion (RRF)** — Most common:
```
RRF Score = Σ 1 / (k + rank_i)
```
Each document's rank from each retriever is combined. `k` is typically 60.

**Linear Score Fusion:**
```
Final Score = α × Dense Score + (1 - α) × Sparse Score
```
`α` is tuned based on domain (typically 0.5–0.7 for semantic-heavy domains).

**Pipeline:**
```
Query
  ├── Dense Retriever → Top-K₁ with scores
  └── Sparse Retriever → Top-K₂ with scores
             ↓
        Fusion (RRF or Linear)
             ↓
        Re-ranked Merged List
             ↓
        Top-K Final Results
```

**Best for:** Production RAG — captures both semantic and exact match signals
**Tools:** LangChain `EnsembleRetriever`, Weaviate hybrid search, Elasticsearch hybrid

---

### 4. Re-Ranking (Post-Retrieval)

**How it works:** After initial retrieval (dense/sparse/hybrid), a cross-encoder re-ranks the top-K results by scoring each (query, chunk) pair jointly.

**Bi-encoder vs Cross-encoder:**
| | Bi-Encoder | Cross-Encoder |
|---|---|---|
| Input | Query & doc separately | Query + doc together |
| Speed | Fast (pre-computed) | Slow (runtime) |
| Accuracy | Good | Superior |
| Use | Initial retrieval | Re-ranking top-K |

**Pipeline:**
```
Initial Top-K Chunks (from any retriever)
  ↓
Cross-Encoder: score(query, chunk_i) for each i
  ↓
Re-sorted by cross-encoder score
  ↓
Top-N passed to LLM (N < K)
```

**Models:** `cross-encoder/ms-marco-MiniLM-L-6-v2`, `Cohere Rerank`, `BGE-Reranker`

**Best for:** Any production RAG where precision matters more than latency

---

### 5. Multi-Vector Retrieval

**How it works:** Each document is represented by multiple vectors (e.g., summary vector + chunk vectors). Query is matched against all vectors; the parent document is retrieved.

**Variants:**
- **Parent-Child Retrieval** — Embed small chunks, retrieve full parent document
- **Hypothetical Document Embeddings (HyDE)** — LLM generates a hypothetical answer → embed it → use it to retrieve real docs
- **Summary + Chunk** — Store both a summary embedding and per-chunk embeddings per document

**HyDE Pipeline:**
```
Query: "What is the return policy?"
  ↓
LLM generates hypothetical answer:
  "The return policy allows 30 days..."
  ↓
Embed hypothetical answer
  ↓
Retrieve actual docs via similarity to hypothetical embedding
  ↓
LLM answers using retrieved real docs
```

**Best for:** Short queries that don't embed well; technical domains with jargon

---

### 6. Graph-Based Retrieval

**How it works:** Documents are parsed into entities and relationships, stored as a knowledge graph. Retrieval traverses edges to find multi-hop relevant nodes.

**Pipeline:**
```
Query
  ↓
Entity Extraction (NER)
  ↓
Graph Lookup (start nodes)
  ↓
Traversal (1-hop, 2-hop, N-hop)
  ↓
Subgraph → Serialized to text
  ↓
LLM
```

**Retrieval Strategies:**
| Strategy | Description |
|---|---|
| **Entity-centric** | Start from named entity, expand neighbors |
| **Relation-centric** | Find paths between two entities |
| **Community-based** | GraphRAG clusters nodes; retrieve by community summary |
| **Cypher/SPARQL query** | Natural language → graph query language |

**Best for:** Entities with rich relationships (org charts, knowledge bases, legal docs, biomedical)

---

### 7. Contextual Compression Retrieval

**How it works:** Retrieved chunks are compressed/filtered before passing to LLM — only the most relevant sentences within each chunk are kept.

**Pipeline:**
```
Query
  ↓
Retrieve Top-K Chunks
  ↓
Compressor (LLM or extractive model)
  → Extracts only relevant sentences per chunk
  ↓
Compressed context passed to LLM
```

**Compressor Types:**
- **LLMChainExtractor** — LLM extracts relevant parts (high quality, slower)
- **EmbeddingsFilter** — Filters sentences by embedding similarity to query (fast)
- **DocumentCompressorPipeline** — Chains multiple compressors

**Best for:** Long documents where chunks still contain much irrelevant text

---

### 8. Time-Aware / Temporal Retrieval

**How it works:** Retrieval incorporates document timestamps as a signal — penalizes or prioritizes based on recency.

**Scoring:**
```
Final Score = Relevance Score × Decay(time)
Decay = e^(-λ × age_in_days)
```

**Variants:**
- **Recency-biased** — Prefer newer documents
- **Epoch-scoped** — Only retrieve docs within a time window
- **Versioned retrieval** — Retrieve docs as of a specific date

**Best for:** News, legal docs, product changelogs, financial reports

---

### 9. Metadata-Filtered Retrieval

**How it works:** Vector search is augmented with structured metadata filters applied pre- or post-retrieval.

**Example:**
```python
retriever.get_relevant_documents(
    query="leave policy",
    filter={"department": "HR", "year": 2024}
)
```

**Filter Application Modes:**
| Mode | How | Trade-off |
|---|---|---|
| **Pre-filter** | Filter first, then vector search within subset | Faster, may miss results |
| **Post-filter** | Vector search first, filter results | Better recall, slower |
| **Hybrid filter** | ANN with metadata constraints simultaneously | Best, requires vector DB support |

**Supported by:** Pinecone, Weaviate, Qdrant, Chroma, Milvus

**Best for:** Multi-tenant RAG, department-scoped retrieval, date-restricted search

---

### 10. Self-Query Retrieval

**How it works:** LLM parses the natural language query into a structured query with both a semantic component and metadata filters automatically.

**Pipeline:**
```
Query: "Find HR policies updated after 2023 about remote work"
  ↓
LLM Self-Query Parser
  ↓
Semantic: "remote work policy"
Filter: {category: "HR", updated_after: "2023-01-01"}
  ↓
Vector DB query with both components
```

**Best for:** User-facing search interfaces where users write natural language but data has rich metadata

---

### 11. Ensemble / Multi-Retriever

**How it works:** Multiple distinct retrievers (different embedding models, different indexes, different sources) run in parallel; results are merged.

```
Query
  ├── Retriever A (Dense, local docs)
  ├── Retriever B (BM25, policy index)
  └── Retriever C (Graph, entity store)
         ↓
    Merge + Deduplicate + Rank
         ↓
    Final context for LLM
```

**Best for:** Agentic RAG where the agent routes across multiple knowledge sources

---

### 12. Front-Matter Injection

**How it works:** Certain chunks — typically the document's title page, copyright page, or metadata header — are **always injected** into the LLM context at query time, regardless of their retrieval score. They bypass the similarity search entirely.

**Why it matters:** Retrieval is score-based, so the front matter of a document (author, title, year, ISBN) often scores low for most queries — but its absence causes the LLM to hallucinate wrong metadata. Front-matter injection pins this grounding context into every answer.

**Pipeline:**
```
Query
  ↓
Similarity Search → Top-K chunks (scored)
  +
Front-matter chunk (always included, score-independent)
  ↓
Combined context → LLM
```

**Real example (from simple-rag project):**
```
[FRONT MATTER]
Title: "Deep Learning" | Authors: Goodfellow, Bengio, Courville | Year: 2016

[RETRIEVED CHUNK 1] ...backpropagation is used to compute gradients...
[RETRIEVED CHUNK 2] ...regularization techniques such as dropout...
```
The `[FRONT MATTER]` tag tells the LLM: *trust this for author/year over anything else in the chunks.*

**Variations:**
| Variant | What's injected | When to use |
|---------|----------------|-------------|
| **Title/copyright page** | Author, year, publisher | Books, reports, academic papers |
| **Document header** | Filename, upload date, version | Internal docs, policies |
| **System metadata** | User role, department, date | Multi-tenant RAG, RBAC-scoped retrieval |
| **Publication year annotation** | Extracted year, labelled explicitly | Prevents LoC/control number confusion |

**Best for:** Any document-based RAG where metadata accuracy matters (citations, policies, legal docs, research papers)

**Relationship to other methods:** Front-matter injection is a lightweight complement to **Metadata-Filtered Retrieval** — instead of filtering by metadata, you always include it. Often combined with a **metadata-aware prompt** that explicitly instructs the LLM to prioritise the injected front matter over inline text.

---

### Retrieval Method Comparison

| Method | Semantic Match | Exact Match | Speed | Complexity | Best Use |
|---|---|---|---|---|---|
| Dense (Vector) | ✅ Excellent | ❌ Poor | Fast | Low | General QA |
| Sparse (BM25) | ❌ Poor | ✅ Excellent | Very Fast | Low | Keyword search |
| Hybrid | ✅ Good | ✅ Good | Medium | Medium | Production default |
| Re-ranking | ✅ Excellent | ✅ Good | Slow | Medium | High-accuracy |
| Graph | ✅ Good | ✅ Good | Medium | High | Multi-hop reasoning |
| HyDE / Multi-vector | ✅ Excellent | ❌ Poor | Medium | High | Short/ambiguous queries |
| Contextual Compression | ✅ Excellent | ✅ Good | Slow | Medium | Long documents |
| Metadata Filtered | ✅ Good | ✅ Good | Fast | Low | Scoped retrieval |
| Front-Matter Injection | ➖ N/A | ✅ Exact | Zero overhead | Very Low | Metadata-critical docs |

---

## 8. Chunking & Chunk Overlap Strategies

Chunking determines how documents are split before embedding. Overlap controls how much context bleeds between adjacent chunks to prevent losing context at boundaries.

---

### Why Overlap Matters

Without overlap, a sentence split across two chunk boundaries loses its context in both:
```
Chunk 1: "The employee is entitled to 20 days annual leave."
Chunk 2: "This does not include sick leave or public holidays."

Query: "How many total leave days including sick leave?"
→ Neither chunk alone answers correctly.
```

With overlap, the boundary region appears in both chunks:
```
Chunk 1: "...entitled to 20 days annual leave. This does not include sick leave..."
Chunk 2: "...annual leave. This does not include sick leave or public holidays."
→ Both chunks now carry the complete context.
```

---

### 1. Fixed-Size Overlap (Token / Character)

**How it works:** Split document into chunks of fixed size `N` tokens/characters. Each chunk overlaps with the previous by `O` tokens.

```
Document: [T1 T2 T3 T4 T5 T6 T7 T8 T9 T10]
Chunk size = 5, Overlap = 2

Chunk 1: [T1 T2 T3 T4 T5]
Chunk 2:          [T4 T5 T6 T7 T8]
Chunk 3:                   [T7 T8 T9 T10]
```

**Parameters:**
| Parameter | Typical Range | Effect |
|---|---|---|
| `chunk_size` | 256–1024 tokens | Larger = more context, less precision |
| `chunk_overlap` | 10–20% of chunk_size | Higher = better boundary coverage, more storage |

**Code (LangChain):**
```python
from langchain.text_splitter import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(
    chunk_size=512,
    chunk_overlap=64
)
```

**Best for:** General-purpose documents, fast prototyping
**Weakness:** Ignores sentence/paragraph structure; may split mid-sentence

---

### 2. Sentence-Level Overlap

**How it works:** Split by sentence boundaries (using NLP sentence tokenizer). Overlap is measured in sentences, not tokens.

```
S1. "The policy applies to all full-time employees."
S2. "Part-time employees are covered under Schedule B."
S3. "Contract workers are excluded."
S4. "All claims must be filed within 30 days."

Chunk size = 2 sentences, Overlap = 1 sentence:
Chunk 1: [S1, S2]
Chunk 2: [S2, S3]   ← S2 repeated
Chunk 3: [S3, S4]   ← S3 repeated
```

**Tools:** spaCy `sentencizer`, NLTK `sent_tokenize`, `spacy-sentence-bert`

**Best for:** QA over structured documents (policies, contracts, reports)
**Weakness:** Sentence tokenizers can fail on bullet points, abbreviations, enumerations

---

### 3. Paragraph-Level Overlap

**How it works:** Split on paragraph boundaries (`\n\n`). Overlap includes the last paragraph of the previous chunk.

```
Paragraph A: "Introduction to leave policy..."
Paragraph B: "Types of leave available..."
Paragraph C: "Eligibility criteria..."

Chunk 1: [Para A + Para B]
Chunk 2: [Para B + Para C]  ← Para B repeated
```

**Best for:** Long-form documents where paragraphs are self-contained units (legal docs, SOWs, manuals)
**Weakness:** Paragraph length varies wildly; some chunks may exceed token limits

---

### 4. Sliding Window Overlap

**How it works:** A fixed window slides across the document with a step size smaller than the window. Every position in the document appears in multiple chunks.

```
Window size = 4, Step = 2:
Window 1: [T1 T2 T3 T4]
Window 2: [T3 T4 T5 T6]
Window 3: [T5 T6 T7 T8]
```

**Coverage guarantee:** Every token appears in `window_size / step` chunks.

**Best for:** Dense technical documents where any sentence might be critical
**Weakness:** High redundancy → large index, slower retrieval

---

### 5. Semantic Chunking (No Fixed Overlap)

**How it works:** Instead of fixed boundaries, detect semantic breakpoints where topic shifts occur. Split at natural topic transitions.

**Algorithm:**
```
1. Embed each sentence
2. Compute cosine similarity between consecutive sentences
3. Detect drops in similarity → breakpoint
4. Split at breakpoints
```

```
Similarity: [0.92, 0.89, 0.91, 0.43←breakpoint, 0.88, 0.87]
                                    ↑
                             Split here
```

**Parameters:**
- `breakpoint_threshold_type`: `percentile`, `standard_deviation`, `interquartile`
- `breakpoint_threshold_amount`: e.g., 95th percentile of similarity drops

**Code (LangChain):**
```python
from langchain_experimental.text_splitter import SemanticChunker
from langchain_openai.embeddings import OpenAIEmbeddings

splitter = SemanticChunker(
    OpenAIEmbeddings(),
    breakpoint_threshold_type="percentile"
)
```

**Best for:** Mixed-topic documents; produces cleaner, more topically coherent chunks
**Weakness:** Slower (requires embedding every sentence); no guaranteed chunk size

---

### 6. Recursive Character Text Splitting (Hierarchical Overlap)

**How it works:** Tries to split on a priority list of separators: `["\n\n", "\n", ". ", " ", ""]`. Falls back to the next separator only if the chunk exceeds the size limit.

```
Priority: ["\n\n" → "\n" → ". " → " " → ""]

Try split on "\n\n" → chunks still too large?
  → Try split on "\n"
    → Still too large?
      → Try split on ". "
        → Still too large?
          → Split on " " (word boundary)
```

**Best for:** General-purpose default — respects natural text structure as much as possible
**This is the LangChain default splitter**

---

### 7. Parent-Child Chunking (Hierarchical Retrieval)

**How it works:** Two chunk sizes are created — small child chunks for precise retrieval and large parent chunks for full context. Query matches against child chunks; the parent is returned to the LLM.

```
Parent Chunk (512 tokens):
  "Leave policy section covering annual leave,
   sick leave, and emergency leave provisions..."

Child Chunks (128 tokens each):
  Child 1: "Annual leave: 20 days per year..."
  Child 2: "Sick leave: up to 10 days..."
  Child 3: "Emergency leave: 3 days..."

Query: "How many sick days?"
→ Matches Child 2
→ Returns Parent (full 512-token context) to LLM
```

**Storage:** Child embeddings in vector DB; parent chunks in a document store (key-value)

**Best for:** Precise retrieval without sacrificing full context
**Tools:** LangChain `ParentDocumentRetriever`

---

### 8. Overlap by Document Structure (Structural Chunking)

**How it works:** Use the document's native structure (headings, sections, chapters) as chunk boundaries. Overlap includes the section heading in every child chunk.

```
# Section 3: Leave Policy          ← Always included in child chunks
## 3.1 Annual Leave
  Content about annual leave...

## 3.2 Sick Leave
  Content about sick leave...
```

Each chunk carries the breadcrumb path:
```
Chunk: "Section 3: Leave Policy > 3.2 Sick Leave: Content..."
```

**Best for:** Markdown docs, PDFs with clear heading hierarchy, SOWs, technical manuals
**Tools:** `MarkdownHeaderTextSplitter`, `HTMLHeaderTextSplitter` (LangChain)

---

### 9. Token-Aware Overlap (Model-Specific)

**How it works:** Chunk boundaries are calculated in tokens (not characters) to respect the embedding model's max input length. Overlap is also in tokens.

```
Model max tokens: 512
Chunk size: 400 tokens
Overlap: 50 tokens
→ Each chunk fits within model limit with 50-token boundary buffer
```

**Important:** Character-based chunking can inadvertently exceed model token limits since 1 character ≠ 1 token. Token-aware splitting prevents embedding truncation.

**Tools:** `tiktoken` (OpenAI), `transformers AutoTokenizer`

```python
from langchain.text_splitter import TokenTextSplitter

splitter = TokenTextSplitter(
    chunk_size=400,
    chunk_overlap=50
)
```

---

### Chunk Size & Overlap Decision Guide

| Document Type | Chunk Size | Overlap | Strategy |
|---|---|---|---|
| Short QA / FAQs | 128–256 tokens | 20–30 tokens | Fixed-size or sentence |
| Policy / Legal docs | 512–1024 tokens | 64–128 tokens | Paragraph or structural |
| Technical manuals | 512 tokens | 64 tokens | Recursive + structural |
| Code | Function-level | None (use AST) | Code splitter |
| Mixed-topic articles | Variable | N/A | Semantic chunking |
| Long reports / SOWs | Parent-child | N/A | Hierarchical |
| Real-time streams | Small, sliding | 25–50% | Sliding window |

---

### Overlap Size Trade-offs

| Overlap | Pros | Cons |
|---|---|---|
| **0% (no overlap)** | Smallest index, fastest | Loses context at boundaries |
| **10–15%** | Balanced; covers most boundary cases | Slight redundancy |
| **20–25%** | Good for dense, interconnected text | Larger index |
| **50%+** | Maximum boundary coverage | 2× storage, high redundancy |
| **Semantic (variable)** | No arbitrary cutoffs | Unpredictable chunk sizes |

---

### Full Pipeline: Chunking → Retrieval → Generation

```
Raw Document
    ↓
[Chunking Strategy]
  ├── Structural (headings/sections)
  ├── Semantic (topic-aware)
  └── Fixed-size with overlap
    ↓
[Embedding]
  └── Model: BGE / E5 / Ada-002 / Local
    ↓
[Index]
  ├── Dense: FAISS / HNSW / Pinecone
  └── Sparse: BM25 / Elasticsearch
    ↓
[Retrieval]
  ├── Hybrid (Dense + Sparse)
  ├── Metadata-filtered
  └── Parent-child lookup
    ↓
[Post-Retrieval]
  ├── Re-ranking (Cross-encoder)
  └── Contextual compression
    ↓
[LLM Generation]
```

---

*Last updated: February 2026 — Notes are live and growing.*
