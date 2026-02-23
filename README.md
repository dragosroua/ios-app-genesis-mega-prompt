# iOS App Genesis Mega Prompt

A comprehensive 23-section template for building iOS apps with AI coding assistants like Claude Code, Codex, or Gemini.

## What is This?

This is a "genesis prompt" - a structured template that covers all the bases needed to build a complete iOS app from scratch. Feed this to your AI coding assistant after filling in the `{{ }}` placeholders with your app-specific details, and it can one-shot your full app.

The prompt covers:

- Project overview and technical requirements
- Design system (colors, typography, spacing, animations)
- App structure and data models
- Screen specifications
- StoreKit 2 In-App Purchase configuration
- Ad monetization (if applicable)
- Core features and content specification
- Settings, persistence, and offline behavior
- Kids App compliance (if applicable)
- Build configuration and Info.plist settings
- Complete App Store metadata
- Privacy and data compliance
- Implementation phases and release checklist

## How to Use

1. **Brainstorm first** - Use a reasoning model (like Claude) to research and brainstorm your app idea. I use my [Assess Decide Do framework skills](https://github.com/dragosroua/add-framework-skills) for this.

2. **Fill the template** - Once you have a clear picture of your app (design, monetization, compliance requirements), have the LLM interpolate all the `{{ }}` placeholders in the genesis prompt.

3. **Feed to your code builder** - Take the completed `prompt.md` and feed it to Claude Code (or your preferred AI coding tool).

4. **Iterate** - Build in small, atomic features. Commit aggressively with Git.

## The Prompt

See [ios-genesis-mega-prompt.md](ios-genesis-mega-prompt.md) for the full template.

## Background

This genesis prompt evolved from building multiple iOS apps using AI coding assistants. Every time I encountered a time-consuming detail (like the `ITSAppUsesNonExemptEncryption` setting that blocks TestFlight builds), I added it back to the template so the next app would have it covered from the start.

For the full story and lessons learned, read the blog post: [Vibe Coding iOS Apps: Lessons and the Genesis Mega Prompt](https://dragosroua.com/vibe-coding-ios-apps-lessons-and-the-genesis-mega-prompt/)

## License

Free to use. Just copy and paste.

## Author

[Dragos Roua](https://dragosroua.com)
