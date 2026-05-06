# Status Indicator for Grok & xAI

> **A beautiful live status widget for grok.com & status.x.ai** — built by Grok for the community.

**Download the latest version:**
- [⬇️ Download ZIP](https://github.com/StarlightSyntax/grok-status-indicator/releases/latest) *(Recommended)*

---

**A lightweight, beautiful, always-up-to-date status widget** that lives directly on `grok.com` and `status.x.ai`.

- **Native Grok UI** — Dark minimalist design matching xAI/grok.com aesthetic (almost-black cards, high-contrast typography, subtle purple accents, smooth animations).
- **Live updates** — Pulls real-time data straight from https://status.x.ai every ~45 seconds (no external APIs or CDNs).
- **Small & non-intrusive** — Collapsible floating widget (closed = elegant pill with status dot; open = rich panel with services, uptime %, model latencies).
- **Works everywhere** — Content script on grok.com + status.x.ai. Bonus: Click the extension icon in toolbar for instant popup status from any tab.
- **Fully local** — 100% self-contained. No tracking, no external dependencies.
- **Cross-browser** — Manifest V3 (Chrome + Firefox compatible).

## Features

- Overall system status banner (green/yellow/red)
- All monitored services with "Available" badges
- Live regional uptime (Inference / Non-inference % for eu-west-1 & us-east-1)
- Model latencies (ITL in ms) — sorted fastest first
- Relative "last updated" timestamps
- Manual refresh button
- Keyboard shortcut: `Ctrl/Cmd + Shift + S`
- Auto-opens once on status.x.ai for convenience
- Error handling with cached fallback

## Installation (Chrome)

### Chrome / Edge / Brave (Recommended)

1. Download the latest `status-indicator-extension-v1.0.1.zip` from the [Releases page](https://github.com/StarlightSyntax/grok-status-indicator/releases/latest)
2. **Extract** the zip file
3. Open Chrome and go to: `chrome://extensions/`
4. Enable **Developer mode** (toggle in top right)
5. Click **Load unpacked**
6. Select the extracted `status-indicator-extension` folder
7. The extension will appear in your extensions list

**Done!** The Status Indicator will now appear in the bottom-right on `grok.com` and `status.x.ai`.

### Optional: Pin the Extension
- Click the puzzle icon in Chrome toolbar
- Pin **Status Indicator - xAI & Grok** so it's always visible

## How It Works

1. Background service worker fetches https://status.x.ai/ periodically.
2. Parses the HTML (robust text + regex extraction for services, metrics, models).
3. Stores clean JSON in `chrome.storage.local`.
4. Content script on supported domains injects the floating widget and listens for updates.
5. UI updates instantly — no page reload needed.

## Customization Ideas (Advanced)

- Edit `styles.css` to tweak colors or spacing.
- Change update interval in `background.js` (`UPDATE_INTERVAL_MINUTES`).
- Add more models or custom thresholds.

## Known Limitations

- Parsing relies on the current structure of status.x.ai. If xAI changes the page layout significantly, the extractor may need minor updates (easy to fix — open an issue).
- No real-time WebSocket push (uses polling + storage events for near-instant feel).
- On very rare fetch failures, shows last cached data.

## Credits & Philosophy

Built with maximum truth-seeking and minimalism in mind — exactly what you'd expect from a Grok-native tool.

Created for StarlightSyntax by Grok 4.20 Heavy (multi-agent swarm) to be distributed freely!.

---

**Enjoy real-time visibility into xAI's infrastructure while chatting with Grok.** 

If you love it, star the repo or share feedback! 

For issues: Check console logs (`background.js` and content script) or open the popup and hit Refresh.
