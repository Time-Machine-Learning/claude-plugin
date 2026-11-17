# Time Machine — Claude Code Plugin

Bring your Time Machine learning platform into Claude Code. This plugin connects Claude Code to the Time Machine MCP server, which exposes tools for courses, modules, exercises, role plays, quizzes, users, documents, AI experts, demo trainings and student analytics — directly from your Claude Code sessions.

## What is Time Machine

[Time Machine](https://timeml.ai) is an AI-powered corporate learning platform for sales enablement, onboarding, and L&D teams. Organizations use it to transform existing documents, recordings, and workflows into scalable training experiences that accelerate onboarding, improve workforce readiness, and replicate top-performer expertise.

## What you get

Once installed, Claude Code can operate on your Time Machine tenant on your behalf:

- **Courses** — list, create, update, publish, archive; assign to roles; AI-generate lessons and questions for topics
- **Modules & Topics** — build course structure and link documents to topics
- **Lessons & Exercises** — author text lessons, voice and video role-play exercises, and knowledge-check questions
- **Quiz questions** — MULTIPLE_CHOICE and OPEN_ENDED at lesson, topic, and module scope
- **Users** — invite via magic-link, deactivate, reactivate; assign to departments and roles
- **Documents & Media** — manage the knowledge base backing your courses and AI experts
- **AI experts** — create persona-based experts and ask them grounded questions over your documents
- **Student insights** — completion rates, time-spent, per-course progress
- **Certificates** — list student certificates and retrieve PDFs
- **Demo trainings** — create video-based trainings and re-process them

AI-generated course content is built from the documents linked to each topic, so upload your documents to Time Machine first. Demo trainings are built from recordings of a sales demo, presentation or product walkthrough that are already uploaded to Time Machine.

## Install

```bash
/plugin install time-machine --marketplace Time-Machine-Learning/claude-plugin
```

On Claude Code versions before 2.1.275, add the marketplace first:

```bash
/plugin marketplace add Time-Machine-Learning/claude-plugin
/plugin install time-machine@time-machine
```

The first time a `tml_*` tool is used, sign in: run `/mcp`, select `plugin:time-machine:time-machine`, and choose **Authenticate**. A browser window opens the Time Machine login page. Sign in with your existing Time Machine account (passwordless magic-link), approve the requested scope, and you're done. Your OAuth token is stored by Claude Code — no API keys or environment variables required.

## Verify

Ask Claude:

> "What tools do you have from the Time Machine server?"

Claude lists the tools whose names start with `tml_`. Then try:

> "List the courses in my company."

Claude calls `tml_list_courses` and shows the results, scoped to your tenant.

## What the plugin connects to

The plugin contains no local code, hooks, commands or scripts. It adds one remote MCP server:

| Property | Value |
|---|---|
| Server name | `time-machine` |
| MCP protocol | Streamable HTTP |
| URL | `https://api.timeml.ai/api/v1/mcp` |
| Authentication | OAuth 2.1 with PKCE + Dynamic Client Registration (RFC 7591) |
| Documentation | <https://api.timeml.ai/oauth/docs> |

Every tool call sends its arguments to that server and returns data from your Time Machine tenant. Nothing is sent anywhere else.

## Prerequisites

- **Claude Code** installed — see the [Claude Code docs](https://code.claude.com/docs)
- An active Time Machine account with a role in a tenant
  - An admin role for content authoring and user management
  - Any role for read-only queries and expert Q&A

If you don't have a Time Machine account, contact <sales@timeml.ai>.

## Security

- OAuth 2.1 with PKCE — Claude Code authenticates as your existing Time Machine user
- Per-user permissions and per-tenant isolation enforced at the API layer
- Access tokens are RS256-signed JWTs, verifiable against the public JWKs endpoint
- When the sign-in expires, Claude Code asks you to authenticate again from `/mcp`

## Privacy

- **Privacy Policy:** <https://timeml.ai/privacy-policy>
- **Terms of Service:** <https://timeml.ai/terms-of-service>

## Support

- **Docs:** <https://api.timeml.ai/oauth/docs>
- **Issues:** <https://github.com/Time-Machine-Learning/claude-plugin/issues>
- **Email:** <support@timeml.ai>

## License

[MIT](./LICENSE)
