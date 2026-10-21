# Awesome-RAG-Frameworks

## Top RAG Frameworks Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Retrieval Abstractions, Typed Pipelines & Production RAG Orchestration*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **RAG Frameworks**. These tools provide the orchestration layer between your data and an LLM — handling ingestion, indexing, retrieval, reranking, and generation as composable pipelines, so you can build grounded applications without wiring every component by hand.

**Examples** include Haystack, LlamaIndex, LangChain, LangGraph, RAGFlow, Kotaemon, Pathway, R2R, DSPy, and Verba (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, explicit component composition, and transparent retrieval logic — ideal for teams prioritizing reproducibility, avoiding framework lock-in, and building RAG systems they can debug and audit.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Vectara](https://www.vectara.com/)**  
  **API-first agentic RAG platform built for governed enterprise deployment.** Provides multi-modal retrieval, orchestration, and always-on governance with step-level audit trails, fine-grained access controls, and real-time policy enforcement. Deployment options include SaaS, VPC, on-premises, and air-gapped environments. SOC 2 Type II and HIPAA certified; never trains on customer data. Quickstart returns **numeric citations plus a factual consistency score** indicating how well the answer is grounded.

- **[deepset Studio](https://www.deepset.ai/)**  
  **Managed platform for Haystack pipelines with production infrastructure.** Built-in tracing for every deployed pipeline, zero-downtime deploys with auto-scaling replicas, built-in testing and analytics playground, plus dashboards for production monitoring. The commercial layer for teams wanting Haystack's pipeline model without operating the infrastructure [citation:7].

- **[Pinecone Nexus](https://www.pinecone.io/)**  
  **Retrieval-native RAG platform from the managed vector database leader.** Distills sources into curated artifacts — typed units like summaries, topics, entities, and events — that are pre-computed and easy to retrieve. At query time, the model writes Python against a retrieval SDK to read artifacts, run semantic and keyword search, and query structured tables. Only distilled evidence enters the prompt, keeping context small and every claim traceable.

- **[Weaviate Cloud](https://weaviate.io/)**  
  **Managed vector database with a turnkey RAG path.** Query Agent handles ingest, chunk, retrieve, and answer on Weaviate Cloud. For full control, use `col.query.hybrid(...)` to combine vector and BM25 retrieval with filters, then send results to any LLM. Free to start across the entire product suite as of June 2026.

## Open-Source GitHub Projects

- **[Haystack](https://github.com/deepset-ai/haystack)**  
  **The typed, explicit-component framework for production RAG** — Apache 2.0 licensed, **26,700+ GitHub stars** [citation:5]. **Pipelines are DAGs you wire yourself** — runs the same way every time, with strict type-checking, reproducibility, and Kubernetes-ready deployment [citation:9][citation:13]. **Components** (retrievers, embedders, generators, evaluators) connect to Document Stores including Qdrant, Pinecone, Weaviate, Elasticsearch, and pgvector. **Agents** hand step-by-step control to the LLM, trading predictability for flexibility [citation:13]. **Hayhooks** turns a Haystack pipeline into a self-hosted REST API (and optional MCP server) with one command. **Best for enterprise pipelines requiring auditable, type-safe execution** with low-to-medium deployment complexity [citation:9].

- **[LlamaIndex](https://github.com/run-llama/llama_index)**  
  **The purpose-built data framework for RAG** — **52,000+ GitHub stars** [citation:4][citation:5]. **160+ data connectors, document parsers, indexing strategies, and query engines** for connecting LLMs to external data. **Advanced retrieval patterns** including recursive retrieval, knowledge graphs, and multi-document agents. **High-level API gets to working RAG in five lines**; lower-level APIs customize any module. **Async-first design** makes concurrent retrieval clean; built-in faithfulness and relevancy evaluation. **The lowest learning curve and deployment complexity** among major frameworks [citation:9]. **Best for teams whose core problem is retrieval** — large document collections and accurate search.

- **[LangChain / LangGraph](https://github.com/langchain-ai/langchain)**  
  **The broadest ecosystem for rapid prototyping and stateful agents** — **147,000+ GitHub stars** [citation:5]. **LangChain** provides composable chains and 100+ integrations for quick experiments; **LangGraph** adds cyclic graphs for complex agentic workflows with human-in-the-loop control and persistence [citation:9][citation:13]. **LangSmith** provides excellent observability for production debugging. **Trade-offs**: **medium-to-high production readiness** for LangChain — abstraction overhead and breaking changes between versions; documentation split across three products [citation:9]. **Best for rapid prototyping and complex stateful agents** rather than pure retrieval pipelines.

- **[RAGFlow](https://github.com/infiniflow/ragflow)**  
  **The deep-document-understanding RAG engine** — **78,300+ GitHub stars**, Apache 2.0 licensed [citation:7]. **Layout-aware DeepDoc parsing** using YOLOv8-based layout detection to segment documents before OCR — preserves column/row coordinate mappings for tables and auto-rotates scanned tables based on OCR confidence [citation:3]. **Hybrid retrieval** (vector + BM25 + custom scoring + re-ranking) with **citation-backed answers pointing to source chunks** [citation:7]. **Visual agent workflow builder** with RAG, tools, and MCP. **April 2026 release** added prebuilt ingestion pipelines, sandbox code execution, and chart generation. **Trade-offs**: **heavier infrastructure** than minimal RAG libraries — full suite requires substantial hardware, making it poorly optimized for single-user consumer GPUs [citation:3][citation:7]. **Best for legal, healthcare, and technical document Q&A** where citation-grade answers and table extraction matter.

- **[Kotaemon](https://github.com/Cinnamon/kotaemon)**  
  **Local-first RAG UI with visual citations and multi-vector retrieval** — Apache 2.0 licensed. **Multi-vector/parent-child indexing**: small child chunks (100-200 tokens) for semantic mapping linked to larger parent sections (1000-2000 tokens) passed as context [citation:3]. **Visual citation feature** — clicking a citation opens a PDF page viewer with a highlighted bounding box on the text segment [citation:3]. **Gradio UI**, note-centric, supports GraphRAG. **Best for local-first document Q&A** with verifiable citations, though it relies heavily on Ollama and does not manage co-resident VRAM state — can OOM on 12 GB rigs when embedding, reranking, and generation run concurrently [citation:3].

- **[Pathway](https://github.com/pathwaycom/pathway)**  
  **High-performance data processing for "Always-Live" RAG** — Apache 2.0 licensed. **Syncs vector indices in real-time as the underlying data source changes**, without full re-indexing [citation:13]. **Best for RAG over continuously updating data** — live feeds, streaming documents, and changing knowledge bases.

- **[R2R](https://github.com/SciPhi-AI/R2R)**  
  **Production-ready agentic retrieval with REST API and knowledge graphs** — **8,000+ GitHub stars** [citation:5]. **Multimodal ingestion, hybrid search, and an automatic knowledge-graph pipeline** — designed to ship RAG-powered applications without building infrastructure from scratch [citation:13]. **Trade-off**: last push in November 2025 according to one source — verify maintenance activity before adopting [citation:5].

- **[DSPy](https://github.com/stanfordnlp/dspy)**  
  **Stanford's framework for programming — rather than prompting — language models.** Compose RAG pipelines from typed modules and let DSPy's optimizers automatically tune prompts and few-shot examples to meet a declared metric, **replacing brittle hand-crafted prompt chains with reproducible, optimizable programs** [citation:13].

- **[Verba](https://github.com/weaviate/Verba)**  
  **Weaviate's "Golden RAGtriever"** — a fully aesthetic, open-source RAG web application pre-configured with best practices for chunking, embedding, and retrieval out of the box [citation:13]. **Best for teams wanting a working RAG application immediately** with sensible defaults.

### Additional Strong Open-Source Options

- **Agentset** — Open-source production-ready RAG platform with built-in agentic reasoning, hybrid search, and multimodal support [citation:9].
- **Cognita** — Modular RAG framework by TrueFoundry that decouples Indexer, Retriever, and Parser for independent scaling and A/B testing [citation:9].
- **UltraRAG** — Low-code, MCP-based framework for composing complex RAG pipelines [citation:5].
- **AutoRAG** — Auto-optimizing RAG that searches modules and parameters against your own evaluation data [citation:5].
- **LightRAG** — Most active general-purpose GraphRAG library with incremental insert/delete and multiple storage backends [citation:11].

**Frameworks for building custom systems**: Combine **Haystack** for typed, auditable pipelines with predictable execution, **LlamaIndex** for purpose-built retrieval with the lowest learning curve, **RAGFlow** for citation-grade document understanding with table extraction, **Kotaemon** for local-first visual citations, **Pathway** for always-live RAG over streaming data, and **DSPy** for optimizable, metric-driven pipelines — to build a RAG framework stack tailored to your document complexity, deployment constraints, and debugging requirements.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- RAG frameworks differ significantly in abstraction level, pipeline determinism, and deployment complexity. **Haystack pipelines are deterministic DAGs** that run the same way every time; **agents trade predictability for handling unenumerated requests** [citation:13]. **RAGFlow has the best document parsing in the OSS RAG space** but requires heavier infrastructure than minimal libraries [citation:7]. **Kotaemon can OOM on 12 GB GPUs** when embedding, reranking, and generation run concurrently — it does not actively manage co-resident VRAM state [citation:3]. **R2R's last push was November 2025** according to one source — verify maintenance before adopting [citation:5]. **LangChain has medium-to-high production readiness** with abstraction overhead and breaking changes between versions [citation:9].
- Self-hosted open-source solutions require proper vector database selection, embedding model configuration, and retrieval quality evaluation against your specific documents and query patterns.

---

**Made for AI engineers, RAG developers, and teams building grounded LLM applications over private data.**
Let's make RAG frameworks more open, retrieval-accurate, and production-ready.
