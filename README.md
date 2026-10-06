# NLU Skylight Café website: uploaded menu version

The café site with a menu that officers post by uploading a file to the `menu/` folder. No scraping and no login system to maintain: GitHub handles who's allowed to upload.

## What's in here

| File | What it does |
|---|---|
| `index.html` | The whole website in one file, with the logo built in |
| `menu/` | Where officers upload the daily menu. Its README is the officer guide |
| `.github/workflows/publish-site.yml` | Publishes the site, plus the newest menu file, every time something is uploaded |
| `logo.png` | The original cropped logo, kept for reference |

## One-time setup

1. **Turn on publishing:** *Settings → Pages → Source:* **GitHub Actions**.
2. **Add officers:** *Settings → Collaborators → Add people*, and enter each officer's GitHub username. They accept the invite from their email.
3. **Test it:** open the `menu` folder, upload a screenshot, wait for the green checkmark under **Actions**, then open
   https://nickmaza.github.io/skylight-cafe-uploaded-menu/

## How it works

When anything is uploaded, the workflow finds the most recently uploaded menu file in `menu/` (screenshot, CSV, or text), copies it to the site as `menu/current.<ext>`, and records when it was posted in `menu/info.json`. The page reads those two files:

- **Posted today:** shows the menu and "Posted [day] at [time]."
- **Not posted today yet:** shows the most recent menu with a notice saying which day it's from.
- **Nothing posted:** says no menu is posted yet, with the café's phone number.

Only `index.html` and that one menu file are published, so nothing else uploaded to the repo goes live.

## Keeping it safe

- Only add people you trust as collaborators. They can change any file in the repo, not just the menu.
- Remove officers when they leave: *Settings → Collaborators → Remove*.
- For a student organization, consider creating a free GitHub Organization and moving this repo into it, so the site doesn't depend on one person's account. Organizations can also require two-factor authentication for everyone.
- Every upload is recorded with who posted it and when (see the repo's commit history), and any change can be undone.

## Previewing

Opening `index.html` straight from your computer (or in the Claude chat preview) will say the menu couldn't be loaded. That's expected: the menu comes from the published site. Check the live link instead.
