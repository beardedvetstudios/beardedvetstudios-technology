# technology.beardedvetstudios.com

Static site for the Bearded Vet Studios "Technology" hub — a landing page
for software tools (starting with QuickInvoice), plus a hosted privacy
policy page. No build step, no framework, no external dependencies.

```
index.html          Hub page — philosophy section + Tools section
privacy/index.html  QuickInvoice privacy policy (also serves as the hosted
                     URL the Chrome Web Store listing requires)
assets/style.css     Shared stylesheet for both pages
assets/quickinvoice-icon.png   QuickInvoice's toolbar icon, reused here
CNAME                GitHub Pages custom-domain file
```

## Deploying with GitHub Pages

1. Put these files at the root of the repo you want to serve this from
   (same pattern as your `assets.beardedvetstudios.com` setup) — either a
   dedicated repo for this subdomain, or a repo with GitHub Pages enabled
   and this content at its root.
2. In that repo's **Settings → Pages**, set the custom domain to
   `technology.beardedvetstudios.com`. GitHub will write/confirm the
   `CNAME` file automatically (the one included here already has the right
   contents, in case you're copying files in manually via git instead).
3. At your DNS provider, add a `CNAME` record:
   - Host: `technology`
   - Value: `<your-github-username>.github.io`
   (Same shape as whatever record you already created for `assets.`.)
4. Enable "Enforce HTTPS" in the Pages settings once the certificate
   provisions (can take a few minutes to a few hours after the DNS record
   goes live).

## Before this goes live

- **Swap the "View on Chrome Web Store" button.** It's currently a
  disabled placeholder (`href="#"`) with a "Launching soon" note next to
  it, since QuickInvoice hasn't been published yet. Once it's live, edit
  `index.html`: remove the `disabled`/`aria-disabled` bits from that `<a>`,
  point `href` at the real Web Store listing URL, and delete (or repurpose)
  the "Launching soon" text next to it.
- **Use this page's `/privacy/` URL for the Chrome Web Store submission.**
  Once this is deployed, `https://technology.beardedvetstudios.com/privacy/`
  is a real hosted URL you can paste directly into the Web Store listing's
  privacy policy field — no separate hosting needed.
- If QuickInvoice's `PRIVACY_POLICY.md` is ever updated in the extension
  repo, mirror the same changes into `privacy/index.html` here so the two
  don't drift apart.
