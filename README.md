# LangChain and Vector Databases in Production — Course Notebooks

Hands-on notebooks for learning LangChain and production-oriented LLM workflows. This repo favors a private, local-first setup using Ollama with the `qwen3:4b` model — no OpenAI API keys required.

## What's Inside

- Module 01: Foundations and guided walkthroughs.
  - Notebooks: see [LLM-Systems-full/Module-01 - LangChain 101 Zero to Hero/LangChain_Complete_Guide.ipynb](LLM-Systems-full/Module-01%20-%20LangChain%20101%20Zero%20to%20Hero/LangChain_Complete_Guide.ipynb)
- Module 02: LLMs and LangChain with Ollama (local models).
  - Notebooks:
    - [LLM-Systems-full/Module-02 - LLMs and LangChain/Intro_to_LLMs.ipynb](LLM-Systems-full/Module-02%20-%20LLMs%20and%20LangChain/Intro_to_LLMs.ipynb)
    - [LLM-Systems-full/Module-02 - LLMs and LangChain/Understanding_Tokens.ipynb](LLM-Systems-full/Module-02%20-%20LLMs%20and%20LangChain/Understanding_Tokens.ipynb)

Key topics covered:
- LLM basics, prompting, and chaining with LangChain
- Chunking strategies (character and recursive) and classic split-process-combine
- Practical QA patterns (single/multi-question, batch processing)
- Tokenization concepts and demos (Hugging Face tokenizers), token budgeting

## Prerequisites

- Python 3.10+
- Git
- Jupyter (Notebook or Lab)
- Ollama installed and running locally: https://ollama.com
- Model pulled locally (consistent with notebooks):

```powershell
ollama pull qwen3:4b
```

> If you prefer a different local model, set `OLLAMA_MODEL` in `.env` and adjust the notebooks accordingly.

## Quick Start

1) Clone the repo

```powershell
git clone https://github.com/williskipsjr/LangChain-and-Vector-DB.git
cd "LangChain & Vector Databases in Production"
```

2) Create a virtual environment and install deps

```powershell
# Windows (PowerShell)
python -m venv .venv
. .venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt
```

3) Configure environment variables

```powershell
# Copy the example and edit locally as needed
Copy-Item .env.example .env
```

Environment variables used by the notebooks:

- OLLAMA_BASE_URL: default `http://localhost:11434`
- OLLAMA_MODEL: default `qwen3:4b`
- LANGCHAIN_TRACING_V2, LANGCHAIN_ENDPOINT, LANGCHAIN_API_KEY: optional if you enable LangSmith/telemetry
- HF_TOKEN: optional for private models on Hugging Face (tokenizers in notebooks do not require this)

4) Launch Jupyter

```powershell
jupyter lab
# or
jupyter notebook
```

Open the notebooks under Module 01 and Module 02 and run cells top-to-bottom. Ensure Ollama is running before executing any LLM cells.

## Notes and Tips

- This repo avoids cloud keys by default. If you enable external providers, never commit secrets — `.env` is ignored; use `.env.example` to document variables.
- If you switch models, make sure to pull it with `ollama pull <model>` and update `OLLAMA_MODEL`.
- On Windows, large model downloads may take several minutes; keep the terminal open.

## Troubleshooting

- Push protection/secrets: GitHub may block pushes that include credentials. Remove the secret and amend/re-push.
- Jupyter kernels: If the Python kernel isn’t found, reactivate the venv and reinstall Jupyter.
- tiktoken wheels: If installation fails, upgrade pip (`python -m pip install -U pip`) and retry.

## Acknowledgements

- LangChain community packages
- Ollama for local model serving
- Hugging Face tokenizers for the token demos
