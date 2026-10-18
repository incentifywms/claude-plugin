---
name: incentify-day
description: Summarize the user's Incentify day — shift, clock state, tasks due and anything waiting on them.
---

Pull the user's current Incentify day and summarize it.

1. `GetCurrentDate` for the workspace's today.
2. `GetMyDaySummary` for shift, breaks and clock state.
3. `GetMyTasks` for what is due or in progress.
4. `ListMyNotifications` for anything waiting on them.

Report as a short brief: where and when they work today, whether they are
clocked in, what is due, and what needs a decision from them. Flag anything
overdue or unacknowledged first.

Read only — do not clock, start, or complete anything from this command.
