# ArturSu TV App — LG webOS

> A **webOS app** for LG C1 (and other webOS TVs) that loads a website from this GitHub repository and displays it fullscreen on your TV.

---

## Install via Homebrew Channel (Recommended)

1. Open **Homebrew Channel** on your LG TV
2. Go to **Settings** (gear icon)
3. Go to **Add Repository**
4. Enter this URL:
   ```
   https://raw.githubusercontent.com/Artur-Su/art-lg-webos-app-website/main/repo.json
   ```
5. The app **"ArturSu TV App"** will appear in the list — click **Install**

---

## How it works

```
Homebrew Channel
  └─ reads repo.json → finds com.artursu.lgapp
       └─ downloads .ipk from GitHub Releases → installs on TV

Your LG TV (after install)
  └─ ArturSu TV App
        │
        ├─ reads  /config.json  (this repo)
        └─ loads  /site/index.html  (this repo, fullscreen iframe)
                          ↑
              Fetched live via raw.githubusercontent.com
```

---

## Repository structure

```
art-lg-webos-app-website/
├── README.md                        ← you are here
├── repo.json                        ← Homebrew Channel repository index
├── com.artursu.lgapp.manifest.json  ← app manifest for Homebrew Channel
├── config.json                      ← app config (siteFolder, branch)
├── assets/
│   ├── icon.png
│   └── largeIcon.png
└── site/
    ├── index.html                   ← YOUR WEBSITE — edit this!
    └── ...                          ← CSS, JS, images
```

---

## Customising your website

Edit **`/site/index.html`** — this is displayed fullscreen on your TV.

- Use plain HTML, CSS, JavaScript
- Reference assets relatively: `<img src="images/photo.jpg">` → put in `/site/images/`
- External CDN links work fine
- After pushing to GitHub, press **🔴 Red** on your remote to reload instantly

---

## config.json

```json
{
  "siteFolder": "site",
  "branch": "main",
  "appName": "ArturSu TV App"
}
```

| Field | Default | Description |
|-------|---------|-------------|
| `siteFolder` | `"site"` | Folder with your website |
| `branch` | `"main"` | Git branch to load from |

---

## Manual install (.ipk)

Download from [Releases](https://github.com/Artur-Su/art-lg-webos-app-website/releases/latest) and sideload via USB or Dev Mode.

```bash
# Via webOS CLI
ares-install com.artursu.lgapp_1.0.0_all.ipk
```

---

## Remote control shortcuts

| Button | Action |
|--------|--------|
| **Back** | Toggle Settings ↔ Player |
| **🟢 Green** | Open Settings |
| **🔴 Red** | Reload the website |
| **D-pad** | Navigate buttons |
| **OK** | Confirm / Save |
| **Magic Remote** | Move pointer to show top bar |

---

## Troubleshooting

**Error 600 in Homebrew Channel** — Make sure you are using the full `repo.json` URL:
```
https://raw.githubusercontent.com/Artur-Su/art-lg-webos-app-website/main/repo.json
```
NOT the GitHub.com page URL.

**Website not loading** — Make sure `/site/index.html` exists in the repo and the repo is public.

---

## App info

| Field | Value |
|-------|-------|
| App ID | `com.artursu.lgapp` |
| Version | `1.0.0` |
| Target | LG webOS TV (C1, C2, C3, OLED) |
| Author | Artur Su |

---

MIT License
