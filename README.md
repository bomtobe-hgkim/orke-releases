<p align="center">
  <img src="docs/images/orke-mark.png" width="88" alt="orke logo">
</p>

<h1 align="center">orke</h1>

<p align="center">
  A workspace for AI coding agents: terminals, web pages and Git in one window, on your own computer.<br>
  Continue the same work from your phone, or run orke on a Linux server and use it from a browser.
</p>

<p align="center">
  <a href="https://orke.bomtobe.com">Homepage</a> ·
  <a href="https://orke.bomtobe.com/support/">Support &amp; FAQ</a> ·
  <a href="https://github.com/bomtobe-hgkim/orke-releases/releases">All releases</a> ·
  <a href="mailto:bomtobe.sw@gmail.com">Contact</a>
</p>

> [!NOTE]
> **The orke interface is in Korean.** This page is in English. Where you need to find something in the app, the Korean label is given with its meaning, for example **설정** (Settings).

## Download

| Platform | Download | Version | Requirements |
| --- | --- | --- | --- |
| **Windows** | [Microsoft Store](https://apps.microsoft.com/detail/9N7G0NK63QGR) | Kept up to date by the Store | Windows, x64 |
| **macOS** | [orke-macOS-arm64.dmg](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.1.3/orke-macOS-arm64.dmg) · [SHA-256](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.1.3/orke-macOS-arm64.dmg.sha256) | 3.1.3 (September 19, 2026) | macOS 26 or later, Apple Silicon |
| **Linux server** | [orke-3.4.0-linux-x64.tar.gz](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.4.0/orke-3.4.0-linux-x64.tar.gz) · [SHA-256](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.4.0/orke-3.4.0-linux-x64.tar.gz.sha256) · [**Install guide**](docs/linux.md) | 3.4.0 (October 9, 2026) | Ubuntu 24.04 LTS, x86_64, no screen needed |
| **Android** | [Google Play](https://play.google.com/store/apps/details?id=com.bomtobe.bom.remote) | 2.0.4 | Opens an orke that is already running. This version was published before the rename, so on the phone it is still called **BOM**; paste your orke address into it. |
| **iPhone** | No orke app yet. You can try Safari (not tested yet). | | The App Store still has the earlier BOM app, which cannot open orke. |

The Android app is a remote screen for an orke that runs on your computer or server. It does not run agents on the phone.

## What you can do with orke

- **Run coding agents next to ordinary terminals.** Claude Code, Codex (ChatGPT), OpenCode, Hermes and Antigravity run in orke's terminals. orke also includes its own NVIDIA agent, which works with your NVIDIA API key.
- **Open web pages inside the workspace.** Agents can read and operate the same page you are looking at. Pick an element on the page and send an instruction about it.
- **Review and commit with Git.** See changed files, diffs, history and the commit graph. Stage, commit, fetch, pull and push.
- **Keep sessions running.** Closing a tab or losing the connection does not stop a terminal while orke is running. Find and reopen sessions from the session list.
- **Manage accounts and usage.** Register more than one Claude or ChatGPT account, switch the account your CLI uses, and see how much usage is left.
- **Manage packages.** Review skills, commands and MCP servers for supported agents, and Hermes scheduled jobs.
- **Use a Docker sandbox if you want one.** Isolated sessions run in a Linux container that cannot read your computer's files directly. It needs a Docker-compatible engine such as Docker Desktop, and you install the agents inside it yourself.
- **Reach your workspace from anywhere.** Open orke from a browser or the Android app through your own ngrok address, protected by a Google sign-in that only lets in the email address you choose.
- **Answer questions from your own services (new in 3.4.0).** With orke support, a website or chat bot you run can send questions over HTTP and get answers from the Claude or ChatGPT subscription you are signed in to.

### What depends on the platform

- **Windows:** the Microsoft Store version does not have Antigravity support or orke support yet. The tray icon and Windows notifications are Windows only.
- **macOS 3.1.3** was built on September 19, 2026, before the product got its current name, so the app is still called **BOM**. It does not have the features added since then: web pages inside the workspace, Jev, the packages window, OpenCode, Hermes (and its scheduled jobs) and Antigravity support, and orke support.
- **Linux server 3.4.0** has no desktop window, so web pages cannot be opened inside orke there, and there is no tray or notifications. You use orke from a browser. The [Linux guide](docs/linux.md#what-has-been-tested) lists what has been tested on a server.
- **NVIDIA agent:** tested on Windows only. The macOS app and the Linux package also include it and offer it as a choice, but it has not been tried there.
- **Docker sandbox:** its image (`ghcr.io/bomtobe-hgkim/orke-env:5.0.0`, about 124 MB to download) is public, so orke downloads it without a GitHub sign-in. It has not been tried on a Linux server yet, and on Apple Silicon Macs it runs under emulation and has not been tested.

## Get started

### Windows

1. Install orke from the [Microsoft Store](https://apps.microsoft.com/detail/9N7G0NK63QGR). The Store installs updates for you.
2. Open orke. If the window does not appear, open the tray icon menu and choose **orke 열기** (Open orke).
3. Install the agents you want to use and sign in to them. See [Agents and accounts](#agents-and-accounts). Ordinary terminals work without any AI account.
4. Press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd> to start a new session. Give it a name and choose an agent and a working folder.

Good to know:

- Closing the window hides it; your terminals keep running. To quit completely, choose **종료** (Quit) in the tray icon menu. Quitting orke also ends its sessions.
- Windows notifications do not appear while orke runs as administrator. If **설정 › 알림** (Settings › Notifications) says that Windows App Runtime 2.4 is missing, install it from [Microsoft](https://aka.ms/windowsappsdk/2.4/latest/windowsappruntimeinstall-x64.exe).

### macOS

1. Download [orke-macOS-arm64.dmg](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.1.3/orke-macOS-arm64.dmg).
2. Optional: to check the download, also download the [SHA-256 file](https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.1.3/orke-macOS-arm64.dmg.sha256) into the same folder and run:

   ```bash
   shasum -a 256 -c orke-macOS-arm64.dmg.sha256
   ```

   It prints `orke-macOS-arm64.dmg: OK` when the file is intact.
3. Open the DMG and drag **BOM.app** to **Applications**. Version 3.1.3 was signed before the product was renamed, so the app inside is still called BOM. It is signed with an Apple Developer ID and notarized by Apple.
4. Open BOM, install the agents you want to use, and start a new session.

### Linux server

The Linux package runs orke on a server without a screen. Install it over SSH with one command, as the user who will use orke:

```bash
curl -fsSL https://orke.bomtobe.com/install.sh | bash
```

It finds the newest Linux package on the releases page, checks its SHA-256 and installs orke into your home folder. Then install ngrok, connect your ngrok address with `orke remote setup`, and run `orke service install` so that orke keeps running after you log out and after a reboot. Until you log in again, type `~/.local/bin/orke` instead of `orke`; the installer prints the full commands. Open orke from a browser or the Android app.

**Follow the [Linux install guide](docs/linux.md)** for the required packages, every step, updating, uninstalling and troubleshooting.

### Phone and other computers

1. Turn on remote access where orke runs:
   - **Windows or macOS:** **설정 › 다른 기기에서 접속** (Settings › Access from other devices). On Windows, orke installs the ngrok program for you; on a Mac, install ngrok first.
   - **Linux server:** install ngrok, run `orke remote setup`, then start orke as a service. See [steps 4 to 6 of the guide](docs/linux.md#4-install-ngrok).

   You need a free [ngrok](https://ngrok.com) account with its free static domain (`name.ngrok-free.app` or `name.ngrok-free.dev`), your ngrok authtoken, and the Google email address you want to allow in.
2. Open your ngrok address in the Android app or in a browser, and sign in with that Google account. On an iPhone you can try Safari; that has not been tested yet.

The work still runs on the computer where orke runs, so it has to stay on and connected to the internet. ngrok's terms and limits apply.

## Agents and accounts

orke does not include the agent programs, except its own NVIDIA agent. Install the ones you want and sign in with your own account. Each provider's terms, usage limits and charges apply.

| Agent | Command | Sign-in |
| --- | --- | --- |
| [Claude Code](https://claude.com/product/claude-code) | `claude` | Your Claude account |
| [Codex](https://github.com/openai/codex) (ChatGPT) | `codex` | Your ChatGPT account |
| [OpenCode](https://opencode.ai) | `opencode` | Managed by OpenCode |
| [Hermes](https://hermes-agent.nousresearch.com) | `hermes` | Managed by Hermes |
| [Antigravity](https://antigravity.google) | `agy` | Managed by agy |
| NVIDIA (included with orke) | none | NVIDIA API key in **설정 › 계정** (Settings › Accounts) |

On Linux, including inside the Docker sandbox, these are the providers' install commands. orke shows the same commands when an agent is missing from the sandbox.

```bash
curl -fsSL https://claude.ai/install.sh | bash                          # Claude Code
curl -fsSL https://chatgpt.com/codex/install.sh | sh                    # Codex
curl -fsSL https://opencode.ai/install | bash                           # OpenCode
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash      # Hermes
curl -fsSL https://antigravity.google/cli/install.sh | bash             # Antigravity
```

On Windows and macOS, follow each provider's own instructions. The [Linux guide](docs/linux.md#7-install-and-sign-in-to-claude-code-and-codex) lists the install commands and versions that were used on the test server.

Signing in on a server or inside the Docker sandbox, where no browser opens by itself:

- **ChatGPT (Codex)** uses a device code. Turn on device code sign-in in your ChatGPT security settings first.
- **Claude** shows a link to open and asks you to paste the code back into the terminal. The code may not appear on screen while you paste it; press <kbd>Enter</kbd> anyway.

## Good to know

- **Your data stays with you.** Settings, accounts and work are saved on the computer where orke runs. orke has no account or cloud service of its own. It connects to other services only for the features you use, for example your AI providers, the websites you open in its web pages, ngrok and Google for remote access, and NVIDIA for the NVIDIA agent. The [privacy policy](https://orke.bomtobe.com/privacy/) (in Korean) describes these connections, including what orke support stores and sends.
- **Agents act on their own.** orke starts agents with their permission prompts skipped. Check what they change in your working folder.
- **Sessions last while orke runs.** They survive closed tabs and dropped connections, but not quitting orke, restarting or updating it, or restarting the computer.

## Update and uninstall

| Platform | Update | Uninstall |
| --- | --- | --- |
| Windows | The Microsoft Store updates orke. | Uninstall orke from Windows Settings › Apps. |
| macOS | Download the new DMG and replace the app in Applications. | Quit the app and move it (BOM.app for 3.1.3) to the Trash. |
| Linux server | Run the [install command](#linux-server) again. It installs the newest version and restarts orke, which ends all running sessions. | In an SSH session, run `orke service uninstall`, then delete `~/.local/share/orke` and `~/.local/bin/orke`. [Details](docs/linux.md#uninstall) |

**Before you uninstall**, if you used orke support: while orke is still running, delete its AIs or rooms in the orke support window. That also deletes their Claude and Codex conversation histories, which are kept outside `~/.orke` (in `~/.claude/projects` and `~/.codex/sessions`), and only orke can find them.

Uninstalling leaves your data in place. Afterwards, keep any work files you need, then remove it yourself:

- the data folder `~/.orke` (macOS 3.1.3: `~/.bom`),
- if you used the Docker sandbox: the container and its volume, with `docker rm -f orke` and then `docker volume rm orke-home` (macOS 3.1.3: `bom` and `bom-home`).

## Where orke keeps your data

| Location | What it holds |
| --- | --- |
| `~/.orke/settings.json` | Runtime and notification settings |
| `~/.orke/accounts.json`, `~/.orke/accounts/` | Registered accounts, including their credentials |
| `~/.orke/remote-access` | Remote access settings and the ngrok authtoken (encrypted; on Linux and macOS the decryption key is in the same folder, so file permissions are what protect it) |
| `~/.orke/support`, `~/.orke/support-work` | orke support: AIs, access-key hashes, MCP secrets, rooms and their work folders |
| `~/.orke/desktop/shell`, `~/.orke/browser` | Web page profile data and history |
| `~/.orke/jev/credentials.json` | Jev API key, if you set one (encrypted) |
| `~/.orke/nvidia` | NVIDIA API key, settings and session records |
| `~/.orke/logs`, `~/.orke/run` | Logs, and the private address file used on Linux and macOS |

To keep orke's data somewhere else, set the `ORKE_HOME` environment variable to an absolute path. macOS 3.1.3 still uses the old names: the folder `~/.bom` and the variable `BOM_HOME`.

## Frequently asked questions

**Is there a Linux desktop app?**
No. The Linux package is for servers and runs without a screen. You use it from a browser or the Android app.

**Is there an iPhone app?**
Not for orke yet. The App Store still has the earlier BOM app, which cannot open orke. On an iPhone you can try your orke address in Safari; that has not been tested yet.

**Does orke run on Intel Macs?**
No. The macOS app supports Apple Silicon only.

**Do I need an AI subscription?**
Not for ordinary terminals. Each agent needs its own account with its provider.

**I refreshed the page and my terminal window disappeared.**
The session is still running. Reopen it from the **세션** (Sessions) button at the top right. Text already printed comes back; a web page that reloads may lose unsaved form input.

**Where can I find more help?**
The [support page](https://orke.bomtobe.com/support/) answers more questions about windows, notifications, terminals, web pages, agents and remote access (in Korean). It has not been fully updated for 3.4.0 yet: where it differs from this page about the iPhone app, this page is current.

## Releases

| Version | Date | Platform | Notes |
| --- | --- | --- | --- |
| [3.4.0](https://github.com/bomtobe-hgkim/orke-releases/releases/tag/v3.4.0) | 2026-10-09 | Linux x64 | First Linux server package. Adds orke support. |
| [3.1.3](https://github.com/bomtobe-hgkim/orke-releases/releases/tag/v3.1.3) | 2026-09-19 | macOS (Apple Silicon) | Signed and notarized DMG. The app is still named BOM. |
| [2.2.2](https://github.com/bomtobe-hgkim/orke-releases/releases/tag/v2.2.2) | 2026-07-12 | macOS | The earlier app (orke-agent), kept for history. |

Windows versions are published through the Microsoft Store.

## Contact

Email [bomtobe.sw@gmail.com](mailto:bomtobe.sw@gmail.com). Please include your orke version (**설정 › 정보**, Settings › About), your operating system and its version, and which agent you were using.

[Homepage](https://orke.bomtobe.com) · [Support](https://orke.bomtobe.com/support/) · [Privacy policy](https://orke.bomtobe.com/privacy/) · [Terms](https://orke.bomtobe.com/terms/)
