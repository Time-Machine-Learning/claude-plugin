# Time Machine — Claude Code Plugin

Bring your Time Machine learning platform into Claude Code. This plugin exposes **116 MCP tools** that mirror the Time Machine public REST API, so you can manage courses, users, documents, experts, and analytics directly from your Claude sessions.

## What is Time Machine

[Time Machine](https://timeml.ai) is an AI-powered organizational learning platform that helps companies build, operate, and continuously improve adaptive learning systems for modern teams. Organizations use Time Machine to transform existing knowledge, documents, recordings, and workflows into scalable training experiences that accelerate onboarding, improve workforce readiness, and replicate top-performer expertise.

## What you get

Once installed, Claude can operate on your Time Machine tenant on your behalf:

- **Courses** — list, create, update, publish, and delete courses; assign roles; generate AI-authored content
- **Users** — list, create, deactivate, and reactivate users; magic-link invitations
- **Documents & Media** — upload, replace, delete files that feed your knowledge base
- **Departments & Roles** — organize your workforce and route learning content by role
- **Experts** — expose subject-matter experts; ask them questions programmatically
- **Demo Trainings** — create and reprocess demo training exercises
- **Course Content** — modules, topics, lessons, exercises, quiz questions
- **Insights** — per-student, per-course, and company-level analytics
- **Certificates** — list student certificates, download certificate PDFs

Full endpoint reference: <https://api.timeml.ai/api/v1/docs>

## Prerequisites

- **Claude Code** installed and configured — see the [Claude Code docs](https://code.claude.com/docs)
- An active Time Machine tenant with **admin** access
- A Time Machine API key — issued from **Settings → API Keys** in the admin panel at <https://web.timeml.ai/settings/api-keys>. The key format is `tml_live_<24 chars>`

## Install

```bash
claude plugin install github.com/1shushi1/claude-plugin
```

Then follow [SETUP.md](./SETUP.md) to configure your API key.

## Verify

After setup, ask Claude:

> "What tools do you have from the Time Machine server?"

Claude should list 116 tools starting with `tml_`. Then try:

> "List the courses in my company."

Claude will call `tml_list_courses` and show the results.

## Server info

| Property | Value |
|---|---|
| Server name | `time-machine` |
| MCP protocol version | `2024-11-05` |
| Transport | Streamable HTTP |
| Production URL | `https://api.timeml.ai/api/v1/mcp` |
| Auth | API key — Bearer token (same as REST) |
| Tools exposed | 116 |

## Support

- **Docs:** <https://api.timeml.ai/api/v1/docs>
- **Issues:** <https://github.com/1shushi1/claude-plugin/issues>
- **Email:** <support@timeml.ai>

## License

[MIT](./LICENSE)