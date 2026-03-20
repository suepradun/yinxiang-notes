# yinxiang-notes

Evernote China (印象笔记) integration skill for OpenClaw. Create, organize, and search notes using Developer Token.

## Features

| Feature | Description |
|---------|-------------|
| **List Notebooks** | Get all notebooks with optional note count |
| **List Tags** | View all tags in your account |
| **Create Notes** | Create notes with title, content (ENML), notebook and tags |
| **Update Notes** | Update title, content, add/remove tags |
| **Delete Notes** | Move notes to trash (recoverable) |
| **Search Notes** | Search by keywords, title, date, etc. |
| **Sync to Obsidian** | Incremental sync to local Obsidian vault |
| **Trash Management** | View and empty trash |

## Prerequisites

1. **Developer Token**: Get from https://app.yinxiang.com/api/DeveloperToken.action
2. **Python 3.7+**
3. **SDK**: `pip install evernote3 thrift html2text`

## Configuration

Create a `.env` file:

```
EVERNOTE_TOKEN=S=s16:U=xxx:E=xxx:C=xxx:P=xxx:A=en-devtoken:V=2:H=xxx
EVERNOTE_NOTESTORE_URL=https://app.yinxiang.com/shard/s16/notestore
```

## Quick Start

```bash
# List notebooks
python scripts/list_notebooks.py

# Create a note
python scripts/create_note.py --title "My Note" --content "<en-note>Content</en-note>"

# Search notes
python scripts/search_notes.py "keyword"

# Sync to Obsidian
python scripts/sync_to_obsidian.py
```

## Scripts

| Script | Description |
|--------|-------------|
| `list_notebooks.py` | List all notebooks |
| `list_tags.py` | List all tags |
| `create_note.py` | Create a new note |
| `update_note.py` | Update note title/content/tags |
| `delete_note.py` | Move note to trash |
| `search_notes.py` | Search notes |
| `sync_to_obsidian.py` | Incremental sync to Obsidian vault |
| `list_trash.py` | View trash |
| `empty_trash.py` | Permanently delete trash |

## Sync to Obsidian

Syncs notes to your local vault (`C:\Users\adun\Documents\印象笔记同步` by default).

**Note types handled**:
- Attachments (files with extension)
- Embedded images
- Plain text notes
- Web clips (converted to Markdown or stored as HTML)

**Frontmatter added**:
```yaml
---
title: Note Title
created: 2026-03-19 10:30:00
updated: 2026-03-19 14:22:00
source: Evernote
source_guid: xxx-xxx-xxx
notebook: Notebook Name
---
```

## License

MIT
