# setup-bf16 — GitHub Action for bf16.ai

Official GitHub Action to install [`bf16ai`](https://www.npmjs.com/package/bf16ai) (`bf16` CLI), wire OpenAI-compatible (`/v1`) and native Anthropic Messages (`https://api.bf16.ai`, no `/v1`) CI variables, and run long-context AI coding / AppSec workflows on [bf16.ai](https://bf16.ai) with strict Zero Data Retention (ZDR).

## Usage (Automated DevSecOps PR Triage)

```yaml
name: DevSecOps SAST Triage
on: [pull_request]

jobs:
  audit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 22
      - uses: BF16-AI/setup-bf16@v1.0.0
        with:
          api-key: ${{ secrets.BF16_API_KEY }}
          doctor: "true"
      - run: npx bf16ai doctor
```

## Links

- Website & API Key: [bf16.ai](https://bf16.ai)
- Open-Source Grants (`$50` free non-cash API credits): [bf16.ai/open-source](https://bf16.ai/open-source)
- CLI package: [`bf16ai` on npm](https://www.npmjs.com/package/bf16ai)
