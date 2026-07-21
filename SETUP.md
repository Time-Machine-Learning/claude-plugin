# Setup — Time Machine Claude Code Plugin

Two steps: get your API key, then export it to your shell.

## 1. Issue an API key

1. Sign in to the Time Machine admin UI at <https://web.timeml.ai> as an **ADMIN** user.
2. Open **Settings → API Keys**.
3. Click **Issue key**, give it a name (e.g. `Claude Code — my laptop`), and click **Create**.
4. **Copy the secret immediately.** The key is shown once and cannot be retrieved later. If you lose it, you have to rotate.

Key format: `tml_live_<24 random chars>` — e.g. `tml_live_uI8AFrlHeJ4jGqCzmqRQ3SCQ`.

The key is bound to **one company**. Every tool call is auto-scoped to that company — there is no way to reach another tenant's data with your key.

## 2. Export the key to your shell

Claude Code reads the key from the `TIME_MACHINE_API_KEY` environment variable.

**macOS / Linux (zsh):**

```bash
echo 'export TIME_MACHINE_API_KEY="tml_live_..."' >> ~/.zshrc
source ~/.zshrc
```

**macOS / Linux (bash):**

```bash
echo 'export TIME_MACHINE_API_KEY="tml_live_..."' >> ~/.bashrc
source ~/.bashrc
```

**Windows (PowerShell):**

```powershell
[Environment]::SetEnvironmentVariable("TIME_MACHINE_API_KEY", "tml_live_...", "User")
```

Then restart your terminal.

## 3. Verify

Start Claude Code and ask:

> "What tools do you have from the Time Machine server?"

You should see 116 tools starting with `tml_`. If Claude reports the server is unreachable or unauthorized, see [Troubleshooting](#troubleshooting) below.

## Rotation

To rotate the key: **Settings → API Keys → … → Rotate**. Update `TIME_MACHINE_API_KEY` in your shell profile with the new secret. The old secret stops working immediately.

## Revocation

To revoke the key: **Settings → API Keys → … → Revoke**. All calls with that key return `401 Unauthorized` from that point on. Revocation is permanent — issue a new key if access is needed again.

## Troubleshooting

| Symptom | Fix |
|---|---|
| `401 Unauthorized` | Key is missing, malformed, or revoked. Verify `TIME_MACHINE_API_KEY` is set and starts with `tml_live_`. Re-issue if needed. |
| `403 Forbidden` | Key is valid but lacks the required role. All keys are ADMIN today, so this is rare. Contact support if it happens. |
| Claude reports the server has no tools | The `TIME_MACHINE_API_KEY` env var isn't visible to Claude Code. Restart your terminal after editing `~/.zshrc` / `~/.bashrc`. |
| `${TIME_MACHINE_API_KEY}` appears literally in requests | The env var isn't exported. Confirm with `echo $TIME_MACHINE_API_KEY` in the same terminal where you launch Claude Code. |

## Security notes

- Never commit `TIME_MACHINE_API_KEY` to source control. Keep it in your shell profile or a secret manager.
- Each API key is bound to one company. Do not share keys across tenants.
- Prefer per-machine keys — if a laptop is lost, rotate that laptop's key without disrupting others.