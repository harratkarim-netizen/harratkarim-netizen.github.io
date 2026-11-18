# My Kitchen — developer site (GitHub Pages)

Three files. This whole folder is what goes into the GitHub repository.

| File | Serves as | Needed by |
| --- | --- | --- |
| `app-ads.txt` | `https://harratkarim-netizen.github.io/app-ads.txt` | AdMob |
| `privacy/index.html` | `https://harratkarim-netizen.github.io/privacy/` | Play Console, Galaxy Store, AdMob |
| `index.html` | `https://harratkarim-netizen.github.io/` | the developer-website field |

## Why the repo name matters

`app-ads.txt` must be at the **root of the domain**. On GitHub Pages only a *user site* repo —
named exactly `harratkarim-netizen.github.io` — is served at a domain root. A project repo
(`harratkarim-netizen.github.io/mykitchen/app-ads.txt`) adds a path segment and **Google will not find it**;
the crawl reports "no app-ads.txt found" and serving stays limited.

## Publish

1. Sign in to GitHub and create a **public** repository named `harratkarim-netizen.github.io`
   (do not add a README, so nothing collides).
2. Upload these three entries keeping their paths: `app-ads.txt`, `index.html`, and the
   `privacy/` folder with `index.html` inside it.
3. Repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`, Save.
4. Wait 1–2 minutes, then check both URLs return 200:
   ```
   curl -I https://harratkarim-netizen.github.io/app-ads.txt
   curl -I https://harratkarim-netizen.github.io/privacy/
   ```
   `app-ads.txt` must come back `content-type: text/plain` and must **not** redirect.

## Values are filled

| Field | Value |
| --- | --- |
| Publisher | `techcomputerhelper` |
| Contact | `techcomputerhelper@gmail.com` — also a `mailto:` link in all three languages |
| Domain | `harratkarim-netizen.github.io` |

No `{{...}}` placeholders and no pre-publication warning paragraph remain in
`privacy/index.html`; the effective date is 2026-11-17. If the Play Console legal name differs from
`techcomputerhelper`, change line 36 of the policy so the two records agree.

## Wire it into the consoles

- **Play Console** → Store presence → Branding → *Website*: `https://harratkarim-netizen.github.io`.
  AdMob has no app-website field of its own — it reads the developer domain back from this Play record.
- **Play Console** → Policy → Privacy policy: `https://harratkarim-netizen.github.io/privacy/`.
- **AdMob** → once the listing exists, *Ajouter un magasin* with the Play Store URL; that is what lifts
  *Diffusion d'annonces limitée*.

## After publishing

Google re-crawls app-ads.txt roughly every 24 hours (occasionally up to 7 days). The file alone does
**not** lift the current *Diffusion d'annonces limitée* state — that clears when the app is linked to a
store listing. Order that works: host this site → publish `app-ads.txt` → publish on Play → link the
store in AdMob → request approval.

## Optional: a custom domain

If you later buy a domain, add it to the same Pages repo (Settings → Pages → Custom domain) and put a
`CNAME` file containing the domain here. The URLs change, so update the policy text and both consoles
in the same change.
