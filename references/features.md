# NotebookLM Feature Reference

Detailed reference for all NotebookLM features. Updated as new information is verified.

## Studio Panel Features

### Audio Overview
- Two AI hosts discuss and synthesize uploaded sources
- **Formats:** Deep Dive (comprehensive), Brief (2-3 min), Standard (5-6 min),
  Extended (8-10 min), Critique (critical analysis), Debate (opposing viewpoints)
- **Customization:** Voice tone, length, language (80+), topic emphasis via prompt
- **Interactive mode:** "Join the Conversation" — real-time voice Q&A during playback
- **Controls:** Smart Pause, Section Jump, Instant Replay, Summary Mode
- **Output:** Download MP3, share via link, embed in notebook
- **Limitation:** Interactive mode is English-only

### Video Overview
- AI-generated video summaries from sources
- Available in 80+ languages
- Rolled out globally July 2025

### Mind Map
- Interactive visualization of topic connections
- Navigate complex relationships at a glance
- Downloadable as image

### Reports / Deep Research
- Generated summary reports from sources
- Deep Research: in-depth research sessions (added Nov 2025)
- Fast Research: quick link retrieval
- Deep Research: comprehensive 60+ source analysis

### Study Aids
- **Study Guide** — structured learning material
- **Flashcards** — key concepts for review
- **Quiz** — comprehension testing

### Presentation
- **Slide Deck** — presentation slides (watermark on free/Plus, removed on Ultra)
- **Infographic** — visual summaries (watermark on free/Plus, removed on Ultra)
- **Briefing Doc** — concise executive summary

## Source Management

### Adding Sources
1. Click "+" in Sources panel
2. Choose: Upload file, Google Drive, Website URL, YouTube URL, paste text
3. Wait for processing (large files may take time)

### Discover Sources (2025+)
- Enter a topic keyword
- NotebookLM auto-finds and recommends up to 10 relevant web sources
- One-click import selected sources
- Useful for bootstrapping research on a new topic

### Source Quality Verification
- Prompt: "Create a table showing publication dates and citation counts for all sources"
- Remove outdated or low-quality sources based on the table

### Source Limits
| Plan | Sources per Notebook | Words per Source | File Size |
|------|---------------------|-----------------|-----------|
| Free | 50 | 500,000 | 200 MB |
| Plus | 300 | 500,000 | 200 MB |
| Ultra | Higher | 500,000 | 200 MB |

## Chat Features

### Chat Modes
- **Default** — general Q&A grounded in sources
- **Learning Tutor** — educational, step-by-step explanations
- **Debate Mode** — argue a position using source material
- **Custom Persona** — set via "Customize" button

### Chat Customization
- Response length: short / default / detailed
- Goal setting for focused conversations
- Save chat as notes → convert notes into new sources

### Citations
- All responses include inline citations linking back to original sources
- Click citation to jump to the relevant passage in the source
- Background playback during Audio allows citation checking

## Sharing

### Consumer Accounts (Gmail)
- Set "Anyone with the link" access
- Share options: Full notebook OR chat-only
- Viewers need a Google account
- Maximum 50 shared users per notebook
- Google Groups NOT supported

### Enterprise / Education
- Share within same organization only
- **Viewer:** view only
- **Editor:** view, add/remove sources and notes, share further
- Google Groups supported
- Unlimited individual users within org

### Audio Overview Sharing
- Independent link sharing (separate from notebook sharing)
- Download as MP3 for distribution
- Deleting the Audio Overview invalidates the shared link

## Integrations

### Gemini Canvas
- Upload entire notebook to Gemini
- Generate slides, charts, or websites from notebook content

### GitHub Integration
- Replace "github.com" with "gittodoc.com" in repo URL
- Import entire repository as a source for code analysis

### Chrome Extensions
- **NotebookLM Web Importer** — batch import browser tabs, RSS feeds, YouTube playlists
- **Fold LM** — add folder organization (workaround for no native folders)

## Timeline of Major Updates

| Date | Update |
|------|--------|
| Jul 2023 | NotebookLM launched (Google Labs experiment) |
| Dec 2024 | NotebookLM Plus announced |
| Feb 2025 | Available as Google Workspace core service |
| Apr 2025 | Audio Overview expanded to 50+ languages |
| Jul 2025 | Video Overviews rolled out globally |
| Sep 2025 | Audio upgraded to 80+ languages + new formats |
| Nov 2025 | Deep Research tool + more file types |
| Late 2025 | Ultra tier ($249.99/mo), Mind Maps, Flashcards, etc. |
| 2026 | Gemini integration, mobile app, public notebook analytics |
