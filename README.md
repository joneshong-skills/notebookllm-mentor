[English](README.md) | [繁體中文](README.zh.md)

# NotebookLM Mentor

A Claude Code skill that serves as a self-improving mentor for Google NotebookLM — providing grounded guidance on features, workflows, and best practices while continuously learning from interactions.

## What It Does

NotebookLM Mentor answers questions and guides tasks across all aspects of NotebookLM:

| Request Type | Action |
|---|---|
| Basic operations | Answer from built-in core knowledge (create, upload, chat) |
| Feature questions | Consult reference files (Audio Overview, Studio, sharing) |
| Advanced / edge cases | Search the web for latest info, then answer |
| Hands-on tasks | Guide step-by-step, using Playwright if browser is available |

**Key design principle:** Like NotebookLM itself, this mentor is grounded in verified knowledge. It searches when uncertain, cites sources, and records new learnings to improve over time.

### Self-Improving Memory

Every interaction that reveals new information (UI changes, feature updates, workarounds) is automatically recorded. Future responses leverage all accumulated learnings.

## Installation

1. Clone this repository into your Claude skills directory:

   ```bash
   git clone https://github.com/joneshong-skills/notebookllm-mentor.git ~/.claude/skills/notebookllm-mentor
   ```

2. Prerequisites:
   - Web search capability (for verifying latest features and pricing)
   - Playwright MCP server (optional, for hands-on browser guidance)

3. The skill activates when you ask about NotebookLM usage, features, or best practices, or use trigger phrases like "NotebookLM how to", "help me use NotebookLM", etc.

## Usage

Just ask Claude naturally. Examples:

- *"How do I create an Audio Overview in NotebookLM?"*
- *"What are the source limits for the free plan?"*
- *"Help me set up a notebook for my research papers"*
- *"What's the best way to organize multiple topics in NotebookLM?"*

## Project Structure

```
notebookllm-mentor/
├── SKILL.md                        # Skill definition, workflow, and core knowledge
├── README.md                       # This file
├── references/
│   └── features.md                 # Detailed feature reference (Studio, Audio, Sharing)
└── memory/
    └── learnings.md                # Accumulated learnings from past interactions
```

## License

MIT
