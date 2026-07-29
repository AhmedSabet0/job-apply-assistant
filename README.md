# Job Application Assistant — Android PWA

An installable Android app (PWA) that shows up in the **Share sheet** of any
other app. Share a job post from LinkedIn, Wuzzuf, Chrome, WhatsApp, etc.,
and it opens this app with the job post already filled in.

## Why it needs hosting (can't just open the HTML file)

Android's Share Target feature only works for PWAs installed from a real
`https://` origin — not from a local file. You need to upload these 5 files
to a free static host once, then install it from your phone.

## Deploy with GitHub Pages (free, ~5 minutes)

1. Create a new **public** repo on GitHub, e.g. `job-apply-assistant`.
2. Upload all files in this folder (`index.html`, `manifest.json`, `sw.js`,
   `icons/icon-192.png`, `icons/icon-512.png`) keeping the same structure
   (the `icons/` folder must stay a subfolder).
3. Go to **Settings → Pages** in the repo, set Source to the `main` branch,
   root folder, and save.
4. After a minute, your app is live at:
   `https://<your-github-username>.github.io/job-apply-assistant/`

## Alternative: Netlify Drop (no Git needed)

1. Go to https://app.netlify.com/drop
2. Drag the whole `job_pwa` folder onto the page.
3. You get an `https://...netlify.app` URL instantly.
4. (Optional) Create a free Netlify account to keep the site permanently
   instead of it expiring.

## Install it on your phone

1. Open the deployed URL on your Android phone in **Chrome**.
2. Tap the **⋮** menu → **Install app** (or you'll see an automatic
   "Add to Home screen" banner).
3. It now behaves like a normal app icon.

## Use it

1. First time: open the app, upload your CV once (it's saved on-device).
2. From any other app, select a job post's text → **Share** → pick
   **Job Application Assistant** from the share sheet.
3. The app opens with the job post pre-filled. Enter your OpenRouter key
   once (also saved), tap **Generate Cover Letter**.
4. Fill in the recruiter's email, tap **Open Gmail Draft** — Gmail opens
   pre-filled and your CV auto-downloads so you can drag it into the
   compose window and hit Send.

## Limitations (be aware)

- **Sharing a link only** (no selected text) won't pull the job description
  automatically — the app can't fetch other sites' content from the browser
  due to CORS. You'll need to open the link and paste the text manually in
  that case.
- This only works on **Android**. iOS Safari does not support the Web Share
  Target API for PWAs — a true iPhone share-sheet integration would require
  a native app with a Share Extension (Xcode + Apple Developer account),
  which is a different, much bigger project.
- Still no fully automatic email sending with attachment — that remains a
  browser security limitation. Gmail draft + auto-downloaded CV is the
  closest practical automation.
