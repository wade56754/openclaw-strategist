## Heartbeat Checklist

### 📥 Inbox Check (every heartbeat)
- Check `work/inbox/` — process any files, then clear

### 🔄 Decision Review (weekly)
- Scan `decisions/` directory
- Find decisions older than 30 days with empty "Review" section
- Remind user to review

### 🧠 Memory Maintenance (every heartbeat)
- Scan recent 2 days of `memory/YYYY-MM-DD.md`
- `[in-progress]` over 24h → move to `MEMORY.md ## Pending Tasks`
- Same pattern ≥ 2 times → extract to `MEMORY.md`
- `×N≥3` in MEMORY.md → add `[promote]` flag
