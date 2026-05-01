# TalentFish Interview Scheduler — Outlook Add-in
## Setup & Deployment Guide

---

## What This Does

Adds a **"Schedule Interview"** button to your Outlook ribbon. When you open any JobDiva interview notification email, click the button and it will:

1. Automatically parse the email (candidate name, role, client, date/time, pay rate, recruiter)
2. Show you an editable form pre-filled with all the details
3. Open a ready-to-send Outlook calendar invite with one click

---

## Files in This Package

```
talentfish-addin/
├── manifest.xml          ← Registers the add-in with Outlook
├── taskpane.html         ← The UI panel that appears in Outlook
├── function-file.html    ← Required helper file
├── assets/               ← Put your icon files here (see below)
└── README.md             ← This file
```

---

## Step 1 — Host the Files (Required)

Outlook add-ins must be served over HTTPS. The easiest free options:

### Option A: GitHub Pages (Recommended — Free)
1. Create a free GitHub account at github.com if you don't have one
2. Create a new repository called `talentfish-addin` (set to Public)
3. Upload all files from this folder into the repo
4. Go to repo Settings → Pages → Source: Deploy from branch `main`
5. Your URL will be: `https://YOUR-GITHUB-USERNAME.github.io/talentfish-addin`

### Option B: Netlify (Also Free)
1. Go to netlify.com and sign up free
2. Drag and drop this entire folder onto the Netlify dashboard
3. It gives you a URL like `https://random-name.netlify.app`

---

## Step 2 — Update the URLs in manifest.xml

Once you have your hosted URL, open `manifest.xml` and replace every instance of:
```
https://YOUR-HOSTED-URL
```
With your actual URL, e.g.:
```
https://jcorletta.github.io/talentfish-addin
```

There are **6 places** to update in manifest.xml. Use Find & Replace.

---

## Step 3 — Create Icon Files

You need 4 icon sizes. Create simple PNG images (or use any icon tool):
- `assets/icon-16.png` (16×16 px)
- `assets/icon-32.png` (32×32 px)
- `assets/icon-64.png` (64×64 px)
- `assets/icon-80.png` (80×80 px)

**Quick option:** Use the TalentFish logo resized to each size, or download a free calendar icon from flaticon.com. Save each to the `assets/` folder.

---

## Step 4 — Install the Add-in in Outlook

### In Outlook Desktop (Windows):
1. Open Outlook
2. Click **File** → **Manage Add-ins** (opens a browser window)
3. Click **My add-ins** → **Add a custom add-in** → **Add from file...**
4. Select the `manifest.xml` file
5. Click **Install**

### In Outlook Web (outlook.office.com):
1. Open any email
2. Click the **three dots (...)** → **Get Add-ins**
3. Click **My add-ins** → **Add a custom add-in** → **Add from URL**
4. Paste the URL to your hosted `manifest.xml`

---

## Step 5 — Using the Add-in

1. Open any JobDiva interview scheduled email in Outlook
2. You'll see a **"Schedule Interview"** button in the ribbon (top toolbar)
3. Click it — a panel slides open on the right
4. Click **"Parse This Email"** — it auto-fills all the fields
5. Review and edit anything as needed
6. Click **"Create Calendar Invite"** — Outlook opens the invite, pre-filled
7. Add any additional attendees, then hit **Send**

---

## Troubleshooting

**Button doesn't appear:**
- Make sure the manifest.xml URLs are all updated to your hosted URL
- Try restarting Outlook after installing

**"Parse This Email" returns empty fields:**
- The AI parsing uses the Anthropic API — the add-in falls back to regex parsing if needed
- You can always fill in fields manually

**Calendar invite doesn't open:**
- Make sure you have ReadWriteItem permission (it's set in manifest.xml already)
- Try the Outlook Web version if desktop has issues

---

## Need Help?

Contact: jcorletta@TalentFish.com
