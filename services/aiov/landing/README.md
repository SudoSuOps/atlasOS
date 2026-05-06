# AIOV Landing Page

The customer-facing landing page for the **AIOV (AI Opinion of Value)** product.

```
Source           services/aiov/landing/index.html
Live at          https://aiov.swarmandbee.ai      (Cloudflare Pages · DNS)
                 https://aiov.eth.link             (ENS gateway · IPFS-resolved)
                 ipfs://<CID>                      (sovereign content layer · always reachable)
```

Single static `index.html`. No external CDN dependencies. No build step. No
JavaScript runtime. The page is **IPFS-pure** by design — flash it to a USB stick
and it works.

---

## Why single file, no dependencies

Three reasons.

1. **Sovereign content layer.** If Cloudflare disappears, if the DNS provider
   disappears, if our datacenter disappears — the page is still pinned on IPFS
   and resolvable via `aiov.eth.link` through ENS contenthash. Nobody can take
   down the AIOV explainer.

2. **Institutional surface.** Family offices and brokerage CTOs read pages from
   secured environments where third-party CDNs and JS-heavy SPAs are blocked.
   A single static HTML file with embedded CSS works behind every corporate
   firewall.

3. **Brand discipline.** The page itself is part of the trust story. Every
   external dependency is a place the page could leak data. Zero externals
   means zero leaks. The page tells the privacy story; the page itself
   demonstrates it.

---

## Deploy paths

### A · Cloudflare Pages (primary)

```
1. Connect this repo to Cloudflare Pages
2. Build command:  (none)
3. Output dir:     services/aiov/landing
4. Custom domain:  aiov.swarmandbee.ai
5. Auto-deploys on every push to main
```

### B · IPFS pin (sovereign content layer)

```bash
# Pick a pinning service: Pinata, Filebase, Storacha, or self-hosted IPFS node.
# Pinata example:

ipfs add -r services/aiov/landing/
# returns CID e.g. bafybeih...

# Pin via service for permanence:
curl -X POST https://api.pinata.cloud/pinning/pinFileToIPFS \
  -H "Authorization: Bearer $PINATA_JWT" \
  -F "file=@services/aiov/landing/index.html"

# Then set ENS contenthash on aiov.eth to ipfs://<CID>
# (via app.ens.domains · Records tab · Content)
```

After the contenthash is set, `aiov.eth.link` and `aiov.eth.limo` both resolve
to the IPFS-pinned page automatically. Browsers with Brave or with an ENS
extension resolve `aiov.eth` directly without `.link`/`.limo`.

### C · Both at the same time

That's the recommended state.

- `aiov.swarmandbee.ai` resolves through Cloudflare for fastest load
- `aiov.eth` resolves through IPFS for sovereign permanence
- Both serve byte-identical content — same `index.html` from this directory

---

## Page anatomy

```
hero            "AIOV · The AI Opinion of Value"
                30 min · $499 · 0 market exposure
                two CTAs

asymmetry       Why a BOV costs you (the listing pressure trap)
how             5-step flow: drop docs · local parse · encrypted brief ·
                ephemeral container · receipt anchored
privacy         "We can't see your deal even if we wanted to" — 5 structural
                claims, each independently verifiable
compare         AIOV vs BOV vs Appraisal table — the kill columns highlighted
receipt         Real Hedera-anchored session record example, formatted as JSON
pricing         $499 / AIOV  ·  $4,999 / yr (12 AIOVs)
the box         Connection to HACKER-PRO + ENS sovereignty
order           Two paths: existing HACKER-PRO owner, or new
founder block   30 years · $8B · "I sat in the pit"
footer          V/V/V trust standard · Caballerz Network LLC · DUNS · GitHub
```

---

## Editing the page

Anyone with a text editor can edit `index.html`. There is no framework, no
component system, no preprocessor. Headlines are inline `<h1>`/`<h2>`. Styles
are in a single `<style>` block at the top.

**Discipline when editing:**
- No emoji. Period.
- Don't introduce external font CDNs (Google Fonts, etc) — the system-font
  stack is part of the IPFS-pure design.
- Don't introduce JavaScript unless absolutely necessary — and if it is, keep
  it inline and minimal.
- Don't add tracking pixels, analytics, or third-party iframes.
- Don't change the privacy claims without updating `INFRA.md` to match.
- The footer disclaimer about AIOV vs licensed appraisals must stay. Legal.

---

## Pricing source of truth

Pricing is duplicated across:
- `index.html` (this directory)
- `PRODUCTS.md` (repo root)
- `aiov.schema.json` (when shipped)
- `aiov_product_family_office.md` (memory · internal)

When pricing changes, update all four in the same commit.

---

## Disclaimer that must stay

The footer carries the explicit disclaimer that AIOV is **not** a state-licensed
appraisal. This is not optional — federal real estate transactions (federally
related transactions over $400K · per FIRREA) require a state-licensed
appraiser, and AIOV is not that.

AIOV is for **owner-side analytical use** before listing, before engaging a
broker, or for portfolio-level value tracking. The disclaimer keeps us out of
state-licensure trouble and keeps the customer's expectations honest.
