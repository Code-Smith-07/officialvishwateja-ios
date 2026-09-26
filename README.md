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
| `Daily Diary Notes/` | Privacy policy, support page, app icon |
| `Control Pro/` | Privacy policy, support page, app icon |
| `Birthdays Reminder Pro/` | Privacy policy, support page, app icon |
| `Prompt Notes Pro/` | Privacy policy, support page, app icon |
| `CodeQuest/` | Privacy policy, support page, app icon |

This is **not** the full native app source code. It is the **legal + support web surface** required by Apple App Store Connect (Privacy Policy URL, Support URL).

---

## ⚠️ URLs already submitted to Apple — never rename, never assume consistency

Once a Privacy Policy URL or Support URL is saved in an app's App Store Connect
record, **that exact URL is what Apple checks against on the live app**, not
whatever this repo's file layout "should" look like. Apple periodically
re-checks these URLs; if one 404s, the app can be flagged and hidden pending a
fix — this already happened once to Birthdays Reminder Pro (see the 1.3.5
changelog entry) because its folder has no matching redirect.

**Do not "clean up" or rename any path in this repo — including a folder name,
an `.html` filename, or a `firebase.json` redirect `source` — without first
confirming, per app, what URL is actually on file in App Store Connect.** The
fastest way to check, without needing App Store Connect access, is to read it
straight off the public App Store listing:

```bash
curl -s -A "Mozilla/5.0" "https://apps.apple.com/us/app/<app-slug>/id<appId>" \
  | grep -oE 'https://officialvishwateja[a-z-]*\.web\.app[^"'"'"'\\ ]*'
```

That prints the literal Privacy Policy / Support hrefs Apple has for that app.
Every app's *actual* App Store record is the source of truth — not this
README, not the folder structure, and not what a "consistent" naming scheme
would suggest.

**Birthdays Reminder Pro is a deliberate exception, not a bug to fix:** its
submitted URLs are the bare `/birthdays-reminder-pro` and
`/birthdays-reminder-pro/support` — no `/privacy` suffix, unlike every other
app's short-redirect convention below. Do not add a `/privacy` suffix or
otherwise make it match the others; that would break the live link Apple has
on file, exactly as happened before.

A new app (no App Store Connect record yet) has no submitted URL to preserve.
Pick whatever it should be, then never change it again once it's been entered
into App Store Connect.

**CodeQuest now has an App Store Connect record** (Apple ID `6816425215`, store
name **Code Quest Pro**, entered 26 September 2026). The URLs pasted into it are
the short aliases `https://officialvishwateja-ios.web.app/codequest/privacy` and
`https://officialvishwateja-ios.web.app/codequest/support`. Those two redirects in
`firebase.json`, and the `CodeQuest/` folder they point to, are now permanent.
The same two URLs are also linked from inside the app (Settings > About), so
renaming them would break the app too, not just the listing.

---

## Current privacy & support links — verified live, 26 September 2026

Every link below was re-checked two ways: read directly off the public App
Store listing with the `curl` command from the warning above (for apps that
are live on the App Store), and then hit with
`curl -sL -o /dev/null -w "%{http_code}"` to confirm it actually resolves.
All 16 returned **200**. Re-run both checks before trusting this table after
any redirect, folder, or filename change.

### Confirmed submitted to Apple (App Store Connect record exists)

| App | Privacy Policy URL | Support URL |
|-----|---------------------|--------------|
| Control Pro – Desktop Remote | https://officialvishwateja-ios.web.app/Control%20Pro/privacy-policy.html | https://officialvishwateja-ios.web.app/Control%20Pro/support/index.html |
| Daily Diary Notes | https://officialvishwateja-ios.web.app/daily-diary-notes/privacy | https://officialvishwateja-ios.web.app/daily-diary-notes/support |
| Birthdays Reminder Pro | https://officialvishwateja-ios.web.app/birthdays-reminder-pro | https://officialvishwateja-ios.web.app/birthdays-reminder-pro/support |
| Prompt Notes Pro (Mac) | https://officialvishwateja-ios.web.app/Prompt%20Notes%20Pro/privacy-policy.html | https://officialvishwateja-ios.web.app/Prompt%20Notes%20Pro/support/ |
| Code Quest Pro (CodeQuest) | https://officialvishwateja-ios.web.app/codequest/privacy | https://officialvishwateja-ios.web.app/codequest/support |

### Not yet on the App Store — repo pages exist and are live, but no Apple record to preserve yet

| App | Privacy Policy URL | Support URL |
|-----|---------------------|--------------|
| Chat Blues | https://officialvishwateja-ios.web.app/Chat%20Blues/privacy-policy.html | https://officialvishwateja-ios.web.app/Chat%20Blues/support/index.html |
| Control Pro Host (macOS, direct-download only — never submitted to any App Store, see deploy-rules.md §5.6) | https://officialvishwateja-ios.web.app/Control%20Pro/host-privacy-policy.html | https://officialvishwateja-ios.web.app/Control%20Pro/host-support/index.html |

