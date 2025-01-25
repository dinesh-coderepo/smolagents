<!--Copyright 2024 The HuggingFace Team. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with
the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.

⚠️ Note that this file is in Markdown but contain specific syntax for our doc-builder (similar to MDX) that may not be
rendered properly in your Markdown viewer.

-->
# ReAct Framework

## 🤔 What is the ReAct framework?

The ReAct framework is a powerful approach used by multi-step agents to perform a series of steps to solve a task. It combines reasoning and acting in a loop, allowing agents to iteratively refine their actions based on observations and feedback.

In the ReAct framework, an agent follows a structured process to achieve its goals. The process typically involves the following steps:

1. **Observation**: The agent gathers information about the current state of the environment or task.
2. **Reasoning**: The agent analyzes the observations and formulates a plan or strategy to achieve the desired outcome.
3. **Action**: The agent executes the planned actions to interact with the environment or perform specific tasks.
4. **Feedback**: The agent receives feedback or observations resulting from its actions, which are used to refine the reasoning and planning process.

This iterative loop continues until the agent successfully completes the task or reaches a satisfactory state.

## How does the ReAct framework work?

The ReAct framework allows agents to perform a series of steps to solve a task. It provides a structured approach to reasoning and acting, enabling agents to handle complex tasks that require multiple actions and decisions.

Here is an example of how the ReAct framework can be implemented in code:

```python
class ReActAgent:
    def __init__(self):
        self.memory = []

    def observe(self, observation):
        self.memory.append(observation)

    def reason(self):
        # Analyze observations and formulate a plan
        plan = self.formulate_plan()
        return plan

    def act(self, plan):
        # Execute the planned actions
        actions = self.execute_plan(plan)
        return actions

    def feedback(self, feedback):
        self.memory.append(feedback)

    def formulate_plan(self):
        # Placeholder for plan formulation logic
        return "Plan"

    def execute_plan(self, plan):
        # Placeholder for plan execution logic
        return "Actions"

# Example usage
agent = ReActAgent()
agent.observe("Observation 1")
plan = agent.reason()
actions = agent.act(plan)
agent.feedback("Feedback 1")
```

In this example, the `ReActAgent` class represents an agent that follows the ReAct framework. The agent observes the environment, reasons about the observations, formulates a plan, executes the plan, and receives feedback. This iterative process allows the agent to refine its actions and improve its performance over time.

## Benefits of the ReAct framework

The ReAct framework offers several benefits for building multi-step agents:

1. **Flexibility**: The framework allows agents to adapt their actions based on observations and feedback, enabling them to handle dynamic and changing environments.
2. **Scalability**: The iterative nature of the framework allows agents to break down complex tasks into smaller, manageable steps, making it easier to scale the agent's capabilities.
3. **Improved Performance**: By continuously refining their actions based on feedback, agents can improve their performance and achieve better results over time.
4. **Modularity**: The framework provides a modular structure, allowing different components (observation, reasoning, action, feedback) to be developed and tested independently.

The ReAct framework is a powerful tool for building intelligent agents that can perform complex tasks by combining reasoning and acting in a structured and iterative manner.
