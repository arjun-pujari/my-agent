# Project Overview

**my-agent** is a lightweight, extensible framework designed to simplify the creation and management of autonomous agents. It provides a clear structure for defining agent behavior, handling communication, and integrating with external tools and APIs.

## Purpose

- **Modularity** – Build agents from reusable components.
- **Extensibility** – Easily plug in new capabilities such as web browsing, file manipulation, or custom logic.
- **Clarity** – Well‑documented interfaces and conventions make onboarding new contributors fast.

## Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your‑username>/my-agent.git
   cd my-agent
   ```
2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows use `venv\Scripts\activate`
   ```
3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
4. **Run the test suite** to ensure everything is working
   ```bash
   pytest
   ```

## Usage Examples

### Running a Simple Agent
```python
from my_agent import Agent

# Define a basic agent that echoes user input
class EchoAgent(Agent):
    def handle_message(self, message: str) -> str:
        return f"Echo: {message}"

if __name__ == "__main__":
    agent = EchoAgent()
    print(agent.handle_message("Hello, world!"))
```

### Extending with a Tool
```python
from my_agent import Agent, Tool

class ReverseTool(Tool):
    name = "reverse"
    description = "Reverses a string."
    def run(self, text: str) -> str:
        return text[::-1]

class SmartAgent(Agent):
    def __init__(self):
        super().__init__(tools=[ReverseTool()])

    def handle_message(self, message: str) -> str:
        # Use the reverse tool internally
        reversed_text = self.tools["reverse"].run(message)
        return f"Reversed: {reversed_text}"

if __name__ == "__main__":
    agent = SmartAgent()
    print(agent.handle_message("my-agent"))
```

### Command‑Line Interface (CLI)
If the project ships a CLI entry point, you can invoke it directly:
```bash
my-agent run --config=config.yaml
```
Check the `cli/` directory for available commands and options.

---

For more detailed documentation, refer to the individual module docstrings and the API reference generated with **Sphinx** (if available).
