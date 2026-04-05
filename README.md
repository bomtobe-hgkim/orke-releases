<div align="center">

# Bom Agent

### Turn your AI subscription into a real desktop assistant

[![Latest Release](https://img.shields.io/github/v/release/bomtobe-hgkim/bom-releases?style=flat-square&color=6366f1&label=Latest)](https://github.com/bomtobe-hgkim/bom-releases/releases/latest)
[![Platform - Windows](https://img.shields.io/badge/Windows-0078D4?style=flat-square&logo=windows11&logoColor=white)](https://apps.microsoft.com/detail/9N7G0NK63QGR)
[![Platform - macOS](https://img.shields.io/badge/macOS-000000?style=flat-square&logo=apple&logoColor=white)](https://github.com/bomtobe-hgkim/bom-releases/releases/latest/download/BomAgent.dmg)
[![Website](https://img.shields.io/badge/Website-bom.bomtobe.com-2dd4bf?style=flat-square)](https://bom.bomtobe.com)

<br>

**Bom Agent** is an AI-powered desktop agent that uses your existing CLI subscriptions  
(Claude Code, Codex) to automate real tasks on your computer — **zero LLM API cost**.

One chat message and your PC handles calendar, browser, files, and more on its own.

<br>

[**Download for Mac**](https://github.com/bomtobe-hgkim/bom-releases/releases/latest/download/BomAgent.dmg) &nbsp;·&nbsp; [**Get on Microsoft Store**](https://apps.microsoft.com/detail/9N7G0NK63QGR) &nbsp;·&nbsp; [**Website**](https://bom.bomtobe.com)

<br>

</div>

---

## How It Works

```
📱 Your Phone / PC  →  ☁️ Secure Relay  →  🖥️ Your Desktop  →  🤖 AI Engine
     (give tasks)        (SignalR)          (runs locally)      (Claude / Codex)
```

1. **Tell** — Describe what you need in plain language, from your phone or desktop
2. **Run** — Your PC executes the task automatically across multiple apps
3. **Check** — Watch real-time progress; risky actions ask permission first

---

## Features

| | Feature | Description |
|---|---|---|
| 🖥️ | **Local PC Control** | Organize files, launch apps, control your browser — right on your computer |
| 🌐 | **Web Automation** | Log into sites, collect data, fill forms — all automated via real Chrome |
| 📱 | **Mobile Remote** | Send commands from your phone, monitor tasks, receive push notifications |
| 🔀 | **Parallel Tasks** | Run multiple tasks at once and get combined results |
| ⏰ | **Scheduled Runs** | Morning briefings, weekly reports — automate recurring tasks with cron |
| 🎙️ | **Voice Commands** | Just speak and it runs — supports 15+ languages |
| 🧠 | **Persistent Memory** | Remembers context across sessions for smarter assistance |
| 🔄 | **Auto-Failover** | If one AI is busy, seamlessly switches to another |
| 🛡️ | **Safety Policies** | Dangerous actions are blocked; sensitive tasks require your approval |
| 💰 | **Zero API Cost** | Uses your existing CLI subscriptions — no API keys needed |

---

## Download

### macOS (Apple Silicon)

Download the latest `.dmg` from [**Releases**](https://github.com/bomtobe-hgkim/bom-releases/releases/latest):

```bash
# Direct download
curl -LO https://github.com/bomtobe-hgkim/bom-releases/releases/latest/download/BomAgent.dmg
```

### Windows

Install from the [**Microsoft Store**](https://apps.microsoft.com/detail/9N7G0NK63QGR) — search for **"BOM Agent"**.

---

## Requirements

- **AI Subscription** — [Claude Pro/Max](https://claude.ai) or [Codex](https://openai.com/codex) CLI subscription
- **macOS** — Apple Silicon (M1+), macOS 14+
- **Windows** — Windows 10 19041+ (x64)
- **Node.js** — v18+ (auto-installed if missing)

---

## Architecture

Bom Agent follows a **brain + hands** design:

- **Brain** — Claude Code / Codex CLI handles reasoning and planning
- **Hands** — Desktop agent executes actions (browser, files, keyboard, mouse)
- **Relay** — Secure SignalR server connects your phone to your desktop

Your data stays on your machine. The server only relays encrypted commands — it never sees your files or screen content.

---

## Links

- 🌐 [**Website**](https://bom.bomtobe.com) — Homepage with demo video
- 📦 [**Releases**](https://github.com/bomtobe-hgkim/bom-releases/releases) — All versions
- 🪟 [**Microsoft Store**](https://apps.microsoft.com/detail/9N7G0NK63QGR) — Windows download

---

<div align="center">

**Built with** &nbsp; Claude Code &nbsp;·&nbsp; .NET MAUI &nbsp;·&nbsp; Blazor &nbsp;·&nbsp; SignalR

Made by [bomtobe](https://bom.bomtobe.com)

</div>
