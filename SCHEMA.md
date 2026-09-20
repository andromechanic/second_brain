# SCHEMA.md — Akhil's Digital Brain

## Storage
HTML = knowledge source of truth
SQLite = search/index/graph cache

## SQLite
### pages
id TEXT PRIMARY KEY
title TEXT NOT NULL
path TEXT NOT NULL UNIQUE
type TEXT
summary TEXT
tags TEXT
updated_at TEXT

### concepts
id TEXT PRIMARY KEY
title TEXT NOT NULL
summary TEXT
page_id TEXT

### edges
source_id TEXT NOT NULL
target_id TEXT NOT NULL
relation TEXT NOT NULL
PRIMARY KEY (source_id, target_id, relation)

## HTML page metadata
<meta name="knowledge-id" content="concept-example">
<meta name="title" content="Example">
<meta name="type" content="concept">
<meta name="parent" content="topic-example">
<meta name="tags" content="tag1,tag2">

## Shared CSS
Use css/style.css and reusable classes.
