# Agentic Research Assistant

Notebook-based examples for building research and multi-agent workflows with [LangGraph](https://langchain-ai.github.io/langgraph/) and LangChain. The project progresses from small graph patterns to a research assistant that creates analyst personas, conducts tool-assisted interviews, and compiles a final report.

## Contents

| Notebook | What it demonstrates |
| --- | --- |
| [`sub-graph.ipynb`](sub-graph.ipynb) | Separate state and reusable subgraphs for failure analysis and question summarization. |
| [`map-reduce.ipynb`](map-reduce.ipynb) | LangGraph `Send` for fan-out map work and a reduce step that selects the best result. |
| [`parallelization.ipynb`](parallelization.ipynb) | Parallel branches, reducers, synchronization, deterministic state updates, and retrieval from Wikipedia and web search. |
| [`research-assistant.ipynb`](research-assistant.ipynb) | Human-in-the-loop analyst generation, multi-turn expert interviews, parallel research, and report compilation. |

The repository also includes [`sub-graph.png`](sub-graph.png), a graph visualization generated from the subgraph example.

## Setup

1. Clone the repository and open it in VS Code or JupyterLab.
2. Create and activate a Python environment.
3. Install the notebook dependencies:

   ```bash
   pip install jupyterlab python-dotenv pydantic langgraph langgraph-sdk langchain langchain-core langchain-openai langchain-community tavily-python
   ```

4. Create a `.env` file in the repository root:

   ```env
   OPENAI_API_KEY=your-openai-api-key
   TAVILY_API_KEY=your-tavily-api-key
   ```

The notebooks load environment variables with `python-dotenv`. Keep `.env` private and do not commit API keys.

## Running the notebooks

Open a notebook, select the configured Python kernel, and run the cells from top to bottom. A practical order is:

1. `sub-graph.ipynb` to understand parent and child graph state.
2. `map-reduce.ipynb` to learn dynamic fan-out with `Send`.
3. `parallelization.ipynb` to explore reducers and external research tools.
4. `research-assistant.ipynb` to run the complete analyst and report workflow.

The research assistant pauses for human feedback while generating analyst personas. Review the proposed analysts, update the feedback state when prompted, and resume the graph before the interviews and final report are generated.

## External services

- **OpenAI** provides the chat model used by the examples.
- **Tavily** provides web search results in the retrieval examples.
- **Wikipedia** is accessed through LangChain's `WikipediaLoader`.
- The final section of `parallelization.ipynb` demonstrates connecting to a local LangGraph API at `http://127.0.0.1:2024`; run a compatible LangGraph server separately if you want to execute that section.

## Notes

- These are educational notebooks, so intermediate graph state and sample outputs are intentionally visible.
- Model names and tool limits are defined inside the notebooks and can be adjusted for your environment and API access.
- No standalone application or API server is included in this repository.