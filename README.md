---
title: AI-Inferoxy AI Hub
emoji: 🚀
colorFrom: purple
colorTo: blue
sdk: gradio
app_file: app.py
pinned: false
hf_oauth: true
hf_oauth_authorized_org:
    - nazdev
---

## 🚀 AI‑Inferoxy AI Hub

A focused, multi‑modal AI workspace. Chat, create images, transform images, generate short videos, and synthesize speech — all routed through AI‑Inferoxy for secure, quota‑aware token management and provider failover.

### Highlights
- Chat, Image, Image‑to‑Image, Video, and TTS in one app
- Works with any HF model exposed by your proxy
- Multi‑provider routing; default provider is `auto`
- Streaming chat and curated examples

### Quick Start (Hugging Face Space)
Add Space secrets:
- `PROXY_URL`: AI‑Inferoxy server URL (e.g., `https://proxy.example.com`)
- `PROXY_KEY`: API key for your proxy
  
Org access control: instead of a custom `ALLOWED_ORGS` secret and runtime checks, configure org restrictions in README metadata using `hf_oauth_authorized_org` per HF Spaces OAuth docs. Example:

```yaml
hf_oauth: true
hf_oauth_authorized_org:
  - your-org-slug
  - another-org
```

The app reads these at runtime — no extra setup required.

### How It Works
1. The app requests a valid token from AI‑Inferoxy for each call.
2. Requests are sent to the selected provider (or `auto`).
3. Status is reported back for rotation and telemetry.

### Using the App
- Chat: message → choose model/provider (`auto` by default) → tune temperature/top‑p/max tokens.
- Image: prompt → optional width/height (÷8), steps, guidance, seed, negative prompt.
- Image‑to‑Image: upload base image → describe the change → generate.
- Video: brief motion prompt → optional steps/guidance/seed.
- TTS: text → pick TTS model → adjust voice/style if supported.

### Configuration
- Model id only (e.g., `openai/gpt-oss-20b`, `stabilityai/stable-diffusion-xl-base-1.0`).
- Provider from dropdown. Default is `auto`.

### Providers
Compatible with providers configured in AI‑Inferoxy, including `auto` (default), `hf-inference`, `cerebras`, `cohere`, `groq`, `together`, `fal-ai`, `replicate`, `nebius`, `nscale`, and others.

### Security
- HF OAuth validates account; org membership is enforced by Space metadata (`hf_oauth_authorized_org`).
- Inference uses proxy‑managed tokens. Secrets are Space secrets.
- RBAC, rotation, and quarantine handled by AI‑Inferoxy.

### Troubleshooting
- 401/403: verify secrets and org access.
- 402/quota: handled by proxy; retry later or switch provider.
- Image size: width/height must be divisible by 8.
- Slow/failures: try smaller models, fewer steps, or another provider.

### License
This project is licensed under the GNU Affero General Public License v3.0 (AGPL-3.0) - see the [LICENSE](LICENSE) file for details.

### Links
- Live Space: [huggingface.co/spaces/nazdridoy/inferoxy-hub](https://huggingface.co/spaces/nazdridoy/inferoxy-hub)
- AI‑Inferoxy docs: [ai-inferoxy/huggingface-hub-integration](https://nazdridoy.github.io/ai-inferoxy-docs)
- Gradio docs: [gradio.app/docs](https://gradio.app/docs/)

— Built with AI‑Inferoxy for intelligent token management.


