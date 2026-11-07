# LangChain and LangGraph Practice

A collection of Jupyter notebooks exploring LangChain, LangGraph, Anthropic's Claude models, tool calling, and multi-agent patterns. These are learning examples; each notebook is run independently.

## Notebooks

| Notebook | What it demonstrates |
| --- | --- |
| [`langchain_api.ipynb`](./langchain_api.ipynb) | Configure `ChatAnthropic`, send a prompt, and stream a response. |
| [`custom_workflows_with_langchain_langgraph.ipynb`](./custom_workflows_with_langchain_langgraph.ipynb) | Build a vacation-planning workflow with LangGraph. It chooses a location, researches destinations, weather, and cuisine in parallel, then produces an itinerary. |
| [`mcp_tool_with_langchain.ipynb`](./mcp_tool_with_langchain.ipynb) | Bind a weather API function as a LangChain tool, then connect Claude to the Microsoft Learn MCP server to retrieve documentation. |
| [`subagents_with_langchain.ipynb`](./subagents_with_langchain.ipynb) | Create a web-search research subagent and a marketing-content subagent, then delegate to them through a supervisor agent. |

The workflow notebook includes a diagram of the vacation-planning graph in [`Images/`](./Images/).

## Setup

Use Python with Jupyter Notebook or JupyterLab. From the project directory, install the packages used across the examples:

```bash
python -m pip install jupyter langchain langchain-anthropic langgraph python-dotenv requests
```

Create a `.env` file in the project directory with your Anthropic API key and the Claude model identifier you want to use:

```dotenv
ANTHROPIC_API_KEY=your_anthropic_api_key
CLAUDE_MODEL=your_claude_model
```

Keep `.env` private; it is excluded from Git. In Jupyter, open a notebook and run its cells from top to bottom. Each notebook loads these settings using `python-dotenv`. The notebooks call external services and require an internet connection; requests to Claude may incur API charges.

## Notes

- The MCP example uses the Microsoft Learn MCP endpoint at `https://learn.microsoft.com/api/mcp`; the weather example calls `https://wttr.in`.
- The subagent research example uses Anthropic's web-search tool.
- The MCP and web-search examples rely on Anthropic SDK capabilities that may require compatible package versions and model access.
