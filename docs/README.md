# My Agent Documentation

Welcome to the **My Agent** documentation. This guide provides in‑depth information on how to use, extend, and contribute to the My Agent framework.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Command Line Interface](#command-line-interface)
- [Using Tools](#using-tools)
- [Streaming Responses](#streaming-responses)
- [Configuration](#configuration)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Overview

My Agent is a lightweight, extensible AI agent framework designed to simplify the creation and orchestration of intelligent agents. It provides a clean API for building agents, managing tools, and handling interactions.

## Installation

```bash
pip install my-agent
```

For the latest development version:

```bash
git clone https://github.com/yourusername/my-agent.git
cd my-agent
pip install -e .
```

## Quick Start

```python
from my_agent import Agent

agent = Agent()
response = agent.run("Hello, who are you?")
print(response)
```

## Command Line Interface

```bash
my-agent "What is the weather today?"
```

## Using Tools

```python
from my_agent import Agent, Tool

class EchoTool(Tool):
    name = "echo"
    description = "Echoes back the input."
    def run(self, input_text: str) -> str:
        return input_text

agent = Agent(tools=[EchoTool()])
result = agent.run("Use the echo tool to repeat 'Hello World'.")
print(result)
```

## Streaming Responses

```python
agent = Agent(stream=True)
for chunk in agent.run("Explain relativity briefly."):
    print(chunk, end="")
```

## Configuration

Configuration can be supplied via environment variables or a `config.yaml` file. See the [configuration guide](config/README.md) for details.

## Testing

Run the test suite with:

```bash
pytest
```

## Contributing

Please see the main repository's [README](../README.md) for contribution guidelines.

## License

MIT License – see the [LICENSE](../LICENSE) file.
