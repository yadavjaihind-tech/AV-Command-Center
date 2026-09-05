# AV Project Command Center — Standalone Copy

A self-contained, single-file build of the AV Project Command Center. No server,
no database, no build step — `index.html` is the entire app, pre-loaded with a
sample project ("Corporate Museum AV Integration") so it's usable the moment
it opens.

## Important: how data storage works here

This copy saves everything to **local storage in the visitor's own browser**.
That means:

- Each person who opens the page (or the same person on a different device)
  gets their own independent copy of the data — nothing syncs between them.
- Clearing browser data / site data for this page wipes what's stored.
- There is no login and no shared "real" database behind this version.

It's the right fit for a demo, a personal single-device tool, or something you
hand a client to click through. It is **not** a shared, multi-person tool —
for that, use the live Claude-hosted version instead, or see "Going further"
below.

## Publish it on GitHub Pages (no coding required)

**Option A — through the GitHub website, no git needed**

1. Go to [github.com/new](https://github.com/new) and create a new repository
   (any name, e.g. `av-command-center`). Public repos get free Pages hosting;
   private repos need a paid GitHub plan for Pages.
2. On the new repo's page, click **"uploading an existing file"** (or
   **Add file → Upload files**).
3. Drag in both `index.html` and this `README.md`, then commit.
4. Go to **Settings → Pages** in that repository.
5. Under **Build and deployment → Source**, choose **Deploy from a branch**,
   pick branch `main` and folder `/ (root)`, then **Save**.
6. Wait about a minute, then refresh — GitHub shows the live URL, something
   like:

   `https://<your-username>.github.io/av-command-center/`

That URL is now yours to share — no `claude.ai` anywhere in it.

**Option B — using git from the command line**

```bash
git init
git add index.html README.md
git commit -m "Add AV Project Command Center"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

Then enable Pages the same way as steps 4–6 above.

## Using your own domain instead of github.io

In the same **Settings → Pages** screen, there's a **Custom domain** field.
Add a `CNAME` DNS record at your domain registrar pointing at
`<your-username>.github.io`, then enter your domain there (e.g.
`avcc.yourcompany.com`). GitHub issues a free HTTPS certificate for it
automatically.

## Going further

If you outgrow the local-storage version and want the same shared,
multi-device experience as the live Claude-hosted app but on your own domain,
that requires an actual backend (a real database, not browser storage) — see
the "Technology Recommendations" and "Complexity Estimate" sheets in the
architecture document for what that involves.