Once any "not yet submitted" app is entered into App Store Connect, whichever
URL you actually paste into its Privacy Policy URL / Support URL fields
becomes permanent per the warning above — move its row up to the confirmed
table and never rename that path again.

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
- **Companion:** **Control Pro Host** (macOS, notarized direct download) — listed under macOS Apps on the landing page; shares this privacy policy and support page  
- **Source repo:** [Control-Pro](https://github.com/Code-Smith-07/Control-Pro)  
- **Privacy:** [`Control Pro/privacy-policy.html`](./Control%20Pro/privacy-policy.html)  
- **Support:** [`Control Pro/support/index.html`](./Control%20Pro/support/index.html)

### 3. Daily Diary Notes
- **Type:** iOS diary / journal (fully offline, zero data collection)  
- **Bundle ID:** `com.officialvishwateja.dailydiarynotes`  
- **Tagline:** A diary that feels like paper — fourteen bindings, real page turns, nothing leaves your device  
- **Privacy:** [`Daily Diary Notes/privacy-policy.html`](./Daily%20Diary%20Notes/privacy-policy.html)  
- **Support:** [`Daily Diary Notes/support/index.html`](./Daily%20Diary%20Notes/support/index.html)

### 4. Birthdays Reminder Pro
- **Type:** iOS productivity / reminders  
- **Tagline:** Never miss a birthday again — timely reminders for important dates  
- **Privacy:** [`Birthdays Reminder Pro/privacy-policy.html`](./Birthdays%20Reminder%20Pro/privacy-policy.html)  
- **Support:** [`Birthdays Reminder Pro/support/index.html`](./Birthdays%20Reminder%20Pro/support/index.html)

### 5. Prompt Notes Pro
- **Type:** macOS utility (AI prompts & code snippets)  
- **Tagline:** Manage AI prompts and code snippets in one native macOS app  
- **Privacy:** [`Prompt Notes Pro/privacy-policy.html`](./Prompt%20Notes%20Pro/privacy-policy.html)  
- **Support:** [`Prompt Notes Pro/support/index.html`](./Prompt%20Notes%20Pro/support/index.html)

### 6. CodeQuest (App Store name: Code Quest Pro)
- **Type:** iOS coding-lessons app (C, C++, Python, CS Foundations — fully offline, zero accounts)  
- **Bundle ID:** `com.vishwateja.codequest` · **App Store Connect Apple ID:** `6816425215`  
- **Names:** App Store listing **Code Quest Pro** ("CodeQuest" and "Code Quest" were already taken by other developers); home-screen name **Code Quest**. The pages here still say "CodeQuest", which is fine: it's the project name.  
- **Submitted URLs:** `/codequest/privacy` and `/codequest/support` (permanent, see the warning at the top)  
- **Tagline:** Learn C, C++, Python and CS Foundations with runnable lessons, quizzes and boss battles  
- **Source repo:** [CodeQuest](https://github.com/Code-Smith-07/CodeQuest)  
- **Privacy:** [`CodeQuest/privacy-policy.html`](./CodeQuest/privacy-policy.html)  
- **Support:** [`CodeQuest/support/index.html`](./CodeQuest/support/index.html)

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
├── Daily Diary Notes/
│   ├── privacy-policy.html
│   ├── icon.png
│   └── support/
│       └── index.html
├── Control Pro/
│   ├── privacy-policy.html
│   ├── icon.png
│   ├── host-icon.png
│   └── support/
│       └── index.html
├── Birthdays Reminder Pro/
│   ├── privacy-policy.html
│   ├── IMG_0802-Photoroom.png
│   └── support/
│       └── index.html
├── Prompt Notes Pro/
│   ├── privacy-policy.html
│   ├── icon.png
│   └── support/
│       └── index.html
└── CodeQuest/
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
| **Daily Diary Notes** | `/Daily%20Diary%20Notes/privacy-policy.html` | `/Daily%20Diary%20Notes/support/index.html` |
| Birthdays Reminder Pro | `/Birthdays%20Reminder%20Pro/privacy-policy.html` | `/Birthdays%20Reminder%20Pro/support/index.html` |
| Prompt Notes Pro | `/Prompt%20Notes%20Pro/privacy-policy.html` | `/Prompt%20Notes%20Pro/support/index.html` |
| **Code Quest Pro** (CodeQuest) | `/codequest/privacy` (short alias, as submitted) | `/codequest/support` (short alias, as submitted) |

Prefix with your Firebase Hosting domain, e.g.  
`https://officialvishwateja-ios.web.app/Chat%20Blues/privacy-policy.html`

Some apps also have short redirects configured in `firebase.json`, which are
easier to type and survive a folder rename:

| Short path | Goes to |
|------------|---------|
| `/daily-diary-notes/privacy` | `/Daily Diary Notes/privacy-policy.html` |
| `/daily-diary-notes/support` | `/Daily Diary Notes/support/` |
| `/control-pro/privacy` | `/Control Pro/privacy-policy.html` |
| `/control-pro/support` | `/Control Pro/support/` |
| `/control-pro/host-privacy` | `/Control Pro/host-privacy-policy.html` |
| `/control-pro/host-support` | `/Control Pro/host-support/` |
| `/control-pro/download` | `https://officialvishwateja-mac.web.app` |
| `/chat-blues/privacy` | `/Chat Blues/privacy-policy.html` |
| `/chat-blues/support` | `/Chat Blues/support/` |
| `/codequest/privacy` | `/CodeQuest/privacy-policy.html` |
| `/codequest/support` | `/CodeQuest/support/` |
| `/birthdays-reminder-pro` **(no `/privacy` — this exact bare path is what's submitted to Apple)** | `/Birthdays Reminder Pro/privacy-policy.html` |
| `/birthdays-reminder-pro/support` | `/Birthdays Reminder Pro/support/` |

---

## Design notes

- Light / dark mode via `prefers-color-scheme`
- Apple-style glass cards, SF Pro / system font stack
- Safe-area padding for notched devices
- Static HTML/CSS only — no analytics SDKs, no trackers
- **Copy style for new or edited text:** no long dashes (em or en). App Review reads these pages, and the
  developer wants them to read as plainly written. Use a period, comma, colon or parentheses instead.
  The CodeQuest pages and its home-page card follow this; older apps' pages haven't been rewritten yet.

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

### 1.3.7 — CodeQuest entered in App Store Connect; policy and support corrections
- CodeQuest has an App Store Connect record (Apple ID `6816425215`, listed as **Code Quest Pro**). Its row moved to
  the "Confirmed submitted" table; `/codequest/privacy` and `/codequest/support` are now permanent.
- Privacy policy: the iOS app no longer has a CDN fallback engine, so that paragraph now says the app never downloads
  code of its own, and that web pages a learner writes and previews load whatever they link to. Explains the only case
  iOS may ask about the camera or microphone (a learner-built page that uses them).
- Support page: the FAQ wrongly said progress couldn't be reset in the app; it points to Settings > Progress > Reset
  progress now. Minimum iOS is 15. Online extras packages are "several MB". Mentions Settings > About.
- Plain punctuation (no long dashes) on both CodeQuest pages and its landing-page card.

### 1.3.6 — CodeQuest legal pages
- Added **CodeQuest** privacy policy, support site, and app icon
- Landing page lists CodeQuest under iOS Apps
- Short redirects added: `/codequest/privacy` and `/codequest/support`
- Not yet submitted to App Store Connect at time of writing — see the "URLs already submitted to Apple" warning above before ever renaming its folder or redirects once it is

### 1.3.5 — Fixed broken Birthdays Reminder Pro links
- `/birthdays-reminder-pro` and `/birthdays-reminder-pro/support` — the exact URLs on file in Birthdays Reminder Pro's App Store Connect record — had **no redirect at all** in `firebase.json` and were 404ing live, risking Apple hiding the app for a broken Privacy Policy URL
- Found by reading the real submitted URLs directly off the public App Store listing (`curl` against `apps.apple.com`, see the warning section above) rather than assuming the newer `/app-name/privacy` convention applied
- Added the missing redirects; added the "URLs already submitted to Apple" section to this README so this doesn't get "cleaned up" back into a 404

### 1.3.4 — Chat Blues short redirects
- Added `/chat-blues/privacy` and `/chat-blues/support`, bringing Chat Blues in line with Control Pro and Daily Diary Notes
- Chat Blues was the only app whose App Store URLs were raw `%20`-encoded folder paths, which break silently if the folder is ever renamed

### 1.3.3 — Chat Blues privacy corrections
- Disclosed that Live Preview's agent mode sends the **current file** to the AI provider you chose with every edit request — §2.4 described where code *runs* but not what leaves the device to get it *changed*
- Logging two earlier Chat Blues corrections that shipped without changelog entries: the privacy policy was matched to the app (`4e0526f`), and the support page's account-deletion, iOS-version and device claims were corrected (`084d7a9`)

### 1.3.2 — Consistent app directory cards
- Kept every app card at the same full page-wide baseline height instead of shrinking cards with shorter descriptions
- Aligned each privacy-policy action consistently along the bottom of its card

### 1.3.1 — Daily Diary Notes launch refresh
- Replaced the website artwork with the exact 1024px icon shipped by the app
- Updated the landing-page description for the current iPhone and iPad feature set
- Expanded support for automatic page creation, autosave, iPad spreads, and alternate app icons
- Clarified the unused microphone declaration in the privacy policy

### 1.3.0 — Daily Diary Notes legal pages
- Added **Daily Diary Notes** privacy policy, support site, and app icon  
- Landing page lists Daily Diary Notes under iOS Apps  
- Short redirects added: `/daily-diary-notes/privacy` and `/daily-diary-notes/support`  
- README App Store Connect URL table updated, and the existing short URLs documented  

### 1.2.0 — Control Pro legal pages
- Added **Control Pro – Desktop Remote** privacy policy, support site, and app icon  
- Landing page lists Control Pro under iOS Apps and **Control Pro Host** under macOS Apps  
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
