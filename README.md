# Incentify for Claude Code

Connect Claude to your [Incentify](https://incentify.cloud/) workspace —
scheduling, time and attendance, tasks, performance and rewards — and ask about
your work in plain language.

## Install

```bash
claude plugin marketplace add incentifywms/claude-plugin
claude plugin install incentify@incentify
```

Then start a new session. The first Incentify tool call opens a standard
OAuth 2.1 sign-in: you authenticate with your Incentify service code, email and
password and approve the connection. Access is scoped to your own account and
mirrors the permissions your Incentify role already has.

The plugin ships no credentials and stores no tokens of its own.

## What you get

**Commands**

- `/incentify-day` — your shift, clock state, tasks due and anything waiting on you
- `/incentify-team` — who's on, who's late, and what's pending approval

**Skill**

`incentify-workforce` loads automatically when you ask about shifts, attendance,
timesheets, leave, tasks, KPIs, points or recognition. It keeps Claude reading
live data rather than guessing, and makes it confirm before anything is written
back to Incentify.

**MCP server**

`https://api.incentify.cloud/mcp` — the full Incentify tool surface, also usable
from Claude.ai, ChatGPT or any other MCP host. See
[incentify.cloud/mcp](https://incentify.cloud/mcp).

## Privacy

Tools run as you. Changes such as clocking in or out, submitting leave or acting
on another employee's work show you a preview and wait for your confirmation. A
small set of low-risk changes to your own data, such as updating your own tasks
or toggling a break, can run without that step. Access tokens last one hour; a
30-day refresh token keeps the connection alive without re-entering your
password.

Questions: support@incentify.cloud

## License

[MIT](LICENSE)
