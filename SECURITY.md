# Vecto Coder security and privacy

## Credentials and provider files

VS Code Secret Storage is the preferred credential store. For cross-IDE portability, provider JSON can reference a variable using `"apiKeySecret": "env:VARIABLE_NAME"`; Vecto Coder reads that value from `~/.vecto/.env` (or the extension process environment) and uses it only for provider authentication. The user `.env` file stores values as plaintext, so restrict access to your user account and never commit or share it. Provider JSON files should contain references only; do not put API key values in provider configuration, workspace files, scripts, or agent instructions. `.env` values are not injected into terminal or MCP processes. Vecto Coder redacts common credential field names and token formats from selected chat output and persisted task text, but pattern-based redaction cannot identify every secret. Review provider responses and workspace content before sharing them with another service.

## Workspace data

When you send a request to a configured model, Vecto Coder sends the request and the workspace context needed for that task to the selected provider. File changes and rollback snapshots stay on the local machine. Tracked snapshots may contain the original file contents in VS Code extension storage so that a change can be reverted. Treat that storage as sensitive and use VS Code's profile and operating-system protections.

Diffs intentionally show the real file contents so you can review and restore changes accurately. Do not open a diff for a file that contains secrets on a screen or share it with people who should not see those contents.

## Network and terminal controls

`vectoCoder.networkAccess` controls public website fetching and defaults to `allow`; set it to `deny` to disable website retrieval. Provider API requests and release checks are separate network functions and are not disabled by this setting. Web fetching permits HTTP(S) public destinations and blocks private and loopback addresses.

`vectoCoder.terminalPolicy` defaults to `ask`. Every terminal command still requires a one-time approval in the Vecto Coder chat. Set it to `deny` to disable terminal commands. Workspace file edits are tracked and can be reverted; MCP processes and every MCP tool call require explicit chat actions and approvals.

## Diagnostics and updates

`vectoCoder.diagnostics.enabled` defaults to `false`. When enabled, the Vecto Coder Diagnostics output channel records structured lifecycle event names, timestamps, and bounded redacted metadata. It does not collect prompts, file contents, provider responses, credentials, telemetry, or remote logs.

Update packages are downloaded from the configured Vecto Coder distribution repository and checked against the SHA-256 value in that channel's `latest.json`. This detects package corruption or a mismatched artifact; it does not provide an independent signature if the repository account or manifest is compromised. Review releases and repository access controls accordingly.
