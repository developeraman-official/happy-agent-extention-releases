<p align="center"><img src="https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/media/vecto-coder-banner.png" alt="Vecto Coder — an AI coding agent for your VS Code workspace" width="100%"></p>

# Vecto Coder

Vecto Coder is an AI coding agent for VS Code-compatible editors, built for professional developers who want capable project work with visible control over decisions and machine changes. Resume recent conversations, choose interactive or automatic task handling, select your own coding agent, and review tracked file edits before deciding what to keep.

<p align="center"><img src="https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/media/vecto-coder-workflow.png" alt="Vecto Coder workflow: describe a goal, review file edits, and approve terminal commands" width="100%"></p>

## What Vecto Coder helps with

- **Understand a workspace:** ask questions, search for relevant code, and use the active or recently edited file as context.
- **Resume project work:** return to recent chat sessions and continue the selected conversation.
- **Choose how the agent collaborates:** Interactive mode asks about consequential unresolved decisions; Auto mode uses safe, reversible defaults for routine choices.
- **Select specialized guidance:** choose bundled frontend, architecture, API, credentials, security, and QA agents, or add project agents under `.vecto/agents/` and user agents under `~/.vecto/agents/` or `~/.agents/agents/`. Project definitions take precedence over user definitions and bundled defaults. Project skills under `.vecto/skills/<name>/SKILL.md` are discovered alongside user skills and bundled skills; only relevant guidance is read into a task.
- **Review every file edit:** inspect tracked diffs in the editor, keep accepted changes, or revert them. File deletion through the coding agent is disabled.
- **Set permission boundaries:** Manual asks before terminal commands; Safe auto-approves a small read-only command list; Full Access enables bounded text-file search and tracked edits outside the workspace.
- **Keep high-impact actions gated:** credential and private-key files are blocked from model reads and edits, and edits to protected operating-system directories are blocked. Other terminal commands require in-chat approval, and common destructive or system-control command patterns are blocked even after approval.
- **Use your preferred models:** connect compatible cloud or local AI providers with your own credentials.
- **Start with Free AI:** Vecto Coder Free AI is preconfigured and works without an account or API key. Its first-use notice explains that prompts and related context are sent to third-party AI providers, which may log or use them to improve their services.
- **Manage providers in chat:** add a supported cloud or local provider from Settings. Enter its name, API protocol, endpoint, and credentials as needed; add multiple credential slots in the UI. Keys are stored in editor Secret Storage and supported model catalogs load automatically.
- **Bring your guidance:** place custom agents in `~/.vecto/agents/`, and skills plus shared rules such as `~/.vecto/skills/rules.md` in `~/.vecto/skills/`.

## Install

Install the stable extension from the Extensions view by searching for **Vecto Coder**, or run:

```sh
code --install-extension developeraman.vecto-coder
```

### Release channels

Stable, beta, and test install as separate extensions and receive updates from their own channel.

| Channel | Extension ID | Install |
| --- | --- | --- |
| Stable | `developeraman.vecto-coder` | [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=developeraman.vecto-coder) |
| Beta | `developeraman.vecto-coder-beta` | [Download latest beta VSIX](https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/channels/beta/latest.vsix) |
| Test | `developeraman.vecto-coder-test` | [Download latest test VSIX](https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/channels/test/latest.vsix) |

For beta or test, download the VSIX and choose **Install from VSIX** from the Extensions view.

## Get started

1. Open a project folder and select the Vecto Coder icon in the Activity Bar.
2. Choose **Free AI** to start without configuring an API key, or open chat Settings to add a provider with your own credentials.
3. Select a model and describe the outcome you want. Review tracked file edits in the editor and approve any proposed terminal command in chat.

On first startup, Vecto Coder creates `~/.vecto/` and an empty `~/.vecto/.env` template if they do not exist. Provider definitions are loaded from `~/.vecto/providers/`. To use portable environment credentials, add a variable to `~/.vecto/.env` and reference it from a provider definition. Do not put real keys in workspace files or share them publicly.

## Built for professional developers

The chat home keeps recent project conversations available for quick switching. Compact controls at the top of the panel configure interaction style, the selected custom agent, and file/terminal permissions. Interactive mode reserves questions for decisions that materially affect security, data loss, compatibility, cost, or architecture; routine choices use a stated, reversible default.

Full Access is designed for deliberate configuration work beyond the opened workspace. It allows bounded reads and text edits to accessible files on local drives, and those edits appear in the same diff review and revert flow as workspace changes. Credential and private-key files stay blocked, edits to protected system directories are blocked, and file deletion through the coding agent is disabled. Terminal commands that are not on the narrow read-only allowlist still require approval in the chat, and common destructive commands are denied. For changes to sensitive external configuration, the agent is instructed to consult official documentation before editing when possible. Scripts may have effects that a static command check cannot predict, so review each command before approving it.

## Privacy and safety

Workspace context needed to answer your request is sent to the model provider you selected. Free AI sends prompts and related context to third-party providers, which may log or use submitted content to improve their services. Do not send confidential or personal data through this route. Provider credentials stay in the editor's secure storage or your `.vecto/.env`. File changes are tracked for review. Permission modes change which local paths the agent can access and which narrow read-only commands can run without individual approval.

Read the [developer guide](./USER_GUIDE.md) for setup and usage details, the [Privacy Policy](https://github.com/developeraman-official/vecto-coder/blob/master/PRIVACY_POLICY.md) for local and provider data handling, the [Terms and Conditions](https://github.com/developeraman-official/vecto-coder/blob/master/TERMS_AND_CONDITIONS.md) for use terms, and [security and privacy notes](./SECURITY.md) for implementation-specific controls.

## License

Vecto Coder use is governed by [LICENSE.txt](./LICENSE.txt) and the [Terms and Conditions](./TERMS_AND_CONDITIONS.md).
