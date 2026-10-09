# Install orke on a Linux server

The Linux package runs orke on a server that has no screen, such as a cloud VM. You install it over SSH with a few commands. After that you open orke from a browser or the orke Android app through your own ngrok address, and only the Google account you choose can get in.

> [!NOTE]
> orke's screens and its command-line messages are in Korean. This guide quotes the Korean text you will see and explains what it means.

**On this page:** [How it works](#how-it-works) · [Before you start](#before-you-start) · [1. Packages](#1-install-the-required-packages) · [2. Download](#2-download-orke-and-check-the-file) · [3. Install](#3-install-orke) · [4. ngrok](#4-install-ngrok) · [5. Connect](#5-connect-your-ngrok-address) · [6. Keep it running](#6-start-orke-and-keep-it-running) · [7. Claude Code and Codex](#7-install-and-sign-in-to-claude-code-and-codex) · [8. Open orke](#8-open-orke) · [orke support](#use-orke-support-optional) · [Everyday commands](#everyday-commands) · [Update](#update) · [Uninstall](#uninstall) · [Troubleshooting](#troubleshooting) · [What has been tested](#what-has-been-tested)

## How it works

- orke runs on the server as your own user, as a background service that starts when the server boots. Its terminals have the same permissions as that user.
- You use orke in a browser, on any computer or phone, at your ngrok address (for example `https://name.ngrok-free.app`). ngrok asks for a Google sign-in and lets in only the email address you set.
- Terminals, coding agents, Git, sessions, accounts and orke support are all used in the browser. The server version has no desktop window, so web pages cannot be opened inside orke there.
- The new-session window also offers NVIDIA, orke's own agent. The Linux package includes it, but it has been tested only on Windows and has not been tried on a server.

## Before you start

You need:

- **A server running Ubuntu 24.04 LTS on x86_64.** `uname -m` should print `x86_64`. The package is for x86_64 only; the installer stops on ARM and other machines. Other distributions have not been tested.
- **systemd.** Ordinary cloud VMs and physical servers have it. Containers and WSL usually do not, and orke cannot install its service there.
- **A regular user account that you log in to with SSH.** Do not use `root`; the installer refuses it.
- **`sudo` rights** for installing system packages. orke itself installs into your home folder without `sudo`.
- **A free [ngrok](https://ngrok.com) account.** In the ngrok dashboard you need two things:
  - your free static domain, on the **Domains** page. It looks like `name.ngrok-free.app` or `name.ngrok-free.dev`. orke accepts only these two forms.
  - your authtoken, on the **Your Authtoken** page.
- **The Google account** you will sign in with.
- **Claude and ChatGPT subscriptions** if you want to use those agents. Ordinary terminals need no AI account.

## 1. Install the required packages

```bash
sudo apt-get update
sudo apt-get install -y libicu74 ca-certificates procps curl git
```

The installer checks for these packages. If one is missing, it stops and prints the command that installs it.

## 2. Download orke and check the file

```bash
curl -fLO https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.4.0/orke-3.4.0-linux-x64.tar.gz
curl -fLO https://github.com/bomtobe-hgkim/orke-releases/releases/download/v3.4.0/orke-3.4.0-linux-x64.tar.gz.sha256
sha256sum -c orke-3.4.0-linux-x64.tar.gz.sha256
```

The last command should print `orke-3.4.0-linux-x64.tar.gz: OK`. If it prints anything else, the download is damaged; download it again.

## 3. Install orke

Run these as the user who will use orke, in the folder where you downloaded the file:

```bash
tar xzf orke-3.4.0-linux-x64.tar.gz
./orke-3.4.0-linux-x64/install.sh
```

The installer:

- copies orke to `~/.local/share/orke` and creates the command `~/.local/bin/orke`,
- does not touch your settings and records in `~/.orke`,
- prints the next commands with their full paths when it finishes.

When it succeeds, it prints `orke 3.4.0 을 설치했습니다` ("orke 3.4.0 has been installed").

> [!TIP]
> If `~/.local/bin` did not exist before, it is not on your `PATH` until your next login (Ubuntu adds it automatically at login). Until then, type `~/.local/bin/orke` instead of `orke`, or log out and back in. This guide writes `orke` for short.

You can delete the downloaded `.tar.gz` file and the extracted folder afterwards.

## 4. Install ngrok

Install ngrok from ngrok's own apt repository. orke needs ngrok 3.39.9 or later. **The snap version of ngrok does not work with orke**, because snap does not let it read orke's settings folder.

```bash
curl -fsSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null
echo "deb https://ngrok-agent.s3.amazonaws.com bookworm main" | sudo tee /etc/apt/sources.list.d/ngrok.list >/dev/null
sudo apt-get update
sudo apt-get install -y ngrok
ngrok version
```

You do not need to run `ngrok config add-authtoken`. orke keeps the authtoken itself, in `~/.orke/remote-access`, after the next step. It is stored encrypted, but on Linux the key that decrypts it is a file in the same folder, so what protects the token is that only your user can read that folder. Keep that folder, and any backup of `~/.orke`, private.

## 5. Connect your ngrok address

```bash
orke remote setup
```

It asks four questions:

| What you see | What it asks | What to enter |
| --- | --- | --- |
| `ngrok 고정 주소(…)` | Your ngrok static domain | For example `name.ngrok-free.app` (no `https://`, no path) |
| `이 주소를 다른 컴퓨터의 orke(예: PC)도 쓰나요? [y/N]` | Does another computer's orke (for example your PC) also use this address? | Press <kbd>Enter</kbd> for **No** |
| `접속을 허락할 본인 Google 이메일` | The Google email address allowed to sign in | Your Google email |
| `ngrok Authtoken(…)` | Your ngrok authtoken | Paste it and press <kbd>Enter</kbd>. Nothing appears while you type; that is normal. Pasting the whole `ngrok config add-authtoken …` command also works. |

**One ngrok address can be used by only one computer at a time.** If your PC's orke has been using the same address, let the server have it: on the PC, stop remote access and turn off **orke을 시작할 때 자동으로 연결** (Connect automatically when orke starts) under **설정 › 다른 기기에서 접속** (Settings › Access from other devices). Otherwise whichever connects second stops with an error.

orke connects every time it starts. If orke is already running when you change these settings, run `orke service restart` (see the note under [Everyday commands](#everyday-commands)).

For scripts, `orke remote setup --hostname <domain> --email <email> --authtoken-stdin` reads the authtoken from standard input instead of asking.

## 6. Start orke and keep it running

**Optional quick test.** Start orke in the foreground:

```bash
orke serve
```

It prints a single line, `orke: UI 는 ngrok 주소로 여세요(…)` ("open the UI at your ngrok address"). You can now open your ngrok address in a browser, as in [step 8](#8-open-orke). Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop it before you continue.

**Install the service:**

```bash
orke service install
```

This:

- creates and starts a systemd user service, `~/.config/systemd/user/orke.service`,
- turns on *linger* for your user, so orke keeps running after you log out and starts at boot without anyone logging in. If your user is not allowed to do that without a password, it prints a warning and the command an administrator should run once: `sudo loginctl enable-linger <your user name>`.
- may suggest reserving orke's network ports. This is optional; it prevents a rare startup failure when another program happens to take one of orke's ports first:

  ```bash
  echo 'net.ipv4.ip_local_reserved_ports=47620-48643,48700' | sudo tee /etc/sysctl.d/90-orke.conf && sudo sysctl --system
  ```

  If the server already reserves other ports (`sysctl net.ipv4.ip_local_reserved_ports` shows them), add them to that line, separated by commas. The setting holds one list, so a new value replaces the old one.

Check that it is running:

```bash
orke service status
```

## 7. Install and sign in to Claude Code and Codex

Install the agents for the same user that runs orke. These are the install methods that were used on the test server:

```bash
# Claude Code (installs ~/.local/bin/claude)
curl -fsSL https://claude.ai/install.sh | bash

# Codex, through npm (Ubuntu's own Node.js and npm)
sudo apt-get install -y nodejs npm
sudo npm install -g @openai/codex
```

The tests used Claude Code 2.1.292 (it updated itself to 2.1.295 during the tests) and Codex 0.160.1, with Ubuntu's Node.js 18 and npm 9. Without a version number these commands install the newest release, which has not been tested with orke 3.4.0. To install the tested Codex, run `sudo npm install -g @openai/codex@0.160.1`. Do the same if orke support shows `이 codex 버전에서는 꺼야 할 기능(…)을 끌 수 없습니다 — orke 업데이트가 필요합니다.` ("orke cannot turn off features it must turn off in this Codex version; orke needs an update").

Sign in, either in your SSH session now or later from a terminal tab inside orke:

```bash
claude auth login
codex login --device-auth
```

- **Claude:** open the link it shows, sign in, then paste the code back into the terminal and press <kbd>Enter</kbd>. The code may not appear on screen while you paste it.
- **Codex:** first turn on device code sign-in in your ChatGPT security settings. Then open <https://auth.openai.com/codex/device> and enter the code that the command shows.

If Claude or ChatGPT gets signed out while orke support is answering, the orke support window shows a banner with **터미널에서 로그인** (Sign in from a terminal). It opens a new terminal tab with the sign-in command already typed; press <kbd>Enter</kbd> to run it.

OpenCode, Hermes and Antigravity can be installed with their own installers (see [Agents and accounts](../README.md#agents-and-accounts)). They have not been tested on a server yet.

## 8. Open orke

1. On your PC or phone, open your ngrok address, for example `https://name.ngrok-free.app`, in a browser. In the orke Android app, save the same address. There is no orke iPhone app yet; use Safari.
2. On a free ngrok domain, ngrok first shows a notice page that starts with "You are about to visit". Choose **Visit Site**.
3. Sign in with the Google account you entered in step 5.

The usage shown at the top right is for the accounts signed in on the server.

**Without ngrok**, you can open orke through an SSH tunnel. The service log names the port:

```bash
journalctl --user -u orke | grep 'ssh -L'
```

On your own computer, run the `ssh -L <port>:127.0.0.1:<port> <user>@<server>` command from that line and keep it open. Use the same port number on both sides, as in that line; orke accepts only its own port. If that port is already taken on your computer, the tunnel will not work. Then, on the server, print the private address:

```bash
sed -n 's/^url=//p' ~/.orke/run/ui.url
```

It prints one address that starts with `http://127.0.0.1:`. Open it in a browser on your own computer while the tunnel is open. It contains a private access token, so do not share it.

## Use orke support (optional)

orke support lets your own services, such as a website or a chat bot, ask questions over HTTP and get answers from the Claude or ChatGPT subscription signed in on the server.

1. Open the **orke support** window from the Dock at the bottom of the screen. Create AIs, keys and settings in a browser on a computer. A phone can only show AIs and their room records (on a phone the window is in the side list).
2. Create an AI, copy its access key (`orke_sk_…`, shown in full only once) and add MCP tools if you need them. The AI's **연결** (Connection) tab shows its address, its key and example requests (curl) for your service.
3. Your service sends its questions to `http://127.0.0.1:48700/v1`. That address is reachable only from the server itself, so to take questions from another computer, put nginx or Caddy with HTTPS in front of it on the server. The button at the bottom of the AI list (it reads **입구 열림**, "ingress open") opens **orke support 설정** (orke support settings), which shows Caddy and nginx examples. With nginx, set `proxy_read_timeout` longer than the AI's time limit (5 minutes by default); nginx's default of 60 seconds is too short.

Good to know:

- orke support answers only with a subscription sign-in. If Codex is signed in with an API key, it refuses and tells you to sign in with your ChatGPT account.
- Your ngrok address is for people opening orke's screen. Services do not send questions through it.
- **Keep 기본 도구 쓰기 (Use built-in tools) off for any AI that answers text from customers.** A Claude AI with built-in tools turned on runs commands with the full permissions of the user that runs orke, even outside its working folder; in a test, its Bash tool wrote a file outside the folder. As orke warns when you turn the tools on, such an AI can read or change orke's files, including other rooms' records and stored secrets.
- On Ubuntu 24.04's default settings, a ChatGPT AI with built-in tools turned on cannot run any command, not even a read-only one: Ubuntu's security settings block the sandbox that Codex uses for commands (measured with Codex 0.160.1). Those failed attempts do not appear in the room record.

## Everyday commands

| Command | What it does |
| --- | --- |
| `orke service status` | Shows whether the service runs, which ngrok program it uses and the last ngrok error |
| `orke service restart` | Restarts orke, for example after `orke remote setup` |
| `orke service uninstall` | Stops and removes the service. Your settings in `~/.orke` stay. |
| `journalctl --user -u orke` | The service log. orke writes one start line there. |
| `less ~/.orke/logs/daemon.log` | orke's own log |

> [!WARNING]
> Restarting orke, with `orke service restart` or by installing an update, ends every terminal session and every running agent on the server, and stops orke support questions that are in progress. Do it when nothing important is running. Run it in an SSH session; if you run it from a terminal tab inside orke, that tab ends too and the browser reconnects to a workspace with no sessions.

## Update

Download the new version from the [releases page](https://github.com/bomtobe-hgkim/orke-releases/releases), check it, unpack it and run its installer, the same way as steps 2 and 3:

```bash
curl -fLO https://github.com/bomtobe-hgkim/orke-releases/releases/download/v<version>/orke-<version>-linux-x64.tar.gz
curl -fLO https://github.com/bomtobe-hgkim/orke-releases/releases/download/v<version>/orke-<version>-linux-x64.tar.gz.sha256
sha256sum -c orke-<version>-linux-x64.tar.gz.sha256
tar xzf orke-<version>-linux-x64.tar.gz
./orke-<version>-linux-x64/install.sh
```

If the service is running, the installer stops it, puts the new version in place and starts it again. Your settings in `~/.orke` are kept. Stopping the service ends all running sessions, as described in the warning above.

- Run the installer in an SSH session, not in a terminal tab inside orke; the installer refuses to run there, because stopping the service would end that tab.
- If you started `orke serve` by hand, stop it with <kbd>Ctrl</kbd>+<kbd>C</kbd> first.

## Uninstall

Remove the service first, then the program:

```bash
~/.local/bin/orke service uninstall
rm -rf ~/.local/share/orke ~/.local/bin/orke
```

Do it in this order. If you delete the program first, the service is left trying to start a program that no longer exists.

Optional clean-up:

- If you used orke support, delete its rooms in orke before uninstalling. Their Claude and Codex conversation histories are kept in `~/.claude/projects` and `~/.codex/sessions`, and deleting a room removes them.
- `rm -rf ~/.orke` deletes all of orke's settings and records, including the remote access settings.
- `loginctl disable-linger $USER` turns linger off again, if nothing else on the server needs it.
- `sudo apt-get remove ngrok` removes ngrok.

## Troubleshooting

| You see | Meaning | What to do |
| --- | --- | --- |
| `오류: orke에 필요한 패키지가 없습니다: …` | Required packages are missing | Run the `sudo apt-get` command it prints, then run the installer again. |
| `root로는 설치하지 않습니다 …` | The installer refuses `root` | Log in as a regular user and run it again. |
| `snap으로 설치한 ngrok은 지원하지 않습니다 …` | ngrok was installed from snap | Remove the snap (`sudo snap remove ngrok`) and install ngrok from the apt repository ([step 4](#4-install-ngrok)). |
| `주의: linger를 켜지 못했습니다 …` | Your user may not turn on linger without a password | Have an administrator run `sudo loginctl enable-linger <your user name>` once. Until then, orke stops when you log out. |
| `orke is already running.` | orke is already running, usually as the service | Use `orke service status` and `orke service restart` instead of `orke serve`. |
| `이 시스템은 systemd로 부팅되지 않아 …` | No systemd (a container or WSL) | orke's service cannot be installed there. orke suggests running `orke serve` directly instead; that has not been tested. |
| `sudo -u·su로 바꾼 셸에서는 그 사용자의 서비스를 다룰 수 없습니다 …` | The service commands do not work in a shell opened with `sudo -u` or `su` | Log in with SSH directly as the user who runs orke. |
| `이 주소를 다른 orke이 쓰고 있습니다` | ngrok error 334: another computer is using the same ngrok address | Stop remote access on the other computer, then run `orke service restart`. |
| `ngrok 인증에 실패했습니다` | ngrok error 105 or 107: ngrok rejected the saved authtoken | Run `orke remote setup` again with the current authtoken from the ngrok dashboard, then `orke service restart`. |
| `연결하지 못했습니다` with a **다시 연결** button | The browser lost the connection for a long time | Press **다시 연결** (Reconnect). |

orke does not keep retrying after ngrok errors 334, 105 and 107. Fix the cause, then run `orke service restart`.

## What has been tested

On one Ubuntu 24.04.5 LTS (x86_64) server on Google Cloud, in October 2026, with test builds of this release's code (installed as 3.3.1 and 3.3.2, before the 3.4.0 version number):

- installing, and updating over a running service, with `install.sh`,
- the service starting at boot without anyone logging in, and running on after logout (for a user in the server's admin groups, where linger could be turned on without a password),
- ngrok connecting again by itself after the network came back,
- opening orke at the ngrok address from a PC browser and from a development build of the Android app,
- signing in to Claude and ChatGPT from a terminal tab inside orke,
- orke support answering questions on the server.

Not tested yet: other distributions, desktop Linux, servers without systemd, ngrok installed other than from its apt repository, ngrok errors 334, 105 and 107 on a real server (checked only by automated tests), Claude Code and Codex sessions started from the new-session window, opening orke through an SSH tunnel, the Google Play version of the Android app, and questions arriving through nginx or Caddy from another computer.
