# Multi-Agent System Example

In this example, we will demonstrate how to create a multi-agent system using the `smolagents` framework. A multi-agent system consists of multiple agents that collaborate to solve a task. Each agent can perform specific actions and share information with other agents to achieve a common goal.

## Setting Up the Environment

First, let's install the necessary dependencies:

```bash
!pip install smolagents
```

## Defining the Agents

We will define two agents: `AgentA` and `AgentB`. Each agent will have its own set of tools and tasks.

```python
from smolagents import Tool, CodeAgent

class AgentA(CodeAgent):
    def __init__(self, tools, model):
        super().__init__(tools, model)
        self.name = "AgentA"

class AgentB(CodeAgent):
    def __init__(self, tools, model):
        super().__init__(tools, model)
        self.name = "AgentB"
```

## Creating the Tools

Next, we will create some tools that the agents can use. For simplicity, we will create a tool that performs a basic arithmetic operation.

```python
class AddTool(Tool):
    name = "add"
    description = "Adds two numbers"
    inputs = {
        "a": {"type": "number", "description": "First number"},
        "b": {"type": "number", "description": "Second number"}
    }
    output_type = "number"

    def forward(self, a, b):
        return a + b

add_tool = AddTool()
```

## Initializing the Agents

Now, we will initialize the agents with the tools and a model. For this example, we will use a simple model that generates random numbers.

```python
from random import randint

class RandomModel:
    def __call__(self, messages):
        return {"content": str(randint(1, 100))}

model = RandomModel()

agent_a = AgentA(tools=[add_tool], model=model)
agent_b = AgentB(tools=[add_tool], model=model)
```

## Defining the Task

We will define a task that requires the collaboration of both agents. The task is to add two numbers, where each agent contributes one number.

```python
task = "AgentA will provide the first number and AgentB will provide the second number. Then, they will add the numbers together."
```

## Running the Multi-Agent System

Finally, we will run the multi-agent system to solve the task.

```python
# AgentA provides the first number
agent_a_output = agent_a.run("Provide the first number")
first_number = int(agent_a_output)

# AgentB provides the second number
agent_b_output = agent_b.run("Provide the second number")
second_number = int(agent_b_output)

# Adding the numbers using the add tool
result = add_tool.forward(first_number, second_number)
print(f"The result of adding {first_number} and {second_number} is {result}")
```

In this example, we demonstrated how to create a multi-agent system using the `smolagents` framework. The agents collaborated to solve a task by sharing information and using tools. This approach can be extended to more complex tasks and multiple agents.
