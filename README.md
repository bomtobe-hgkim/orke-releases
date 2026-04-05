<div align="center">

<br>

# Bom Agent

**AI Desktop Agent — Your CLI subscription, working for real.**

[![Release](https://img.shields.io/github/v/release/bomtobe-hgkim/bom-releases?style=flat-square&color=6366f1&label=release)](https://github.com/bomtobe-hgkim/bom-releases/releases/latest)
[![Windows](https://img.shields.io/badge/Windows-0078D4?style=flat-square&logo=windows11&logoColor=white)](https://apps.microsoft.com/detail/9N7G0NK63QGR)
[![macOS](https://img.shields.io/badge/macOS-000000?style=flat-square&logo=apple&logoColor=white)](https://github.com/bomtobe-hgkim/bom-releases/releases/latest/download/BomAgent.dmg)
[![iOS](https://img.shields.io/badge/iOS-000000?style=flat-square&logo=appstore&logoColor=white)](https://apps.apple.com/app/bom-ai-agent/id6761526339)
[![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=com.bomtobe.bom.remote)
[![Web](https://img.shields.io/badge/bom.bomtobe.com-2dd4bf?style=flat-square)](https://bom.bomtobe.com)

Turn the AI subscription you already pay for into a real desktop assistant.<br>
One message and your PC handles calendar, browser, and files on its own.<br>
**No API keys. No extra cost.**

[Download for Mac](https://github.com/bomtobe-hgkim/bom-releases/releases/latest/download/BomAgent.dmg) ·
[Get on Microsoft Store](https://apps.microsoft.com/detail/9N7G0NK63QGR) ·
[App Store](https://apps.apple.com/app/bom-ai-agent/id6761526339) ·
[Google Play](https://play.google.com/store/apps/details?id=com.bomtobe.bom.remote) ·
[Homepage](https://bom.bomtobe.com)

<br>

</div>

## How It Works

Bom Agent follows a **brain + hands** architecture:

- **Brain** — Claude Code or Codex CLI handles reasoning and decision-making
- **Hands** — The desktop agent executes real actions on your computer
- **Relay** — A lightweight SignalR server connects your phone to your desktop

```
Your Phone / PC ──→ Secure Relay ──→ Your Desktop ──→ AI Engine
  give tasks          SignalR         runs locally     Claude / Codex
```

**Tell** what you need in plain language. **Your PC runs it** across multiple apps automatically. **Watch progress** in real time — risky actions always ask permission first.

## What It Can Do

| Feature | |
|:---|:---|
| **Local PC Control** | Organize files, launch apps, control your browser — right on your machine |
| **Web Automation** | Log into sites, collect data, fill forms via real Chrome with your cookies |
| **Mobile Remote** | Send commands from your phone, monitor progress, get push notifications |
| **Parallel Execution** | Run multiple independent tasks simultaneously |
| **Scheduled Tasks** | Morning briefings, weekly reports — recurring automation with cron syntax |
| **Voice Input** | Speak naturally in 15+ languages — no typing required |
| **Persistent Memory** | Remembers context across sessions for smarter follow-ups |
| **Model Failover** | If one AI hits a rate limit, seamlessly switches to another |
| **Safety First** | Destructive actions are blocked. Sensitive tasks require explicit approval |

## Download

### Desktop

**macOS** (Apple Silicon) — grab the `.dmg` from [Releases](https://github.com/bomtobe-hgkim/bom-releases/releases/latest):

```
curl -LO https://github.com/bomtobe-hgkim/bom-releases/releases/latest/download/BomAgent.dmg
```

**Windows** — install from the [Microsoft Store](https://apps.microsoft.com/detail/9N7G0NK63QGR) (search "BOM Agent").

### Mobile Remote

Control your desktop agent from your phone — send commands, monitor tasks, get push notifications.

- [App Store](https://apps.apple.com/app/bom-ai-agent/id6761526339) (iOS)
- [Google Play](https://play.google.com/store/apps/details?id=com.bomtobe.bom.remote) (Android)

## Requirements

- [Claude Pro/Max](https://claude.ai) or [Codex](https://openai.com/codex) CLI subscription
- macOS 14+ (Apple Silicon) or Windows 10 19041+ (x64)
- Node.js 18+ (auto-provisioned on first launch)

## Privacy

Your data stays on your machine. The relay server passes encrypted commands between devices — it never stores your files, screen content, or conversation history. All AI processing runs locally through your own CLI.

## Links

- [Homepage](https://bom.bomtobe.com) — Overview and demo video
- [Releases](https://github.com/bomtobe-hgkim/bom-releases/releases) — All versions
- [Microsoft Store](https://apps.microsoft.com/detail/9N7G0NK63QGR) — Windows
- [App Store](https://apps.apple.com/app/bom-ai-agent/id6761526339) — iOS
- [Google Play](https://play.google.com/store/apps/details?id=com.bomtobe.bom.remote) — Android

---

<div align="center">
<sub>BOMTOBE</sub>
</div>
