<p align="center">
  <img src="preview.png" alt="GGamers Proxy Client" width="100%">
</p>

<h1 align="center">GGamers Proxy Client</h1>

<p align="center">
  <b>Low-latency tunnel for online gaming — SOCKS5 &amp; TUIC v5 (QUIC), TCP &amp; UDP, per-app or global.</b>
</p>

<p align="center">
  <a href="GGamers-Client.exe"><img src="https://img.shields.io/badge/version-5.0.0-19E3C0?style=for-the-badge" alt="version"></a>
  &nbsp;
  <a href="GGamers-Client.exe"><img src="https://img.shields.io/badge/⬇%20Download-GGamers--Client.exe-2ecc71?style=for-the-badge" alt="download"></a>
</p>

<p align="center">
  <sub>Windows 10/11 · 64-bit · single self-contained file · runs as Administrator</sub>
</p>

> **Download the latest build:** click **Download** above (it grabs
> `GGamers-Client.exe` straight from this repo). Older versions are on the
> [Releases](../../releases) page.

---

## Table of contents

1. [What is it?](#what-is-it)
2. [Highlights](#highlights)
3. [Requirements](#requirements)
4. [Install &amp; first run](#install--first-run)
5. [Quick start](#quick-start)
6. [The app, tab by tab](#the-app-tab-by-tab)
7. [How it works](#how-it-works)
8. [Updating](#updating)
9. [Troubleshooting](#troubleshooting)
10. [Credits](#credits)

---

## What is it?

A Windows desktop app that transparently routes your traffic through a remote
server — **all of it** (VPN-style), **only the apps you pick** (your game, your
browser), or **only what you launch from inside the app** — with no per-app proxy
settings, no browser extensions and no virtual network adapter.

It's built for **online gaming**: low-latency TCP **and** UDP, a self-healing UDP
relay that survives router/CGNAT idle timeouts, deep socket tuning, and a
per-flow engine that never half-tunnels a connection (which is what gets you
flagged on anti-cheat servers).

**Version 4.0.0 is a full rewrite in C# / .NET** — the older Python build could
briefly stutter or hang the machine mid-game; this one runs natively with none of
that.

---

## Highlights

- **Two transports:**
  - **SOCKS5** — **Custom** (a saved list of your own servers: add several, pick from
    a dropdown, edit or delete with the ⚙ button) or **Subscription** (auto-fetch your
    server list and ping them, pick the fastest).
  - **TUIC v5 (QUIC)** — paste a `tuic://` share link; a bundled client dials your
    server over QUIC with native UDP relay + BBR congestion control. Great for games.
- **Live server ping** next to the selected server (refreshes every 5 s), with its
  country flag — for all three transports.
- **3× UDP redundancy** (optional) — send each game packet three times to ride out
  packet loss. Off by default each launch.
- **Three modes:** **Global** (everything), **Per-app** (only apps you select — with
  icons; double-click to add/remove), **Proxy Debug** (only what you launch).
- **Self-healing UDP relay** — keepalives + automatic re-association so a game
  never silently loses its connection after a few minutes idle in a lobby.
- **Live Connections view** — every connection with its **app icon**, destination,
  a **TUNNEL / DIRECT** badge, ping, jitter, packets and bytes, plus a **live
  up/down bandwidth graph** with session totals.
- **One-click gaming preset** on the Server tab, with a **⚙ Settings** popup for
  fine-grained TCP/UDP low-latency tuning (Save / Cancel / Reset).
- **Quality-of-life** — Dark / Light themes, a guided first run, minimise-to-tray,
  start-with-Windows, a desktop notification when one of your apps starts tunneling,
  **back up / restore your settings** (Export / Import config), and a built-in **updater**.
- **Readable log** — normal activity and errors are always shown; routine warnings
  are tucked behind a **Show warnings** toggle. Everything is also saved to a
  session log file for support.
- **Single self-contained `GGamers.exe`** — nothing to install alongside it.

---

## Requirements

- **Windows 10 or 11, 64-bit.**
- **Administrator** — the app uses a kernel network driver (WinDivert) to capture
  traffic, so Windows shows a **UAC prompt** each time it starts. That's normal
  and required; just click **Yes**.

That's it — **no .NET runtime to install** and no other prerequisites. The .NET
runtime, the network driver and the TUIC client are all bundled inside the one exe.

---

## Install &amp; first run

1. **Download** `GGamers-Client.exe` (button above) and run it.
2. It installs itself into `%LOCALAPPDATA%\GGamers`, creates Desktop + Start-menu
   shortcuts (optionally pins to Start), and launches.
3. Running the downloaded file again later shows **Repair / Uninstall / Open**.

Your settings live in the install folder and are kept across updates.

---

## Quick start

1. Open the **Connection** tab and choose a server:
   - **Custom SOCKS5** — click **+ Add server**, enter host / port / (optional)
     credentials; add as many as you like and pick from the dropdown, or
   - **Subscribed SOCKS5** — press **Refresh list**, then pick the fastest server, or
   - **TUIC v5** — press **📋 Paste from clipboard** with a `tuic://` link copied.
2. (Optional) **Test connection** to confirm the server answers.
3. Pick a **mode** on **Mode &amp; Apps** — for gaming, **Per-app** and double-click
   your game to add it.
4. Press **▶ Start** (accept the UAC prompt). The button turns into **■ Stop**.
5. Watch the **Connections** tab to see your game tunneling.

While it's running the connection / mode / tuning settings are locked so nothing
conflicting changes mid-session — press **Stop** to change them.

---

## The app, tab by tab

- **Server** — pick your server (Custom / Subscription / TUIC), protocol
  (UDP relay for games, or TCP-only), and options (bypass web, bypass LAN,
  3× UDP redundancy, tunnel DNS). The **🎮 gaming preset** and a **⚙ Settings**
  popup (low-latency TCP/UDP tuning, Save / Cancel / Reset) sit at the top, and
  **Test connection** checks it end-to-end.
- **Mode &amp; Apps** — Global / Per-app / Debug, and the app pickers (with icons;
  double-click to add or remove).
- **Connections** — live tunnel activity, the bandwidth graph and the
  *Show direct connections* toggle. Latency is re-measured every few seconds (TCP
  port-ping for accuracy). **Right-click a connection** to copy its IP, terminate it,
  or set a temporary **speed cap** (upload/download) — capped rows show a purple
  **CAPPED** badge and the cap clears when the connection ends or you close the app.
- **Log** — what the engine is doing, and connection-test results. Normal lines and
  errors are always shown; tick **Show warnings** to mix routine warnings back in.
  Everything is also written to `%LOCALAPPDATA%\GGamers\session.log`.
- **About** — version, links, **Check for updates**, and **Export / Import** your
  configuration (a handy backup; saved passwords stay encrypted to this PC).

---

## How it works

Your outbound packets are captured by the **WinDivert** kernel driver, NAT'd to a
local listener, and forwarded to your server — over **SOCKS5** (`CONNECT` for TCP,
`UDP ASSOCIATE` for UDP), or through a **bundled TUIC client** that carries
everything inside a single QUIC tunnel. Replies are rewritten on the way back so
your apps only ever see the real remote peer. A sticky per-flow decision means a
connection is either fully tunneled or fully direct — never split.

---

## Updating

Open **About → Check for updates**. If a newer version is published it downloads,
replaces the app and relaunches. You can also just re-download `GGamers-Client.exe`
from here any time.

---

## Troubleshooting

- **No UAC prompt / won't start** — it must run as Administrator; right-click →
  *Run as administrator*.
- **"Server unreachable" / Test fails** — double-check host/port (and for TUIC,
  that the `tuic://` link is exactly the one from your panel), and that the server
  is up.
- **Game connects but lobby/join fails on a QUIC transport** — turn **bypass web
  off** and use **Per-app** mode, so downloads and gameplay share one exit IP.
- **UDP not working** — some servers don't support UDP relay; the app falls back
  to TCP-only automatically (shown in the Log).
- **Something misbehaved mid-session** — open the Log and tick **Show warnings**, or
  send the session log at `%LOCALAPPDATA%\GGamers\session.log` — it records the full
  run (including the tunnel client's own messages).

---

## Credits

Made by **Yakuza** — [GGamers.net](https://GGamers.net) ·
Telegram [@Yakuza4](https://t.me/Yakuza4) · Snapchat
[@yakuuo](https://www.snapchat.com/add/yakuuo). Made by gamers for gamers ❤️

Free for personal use. The author is not responsible for any ToS violations
resulting from proxy use in online services.
