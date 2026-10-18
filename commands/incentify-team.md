---
name: incentify-team
description: Show the current state of the user's Incentify team — who is on, who is late, and what is pending approval.
---

Report the live state of the user's team.

1. `GetTeamLiveStatus` for who is clocked in, late or absent.
2. `GetTeamTrackerSnapshot` for coverage against the schedule.
3. `GetTeamRequests` for leave, swap and claim requests awaiting a decision.

Lead with gaps: uncovered shifts, no-shows, and requests that have been waiting
longest. Then the roll-up.

If the user lacks manager permissions, `GetMyPermissions` will say so — report
that plainly instead of falling back to their own data.

Read only — approvals and assignments need their own explicit confirmation.
