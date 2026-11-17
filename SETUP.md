# Setup — Time Machine Claude Code Plugin

Install the plugin, then sign in via magic-link the first time you use a tool.

## Install

```bash
/plugin install time-machine --marketplace Time-Machine-Learning/claude-plugin
```

On Claude Code versions before 2.1.275:

```bash
/plugin marketplace add Time-Machine-Learning/claude-plugin
/plugin install time-machine@time-machine
```

## Sign in

1. Run `/mcp`, select `plugin:time-machine:time-machine` and choose **Authenticate**
2. A browser window opens the Time Machine login page (`https://api.timeml.ai/login`)
3. Enter the email of your existing Time Machine account and click **Continue**
4. Check your inbox for a magic-link email and click the link
5. Review the requested scope on the consent screen and click **Authorize**
6. You are returned to Claude Code — the tools are ready

Your OAuth access token is stored by Claude Code. When the sign-in expires, Claude Code reports that the Time Machine server needs authentication: repeat the steps above.

## Verify

Ask Claude:

> "What tools do you have from the Time Machine server?"

You should see tools whose names start with `tml_`.

## Before you generate content

- **Courses** — AI content for a topic is built from the documents linked to it. Upload documents in Time Machine, wait until they are processed, and ask Claude to link them to the topics before generating content.
- **Demo trainings** — upload the recording in Time Machine first. Use a recording of a sales demo, presentation or product walkthrough; promotional videos are rejected during processing.

## Revoke access

- **From Claude Code** — run `/mcp`, select `plugin:time-machine:time-machine` and clear its authentication, or uninstall with `/plugin uninstall time-machine`
- **From Time Machine** — contact <support@timeml.ai> to revoke the connection on the server

## Troubleshooting

| Symptom | Fix |
|---|---|
| `/plugin marketplace add` fails | Update Claude Code, then run the install commands again. |
| Browser does not open on Authenticate | Confirm Claude Code has network access, then run `/mcp` and choose **Authenticate** again. |
| Magic-link email does not arrive | Check spam folder. Time Machine throttles resends — wait 5 minutes and try again. |
| The server needs authentication again | The sign-in expired. Run `/mcp`, select `plugin:time-machine:time-machine` and choose **Authenticate**. |
| A generated topic has no lessons | No document was linked to the topic. Link a processed document and generate the topic again. |
| Claude reports no tools from server | The sign-in did not finish. Run `/mcp` and authenticate again. |

## Security notes

- OAuth tokens are stored by Claude Code, not in shell profiles or env vars
- Each token is scoped to one Time Machine user and one tenant via the `companyId` claim in the JWT
- Full security details: <https://api.timeml.ai/oauth/docs>
- Privacy Policy: <https://timeml.ai/privacy-policy>
