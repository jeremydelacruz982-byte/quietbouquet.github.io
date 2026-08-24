

## 1. Put it on GitHub

If you don't have Git set up locally, install it first (git-scm.com) and
create a free GitHub account.

1. On github.com, click **New repository**, name it (e.g. `quiet-bouquet`),
   leave it empty (no README/gitignore), and click **Create repository**.
2. On your computer, open a terminal in this project folder and run:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/quiet-bouquet.git
   git push -u origin main
   ```

Your code is now on GitHub.

## 2. Run it locally (optional, to check it first)

```bash
npm install
npm run dev
```

This opens the site at `http://localhost:5173`.

## 3. Deploy it for free (Vercel, easiest option)

1. Go to vercel.com and sign in with your GitHub account.
2. Click **Add New → Project**, pick your `quiet-bouquet` repo.
3. Vercel auto-detects Vite — leave the defaults, click **Deploy**.
4. You'll get a live URL like `quiet-bouquet.vercel.app` in about a minute.

(Netlify and GitHub Pages both work too, if you prefer those.)

Every time you `git push` new changes to `main`, Vercel automatically
redeploys.

## Making it real (multi-user, secure)

To actually launch this for other people, two pieces need to move from
"demo" to "real":

1. **Storage** — replace the localStorage shim in `src/main.jsx` with a real
   shared database, e.g. [Firebase Firestore](https://firebase.google.com/docs/firestore)
   or [Supabase](https://supabase.com/docs). Both have free tiers and
   straightforward JS SDKs — the app's `sGet`/`sSet`/`sList`/`sDelete`
   helper functions in `src/App.jsx` are the only place that needs rewiring
   to call the new backend instead.
2. **Sign-in** — replace the demo name/email modal with real
   [Google Sign-In via Firebase Auth](https://firebase.google.com/docs/auth/web/google-signin).
3. **Admin passcode** — currently hardcoded in `src/App.jsx`
   (`ADMIN_PASSCODE`), visible to anyone who views the page source. Move
   moderation actions behind real server-side auth (e.g. a Firebase
   Cloud Function that checks the admin's own signed-in account) instead
   of a shared password in the client.

I can help build any of these three when you're ready — just ask.
