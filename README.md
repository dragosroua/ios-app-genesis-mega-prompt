Here's the updated README you can copy over:

```markdown
# iOS App Genesis Mega Prompt

A comprehensive 23-section template for building iOS apps with AI coding assistants like Claude Code, Codex, or Gemini.

## What is This?

This is a "genesis prompt" — a structured template that covers all the bases needed to build a complete iOS app from scratch. Fill in the `{{ }}` placeholders with your app-specific details and feed it to your AI coding assistant.

There are two versions:

- **Full version** (`ios-genesis-mega-prompt.md`) — 23 sections covering everything from design system to App Store metadata, compliance, and release checklist. Best for larger models and one-shot full apps.
- **Simplified version** (`ios-genesis-prompt-xs.md`) — condensed version focused on generating working SwiftUI code. Designed for local models (especially under ~9B) and the "Local AI Coding" series tests.

## How to Use

1. **Brainstorm first** — Use a reasoning model (like Claude) to research and brainstorm your app idea. I use my Assess Decide Do framework skills for this.
2. **Fill the template** — Once you have a clear picture of your app (design, monetization, compliance requirements), have the LLM interpolate all the `{{ }}` placeholders.
3. **Feed to your code builder** — Take the completed prompt and feed it to Claude Code (or your preferred AI coding tool), or to a local model for the XS version.
4. **Iterate** — Build in small, atomic features. Commit aggressively with Git.

## The Prompts

- Full 23-section template: [ios-genesis-mega-prompt.md](ios-genesis-mega-prompt.md)
- Simplified XS version (for local models): [ios-genesis-prompt-xs.md](ios-genesis-prompt-xs.md)

The XS version is used in the Local AI Coding series (testing small post-trained and distilled models on generating iOS apps). Videos and notes will be linked here as they are published.
```
