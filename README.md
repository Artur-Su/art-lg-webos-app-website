# ArturSu TV App — LG webOS

> A **webOS app** for LG C1 (and other webOS TVs) that loads a website from this GitHub repository and displays it fullscreen on your TV.

---

## How it works

```
Your LG TV
  └─ ArturSu TV App (webOS .ipk)
        │
        ├─ reads  → /config.json          (this repo, optional)
        └─ loads  → /site/index.html      (this repo, required)
                          ↑
              Fetched via raw.githubusercontent.com
              and rendered in a fullscreen iframe
```

1. Install the `.ipk` on your TV via **Homebrew Channel**.
2. Open the app — on first launch the **Settings** screen appears.
3. Paste this repository URL:
   ```
   https://github.com/Artur-Su/art-lg-webos-app-website
   ```
4. Press **Save & Open** — the app fetches `/site/index.html` and shows it fullscreen.

---

## Repository structure

```
art-lg-webos-app-website/
├── README.md          ← you are here
├── config.json        ← app configuration (optional overrides)
└── site/
    ├── index.html     ← YOUR WEBSITE — edit this!
    └── ...            ← CSS, JS, images, fonts, etc.
```

---

## config.json reference

Located at the **root** of this repo. All fields are optional:

```json
{
  "siteFolder": "site",
  "branch":     "main",
  "appName":    "ArturSu TV App"
}
```

| Field | Default | Description |
|-------|---------|-------------|
| `siteFolder` | `"site"` | Folder containing your website |
| `branch` | `"main"` | Git branch to load from |
| `appName` | `"ArturSu TV App"` | Display name (future use) |

---

## Customising your website

Edit **`/site/index.html`** — this is what gets displayed on your TV.

- You can use plain HTML, CSS, JavaScript
- Reference assets relatively: `<img src="images/photo.jpg">` → put them in `/site/images/`
- External CDN links (e.g. `https://cdn.jsdelivr.net/...`) work fine
- The app injects a `<base>` tag so all relative paths resolve correctly via `raw.githubusercontent.com`

> **Tip:** After pushing changes to GitHub, press the **🔴 Red** button on your remote to reload the site without reopening the app.

---

## Installing the app (.ipk)

### Option A — USB sideload (easiest)
1. Download `com.artursu.lgapp_1.0.0_all.ipk` from the [Releases](../../releases) page
2. Copy it to a USB drive (FAT32)
3. Plug into your LG C1
4. Open **Homebrew Channel** → **⚙ Settings** → install from USB

### Option B — Dev Mode (webOS CLI)
```bash
# Install webOS CLI
npm install -g @webosose/ares-cli

# Setup Dev Mode on your TV first, then:
ares-setup-device
ares-install com.artursu.lgapp_1.0.0_all.ipk
```

---

## Remote control shortcuts

| Button | Action |
|--------|--------|
| **Back** | Toggle between Settings and Player |
| **🟢 Green** | Open Settings |
| **🔴 Red** | Reload the website |
| **D-pad ↑↓←→** | Navigate buttons |
| **OK** | Confirm / Save |
| **Magic Remote** | Move pointer over top bar to show controls |

---

## App info

| Field | Value |
|-------|-------|
| App ID | `com.artursu.lgapp` |
| Version | `1.0.0` |
| Target | LG webOS TV (C1, C2, C3, OLED) |
| Author | Artur Su |
| Type | Web app (HTML/CSS/JS) |

---

## Troubleshooting

**❌ "Failed to Load Website"**
- Make sure this repository is **public**
- Verify `/site/index.html` exists
- Check the repository URL has no typos
- Press **Retry** or **Open Settings** to re-enter the URL

**❌ Images / CSS not loading**
- Use **relative paths** in your HTML (e.g. `./style.css` not `/style.css`)
- Avoid absolute paths that reference `localhost` or private servers

**❌ App not appearing after install**
- Restart Homebrew Channel
- Check that Dev Mode / Homebrew Channel is still active on your TV

---

## License

MIT — free to use, modify and redistribute.
