<p align="center">
  <a href="https://github.com/runapi-ai/mimo">
    <h3 align="center">MiMo API Skill for RunAPI</h3>
  </a>
</p>

<p align="center">
  Configure OpenAI-compatible or Anthropic-compatible clients to use MiMo text models on RunAPI.
</p>

<p align="center">
  <a href="https://runapi.ai/models/mimo"><strong>Model Reference</strong></a> | <a href="https://github.com/runapi-ai/mimo"><strong>Skill Repo</strong></a> | <a href="https://runapi.ai/models"><strong>All Models</strong></a>
</p>

<div align="center">

[![skills.sh](https://www.skills.sh/b/runapi-ai/mimo)](https://www.skills.sh/runapi-ai/mimo/mimo)
[![ClawHub](https://img.shields.io/badge/ClawHub-runapi--mimo-111827)](https://clawhub.ai/runapi-ai/runapi-mimo)
[![License](https://img.shields.io/github/license/runapi-ai/mimo)](https://github.com/runapi-ai/mimo/blob/main/LICENSE)

</div>
<br/>

Call MiMo through RunAPI with Chat Completions, Responses, or Messages. Point
OpenAI-compatible clients at `https://runapi.ai/v1`, use `mimo-v2.5-pro` or
`mimo-v2.5`, and keep billing on one RunAPI balance. This skill teaches Claude
Code, Codex, Gemini CLI, Cursor, and 50+ agents how to configure MiMo clients.

The canonical agent file is `skills/mimo/SKILL.md`.

## Install the skill

```bash
npx skills add runapi-ai/mimo -g
```

Or paste this prompt to your AI agent:

```text
Install the mimo skill for me:

1. Clone https://github.com/runapi-ai/mimo
2. Copy the skills/mimo/ directory into your
   user-level skills directory (e.g. ~/.claude/skills/
   for Claude Code, ~/.codex/skills/ for Codex).
3. Verify that SKILL.md is present.
4. Confirm the install path when done.
```

## Use MiMo on RunAPI

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_RUNAPI_TOKEN",
    base_url="https://runapi.ai/v1",
)

response = client.chat.completions.create(
    model="mimo-v2.5-pro",
    messages=[{"role": "user", "content": "Draft a concise answer."}],
)
print(response.choices[0].message.content)
```

```javascript
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: "YOUR_RUNAPI_TOKEN",
  baseURL: "https://runapi.ai/v1",
});

const response = await client.responses.create({
  model: "mimo-v2.5",
  input: "Summarize this report.",
});
console.log(response.output_text);
```

Get a RunAPI API Key at <https://runapi.ai/api_keys>.

## Supported MiMo models

| Model ID | Notes |
|---|---|
| `mimo-v2.5-pro` | Higher-quality MiMo text generation |
| `mimo-v2.5` | Efficient MiMo text generation |

## Protocol boundary

- Basic text supports sync and SSE on Chat Completions, Responses, and Messages.
- Tools, reasoning controls, continuation state, documents, images, audio, and
  other multimodal input are rejected before usage is reserved.
- Responses preserve the requested canonical model ID.

## Links

- MiMo API on RunAPI: <https://runapi.ai/models/mimo>
- Provider page: <https://runapi.ai/providers/xiaomi>
- Browse the catalog: <https://runapi.ai/models>

## Agent rules

- Keep API keys in environment variables or a secret manager.
- Use streaming for long responses.
- Link to <https://runapi.ai/models/mimo> for pricing instead of copying values.

## License

Licensed under the Apache License, Version 2.0.
