# dayflow-export

Export [Dayflow](https://github.com/JerryZLiu/Dayflow) activity data to markdown transcripts for consumption by Claude or other LLMs.

## What it does

Generates daily markdown files from Dayflow's SQLite database containing:

- **Timeline cards** with category, apps/sites, and activity summaries
- **Detailed observations** with timestamps (when available)
- **Screenshot links** (sampled, up to 5 per observation period)
- **Distractions** noted during each activity period

## Installation

```bash
git clone https://github.com/obra/dayflow-export.git
cd dayflow-export
```

No dependencies required - uses only Python 3 standard library.

## Usage

```bash
# Export all days not yet exported (incremental)
./dayflow-export /path/to/Dayflow

# Export a specific date
./dayflow-export /path/to/Dayflow --date 2025-12-17

# Export a date range (overwrites existing files)
./dayflow-export /path/to/Dayflow --from 2025-12-14 --to 2025-12-17
```

The Dayflow data directory is typically:
- macOS: `~/Library/Application Support/Dayflow`

## Output

Creates a `transcripts/` directory inside your Dayflow data folder:

```
Dayflow/
├── chunks.sqlite
├── recordings/
│   └── *.jpg
└── transcripts/          # Created by dayflow-export
    ├── 2025-12-14.md
    ├── 2025-12-15.md
    └── ...
```

Each markdown file contains the full activity log for that day, with relative links to screenshots in `../recordings/`.

## Example output

```markdown
# Activity Log: 2025-12-17

## 9:13 AM - 9:43 AM: Debugged code and researched Claude

**Category:** Work > Software Development
**Apps/Sites:** terminal, claude.ai

### Summary

Worked on code, running commands in the terminal...

### Detailed Activity

**9:13 AM - 9:21 AM:**
User is actively engaged in debugging, reviewing error messages...

![](../recordings/20251217_091344027.jpg)
![](../recordings/20251217_091453753.jpg)

---
```

## License

MIT
