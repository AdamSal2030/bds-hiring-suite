# BDS Corp — Hiring Suite

Two self-contained web apps for BDS Corp's hiring (built for use in Pakistan):

| File | What it is | Who uses it |
|------|------------|-------------|
| [`assessment.html`](assessment.html) | **Candidate assessment** — five timed sections: a typing speed/accuracy test, an Excel data-entry task (build the sheet and upload it), a sales email written in real Gmail, and two short written answers (background, and "why you're the best fit"). Per-section timing throughout. | Job candidates (on the office computer) |
| [`portal.html`](portal.html) | **HR portal** — analytics dashboard, applicant pipeline with interview tracking, a BDS Employees onboarding section, and an Analytics tab. | The hiring team |
| [`index.html`](index.html) | Simple landing page linking to both. | — |

**HR portal demo login:** username `admin` · password `bds2026`

---

## Features

**Candidate assessment (`assessment.html`)**
- Click-to-start typing test (WPM, accuracy, time; paste disabled)
- Excel data-entry task — candidate reads mixed dispatch notes, builds a real `.xlsx`, saves it under their name, and uploads it (attach / remove / re-attach)
- Sales email task — candidate drafts a price-justification email to a client in real Gmail, then marks it sent; subject + body are captured
- Two freeform written sections (up to 200 words each, paste allowed)
- Skip a section to review it on a first pass, plus a final review screen
- Per-section start/end times and durations in the results
- Copy or download the results as a text file; all of it (including the uploaded Excel) flows to the HR portal on the same site
- Light / dark theme toggle (header stays dark)

**HR portal (`portal.html`)**
- **Assessment results** — KPIs and charts (candidates per day, average typing speed)
- **Applicants & interviews** — add candidates from CVs, status pipeline (New → Hired), interview scheduling, notes/call log, rating, sources (Walk-in, Referral, LinkedIn, Instagram, WhatsApp, …), typing-test result, document uploads (photo / CV / CNIC), CSV export
- **BDS Employees** — hired candidates move here; onboarding fields (CNIC, father's name, DOB, address, emergency contact, bank account, employment type, joining/probation dates, PKR basic salary); CSV export
- **Analytics** — upcoming interviews (this week), hiring funnel, source effectiveness, typing pass-rate with an adjustable pass mark, speed distribution, and top performers
- Light / dark theme (the header stays dark), full-width layout, BDS Corp branding

---

## Run locally

These are plain static HTML files — no build step.

```bash
# from this folder
python3 -m http.server 8000
# then open http://localhost:8000
```

Or just double-click `index.html`.

## Deploy (static hosting)

Any static host works. Examples:

- **Vercel** — `vercel` (or import the repo at vercel.com). No config needed.
- **Netlify** — drag the folder onto app.netlify.com, or connect the repo.
- **GitHub Pages** — repo Settings → Pages → deploy from the `main` branch (root). Your site will be at `https://<user>.github.io/<repo>/`.

---

## Important note on data

Right now all HR data (applicants, employees, uploaded documents) is stored in the **browser's localStorage**, which means:

- It persists on **that one computer/browser**, but is **not shared** across devices.
- Uploaded files are capped (~1.5 MB each) and total browser storage is limited.

For real day-to-day use — candidates on any office computer, results and CNIC/bank data shared securely across devices — the next step is a **database-backed version** with real login and secure storage. That's a separate build.

The people/phone numbers shown in the apps are **sample demo data** (Pakistani names, +92 numbers, PKR salaries) so the dashboard isn't empty; real candidates replace them.
