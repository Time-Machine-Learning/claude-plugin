# Setup — Time Machine Claude Code Plugin

Two commands to install, then sign in via magic-link the first time you use a tool.

## Install

```bash
/plugin marketplace add Time-Machine-Learning/claude-plugin
/plugin install time-machine
```

## Sign in

On first use of any `tml_*` tool, Claude Code opens a browser window to the Time Machine login page (`https://api.timeml.ai/login`).

1. Enter the email of your existing Time Machine account
2. Click **Continue**
3. Check your inbox for a magic-link email and click the link
4. Review the requested scope on the consent screen and click **Authorize**
5. You are returned to Claude Code — the tools are ready

Your OAuth access token is stored securely by Claude Code. Refresh tokens rotate automatically — no re-login needed unless you explicitly sign out.

## Verify

Ask Claude:

> "What tools do you have from the Time Machine server?"

You should see 119 tools starting with `tml_`.

## Revoke access

Two options:

1. **From Time Machine** — Settings → Connected Apps → Revoke `Claude Code`
2. **From Claude Code** — `/plugin uninstall time-machine`

## Troubleshooting

| Symptom | Fix |
|---|---|
| Browser does not open on first use | Confirm Claude Code has network access. Try `/plugin uninstall time-machine` and reinstall. |
| Magic-link email does not arrive | Check spam folder. Time Machine throttles resends — wait 5 minutes and try again. |
| `401 Unauthorized` after weeks of use | Refresh token expired. Sign in again — Claude Code opens the browser automatically. |
| Wrong tenant showing up | Your account has multiple tenant memberships. Contact <support@timeml.ai> to switch default. |
| Claude reports no tools from server | Initial OAuth handshake failed. `/plugin uninstall time-machine` → reinstall → retry. |

## Security notes

- OAuth tokens are stored in Claude Code's secure credentials store, not in shell profiles or env vars
- Each token is scoped to one Time Machine user and one tenant via the `companyId` claim in the JWT
- Revoking from Time Machine invalidates all tokens for that connection immediately
- Full security details: <https://api.timeml.ai/oauth/docs>