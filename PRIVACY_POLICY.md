# Vecto Coder Privacy Policy

**Effective date: October 20, 2026**

This policy describes data handling by the Vecto Coder VS Code extension, published by Developeraman. Vecto Coder is a local editor extension; it does not operate the AI model providers or control their data practices.

## Information processed on your device

The Extension reads the files, workspace paths, editor state, provider configuration, and agent/skill guidance needed for the actions you request. It stores provider definitions, task records, agent settings, and skills under `~/.vecto` or the workspace `.vecto` directory. Task records can contain your request text, task steps, selected provider/model identifiers, and bounded tool-call status. Conversation transcripts are held in memory for the active chat and are not written as a complete transcript by the Extension.

API credentials entered through the Extension are stored in the editor’s Secret Storage. If you choose to use `~/.vecto/.env`, those values are stored as local plaintext; protect that file with your operating-system account permissions and do not commit or share it. Provider JSON should contain secret references rather than actual keys.

Edit snapshots used for review and revert are stored in local editor extension storage. Diagnostics are off by default. When enabled, the diagnostics output contains redacted lifecycle event names and bounded metadata; it is not designed to collect prompts or file contents. Pattern-based redaction cannot guarantee that every secret is detected.

## Information sent to providers

When sponsored recommendations are enabled, Vecto Coder extracts topic, category, and intent signals locally from your message and sends those signals, plus a random chat-session identifier, to Idlen for ad selection using Idlen's client-side SDK. Raw prompts, model responses, file contents, and workspace paths are not sent to Idlen. The SDK uses a publishable `idl_pk_` key in the webview; this key is public by design and is not an API secret. The ad service may receive impression and click events to measure delivery. Ads are displayed separately from the conversation and are not added to chat history or sent to the AI model. You can disable this feature with the `Vecto Coder: Idlen Ads Enabled` setting.

When you submit a request, Vecto Coder sends the prompt and the conversation or workspace context selected for that request to the AI provider and model you selected. This may include file excerpts, tool definitions, agent/skill guidance, and results returned by tools. If you ask the Extension to fetch a public website, retrieved page text may also be included in the provider request. Provider credentials are sent to the relevant provider for authentication.

Each provider independently determines how it processes, retains, reviews, and may use prompts, outputs, and other request data, including whether data may be used to improve or train its services. These practices vary by provider, account type, model, endpoint, and settings, and may change. Vecto Coder cannot set or guarantee a provider’s retention, training, security, or deletion practices. Read the provider’s current privacy notice and terms before sending data, and do not send confidential or regulated information unless your agreements and provider settings permit it.

Kilo Auto Free is preconfigured as an optional keyless provider. Kilo documents that Auto Free can route requests to providers that log prompts and outputs and use them to improve services, and that NVIDIA trial endpoints are for evaluation rather than production use. Do not send personal, confidential, or production data through this route. See [Kilo’s provider documentation](https://kilo.ai/docs/gateway/models-and-providers) and [NVIDIA’s API Trial Terms](https://assets.ngc.nvidia.com/products/api-catalog/legal/NVIDIA%20API%20Trial%20Terms%20of%20Service.pdf).

## Other network connections

The Extension may contact the provider you selected, retrieve public websites when website access is enabled, and check the configured release channel for updates. These connections are separate. The website access setting does not block provider requests or release checks. The Extension does not include its own account service or transmit diagnostic telemetry by default.

## Retention and deletion

You control local workspace task records and user configuration and can remove them from `.vecto` and `~/.vecto`. VS Code manages Secret Storage and extension storage through the editor profile; use the editor’s profile and extension-management controls to remove those local records. Vecto Coder cannot delete information already sent to an AI or website provider; contact that provider and follow its current deletion process.

## Children and changes

The Extension is intended for professional development use and is not designed for children. This policy may be updated as the Extension changes; the effective date above identifies the latest published revision.

## Contact

For privacy questions, use the contact links on the [Developeraman website](https://developeraman.vercel.app/).
