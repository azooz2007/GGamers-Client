<p align="center">
  <img src="preview.png" alt="GGamers Proxy Client" width="100%">
</p>

<h1 align="center">GGamers Proxy Client</h1>

<p align="center">
  <b>Low-latency SOCKS5 tunnel for online gaming — TCP &amp; UDP, per-app or global.</b>
</p>

<p align="center">
  <a href="GGamers-Client.exe"><img src="https://img.shields.io/badge/version-3.4.0-19E3C0?style=for-the-badge" alt="version"></a>
  &nbsp;
  <a href="GGamers-Client.exe"><img src="https://img.shields.io/badge/⬇%20Download-GGamers--Client.exe-2ecc71?style=for-the-badge" alt="download"></a>
</p>

<p align="center">
  <sub>Windows 10/11 · 64-bit · run as Administrator · ~40&nbsp;MB single file</sub>
</p>

> **Download the latest build:** click **Download** above (it grabs
> `GGamers-Client.exe` straight from this repo). Older versions are on the
> [Releases](../../releases) page.

---

## What is it?

GGamers routes your game — or your whole PC — through a **SOCKS5 proxy**, the
way a gaming VPN would, but with far more control and no virtual adapter. It's
built for **online play and streaming**: a self-healing UDP relay, per-app
routing that never half-tunnels a connection, deep socket tuning, and a clean
UI that stays out of your way.

Point it at any SOCKS5 server (your own, or a subscription like **Mudfish**)
and play.

## Highlights

- **🎮 Basic or Advanced mode** — pick on first launch. **Basic** is stripped
  down and game-ready (gaming tuning always on, just pick a server and play);
  **Advanced** unlocks everything. Switch anytime from the top-right corner.
- **Three routing modes** — **Global** (whole PC, VPN-style), **Per-app** (only
  the games/apps you choose, matched by exe including child processes), and
  **Proxy Debug** (only apps you launch from inside).
- **TCP &amp; UDP** — full `CONNECT` and `UDP ASSOCIATE`, with a supervised,
  self-healing UDP association. Falls back to TCP-only if your server has no UDP.
- **Subscribed servers** — built-in **Mudfish** server list: fetched, ping-sorted,
  searchable, with **pinnable ★ favourites** that stay on top regardless of ping.
- **Smart bypass** — keep web / voice / streaming / CDN traffic (TCP 80/443,
  UDP 443/QUIC, WebSocket) **off** the proxy so only real game traffic is
  tunneled and your subscription isn't drained — in Global *and* Per-app mode.
- **🔎 Test connection** — before you press Start: reachability, auth, a real
  `CONNECT` with RTT, `UDP ASSOCIATE`, and datagrams relayed both ways.
- **Live health &amp; analytics** — a real 5-second proxy ping (min/avg/max) in
  the status bar and a latency wave; a per-app **session report** (data, packets,
  latency, jitter, hiccups) logged when an app stops.
- **Windows notifications** — get told when a selected app starts and stops
  being proxied (with the app's name).
- **Encrypted passwords** — SOCKS5 passwords are stored encrypted (Windows
  DPAPI, tied to your account), never in plaintext.
- **Deep tuning (Advanced)** — DSCP EF via qWAVE, Don't-Fragment / MTU guard,
  TIME_CRITICAL relay threads + HIGH process priority, WSAECONNRESET/NETRESET
  handling, and an optional mobile/lossy-link duplication enhancer.
- **Packet toolbox (Advanced)** — live capture, protocol decoders, a WebSocket
  sender, rewrite rules, and a conversation recorder/replay.

## Download &amp; run

1. Click **⬇ Download** above to get **`GGamers-Client.exe`**.
2. **Right-click → Run as administrator.** The app uses the WinDivert kernel
   driver to capture traffic, which needs elevation. (It requests it
   automatically; approve the UAC prompt.)
3. On first launch, pick **Basic** or **Advanced**.
4. Enter a SOCKS5 server on the **Connection** tab — either a **Custom** server
   (host / port / username / password) or a **Subscribed** one (e.g. Mudfish:
   set your username/password, update the list, pick a server).
5. *(Optional)* Click **🔎 Test connection** to confirm it works.
6. Choose your mode on **Mode / Apps** (in Basic it's Per-app: add your game),
   then press **Start**.

It's a single portable `.exe` — no installer. It writes its `config.json`,
`subscribed-server.json` and a log next to itself.

> **SmartScreen note:** the download isn't code-signed yet, so Windows may show
> a "Windows protected your PC" prompt — choose **More info → Run anyway**.

## Modes at a glance

| Mode | Tunnels | Use it for |
|------|---------|------------|
| **Global** | Everything (except LAN, the proxy itself, web/voice if bypass is on) | Whole-PC, VPN-style |
| **Per-app** | Only the exes you list (and their children) | Just your game, nothing else |
| **Proxy Debug** | Only apps you launch from inside | Inspecting one app / Charles-Fiddler |

## Troubleshooting

- **"Must run as Administrator"** — right-click the exe → *Run as administrator*.
- **A random 1-second lag spike** on a stable server (Mudfish etc.) — turn
  **off** *Auto re-associate on relay silence* in **Tuning → UDP**; the auto
  re-associate is only needed for servers that recycle UDP sessions.
- **Game's 443 traffic still going through the proxy** — tick **Bypass web /
  voice / streaming** on the Connection tab (works in Per-app mode too).
- **Notifications don't appear** — make sure notifications are enabled for the
  app in Windows Settings and Focus Assist is off.

## Legal / safety

Use GGamers only with proxy servers you own or are authorised to use, and in
line with each game's terms of service. This is a networking tool provided
**as-is, without warranty**; you are responsible for how you use it.

---

<p align="center"><sub>© GGamers · <a href="https://GGamers.net">GGamers.net</a></sub></p>
