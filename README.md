# Time Machine — Claude Code Plugin

Bring your Time Machine learning platform into Claude Code. This plugin exposes **119 MCP tools** covering courses, modules, exercises, quizzes, users, documents, AI experts, and student analytics — directly from your Claude Code sessions.

## What is Time Machine

[Time Machine](https://timeml.ai) is an AI-powered corporate learning platform for sales enablement, onboarding, and L&D teams. Organizations use it to transform existing documents, recordings, and workflows into scalable training experiences that accelerate onboarding, improve workforce readiness, and replicate top-performer expertise.

## What you get

Once installed, Claude Code can operate on your Time Machine tenant on your behalf:

- **Courses** — list, create, update, publish, archive; assign to roles; AI-generate full content from a plan
- **Modules & Topics** — build course structure with a natural-language description
- **Lessons & Exercises** — author text lessons, role-play voice/video exercises, and knowledge-check questions
- **Quiz questions** — MULTIPLE_CHOICE and OPEN_ENDED at lesson, topic, and module scope
- **Users** — invite via magic-link, deactivate, reactivate; assign to departments and roles
- **Documents & Media** — manage the knowledge base backing your AI experts
- **AI experts** — create persona-based experts and ask them grounded questions over your documents
- **Student insights** — completion rates, time-spent, per-course progress
- **Certificates** — list student certificates and retrieve PDFs
- **Demo trainings** — create video-based trainings and re-process transcripts

## Install

```bash
/plugin marketplace add Time-Machine-Learning/claude-plugin
/plugin install time-machine
```

On first use of any `tml_*` tool, Claude Code opens a browser window to the Time Machine login page. Sign in with your existing Time Machine account (passwordless magic-link), approve the requested scope, and you're done. Your OAuth token is stored securely by Claude Code — no API keys or environment variables required.

## Verify

Ask Claude:

> "What tools do you have from the Time Machine server?"

Claude lists 119 tools starting with `tml_`. Then try:

> "List the courses in my company."

Claude calls `tml_list_courses` and shows the results, scoped to your tenant.

## Server info

| Property | Value |
|---|---|
| Server name | `time-machine` |
| MCP protocol | Streamable HTTP |
| Production URL | `https://api.timeml.ai/api/v1/mcp` |
| Authentication | OAuth 2.1 with PKCE + Dynamic Client Registration (RFC 7591) |
| Tools exposed | 119 |
| Documentation | <https://api.timeml.ai/oauth/docs> |

## Prerequisites

- **Claude Code** installed — see the [Claude Code docs](https://code.claude.com/docs)
- An active Time Machine account with a role in one or more tenants
  - `ADMIN` for content authoring and user management
  - Any role for read-only queries and expert Q&A

If you don't have a Time Machine account, contact <sales@timeml.ai>.

## Security

- OAuth 2.1 with PKCE — Claude Code authenticates as your existing Time Machine user
- Per-user permissions and per-tenant isolation enforced at the API layer
- Access tokens are RS256-signed JWTs, verifiable against the public JWKs endpoint
- Refresh tokens rotate on every use
- Revoke access anytime from Time Machine account settings or by uninstalling the plugin

## Support

- **Docs:** <https://api.timeml.ai/oauth/docs>
- **Issues:** <https://github.com/Time-Machine-Learning/claude-plugin/issues>
- **Email:** <support@timeml.ai>

## License

[MIT](./LICENSE)