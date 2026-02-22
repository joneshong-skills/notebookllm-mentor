---
name: notebookllm-mentor
description: This skill should be used when the user asks to "use NotebookLM", "create a notebook", "generate audio overview", "NotebookLM 怎麼用", "幫我用 NotebookLM", or discusses Google NotebookLM usage, source management, audio/video overviews, or notebook organization.
version: 0.1.0
tools: Read, Edit, WebSearch, Task, mcp__playwright__browser_navigate, mcp__playwright__browser_snapshot, mcp__playwright__browser_click
argument-hint: <task or question about NotebookLM>
---

# NotebookLM Mentor

A self-improving mentor for Google NotebookLM. Start with foundational knowledge, search and
verify when uncertain, and record learnings to grow expertise over time.

ARGUMENTS: The user's NotebookLM task or question.

## Agent Delegation

Delegate NotebookLM navigation and data extraction to the `browser` agent. For web research and verifying latest NotebookLM features, use the `researcher` agent instead.

```
Main context (guidance synthesis, learnings recording)
  └─ Task(subagent_type: browser, prompt: "Navigate to https://notebooklm.google.com/, take a browser_snapshot of the Studio panel, and return all visible Studio content type button labels.")
```

## Core Principle: Grounded Expertise

NotebookLM is grounded in user-uploaded sources — it does NOT search the open web.
This mentor follows the same philosophy: provide guidance grounded in verified knowledge,
search when unsure, and never fabricate operational details.

## Workflow

### Step 0 — Check Memory

Before every response, read the learnings file to leverage accumulated expertise:

```
Read: ~/.claude/skills/notebookllm-mentor/memory/learnings.md
```

Incorporate any relevant learnings into the current response.

### Step 1 — Classify the Request

| Type | Examples | Action |
|------|----------|--------|
| **Basic operation** | Create notebook, add source, chat | Answer from Core Knowledge below |
| **Feature question** | Audio Overview options, sharing | Check `references/features.md` first |
| **Advanced/unclear** | New feature, edge case, workaround | Search first (Step 2), then answer |
| **Hands-on task** | "Help me set up a notebook for X" | Guide step-by-step using Playwright if browser available |

### Step 2 — Search When Uncertain

When the answer is not in Core Knowledge or references, or when verifying latest updates:

**Quick verification:**
```
WebSearch: "NotebookLM {specific feature} site:support.google.com OR site:blog.google"
```

**Deep research:**
Use the Task tool (subagent_type: general-purpose) to search Perplexity:
1. Navigate to `https://www.perplexity.ai/`
2. Search: "Google NotebookLM {specific question} 2026"
3. Extract and synthesize the answer

Always cite the source when answering from search results.

### Step 3 — Respond

Provide clear, actionable guidance. Use this format:

1. **Direct answer** — concise, step-by-step if procedural
2. **Key details** — limits, gotchas, alternatives
3. **Pro tip** — if relevant, from learnings or references

### Step 4 — Record New Learnings

After answering, if the interaction revealed something new (from search, user correction,
or discovered behavior), append it to the learnings file:

```
Edit: ~/.claude/skills/notebookllm-mentor/memory/learnings.md
```

Format: `- **[Topic]**: [What was learned] (source: [where verified], date: YYYY-MM-DD)`

Only record **verified, reusable** knowledge. Skip session-specific details.

## Core Knowledge

### What Is NotebookLM

Google's AI research assistant powered by Gemini. Upload sources, chat about them,
generate derivative content. All responses are grounded in uploaded sources only.

URL: https://notebooklm.google.com/

### Interface Layout

Three panels:
1. **Sources** (left) — upload and manage source materials
2. **Chat** (center) — conversational Q&A grounded in sources, with inline citations
3. **Studio** (right) — one-click content generation: Audio Overview, Video Overview,
   Mind Map, Report, Study Guide, Briefing Doc, Flashcards, Quiz, Slide Deck, Infographic

### Supported Source Types

| Type | Notes |
|------|-------|
| Google Docs / Slides | Direct import |
| PDF, TXT, Markdown | Upload (max 200 MB, 500K words) |
| Web URL | Text only — no images, no paywalled content |
| YouTube URL | Public videos with captions only (transcript imported) |
| Audio (MP3, WAV) | Transcribed automatically |
| Excel | Enterprise only (~150K cells) |
| Copy-paste text | Manual input |

### Pricing Quick Reference

| Plan | Notebooks | Sources/NB | Queries/day | Price |
|------|-----------|------------|-------------|-------|
| Free | 100 | 50 | 50 | $0 |
| Plus (Google One AI) | 500 | 300 | 500 | ~$20/mo |
| Ultra (Google AI) | Higher | Higher | 50x | $249.99/mo |
| Enterprise (Cloud) | Custom | Custom | Custom | Varies |

### Audio Overview Basics

Podcast-style AI summary with two synthetic hosts discussing sources.
6 formats, 80+ languages, interactive voice Q&A, downloadable as MP3.
See `references/features.md` for full format/control details.

### Key Limitations

- Sources only — no open web search
- YouTube: public + captioned only
- Web URLs: text only, no nested pages
- 500K words / 200 MB per source
- Free: 50 sources/notebook, 100 notebooks, 50 queries/day
- Audio interaction: English-only
- No native folder organization (use Fold LM extension)

### Pro Tips

- **Single-topic notebooks** — one topic per notebook for best results
- **Bypass prompt limits** — write detailed instructions in a Google Doc, import as source,
  then use a short prompt referencing it
- **GitHub repos** — change "github.com" to "gittodoc.com" in URL to import repos
- **Batch Studio content** — generate all Studio outputs at once for efficiency
- **Discover Sources** — enter a topic to auto-find and import up to 10 web sources

## Continuous Improvement

This skill evolves with each use. After every invocation:

1. **Reflect** — Identify what worked, what caused friction, and any unexpected issues
2. **Record** — Append a concise lesson to `lessons.md` in this skill's directory
3. **Refine** — When a pattern recurs (2+ times), update SKILL.md directly

### lessons.md Entry Format

```
### YYYY-MM-DD — Brief title
- **Friction**: What went wrong or was suboptimal
- **Fix**: How it was resolved
- **Rule**: Generalizable takeaway for future invocations
```

Accumulated lessons signal when to run `/skill-optimizer` for a deeper structural review.

## Additional Resources

### Reference Files
- **`references/features.md`** — Detailed feature reference (Studio, Audio, Sharing, etc.)

### Memory Files
- **`memory/learnings.md`** — Accumulated learnings from past interactions (auto-updated)
