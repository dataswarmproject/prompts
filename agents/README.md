# AI Agents and Solutions

**Building autonomous AI agents and intelligent automation systems.**

## What are AI Agents?

AI agents are autonomous systems that can:
- Perceive their environment
- Make decisions based on goals
- Take actions to achieve objectives
- Learn from feedback
- Use tools and APIs
- Collaborate with other agents

## Table of Contents

1. [Agent Architectures](#agent-architectures)
2. [Agent Frameworks](#agent-frameworks)
3. [Pre-built Agent Solutions](#pre-built-agent-solutions)
4. [Building Custom Agents](#building-custom-agents)
5. [Multi-Agent Systems](#multi-agent-systems)

---

## Agent Architectures

### 1. ReAct (Reason + Act)

**Pattern**: Think → Act → Observe → Repeat

**Structure**:
```
Thought: I need to search for information about X
Action: search("X")
Observation: [Search results]
Thought: Based on results, I should...
Action: [Next action]
```

**When to Use**:
- Complex problem-solving
- Research tasks
- Multi-step workflows

**Example Implementation**:
```python
def react_agent(question, tools, max_iterations=10):
    context = question

    for i in range(max_iterations):
        # Reason
        thought = llm.generate(
            f"{context}\nThought:"
        )

        # Decide action
        action = parse_action(thought)

        if action.type == "Final Answer":
            return action.value

        # Act
        observation = execute_tool(action.tool, action.input)

        # Update context
        context += f"\nThought: {thought}\nAction: {action}\nObservation: {observation}"

    return "Max iterations reached"
```

---

### 2. Plan-and-Execute

**Pattern**: Plan → Execute steps → Replan if needed

**Structure**:
```
1. Create high-level plan
2. Execute first step
3. Validate results
4. Adjust plan if needed
5. Continue until goal achieved
```

**When to Use**:
- Long-term tasks
- Complex projects
- Resource optimization needed

**Example**:
```python
class PlanExecuteAgent:
    def run(self, goal):
        # Create plan
        plan = self.create_plan(goal)

        for step in plan:
            # Execute step
            result = self.execute_step(step)

            # Validate
            if not self.validate(result, step):
                # Replan
                plan = self.replan(goal, result, remaining_steps)

        return self.final_result

    def create_plan(self, goal):
        prompt = f"""Create a step-by-step plan to: {goal}

        Format:
        1. [First step]
        2. [Second step]
        ..."""

        return llm.generate(prompt)
```

---

### 3. Reflexion

**Pattern**: Act → Reflect → Learn → Improve

**When to Use**:
- Tasks requiring iteration
- Learning from mistakes
- Quality improvement

**Example**:
```python
def reflexion_agent(task, max_attempts=3):
    memory = []

    for attempt in range(max_attempts):
        # Attempt task
        result = execute_task(task, memory)

        # Reflect on performance
        reflection = llm.generate(
            f"Task: {task}\nResult: {result}\nWhat went wrong? How to improve?"
        )

        memory.append({
            "attempt": attempt,
            "result": result,
            "reflection": reflection
        })

        # Check if satisfactory
        if evaluate_quality(result):
            return result

    return best_result(memory)
```

---

## Agent Frameworks

### 1. LangChain Agents

**What**: Flexible agent framework with many tools

**Installation**:
```bash
pip install langchain langchain-openai
```

**Quick Start**:
```python
from langchain.agents import create_openai_functions_agent, AgentExecutor
from langchain_openai import ChatOpenAI
from langchain.tools import Tool
from langchain.prompts import ChatPromptTemplate

# Define tools
def search(query: str) -> str:
    # Implementation
    return f"Results for {query}"

tools = [
    Tool(
        name="Search",
        func=search,
        description="Useful for searching information"
    )
]

# Create agent
llm = ChatOpenAI(model="gpt-4-turbo")
prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful assistant"),
    ("human", "{input}"),
    ("placeholder", "{agent_scratchpad}"),
])

agent = create_openai_functions_agent(llm, tools, prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)

# Run
result = agent_executor.invoke({"input": "Find information about AI agents"})
```

**Best For**:
- Rapid prototyping
- Many available tools
- LLM integration

---

### 2. AutoGPT

**What**: Autonomous GPT-4 agent for goal completion

**Installation**:
```bash
git clone https://github.com/Significant-Gravitas/AutoGPT
cd AutoGPT
pip install -r requirements.txt
```

**Usage**:
```bash
python -m autogpt --ai-name "MyAgent" --ai-role "Developer" --ai-goals "Build a web scraper"
```

**Features**:
- Internet access
- File operations
- Code execution
- Memory management
- Self-improvement

**Best For**:
- Autonomous tasks
- Long-running projects
- Experimental applications

---

### 3. BabyAGI

**What**: Simple task-driven autonomous agent

**Key Concept**: Task list + execution + result storage + new task creation

**Implementation**:
```python
from collections import deque

class BabyAGI:
    def __init__(self, objective):
        self.objective = objective
        self.task_list = deque([{"task_id": 1, "task_name": objective}])
        self.results = []

    def task_creation(self, result, task_description):
        prompt = f"""
        Objective: {self.objective}
        Last task: {task_description}
        Result: {result}

        Create new tasks to complete the objective.
        Return as numbered list.
        """
        new_tasks = llm.generate(prompt)
        return parse_tasks(new_tasks)

    def prioritize_tasks(self):
        prompt = f"""
        Tasks: {list(self.task_list)}
        Objective: {self.objective}

        Prioritize these tasks. Return task IDs in order.
        """
        # Reorder task list based on priorities

    def execute_task(self, task):
        prompt = f"""
        Objective: {self.objective}
        Task: {task['task_name']}
        Context: {self.results[-5:]}  # Last 5 results

        Complete this task.
        """
        return llm.generate(prompt)

    def run(self, max_iterations=10):
        for i in range(max_iterations):
            if not self.task_list:
                break

            # Get next task
            task = self.task_list.popleft()

            # Execute
            result = self.execute_task(task)
            self.results.append({"task": task, "result": result})

            # Create new tasks
            new_tasks = self.task_creation(result, task['task_name'])
            self.task_list.extend(new_tasks)

            # Reprioritize
            self.prioritize_tasks()

        return self.results
```

**Best For**:
- Learning agent concepts
- Simple autonomous tasks
- Customization

---

### 4. CrewAI

**What**: Multi-agent collaboration framework

**Installation**:
```bash
pip install crewai
```

**Quick Start**:
```python
from crewai import Agent, Task, Crew

# Define agents
researcher = Agent(
    role='Researcher',
    goal='Find accurate information',
    backstory='Expert at research and fact-checking',
    verbose=True
)

writer = Agent(
    role='Writer',
    goal='Write engaging content',
    backstory='Professional content writer',
    verbose=True
)

# Define tasks
research_task = Task(
    description='Research AI agent architectures',
    agent=researcher
)

writing_task = Task(
    description='Write a blog post about the research',
    agent=writer
)

# Create crew
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    verbose=2
)

# Execute
result = crew.kickoff()
```

**Best For**:
- Team simulations
- Complex workflows
- Role-based tasks

---

### 5. Microsoft Semantic Kernel

**What**: Enterprise-grade agent framework

**Installation**:
```bash
pip install semantic-kernel
```

**Quick Start**:
```python
import semantic_kernel as sk
from semantic_kernel.connectors.ai.open_ai import OpenAIChatCompletion

kernel = sk.Kernel()

# Add AI service
kernel.add_chat_service(
    "chat",
    OpenAIChatCompletion("gpt-4", api_key)
)

# Define function
@sk.kernel_function(description="Search the web")
def search(query: str) -> str:
    # Implementation
    return f"Results for {query}"

kernel.import_native_skill_from_directory("./skills")

# Create planner
from semantic_kernel.planning import SequentialPlanner
planner = SequentialPlanner(kernel)

# Generate plan
plan = await planner.create_plan_async("Research AI and write summary")

# Execute
result = await plan.invoke_async()
```

**Best For**:
- Enterprise applications
- .NET integration
- Azure integration

---

## Pre-built Agent Solutions

### 1. Agent GPT (Web-based)

**URL**: https://agentgpt.reworkd.ai

**Features**:
- Web interface
- No coding required
- Deploy autonomous agents
- Goal-oriented

**Use Cases**:
- Quick experiments
- Non-technical users
- Demonstrations

---

### 2. Zapier AI Actions

**What**: AI agents for workflow automation

**Features**:
- 5000+ app integrations
- Natural language workflows
- Triggered automation
- Data transformation

**Example**:
```
When: New email received
AI Agent: Classify email priority
Then:
  If high priority → Send Slack notification
  Else → Add to Notion database
```

**Best For**:
- Business automation
- No-code solutions
- Integration-heavy tasks

---

### 3. Relevance AI Agents

**What**: Build and deploy AI agent workflows

**Features**:
- Visual workflow builder
- Pre-built templates
- API deployment
- Team collaboration

**Use Cases**:
- Customer support
- Data processing
- Content generation

---

## Building Custom Agents

### Simple Tool-Using Agent

```python
from anthropic import Anthropic
import json

class SimpleAgent:
    def __init__(self, api_key):
        self.client = Anthropic(api_key=api_key)
        self.tools = self.define_tools()

    def define_tools(self):
        return [
            {
                "name": "search",
                "description": "Search the web for information",
                "input_schema": {
                    "type": "object",
                    "properties": {
                        "query": {"type": "string"}
                    },
                    "required": ["query"]
                }
            },
            {
                "name": "calculator",
                "description": "Perform calculations",
                "input_schema": {
                    "type": "object",
                    "properties": {
                        "expression": {"type": "string"}
                    },
                    "required": ["expression"]
                }
            }
        ]

    def execute_tool(self, tool_name, tool_input):
        if tool_name == "search":
            return f"Search results for: {tool_input['query']}"
        elif tool_name == "calculator":
            return str(eval(tool_input['expression']))

    def run(self, user_message, max_iterations=10):
        messages = [{"role": "user", "content": user_message}]

        for i in range(max_iterations):
            response = self.client.messages.create(
                model="claude-3-5-sonnet-20241022",
                max_tokens=1024,
                tools=self.tools,
                messages=messages
            )

            # Check if done
            if response.stop_reason == "end_turn":
                final_text = next(
                    (block.text for block in response.content if hasattr(block, "text")),
                    None
                )
                return final_text

            # Execute tools
            if response.stop_reason == "tool_use":
                # Add assistant response
                messages.append({
                    "role": "assistant",
                    "content": response.content
                })

                # Execute each tool
                tool_results = []
                for block in response.content:
                    if block.type == "tool_use":
                        result = self.execute_tool(block.name, block.input)
                        tool_results.append({
                            "type": "tool_result",
                            "tool_use_id": block.id,
                            "content": result
                        })

                # Add tool results
                messages.append({
                    "role": "user",
                    "content": tool_results
                })

        return "Max iterations reached"

# Usage
agent = SimpleAgent(api_key="your_key")
result = agent.run("What is 15 * 23? Then search for information about that number.")
print(result)
```

---

### Agent with Memory

```python
class MemoryAgent:
    def __init__(self, api_key):
        self.client = Anthropic(api_key=api_key)
        self.short_term_memory = []  # Conversation history
        self.long_term_memory = {}   # Persistent facts

    def remember(self, key, value):
        """Store in long-term memory"""
        self.long_term_memory[key] = value

    def recall(self, key):
        """Retrieve from long-term memory"""
        return self.long_term_memory.get(key)

    def run(self, user_message):
        # Add to short-term memory
        self.short_term_memory.append({
            "role": "user",
            "content": user_message
        })

        # Include relevant long-term memories in context
        context = self.build_context()

        # Generate response
        response = self.client.messages.create(
            model="claude-3-5-sonnet-20241022",
            max_tokens=1024,
            system=context,
            messages=self.short_term_memory
        )

        # Add to short-term memory
        self.short_term_memory.append({
            "role": "assistant",
            "content": response.content[0].text
        })

        # Extract and store new facts
        self.extract_facts(user_message, response.content[0].text)

        return response.content[0].text

    def build_context(self):
        context = "You are a helpful assistant.\n\n"
        if self.long_term_memory:
            context += "Known facts:\n"
            for key, value in self.long_term_memory.items():
                context += f"- {key}: {value}\n"
        return context

    def extract_facts(self, user_msg, assistant_msg):
        # Simple fact extraction (could use LLM for better results)
        if "my name is" in user_msg.lower():
            name = user_msg.lower().split("my name is")[1].strip()
            self.remember("user_name", name)
```

---

## Multi-Agent Systems

### Collaboration Pattern

```python
class MultiAgentSystem:
    def __init__(self):
        self.agents = {
            "researcher": self.create_agent("researcher"),
            "analyst": self.create_agent("analyst"),
            "writer": self.create_agent("writer")
        }

    def create_agent(self, role):
        role_prompts = {
            "researcher": "You are a researcher. Find accurate information.",
            "analyst": "You are an analyst. Analyze data and draw insights.",
            "writer": "You are a writer. Create engaging content."
        }

        return {
            "role": role,
            "system_prompt": role_prompts[role],
            "memory": []
        }

    def run_agent(self, agent_name, task, context=None):
        agent = self.agents[agent_name]

        prompt = f"{agent['system_prompt']}\n\nTask: {task}"
        if context:
            prompt += f"\n\nContext: {context}"

        response = llm.generate(prompt)
        agent['memory'].append({"task": task, "result": response})

        return response

    def collaborative_task(self, goal):
        # Step 1: Research
        research = self.run_agent("researcher", f"Research: {goal}")

        # Step 2: Analyze
        analysis = self.run_agent("analyst", "Analyze this research", research)

        # Step 3: Write
        article = self.run_agent("writer", "Write article based on analysis", analysis)

        return {
            "research": research,
            "analysis": analysis,
            "article": article
        }

# Usage
system = MultiAgentSystem()
result = system.collaborative_task("The future of AI agents")
```

---

## Agent Design Patterns

### 1. Tool Use Pattern
- Agent has access to external tools/APIs
- Decides when and how to use tools
- Combines tool results with reasoning

### 2. Chain Pattern
- Sequential agent execution
- Output of one feeds into next
- Linear workflow

### 3. Router Pattern
- Input classification
- Route to specialized agent
- Aggregateresults

### 4. Supervisor Pattern
- Master agent delegates to workers
- Monitors progress
- Combines results

---

## Best Practices

### 1. Goal Definition
```python
# Bad: Vague goal
goal = "Help me with marketing"

# Good: Specific goal
goal = """
Create a social media marketing campaign for product X:
1. Research target audience
2. Generate 10 post ideas
3. Write copy for top 3 posts
4. Suggest posting schedule
Success criteria: Posts should match brand voice and target audience interests
"""
```

### 2. Error Handling
```python
def robust_agent_run(agent, task, max_retries=3):
    for attempt in range(max_retries):
        try:
            result = agent.run(task)
            if validate_result(result):
                return result
            else:
                task = improve_task(task, result)
        except Exception as e:
            if attempt == max_retries - 1:
                return fallback_result(task)
            continue
```

### 3. Cost Management
- Set max iterations
- Use cheaper models for simple sub-tasks
- Cache repeated operations
- Monitor token usage

### 4. Safety
- Validate tool inputs
- Sandbox code execution
- Review actions before execution
- Set permissions appropriately

---

## Resources

- **LangChain Agents**: https://python.langchain.com/docs/modules/agents
- **AutoGPT**: https://github.com/Significant-Gravitas/AutoGPT
- **CrewAI**: https://github.com/joaomdmoura/crewAI
- **Semantic Kernel**: https://github.com/microsoft/semantic-kernel
- **Agent Papers**: https://github.com/WooooDyy/LLM-Agent-Paper-List

---

**Last Updated**: 2025-10-28

**See Also**:
- [APIs](../apis/)
- [Tools](../tools/)
- [Best Practices](../AI-BEST-PRACTICES.md)
