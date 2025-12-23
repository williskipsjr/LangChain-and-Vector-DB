# Module-01: LangChain 101 — LangChain and Vector Databases in Production

This module is a modernized, runnable notebook and guide based on the ActiveLoop course materials from ~3 years ago. Since LangChain has evolved significantly, the examples here use the current LCEL (LangChain Expression Language) instead of deprecated chain classes and modules.

## What Changed (Modernization Summary)
- Replaced deprecated imports (e.g., `langchain.prompts`, `langchain.chains`, `langchain.callbacks`) with stable `langchain_core.*` APIs.
- Adopted LCEL pipelines using the `|` operator instead of `LLMChain`, `ConversationChain`, `SequentialChain`, etc.
- Updated memory to `RunnableWithMessageHistory` + `InMemoryChatMessageHistory`.
- Switched DeepLake usage to local dataset paths to avoid hub entity issues; kept an option to use the hub if desired.
- Fixed text splitter and document imports (`langchain_text_splitters`, `langchain_core.documents`).
- Configured semantic search to use an embedding-capable Ollama model (`nomic-embed-text`).
- Continued using Ollama with the local `qwen3:4b` LLM for generation.

## Folder Structure
```
Module-01 - LangChain 101 — LangChain and Vector Databases in Production/
  README.md
  LangChain_Complete_Guide.ipynb
```

The notebook covers:
1. Environment setup
2. LLM via Ollama (`qwen3:4b`)
3. Prompt templates
4. LCEL chains
5. Conversation memory
6. Advanced memory concepts
7. Vector DB (DeepLake) + embeddings
8. Semantic search
9. RAG pipeline
10. Sequential chains
11. Output parsing
12. Summary & best practices

## Prerequisites
- Python 3.11+ (tested with 3.13)
- VS Code with Jupyter extension
- Ollama installed and running locally
- DeepLake account/token (optional, only if using hub path)

## Quick Start
1. Create/activate a virtual environment.
2. Install dependencies:
```
pip install -q langchain langchain-community deeplake python-dotenv requests openai langchain-text-splitters
```
3. Pull required Ollama models:
```
ollama pull qwen2:4b  # or qwen3:4b if available
ollama pull nomic-embed-text
ollama serve
```
4. Open the notebook `LangChain_Complete_Guide.ipynb` in VS Code and select the correct Python kernel.
5. Run cells in order. Ensure the `.env` is accessible (ACTIVELOOP_TOKEN, GOOGLE_API_KEY as needed).

## Configuration Notes
- `.env` is loaded explicitly in the notebook; keep your secrets there.
- For DeepLake:
  - Local dataset path: `./deeplake_langchain_demo` (auto-created when adding documents)
  - To use hub: set `dataset_path = "hub://<org>/<dataset>"` and ensure `ACTIVELOOP_TOKEN` is set.
- Embeddings:
  - Use `nomic-embed-text` for embeddings, as some LLMs (e.g., `qwen3:4b`) do not provide embedding endpoints.

## Why LCEL?
LCEL provides composable, declarative chains that are easier to maintain and reason about. It aligns with the latest LangChain design and avoids deprecated class-based chains.

## .gitignore
A workspace-level `.gitignore` excludes virtual environments, `.env`, notebook checkpoints, and local DeepLake datasets so you don't leak secrets or bulky artifacts.

## Contributing / Extending
- Add Agent examples (tool use, planning)
- Swap vector store to other providers (FAISS, Chroma, etc.)
- Try streaming outputs and structured parsing (JSON Schema)

## License
This module adapts educational content for modern LangChain usage. No original course content is included; only runnable code and explanations.
