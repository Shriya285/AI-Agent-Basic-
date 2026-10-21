# AI-Agent-Basic

A small research agent built with LangChain and Claude. You type a topic, the agent searches the web and Wikipedia, and returns a structured answer (topic, summary, sources, tools used).

## Requirements

- Python 3.10 or newer (built and tested on 3.11)
- An Anthropic API key (console.anthropic.com)

## Setup

```bash
# 1. Clone and enter the project
git clone <your-repo-url>
cd AI-Agent-Basic-

# 2. Create and activate a virtual environment
python3.11 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

## Add your API key

Create a file named `.env` in the project folder with one line, no quotes and no spaces:

```
ANTHROPIC_API_KEY=your-key-here
```

Never commit `.env`. Add these lines to `.gitignore`:

```
.env
.venv/
__pycache__/
```

## Run

```bash
python main.py
```

When prompted, type a topic, for example `agentic ai`. The agent prints its reasoning steps (verbose mode) and then the structured result.

## Files

- `main.py`: the agent (model, prompt, output parser, agent executor)
- `tools.py`: the tools the agent can call (web search, Wikipedia, save to text file)
- `requirements.txt`: Python packages

## Troubleshooting

- `Illegal header value ...\n`: your API key has a trailing line break. Re-type the `.env` line and save.
- `ImportError` from `langchain.agents`: install `langchain-classic` and import from `langchain_classic.agents`.
- `Unsupported protocol version 0x304`: your Python is built with LibreSSL (the macOS system Python). Use a Homebrew Python 3.10+.
- `No results found` from search: the agent retries with a shorter query, or run again.
