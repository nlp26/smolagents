# smolagents

Notebook exercising Hugging Face `smolagents` — picking up which agent shape and which tools fit which use case. Single notebook, four progressive experiments.

## What's inside

`smolagents.ipynb`, top to bottom:

1. **Bare `CodeAgent`** — no tools, single LLM call wrapped as an agent. Solves a Fibonacci question end-to-end to confirm the harness works.
2. **`CodeAgent` + `DuckDuckGoSearchTool`** — adds search. First place the agent earns its keep.
3. **Multi-tool `CodeAgent`** — `DuckDuckGoSearchTool` + `VisitWebpageTool` + `PythonInterpreterTool`. Web search plus the ability to read pages and run code.
4. **PDF RAG `CodeAgent`** — custom `Tool` wrapping FAISS + Sentence Transformers + `pypdf`. The agent answers from a local PDF instead of the web.

All four use `meta-llama/Llama-3.3-70B-Instruct` via `InferenceClientModel`. Set `HF_TOKEN` in the env before running.

## Takeaway

`CodeAgent` is the workhorse. Tools are plain Python callables registered with the agent — no schema gymnastics. Going from "no tools" to "RAG over a PDF" is four cells of incremental change.

## Run

```bash
pip install smolagents sentence-transformers faiss-cpu pypdf
export HF_TOKEN=...
jupyter notebook smolagents.ipynb
```

## License

Apache-2.0
