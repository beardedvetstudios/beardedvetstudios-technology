# technology.beardedvetstudios.com

Static site for the Bearded Vet Studios "Technology" hub — a landing page
for software tools (starting with InvoicePO), plus a shared privacy
policy page covering all of them. No build step, no framework, no external
dependencies. Live at https://technology.beardedvetstudios.com/.

```
index.html          Hub page — philosophy section + Tools section
privacy/index.html  Shared "Technology Privacy Policy" — one page covering
                     every product listed here, each in its own clearly
                     labeled section (see below). Also serves as the hosted
                     URL the Chrome Web Store listing requires.
assets/style.css     Shared stylesheet for both pages
assets/invoicepo-icon.png   InvoicePO's toolbar icon, reused here
CNAME                GitHub Pages custom-domain file
```

## Redeploying after an edit

Same flow as your other GitHub Pages repos: push changes to the branch
GitHub Pages serves from (usually `main`), and it redeploys automatically —
usually live within a minute or two. No separate build/CNAME step needed
once the custom domain and DNS are already set up, which they are.

## The privacy policy is one shared page, not one per product

`privacy/index.html` is intentionally a single "Technology Privacy Policy"
rather than a dedicated page per product. Chrome Web Store policy doesn't
require a dedicated policy per extension — it requires the policy to
accurately reflect what each specific product actually does, and to stay
consistent with that product's "Privacy practices" disclosures in the
developer dashboard. So the page is structured as:

1. A shared "Our approach to data" section (applies to everything listed here).
2. One `<section class="product-policy">` block per product — currently
   just InvoicePO — containing that product's specific, accurate
   disclosures (permissions used, what's stored where, third-party
   services involved, etc).
3. Shared closing sections (Changes to this policy, Contact).

**Adding a second product later:** copy the InvoicePO `<section
class="product-policy">` block in `privacy/index.html`, relabel it, and
fill in that product's actual data practices — don't just reuse
InvoicePO's wording, since the whole point of the per-product section is
that it has to be accurate for that specific product. Also add a matching
`.tool-card` to `index.html`'s Tools section.

## Before InvoicePO's Chrome Web Store submission

- **Swap the "View on Chrome Web Store" button.** It's currently a
  disabled placeholder (`href="#"`) with a "Launching soon" note next to
  it, since InvoicePO hasn't been published yet. Once it's live, edit
  `index.html`: remove the `disabled`/`aria-disabled` bits from that `<a>`,
  point `href` at the real Web Store listing URL, and delete (or repurpose)
  the "Launching soon" text next to it.
- **Use `https://technology.beardedvetstudios.com/privacy/`** as the
  privacy policy URL in the Web Store listing.
- If InvoicePO's data practices ever change (new permission, new
  storage behavior, etc.), update its section in `privacy/index.html`
  *and* make sure the Web Store dashboard's "Privacy practices" tab for
  that listing still matches — Google explicitly treats a mismatch between
  the two as a policy violation.
