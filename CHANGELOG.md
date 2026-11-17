# Changelog

All notable changes to the Time Machine Claude Code plugin will be documented here.

## [1.1.1] — 2026-11-17

### Fixed
- Installing from GitHub works: the repository now carries `.claude-plugin/marketplace.json`, so `/plugin marketplace add Time-Machine-Learning/claude-plugin` no longer fails with "Marketplace file not found".
- `plugin.json` declares `privacyPolicyUrl`; README links the Privacy Policy and Terms of Service.
- README and SETUP describe sign-in, session expiry and revocation as they work today, and drop the fixed tool count.

### Added
- README section on what the plugin connects to and what it sends.
- SETUP notes on uploading documents before generating course content and on which recordings make a demo training.

## [1.1.0] — 2026-08-17

### Changed
- **BREAKING:** Authentication migrated from static API key (Bearer token via `TIME_MACHINE_API_KEY` env var) to OAuth 2.1 with PKCE and Dynamic Client Registration (RFC 7591). Claude Code handles the OAuth flow automatically on first use; users no longer need to manage an env var.
- Tool count 116 → 119 (added `tml_generate_course`, `tml_generate_course_content`, `tml_get_course_generation_status` for AI-authored course generation).
- Repository moved from `1shushi1/claude-plugin` to `Time-Machine-Learning/claude-plugin`.
- Documentation URL updated to <https://api.timeml.ai/oauth/docs>.

### Migration from 1.0.0
1. `/plugin uninstall time-machine`
2. Unset `TIME_MACHINE_API_KEY` from your shell profile (no longer needed)
3. `/plugin marketplace update` then `/plugin install time-machine`
4. On first tool use, sign in via magic-link in the browser

## [1.0.0] — 2026-07-21

Initial release. 116 MCP tools with Bearer API key authentication.