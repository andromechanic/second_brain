# AGENTS.md — Akhil's Digital Brain

## PURPOSE
This repository is a personal HTML knowledge base / digital brain.

Core workflow:
Raw notes → understand → locate relevant page → edit HTML → update links/index → update SQLite graph → Git.

## RULES
1. Read this file before changes.
2. Read only files relevant to the current note.
3. HTML is the source of truth for actual knowledge.
4. SQLite is a fast index/search/graph layer, not the permanent note store.
5. Use one shared stylesheet: `css/style.css`.
6. Prefer reusable CSS classes over inline styles.
7. Make the smallest correct edit.
8. Never delete user knowledge silently.
9. Use Gemini only for semantic tasks; deterministic work should be done locally.
10. Minimize Gemini tokens by searching SQLite first and sending only compact, relevant context.
11. Before creating a page, search existing pages/concepts.
12. Keep the repository portable and GitHub-friendly.
13. Never commit API keys or secrets.
14. Keep agent completion replies short and token-efficient. Do not restate or re-explain note contents.
15. Write in an enduring, conceptual tone for general knowledge. Never frame notes as exam prep, study guides, or student cheat sheets (avoid "exam trick", "exam shortcut", "cheat sheet", etc.).

## NOTE WORKFLOW
The user writes raw material into `inbox.md`.

Process:
1. Read `inbox.md`.
2. Search SQLite for relevant existing concepts/pages.
3. Inspect only candidate HTML pages.
4. Ask Gemini for semantic organization only when needed.
5. Update the correct HTML page(s).
6. Add/update links and graph relationships.
7. Update SQLite.
8. Update `index.html` only when the page structure changes.
9. Clear `inbox.md` after successful processing.
10. Keep a Git history of meaningful changes.
11. Reply with a short summary (changed files, graph edges, git status) to minimize output tokens.

## GEMINI TOKEN MINIMIZATION
Never send the whole repository or whole knowledge base to Gemini.

Use:
raw note → local SQLite/FTS search → top candidates → compact excerpts/summaries → Gemini.

Do not use Gemini for file I/O, sorting, link generation, timestamps, indexing, or other deterministic operations.

Keep assistant responses brief (2–4 lines max). Report only the affected page links, graph updates, and git commit status. Never regurgitate note contents back to the user.

## KNOWLEDGE GRAPH
Every knowledge page should have stable metadata such as:

<meta name="knowledge-id" content="concept-example">
<meta name="title" content="Example">
<meta name="type" content="concept">
<meta name="parent" content="topic-example">
<meta name="tags" content="tag1,tag2">

SQLite stores nodes and edges.

Relations include:
related, prerequisite, contains, extends, example-of, depends-on, contrasts-with, references.

The Digital Brain visualization reads the SQLite graph.

## GIT
Never force-push. Never commit secrets.
Use clear commits such as:
notes: add transformer self-attention
style: refine note callouts
index: add reinforcement learning section

## GOLDEN RULE
The user should feel like they are writing into their own brain, not managing a database.
