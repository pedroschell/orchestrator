# orchestrator

[Português](README.md) | **English**

A Claude Code subagent that **plans complex tasks before a single line of code is written**: it understands the goal, points out the risks, suggests the specialists and the stack, and defines the execution order.

On large projects, the most expensive mistake is starting the implementation from the wrong end. This agent exists for the step before that: it doesn't implement, doesn't review, and doesn't write documentation. It only decides the path, and delivers the plan in at most three paragraphs.

## What it delivers

- the recommended strategy;
- the suggested specialists and stack;
- the execution order;
- the identified risks;
- the next step.

## Why it is lean on purpose

- It reads only the context it needs, so it doesn't use up the main conversation's context window.
- It favors the smallest possible solution and avoids irreversible decisions unless they are necessary.
- It runs on the `opus` model with read-only tools only (`Read`, `Grep`, `Glob`, `WebFetch`, `WebSearch`), so it doesn't change anything in the project.

## How to install

For all your projects:

```bash
mkdir -p ~/.claude/agents
curl -o ~/.claude/agents/orchestrator.md https://raw.githubusercontent.com/pedroschell/orchestrator/main/orchestrator.md
```

Or for a single project, by saving the file to `.claude/agents/orchestrator.md` inside it.

Then ask for something like *"use the orchestrator to plan the database migration"*. Claude also invokes the agent on its own when the task calls for coordination.

## Works well with

The [delivery-reviewer](https://github.com/pedroschell/delivery-reviewer), which reviews the delivery once it's done. The orchestrator plans, the delivery-reviewer checks.

## License

MIT
