# Paperclip (Archived)

**Status:** Archived. The Compose files are retained for reference; the Paperclip container and its data volume have been removed.

## Why it was archived

This setup was intended to run a Codex agent against CommandCode's OpenAI-compatible Responses API at `https://api.commandcode.ai/provider/v1`. CommandCode lists `deepseek/deepseek-v4.1-flash` as supporting `/responses`.

The agent used an explicit per-login `CODEX_HOME`. Paperclip only injects `PAPERCLIP_CODEX_PROVIDERS` into its managed Codex home, so that custom home bypassed the CommandCode configuration. Runs consequently went to `https://api.openai.com/v1/responses` and failed with a model-not-found 404. Paperclip also rejected per-agent Codex CLI provider overrides while the managed “Responsible user's connection” was selected.

Until Paperclip supports custom-provider routing for this self-managed Codex home/connection combination, this Docker setup does not meet the CommandCode use case. Do not start it expecting CommandCode routing to work.

## Retained files

- `docker-compose.yml` — archived service definition.
- `.env.example` — sanitized configuration template; contains no provider API keys.
- `.env` — local-only ignored file, if present; never commit or publish it.