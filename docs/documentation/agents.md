# Agents Documentation

## Overview

The `smolagents` repository provides a framework for building agents that use LLMs to perform tasks. The `smolagents` library allows the creation of agents that can use tools and perform multi-step tasks. The actions performed by LLMs in `smolagents` are defined by the tools and tasks provided to the agents.

## Main Code for Defining and Running Agents

The main code for defining and running agents is contained in the `src/smolagents/agents.py` file. This file includes the core classes and methods that define the behavior of agents in the `smolagents` framework.

### Key Classes and Methods

#### `MultiStepAgent`

The `MultiStepAgent` class is the base class for all agents in the `smolagents` framework. It provides the core functionality for agents to perform multi-step tasks.

```python
class MultiStepAgent:
    def __init__(self, tools, model, max_steps=5, verbosity_level=1):
        self.tools = tools
        self.model = model
        self.max_steps = max_steps
        self.verbosity_level = verbosity_level
        self.logs = []

    def run(self, task):
        self.logs.append(f"Task: {task}")
        for step in range(self.max_steps):
            action = self.model.generate_action(self.logs)
            result = self.execute_action(action)
            self.logs.append(f"Step {step + 1}: {action} -> {result}")
            if self.is_task_complete(result):
                break
        return self.logs

    def execute_action(self, action):
        # Execute the action using the appropriate tool
        pass

    def is_task_complete(self, result):
        # Determine if the task is complete based on the result
        pass
```

#### `CodeAgent`

The `CodeAgent` class is a specialized agent that writes its actions in code. It inherits from the `MultiStepAgent` class and provides additional functionality for handling code-based actions.

```python
class CodeAgent(MultiStepAgent):
    def __init__(self, tools, model, max_steps=5, verbosity_level=1):
        super().__init__(tools, model, max_steps, verbosity_level)

    def execute_action(self, action):
        # Execute the action as code
        pass
```

#### `ToolCallingAgent`

The `ToolCallingAgent` class is another specialized agent that writes its actions as JSON. It also inherits from the `MultiStepAgent` class and provides functionality for handling JSON-based actions.

```python
class ToolCallingAgent(MultiStepAgent):
    def __init__(self, tools, model, max_steps=5, verbosity_level=1):
        super().__init__(tools, model, max_steps, verbosity_level)

    def execute_action(self, action):
        # Execute the action as a JSON tool call
        pass
```

## Detailed Explanations and Examples

### Example: Multi-Agent System

The `docs/documentation/examples/multiagents.md` file provides an example of a multi-agent system. This example demonstrates how multiple agents can collaborate to solve a task using the `smolagents` framework.

### Example: Retrieval-Augmented-Generation (RAG) Agent

The `docs/documentation/examples/rag.md` file demonstrates how to create a Retrieval-Augmented-Generation (RAG) agent. This example explains the benefits of using a RAG agent for grounding answers on true facts.

### Example: Text-to-SQL Agent

The `docs/documentation/examples/text_to_sql.md` file shows how to implement a text-to-SQL agent. This example explains the advantages of using an agentic system for text-to-SQL tasks.

## Conclusion

The `smolagents` framework provides a powerful and flexible way to build agents that use LLMs to perform tasks. By leveraging the tools and multi-step capabilities of the `smolagents` library, developers can create sophisticated agentic systems that can handle a wide range of tasks.
