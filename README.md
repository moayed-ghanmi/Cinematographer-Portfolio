# Slim Allouche — Portfolio

Two static pages, no build step, no backend required.

## Files
- `index.html` — the public portfolio (hero, selected works, about, contact)
- `admin.html` — password-gated page to add/edit/reorder projects (passcode: `reel2026` — change it before deploying, search for `PASSCODE` near the top of the file)

## How the two pages connect
- `admin.html` writes project data to `localStorage` under the key `slim_projects`.
- `index.html` reads that same key on load, and falls back to its built-in `DEFAULT_PROJECTS` array if nothing's saved yet.
- Because `localStorage` is shared per browser + per domain, edits made in `admin.html` show up on `index.html` immediately — as long as you're viewing both on the same device, on the same deployed domain.
- The "View site" link in the admin header, and the relative paths below, assume both files sit in the same folder at the root of your domain (e.g. `yoursite.com/` and `yoursite.com/admin.html`).

## To make an edit visible to every visitor (not just your own browser)
1. Go to `admin.html`, add/edit/reorder your projects.
2. Click **Export code** — it copies an updated `DEFAULT_PROJECTS` array.
3. Open `index.html`, find the `const DEFAULT_PROJECTS = [...]` block near the bottom, and replace it with the copied version.
4. Redeploy (push to GitHub if using GitHub Pages/Vercel/Netlify, or re-upload the file).

## Deploying
Any static host works — no server, no database:
- **Netlify / Vercel**: drag-and-drop this folder into their dashboard, or connect a GitHub repo.
- **GitHub Pages**: push these files to a repo, enable Pages on the `main` branch.

## Before going live
- Change the admin passcode (`PASSCODE` constant in `admin.html`) — the current one is a placeholder and not real security.
- Wire up the contact form: create a free form at formspree.io pointed at slimallouche12@gmail.com, then replace `YOUR_FORM_ID` in the `fetch(...)` call inside `index.html`'s contact section.
- Swap the hero's CSS gradient background for a real looping showreel video if you have one.
