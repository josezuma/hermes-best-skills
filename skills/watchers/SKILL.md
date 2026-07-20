---
name: watchers
description: "Use when monitoring RSS feeds, JSON APIs, or GitHub endpoints for changes. Tracks seen items via watermark dedup to avoid duplicate notifications."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [monitoring, rss, api, cron, dedup]
    related_skills: [blogwatcher, cronjob]
---

# Watchers — Cron-Based Change Detection

## Overview

The `watchers` skill implements a lightweight change-detection pattern using Hermes cron jobs. It polls RSS feeds, JSON API endpoints, or GitHub commits, tracks a "watermark" (last-seen cursor) per target, and reports only new items since the last poll.

This is useful for:
- Monitoring competitor blog posts
- Detecting new GitHub releases
- Watching API endpoints for data changes
- Content tracking without external monitoring services

## When to Use

- You need to monitor a recurring data source (RSS, JSON API, GitHub)
- The source does not offer webhooks
- The poll interval can tolerate minutes to hours
- You already have a `cronjob` scheduled for periodic work

Do NOT use for: real-time monitoring (sub-second latency), high-volume streaming (use dedicated event infrastructure), or sources that offer webhooks (use those first).

## How It Works

1. A cron job runs on a schedule (e.g., every hour)
2. The job reads a watermark file (saved to `~/.hermes/data/watchers/<name>.json`)
3. The job fetches the latest data from the target endpoint
4. It filters out items older than the watermark (or dedup by ID)
5. New items are reported in the cron job output
6. The watermark is updated to the latest seen timestamp/ID

## Implementation

```python
# Minimal watcher script template
import json, pathlib, time, requests

WATCHER = "my-feed"
DATA_DIR = pathlib.Path.home() / ".hermes" / "data" / "watchers"
DATA_DIR.mkdir(parents=True, exist_ok=True)
WATERMARK_FILE = DATA_DIR / f"{WATCHER}.json"

# Load previous watermark
watermark = {}
if WATERMARK_FILE.exists():
    watermark = json.loads(WATERMARK_FILE.read_text())

# Fetch data
resp = requests.get("https://example.com/api/items", timeout=30)
items = resp.json()

# Filter new items
cutoff = watermark.get("last_seen", 0)
new_items = [i for i in items if i["id"] > cutoff]

# Report
if new_items:
    print(f"Found {len(new_items)} new items:")
    for item in new_items:
        print(f"  - {item['title']}: {item['url']}")
else:
    print("No new items.")

# Update watermark
if items:
    watermark["last_seen"] = max(i["id"] for i in items)
    WATERMARK_FILE.write_text(json.dumps(watermark, indent=2))
```

## Common Pitfalls

1. **Watermark drift** — If the source does not guarantee monotonic IDs, use timestamps
2. **API rate limits** — Respect `Retry-After` headers from polling too frequently
3. **Token expiry** — Cron jobs run with no user present; use long-lived API tokens
4. **Hardcoded paths** — Always use `pathlib.Path.home()` so the watcher works on any machine

## Verification Checklist

- [ ] Watcher script can run standalone and produces output
- [ ] Watermark file is created after first run
- [ ] Second run reports "No new items" (if no data changed)
- [ ] Cron schedule is set and cron list shows the job
