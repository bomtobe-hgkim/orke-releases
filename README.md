# orke

A desktop workspace that brings terminals, web pages, and coding agents together. Work on your PC, review changes in Git, and continue from another device through an optional ngrok connection.

[Homepage](https://orke.bomtobe.com) · [Support](https://orke.bomtobe.com/support/) · [Source repository](https://github.com/bomtobe-hgkim/orke) · [Release history](https://github.com/bomtobe-hgkim/orke-releases/releases)

## Downloads

| Platform | Download | Supported environment |
| --- | --- | --- |
| Windows | [Microsoft Store](https://apps.microsoft.com/detail/9N7G0NK63QGR) | x64 |
| macOS | [orke 3.1.3 DMG](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.1.3/orke-macOS-arm64.dmg) · [SHA-256](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.1.3/orke-macOS-arm64.dmg.sha256) | macOS 26 or later, Apple Silicon |
| Android | [Google Play](https://play.google.com/store/apps/details?id=com.bomtobe.bom.remote) | Connects to orke running on your PC |
| iPhone | [App Store](https://apps.apple.com/app/id6761526339) | Connects to orke running on your PC |

This repository hosts release downloads. [v3.1.3](https://github.com/bomtobe-hgkim/orke-releases/releases/tag/v3.1.3) is the current macOS release. [v2.2.2](https://github.com/bomtobe-hgkim/orke-releases/releases/tag/v2.2.2) is retained as earlier application history.

## What you can do

- Use Claude Code, Codex, OpenCode, and Hermes alongside ordinary terminals. The bundled NVIDIA agent is available in the Windows host environment.
- Open web pages in your workspace and let agents read and operate the same pages you use.
- Review Git changes, diffs, and history; stage, commit, fetch, pull, and push.
- Find and reopen terminal sessions, manage supported accounts and usage, and organize skills, commands, and MCP tools.
- Choose your PC environment or an optional Docker Linux environment; install agents and tools yourself inside Docker.
- Access your PC workspace from a browser or the mobile app through your own ngrok account.

The interface is in Korean. Agent CLIs and their service authentication are prepared separately; provider terms, usage limits, and charges apply. Ordinary terminals do not require an AI account.

Terminal sessions continue while orke is running, including after a workspace tab closes or a remote connection drops. Remote access requires the PC and orke to remain running and connected to the internet.

For installation and platform differences, see [support](https://orke.bomtobe.com/support/). Contact: [bomtobe.sw@gmail.com](mailto:bomtobe.sw@gmail.com).
