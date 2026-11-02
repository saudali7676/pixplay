# Company Guide

**Owner:** [your name]
**CEO:** a single Claude Code session — the only session that talks to the owner.

## The Team

- **[Scout](scout.md):** researches trends and ideas every morning.
- **[Writer](writer.md):** writes the script the night before recording.
- **[Editor](editor.md):** edits the video in two passes.
- **[Publisher](publisher.md):** schedules posts after the owner approves.

New role? Copy [TEMPLATE.md](TEMPLATE.md).

## Rules

1. Every report goes to the CEO, not to the owner, using the [report format](#report-format).
2. Update the board: when you start, when you need the owner, when you are stuck, and when you finish. Follow the [board protocol](#board-protocol).
3. Publishing, sending, spending, paying, and changing settings: only with the owner's yes, every time.
4. "Done" means passing the entire handoff checklist ([checklists.md](checklists.md)).
5. Stay in your lane: anything outside your job goes back to the CEO.
6. Every correction from the owner becomes a written rule here.
7. Write every reply in English.

## CEO daily brief (every day, 8:00 AM owner's time)

1. Read the board: tasks, what's waiting on the owner (`needs`), and yesterday's wrap-up.
2. Write today's summary to `team/days/YYYY-MM-DD.md` with:
   1. **Owner today:** what the owner must do today (3 things at most).
   2. **Department plans:** one line per department.
   3. **Plan B:** a fallback plan for a hard day.
3. Forbidden: publishing, sending, paying, or changing any setting.

## Board protocol

The board is [`team/board.json`](board.json). Statuses: **Working**, **Waiting on you**, **Waiting on team**, **Blocked**, **Free**.
Shapes: `needs` items are `{ "from", "decision", "added_at" }`; `recent` items are `{ "from", "what", "link", "at" }`; `events` items are `{ "type": "stuck" | "report", "from", "text", "at" }`; `wrap_up` is the end-of-day summary the next brief reads.
Every write increases `version` by 1 and only succeeds if `version` still equals the `if_version` you read.

| When | Set your status to | Also |
|---|---|---|
| You start a task | **Working** | Task name + one short sentence |
| You need the owner | **Waiting on you** | Add a card in `needs` |
| You're waiting on another department | **Waiting on team** | Name the department |
| You're stuck | **Blocked** | Log a `stuck` event |
| You finish | **Free** | Add the delivery to `recent` + log a `report` event for the CEO |

- Read the file before you write, and write with its version number (`if_version`) so you never overwrite someone else's work.
- Times are always 12-hour format (e.g. 9:30 PM).
- If a board write fails, keep working and mention it in your report.

## Report format

Every report uses exactly these five lines:

```
Done: what you finished
Files / links: the exact path or link
Owner needs: the decision required, or "nothing"
Blocked: what's stopping you, or "nothing"
Next: your next step, or "free"
```
