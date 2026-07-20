# Official Vishwateja — iOS / Mac App Legal Hub

**Repository:** `officialvishwateja-ios`  
**Developer:** Vishwateja S B (Official Vishwateja)  
**GitHub:** [Code-Smith-07](https://github.com/Code-Smith-07)

Static hosting site for **App Store / Mac App Store** privacy policies, support pages, and a public landing page that lists Official Vishwateja apps. Designed to be deployed with **Firebase Hosting** (project id: `officialvishwateja-ios`).

---

## What’s in this repo

| Path | Description |
|------|-------------|
| `index.html` | Glassmorphism landing page — lists published apps |
| `favicon.svg` | Site favicon |
| `firebase.json` | Firebase Hosting config (`public: "."`) |
| `.firebaserc` | Default Firebase project: `officialvishwateja-ios` |
| `Chat Blues/` | Privacy policy, support page, app icon |
| `Control Pro/` | Privacy policy, support page, app icon |
| `Birthdays Reminder Pro/` | Privacy policy, support page, app icon |
| `Prompt Notes Pro/` | Privacy policy, support page, app icon |

This is **not** the full native app source code. It is the **legal + support web surface** required by Apple App Store Connect (Privacy Policy URL, Support URL).

---

## Apps covered

### 1. Chat Blues
- **Type:** iOS AI chat / productivity (BYOK + on-device models)  
- **Bundle ID:** `com.officialvishwateja.chatblues`  
- **Tagline:** Free AI chat with your own keys or private on-device models  
- **Product site:** [chatblues.com](https://chatblues.com/)  
- **Privacy:** [`Chat Blues/privacy-policy.html`](./Chat%20Blues/privacy-policy.html)  
- **Support:** [`Chat Blues/support/index.html`](./Chat%20Blues/support/index.html)

### 2. Control Pro – Desktop Remote
- **Type:** iOS remote control / screen mirroring (local network, TLS, zero data collection)  
- **Bundle ID:** `com.controlpro.ioscontroller`  
- **Tagline:** Wireless trackpad, keyboard, and live screen mirror for your computer  
- **Source repo:** [Control-Pro](https://github.com/Code-Smith-07/Control-Pro)  
- **Privacy:** [`Control Pro/privacy-policy.html`](./Control%20Pro/privacy-policy.html)  
- **Support:** [`Control Pro/support/index.html`](./Control%20Pro/support/index.html)

### 3. Birthdays Reminder Pro
- **Type:** iOS productivity / reminders  
- **Tagline:** Never miss a birthday again — timely reminders for important dates  
- **Privacy:** [`Birthdays Reminder Pro/privacy-policy.html`](./Birthdays%20Reminder%20Pro/privacy-policy.html)  
- **Support:** [`Birthdays Reminder Pro/support/index.html`](./Birthdays%20Reminder%20Pro/support/index.html)

### 4. Prompt Notes Pro
- **Type:** macOS utility (AI prompts & code snippets)  
- **Tagline:** Manage AI prompts and code snippets in one native macOS app  
- **Privacy:** [`Prompt Notes Pro/privacy-policy.html`](./Prompt%20Notes%20Pro/privacy-policy.html)  
- **Support:** [`Prompt Notes Pro/support/index.html`](./Prompt%20Notes%20Pro/support/index.html)

---

## Folder structure

```text
officialvishwateja-ios/
├── README.md
├── index.html                 # App directory landing page
├── favicon.svg
├── firebase.json              # Firebase Hosting
├── .firebaserc
├── Chat Blues/
│   ├── privacy-policy.html
│   ├── icon.png
│   └── support/
│       └── index.html
├── Control Pro/
│   ├── privacy-policy.html
│   ├── icon.png
│   └── support/
│       └── index.html
├── Birthdays Reminder Pro/
│   ├── privacy-policy.html
│   ├── IMG_0802-Photoroom.png
│   └── support/
│       └── index.html
└── Prompt Notes Pro/
    ├── privacy-policy.html
    ├── icon.png
    └── support/
        └── index.html
```

---

## Local preview

No build step. Open the landing page in a browser:

```bash
cd officialvishwateja-ios
open index.html
# or serve with any static server:
npx --yes serve .
```

---

## Deploy (Firebase Hosting)

Prerequisites: [Firebase CLI](https://firebase.google.com/docs/cli) and access to project `officialvishwateja-ios`.

```bash
cd officialvishwateja-ios
firebase login
firebase deploy --only hosting
```

Hosting serves the repo root (see `firebase.json`). Paths with spaces (app folder names) work as relative URLs from `index.html`.

---

## App Store Connect usage

Point each app’s metadata to the hosted URLs, for example:

| App | Privacy Policy URL (path) | Support URL (path) |
|-----|---------------------------|--------------------|
| **Chat Blues** | `/Chat%20Blues/privacy-policy.html` | `/Chat%20Blues/support/index.html` |
| **Control Pro – Desktop Remote** | `/Control%20Pro/privacy-policy.html` | `/Control%20Pro/support/index.html` |
| Birthdays Reminder Pro | `/Birthdays%20Reminder%20Pro/privacy-policy.html` | `/Birthdays%20Reminder%20Pro/support/index.html` |
| Prompt Notes Pro | `/Prompt%20Notes%20Pro/privacy-policy.html` | `/Prompt%20Notes%20Pro/support/index.html` |

Prefix with your Firebase Hosting domain, e.g.  
`https://officialvishwateja-ios.web.app/Chat%20Blues/privacy-policy.html`

---

## Design notes

- Light / dark mode via `prefers-color-scheme`
- Apple-style glass cards, SF Pro / system font stack
- Safe-area padding for notched devices
- Static HTML/CSS only — no analytics SDKs, no trackers

---

## Related repositories

| Repo | Purpose |
|------|---------|
| [Prompt-Notes](https://github.com/Code-Smith-07/Prompt-Notes) | Prompt Notes product monorepo (web / Electron Mac app, etc.) |

---

## License

Copyright © 2026 Official Vishwateja (Vishwateja S B). All rights reserved.

Privacy policy and support HTML are provided for App Store compliance. Reuse of branding, icons, or copy requires permission from the developer.

---

## Contact

- **Developer:** Vishwateja S B  
- **GitHub:** [@Code-Smith-07](https://github.com/Code-Smith-07)  
- **Email:** officialvishwateja@proton.me  

---

## Changelog

### 1.2.0 — Control Pro legal pages
- Added **Control Pro – Desktop Remote** privacy policy, support site, and app icon  
- Landing page lists Control Pro under iOS Apps  
- README App Store Connect URL table updated  

### 1.1.0 — Chat Blues legal pages
- Added **Chat Blues** privacy policy, support site, and app icon  
- Landing page lists Chat Blues under iOS Apps  
- README App Store Connect URL table updated  

### 1.0.0 — Initial public upload
- Landing page for Official Vishwateja apps  
- Birthdays Reminder Pro privacy + support  
- Prompt Notes Pro privacy + support  
- Firebase Hosting configuration  
