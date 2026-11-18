# Verse by Verse

A Bible memorisation app you can add to your iPhone Home Screen.
Read → Fill gaps → First letters → Write out, one verse at a time.

Verses come from your Google Sheet **"Verse by Verse – NIV verses"**, served by a small Apps Script, so nobody else needs the PDF.

## Files

| File | What it is |
|---|---|
| `index.html` | The app |
| `config.js` | Holds your Apps Script link — the only file you edit |
| `manifest.webmanifest`, `sw.js`, `icons/` | Make it installable and work offline |
| `apps-script/Code.gs` | The script to paste into your Google Sheet (not used by the website) |

## One-time setup

### 1. Connect the Sheet (about 5 minutes)
1. Open the Sheet **Verse by Verse – NIV verses** in Google Drive.
2. **Extensions → Apps Script**. Delete what's there and paste in everything from `apps-script/Code.gs`. Save.
3. **Project Settings** (gear icon) → **Script properties** → **Add script property**:
   name `OWNER_KEY`, value = a secret word only you know. Save.
4. **Deploy → New deployment** → type **Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
   Click **Deploy**, allow the permissions, and copy the **Web app URL** (ends in `/exec`).
5. Paste that link into `config.js` between the quotes.

### 2. Put it online with GitHub Pages
1. On github.com (signed in as JosephO116), create a new **public** repository, e.g. `verse-by-verse`.
2. Upload all the files and folders here (keep `icons/` as a folder).
3. Repository **Settings → Pages** → Source: **Deploy from a branch**, branch **main**, folder **/ (root)** → Save.
4. After a minute your app is live at `https://josepho116.github.io/verse-by-verse/`.

### 3. Add your verses (owner only)
1. Open the app, scroll to the bottom and tap **Owner tools**.
2. Enter your `OWNER_KEY` and tap **Save key**.
3. **Choose NIV PDF** (your own copy), then upload **This chapter**, **This book** or **Whole Bible**.
Everyone with the link now gets those verses. You can also fix a verse straight in the Sheet.

### 4. Install on iPhone
Open the link in **Safari** → **Share** → **Add to Home Screen**.

## Updating
- Changed `Code.gs`? **Deploy → Manage deployments → edit → Version: New version → Deploy** (the link stays the same).
- Changed the app files? Upload them to the repo again; phones pick up the new version next time they open it online.
