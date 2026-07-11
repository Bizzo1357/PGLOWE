# PGLOWE — delivery ticket PWA

Offline field app for documenting refrigeration unit deliveries: job stages, unit
serial numbers, damage photos, and a one-tap PDF export.

This version is **self-contained**: the entire app (styles, code, and PDF engine)
lives inside `index.html`. There are no separate CSS/JS files that can go missing.

## Files to upload (keep them all together at the repo root)

```
index.html          <- the whole app
manifest.json       <- makes it installable
service-worker.js   <- makes it work offline
icons/icon-192.png
icons/icon-512.png
icons/icon-512-maskable.png
```

IMPORTANT: put these at the TOP LEVEL of the repo, not inside a subfolder. The
`icons` folder stays as a folder. If `index.html` ends up inside a subfolder, the
GitHub Pages URL changes and the icons/manifest won't be found.

## Deploy on GitHub Pages

1. Create a repo and upload the files above (drag them into the repo's file list;
   for the icons, create the `icons` folder or upload the folder itself).
2. Settings -> Pages -> Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
3. Wait a minute, then open the URL GitHub gives you
   (`https://username.github.io/repo-name/`).

## Install on your phone

Open the URL once while online, then:
- Android (Chrome): menu (three dots) -> Add to Home screen / Install app.
- iPhone (Safari): Share -> Add to Home Screen.

Open it once from the home-screen icon while still online so it finishes caching.
After that it runs fully offline.

## Notes

- Data (jobs + photos) is stored on the phone via IndexedDB. Nothing uploads anywhere;
  jobs don't sync between devices. Export PDFs for anything you need to keep.
- PDF export goes through the phone's share sheet (Save to Files, email, Drive...),
  with a plain download as fallback.
- After you re-deploy an update, bump `pglowe-v4` in `service-worker.js` to `v5` so
  installed phones pick it up. To refresh the icon, remove the app from the home
  screen and re-add it.
