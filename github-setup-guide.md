# Publishing Sarah's website on GitHub Pages — step by step

This guide moves the site from Wix to **GitHub Pages**, which is free. You keep the domain
name (sarahtreulroberts.com); you just stop paying Wix for hosting. No coding or command
line needed — everything is done in a web browser by dragging and dropping files.

**Important:** Don't cancel Wix until the very end, after the new site is confirmed working
at the domain. The steps are ordered so the site is never down.

*(This guide is just for reference — you don't need to upload this file to the website.)*

---

## Phase 1 — Create a free GitHub account

1. Go to https://github.com and click **Sign up**.
2. Use an email, pick a username, and choose the **Free** plan.
3. Verify the email when GitHub asks.

The username becomes part of a temporary web address (see Phase 4), so something clean like
`sarahtreul` or `streul` is nice. It doesn't have to be perfect.

---

## Phase 2 — Create a repository (a folder GitHub stores for you)

1. Once logged in, click the **+** in the top-right corner → **New repository**.
2. **Repository name:** type the username followed by `.github.io` — for example, if the
   username is `sarahtreul`, name the repo `sarahtreul.github.io`. (This special name tells
   GitHub it's a personal website. Watch out: don't type just `.github.io` — the username
   must be in front.)
3. Set it to **Public**.
4. Check **Add a README file**.
5. Click **Create repository**.

---

## Phase 3 — Upload the website files

1. On the new repository page, click **Add file** → **Upload files**.
2. Open the `Sarah Webpage` folder on the computer.
3. Select the files **inside** it — `index.html`, the headshot image, and every `treul_*.pdf`
   (including `treul_cv.pdf`). You can skip `github-setup-guide.md` and the
   `_draft_prosecutor_aclr.pdf` file. **Drag the files themselves, not the folder.**
4. Wait for them to finish, scroll down, and click **Commit changes**.

The most important file is `index.html` (the homepage); the PDFs and photo must sit alongside
it at the top level, not in a subfolder. At the top of the upload screen GitHub shows the
path — it should just be the repo name, with no folder in front of the filenames.

---

## Phase 4 — Turn on GitHub Pages

1. In the repository, click **Settings** (top menu).
2. In the left sidebar, click **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, pick **main** and the **/ (root)** folder, then click **Save**.
5. Wait 1–2 minutes and refresh. GitHub shows a link like `https://username.github.io`.
   Click it — the site should appear. (It's not at the custom domain yet; that's next.)

---

## Phase 5 — Connect the domain (sarahtreulroberts.com)

### 5a. Tell GitHub the domain

1. Still in **Settings → Pages**, find **Custom domain**.
2. Type `sarahtreulroberts.com` and click **Save**. (GitHub adds a small CNAME file to the
   repo — that's expected; leave it alone.)

### 5b. Update the DNS records in Wix

1. Go to https://www.wix.com/account/domains and log in.
2. Find **sarahtreulroberts.com**, click the **Domain Actions** icon (the "…") next to it →
   **Manage DNS Records**.

Touch only two sections — **A (Host)** and **CNAME (Alias)**. **Leave everything else alone**,
especially any MX or TXT records (those run email).

**A (Host) records — point the bare domain to GitHub.** Make four `@` records with these
values (edit the existing Wix one to the first, then **+ Add Record** for the rest):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**CNAME (Alias) record — point www to GitHub.** Set the `www` record's value to:

```
username.github.io
```

(Replace `username` with the actual GitHub username from Phase 1.)

3. Click **Save** / **Save Changes**. Wix may warn that this disconnects the domain from the
   Wix site — that's what you want, so confirm.

DNS changes can take anywhere from a few minutes to 24 hours to take effect.

---

## Phase 6 — Turn on HTTPS (the padlock)

1. Back in **Settings → Pages**, wait for the custom-domain check to show a green checkmark.
   GitHub then issues a security certificate automatically — this can take a few minutes to a
   day after the DNS check passes.
2. Once the **Enforce HTTPS** checkbox is no longer greyed out, tick it.

If the certificate seems stuck after several hours: in **Settings → Pages**, clear the
**Custom domain** box, Save, wait a minute, re-enter `sarahtreulroberts.com`, and Save again.
That restarts the certificate process now that DNS is in place.

---

## Phase 7 — Confirm, then cancel Wix

1. Visit `https://sarahtreulroberts.com`, click around, and open a few PDFs to make sure
   everything works.
2. Only then, cancel the Wix **site/Premium plan**.
3. **Keep the domain subscription** (with auto-renew on) so you don't lose
   sarahtreulroberts.com. At Wix, the domain and the site plan are separate subscriptions —
   cancel the plan, keep the domain.

---

## Updating the site later

1. Note what to change (a new article, a fixed link, edited text).
2. In the GitHub repo, click **Add file → Upload files**, drag in the changed file(s) — usually
   just `index.html` and maybe a new PDF — and **Commit changes**.
3. The live site updates within a minute or two.
