# My Agent

## Overview

My Agent is a lightweight, extensible AI agent framework designed to simplify the creation and orchestration of intelligent agents. It provides a clean API for building agents, managing tools, and handling interactions.

## Installation

You can install **My Agent** from PyPI:

```bash
pip install my-agent
```

Or install the latest development version directly from the repository:

```bash
git clone https://github.com/yourusername/my-agent.git
cd my-agent
pip install -e .
```

## Quick Start

Below is a minimal example showing how to create and run an agent:

```python
from my_agent import Agent

# Initialize the agent (customize as needed)
agent = Agent()

# Run the agent with a prompt
response = agent.run("Hello, who are you?")
print(response)
```

### Command Line Interface

My Agent also ships with a convenient CLI:

```bash
my-agent "What is the weather today?"
```

For more advanced usage, refer to the [Documentation](docs/README.md).

## Detailed Usage Examples

### Using Tools

```python
from my_agent import Agent, Tool

# Define a simple tool
class EchoTool(Tool):
    name = "echo"
    description = "Echoes back the input."

    def run(self, input_text: str) -> str:
        return input_text

# Register the tool with the agent
agent = Agent(tools=[EchoTool()])

result = agent.run("Use the echo tool to repeat 'Hello World'.")
print(result)
```

### Streaming Responses

```python
from my_agent import Agent

agent = Agent(stream=True)

for chunk in agent.run("Explain the theory of relativity in short sentences."):
    print(chunk, end="")
```

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** and ensure the code passes linting and tests.
4. **Commit your changes** with a clear commit message.
5. **Push to your fork** and open a Pull Request against the `main` branch.

### Development Setup

```bash
# Clone the repo
git clone https://github.com/yourusername/my-agent.git
cd my-agent

# Install development dependencies
pip install -e .[dev]
```

### Code Style & Testing

- Follow the existing code style (PEP 8).
- Run tests before submitting:
  ```bash
  pytest
  ```
- Lint the code using:
  ```bash
  flake8 .
  ```

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.