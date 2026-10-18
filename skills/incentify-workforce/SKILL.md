---
name: incentify-workforce
description: Use when the user asks about their own or their team's shifts, schedule, clock-in/out, attendance, timesheets, leave balances, tasks, KPIs, points, rewards or recognition — or names Incentify. Covers how to read Incentify data safely and how to confirm before writing.
---

# Working with Incentify

Incentify is a workforce platform: scheduling, time and attendance, tasks,
performance and rewards. The `incentify` MCP server exposes it as tools.

## Read before you answer

Never answer a workforce question from memory or from an earlier turn's data —
shifts get swapped, clocks run, approvals land. Call a tool.

Common entry points:

| The user asks | Start with |
|---|---|
| "what's on today?" | `GetMyDaySummary` |
| "am I clocked in?" / "clock me in" | `ClockAction` |
| "what do I owe?" | `GetMyTasks`, `GetMyKpis` |
| "how's the team right now?" | `GetTeamLiveStatus`, `GetTeamTrackerSnapshot` |
| "who's off / who asked for leave?" | `GetTeamRequests`, `ListMyLeavePolicies` |
| "how many points do I have?" | `GetMyPoints`, `ListRewardCatalog` |
| anything you can't place | `SearchEverything` |

`GetCurrentDate` first whenever the user says "today", "this week" or
"tomorrow" — do not assume the host clock matches their workspace timezone.

## Permissions are the user's, not yours

Every tool runs as the signed-in Incentify user, scoped to their role. If a
call comes back empty or forbidden, that is the answer — report it. Do not
retry through a different tool hoping for wider access, and do not reconstruct
a restricted figure by combining calls the user can make.

`GetMyPermissions` and `GetMyPlanModules` tell you what is actually available
before you promise a capability.

## Confirm every write

Tools that change data — clocking, claiming or swapping shifts, assigning or
completing tasks, submitting leave, issuing a write-up, spending recognition
budget, redeeming a reward, posting to a feed — change a real record that other
people see, and some of them spend real money or affect someone's pay.

Show the user exactly what will change and wait for a clear yes:

> Clocking you in at the Main Branch site, 08:12 local. Confirm?

One approval covers one action. A yes to clocking in is not a yes to also
submitting a leave request. Batch tools (`BulkAssignTaskToMembers`,
`BulkUnassignShifts`, `BulkDecideSwapRequests`) need the full list in the
preview, not a count.

Never issue a write-up, reject a request, or spend another person's budget on
the strength of a tool result alone — those read as management decisions and
belong to the user.

## Reporting back

Lead with the answer, not the plumbing. "You're on 14:00–22:00 at Main Branch,
with a 30-minute break at 17:30" beats narrating which tools you called.

Numbers that came from a report tool (`GetTimesheetReport`, `GetScheduleCost`,
`GetHoursCostSummary`) carry a period — say which period, or the number is
unreadable.
