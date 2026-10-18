```table-of-contents
```
---
## 1. INTRODUCTION - ADVANCED

### 1.1 What are Claude Code, Codex, and/or Copilot, and what will I learn?

Claude Code, Codex, and GitHub Copilot represent different approaches to integrating **LLMs and agents into the software development lifecycle**.

At this level, we do not start with the basics of what an LLM, prompting, or code generation is. The goal is to analyze these tools as **agentic development environments**, paying special attention to their capabilities, limitations, and control mechanisms.

We will work on concepts such as:

- Agents and tools.
- Context engineering.
- Multi-step planning and execution.
- Agent supervision and control.
- Memory and context persistence.
- Skills, MCP, plugins, and hooks.
- Sub-agents and parallelization.
- Automated verification and feedback loops.
- Patterns for building reproducible agentic workflows.

The objective is to learn how to **design and optimize an agentic development environment**, not simply how to use a coding assistant.

### 1.2 What is an agent and the "agentic loop"?

At this level, we will delve into the agent as a system that combines **model, context, tools, state, and feedback mechanisms**.

The agentic loop can be conceptually represented as:

**Context → reasoning → tool selection → execution → observation → context update → new decision**

An agent's capability does not depend solely on the model. It also depends on **which tools are available, what information is received, how the context is structured, and what mechanisms exist to verify its actions**.

We will analyze issues such as:

- How tool selection occurs.
- How state is maintained during a task.
- How context affects agent behavior.
- When manual intervention is appropriate.
- How to design verification mechanisms.
- How to reduce unnecessary iterations.
- How to avoid loops and incorrect actions.
- How to break down complex problems among different agents.
- How to design reproducible and auditable workflows. The goal is to shift from simply **using agents** to **understanding and designing efficient agentic work systems**.

### 1.3 Installing Claude Code, Codex, and/or Copilot

We will set up the development environment with a focus on **agentic engineering**.

Beyond the basic installation, we will examine how each tool structures its execution environment, context management, permissions, tools, and configuration.

We will cover aspects such as:

- CLI-based installation and configuration.
- Authentication and credential management.
- User-level and project-level configuration.
- Permissions and sandboxing.
- Git integration.
- Environment variables.
- Model configuration.
- IDE integration.
- Reproducible environment configuration.
- Differences between the various agents.

The aim is to ensure the environment not only functions correctly but is also **ready for building more complex agentic development workflows**.

### 1.4 First steps: onboarding, authentication, and graphical interface

Rather than limiting this section to a mere walkthrough of the interface, we will use the initial sessions to **analyze the agent's internal operations from the user's perspective**.

We will observe:

- The context received by the model.
- The available tools.
- How it decides which tool to use.
- How it interprets results.
- How it handles errors.
- What information it retains during the session.
- When it requests authorization.
- How we can intervene in the process.

We will also begin identifying patterns to improve our interactions: **context engineering, persistent instructions, scope definition, acceptance criteria, and verification mechanisms**.

The goal is for advanced students to start working with the agent—from the very first session—as a **configurable and orchestratable system**, rather than merely as a chat interface for writing code.

### 1.5 AI-assisted secure coding checklist
## 2. Actions, modes, and initial basic commands
### 2.1 Chatbot vs Agent
- https://www.omago.ai/blog/ai-agent-vs-live-chat-vs-chatbot

|                                     | Chat AI       |     AI Agents |
| ----------------------------------- | ------------- | ------------: |
| **Monthly users**                   | **~1.5–2.5B** | **~100–300M** |
| **Daily users**                     | **~500M–1B**  |  **~30–100M** |
| **% of Chat AI users using agents** | —             |    **~5–15%** |
### 2.2 The `.claude` directory
- https://code.claude.com/docs/en/claude-directory#ce-skills
## 3. Models
### 3.1 Anthropic: (Haiku, Sonnet, Opus, and Fable), effort, and "thinking" mode
### 3.2 OpenAI: GPT 5.6 Sol, Terra, and Luna, and GPT 6 Astra

## 4. Editing modes: manual, accept edits, and auto

### 4.1. Plan mode: first real project, review, approval, and verification

### 4.2. Iteration and change control via checkpoints

## 5. Context, memory, and harness engineering

### 5.1. Persistent memory with CLAUDE.md, file referencing, and shell mode

### 5.2. Additional project-level rules and Auto Memory

## 6. Commands: Creating and using custom commands

## 7. Skills: Creation, installation, and usage
- https://code.claude.com/docs/en/skills
### 7.1. Introduction to skill development for AI agents

### 7.2. What an agent skill is and how it works

### 7.3. Preparing the practice project

### 7.4. Creating your first skill from scratch: anatomy, invocation, and parameters

### 7.5. Advanced skills: references, resources, and scripts

### 7.6. Using skills across agents: Claude Code, Codex, and Copilot

### 7.7. How to use third-party skills: managers and popular resources

### 7.8. Recommendations and next steps

## 8. MCP (Model Context Protocol): connection and usage
- https://code.claude.com/docs/en/mcp-quickstart
## 9. Plugins & Marketplace
### 9.1 Plugins: commands + skills + MCPs + hooks in a single package
- https://code.claude.com/docs/en/discover-plugins
### 9.2 Marketplace: visual management of skills and connectors
- https://claude.com/plugins

## 10. Sub-agents, orchestration, and "agent teams"
- https://code.claude.com/docs/en/agents

## 11. Claude Code and Codex from the IDE
- https://code.claude.com/docs/en/vs-code
## 12. Hooks: custom actions during the "agentic loop"
- https://code.claude.com/docs/en/hooks-guide
## 13. Using Claude Code with free local AI models

## 14. Extra commands (loop, goal, schedule, background...)

## 15. Best practices and bypass mode
### 51.1 Implementing SDD: Spec-Driven Development

## 16. Conclusions and recommendations