# TrueRecord — Grievance Reporting Portal

> A self-contained, privacy-first workplace grievance reporting tool. No server required. No framework setup. Just open `index.html`.

![Status](https://img.shields.io/badge/status-active-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![No dependencies](https://img.shields.io/badge/dependencies-none-lightgrey)

---

## What is this?

TrueRecord is a browser-based grievance reporting portal designed for HR teams and organizations that want a lightweight, deployable tool for collecting, tracking, and triaging workplace concerns — with strong privacy defaults built in.

It runs entirely in the browser. All data is stored locally via `localStorage`. There is no backend, no database, and no data leaves the user's device unless you wire it up yourself.

---

## Features

### For Employees
- **Submit reports** with incident type, department, priority, date, location, tags, and attachments
- **Anonymous submissions** — identity fields are disabled and never stored
- **Confidentiality toggle** — restrict visibility to authorized HR reviewers only
- **Blockchain-backed cryptographic commitment** — each submission generates a unique hash and nonce, creating tamper-evident proof of what was reported and when
- **Track your reports** — the My Reports tab shows live status for any report you submitted in this browser

### For HR / Admins
- **Inbox view** with search, status filter, and priority filter
- **Inline status updates** (New → Under Review → In Progress → Resolved → Closed)
- **Audit chain** — every status change is logged with a hash, actor, and timestamp
- **Export to CSV** — one-click export of filtered results
- **Analytics dashboard** — breakdown by status, priority, and incident type

### Privacy Architecture
Each report generates a cryptographic commitment using a one-way hash function and a random nonce. This creates a verifiable, tamper-evident fingerprint of the report at the moment of submission — consistent with blockchain-based audit trail principles. The hash is shown to the reporter at submission and stored alongside the record.

> Note: In this demo, all data is stored in browser `localStorage`. For production use, replace the `apiCreate` / `apiUpdate` / `apiDelete` functions with calls to your backend or case management system.

---

## Getting Started

### Option 1 — Just open it
Download `index.html` and open it in any modern browser — the reporting form loads immediately. No installation, no build step.

### Option 2 — Host on GitHub Pages
1. Fork this repository
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your landing page will be live at `https://samirsaad786.github.io/truerecord/app.html`
5. The reporting form will be at `https://samirsaad786.github.io/truerecord/app.html`

---

## Customization

All configuration is at the top of the `<script>` block inside `index.html`:

```js
const INCIDENT_TYPES = ["Harassment", "Discrimination", "Safety / Hazard", ...];
const DEPTS = ["Operations", "Sales", "HR", "Engineering", ...];
const PRIORITIES = ["Low", "Medium", "High", "Critical"];
```

To connect to a real backend, replace the mock API functions:

```js
async function apiCreate(payload) { /* POST to your endpoint */ }
async function apiUpdate(id, patch) { /* PATCH to your endpoint */ }
async function apiDelete(id) { /* DELETE to your endpoint */ }
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 (CDN) |
| Transpiler | Babel Standalone (CDN) |
| Styling | Vanilla CSS-in-JS |
| Storage | Browser `localStorage` |
| Cryptography | Custom hash function (djb2 variant) |
| Fonts | DM Sans + JetBrains Mono (Google Fonts) |

No npm. No build tools. No config files. Single `.html` file.

---

## File Structure

```
truerecord/
└── index.html      ← Everything. The whole app.
└── README.md       ← This file.
```

---

## Roadmap / Contribution Ideas

- [ ] Backend adapter (Supabase, Firebase, custom REST)
- [ ] Email notification on submission
- [ ] Role-based access for the Admin tab
- [ ] Multi-language / i18n support
- [ ] PDF export of individual reports
- [ ] Integration with HRIS / ticketing systems (Jira, ServiceNow)

Pull requests welcome.

---

## License

MIT — free to use, modify, and deploy. Attribution appreciated but not required.

---

## Author

Built by [@SamirSaad786](https://github.com/SamirSaad786)
