# Atlas OS · docs site

The customer-facing documentation site for AtlasOS.

```
Source           docs/site/
Live at          https://docs.swarmandbee.ai      (Cloudflare Pages · DNS)
                 https://docs.atlasos.eth.link    (ENS gateway · IPFS-resolved · planned)
                 ipfs://<CID>                     (sovereign content · planned)
```

Multi-page static site. Same IPFS-pure principles as the AIOV landing — no
external CDN, no JS framework, no build step. Each page is a self-contained
HTML file that references one shared `_shared.css` for visual consistency.

---

## Pages shipped (initial commit)

| Page | URL path | Audience |
|---|---|---|
| Overview | `/` (`index.html`) | Anyone landing for the first time |
| Getting started | `/getting-started.html` | New HACKER owners (post-purchase) |
| AIOV in depth | `/aiov.html` | HACKER-PRO owners · integration developers · counsel |
| Personas &amp; ENS | `/personas.html` | Anyone wanting to understand the sovereignty model |

## Pages planned (subsequent commits)

```
/products.html              HACKER · HACKER-PRO · HACKER-AGX deep dive
/rainmaker.html             Rainmaker matchmaking service guide
/x402.html                  Agent-to-agent integration spec (developer)
/schemas.html               LOI · NDA · OM · AIOV schema reference
/defendable.html            Receipt audit walkthrough · 30-second verification
/legal.html                 FIRREA · brokerage licensure · disclosures
/changelog.html             Release notes · cook updates · model versions
```

---

## Deploy

### Cloudflare Pages (primary)

Same flow as the AIOV landing — connect this repo, point at `docs/site/`,
add `docs.swarmandbee.ai` as the custom domain.

```
Cloudflare dashboard → Pages → Create project → Connect to Git
  Repository:    SudoSuOps/atlasOS
  Branch:        main
  Build command: (none · static)
  Output dir:    docs/site
  Custom domain: docs.swarmandbee.ai
  → Deploy
```

After setup, every push to `main` auto-deploys within ~30 seconds.

### IPFS pin (sovereign content layer · planned)

```bash
# After the page count stabilizes, pin the directory:
ipfs add -r docs/site/

# Then set ENS contenthash on docs.atlasos.eth (subdomain of atlasos.eth)
# to ipfs://<CID>.
# Once set, docs.atlasos.eth.link resolves through IPFS gateways.
```

The site is engineered to work over `ipfs://` directly — relative paths only
(`./getting-started.html`), no absolute URLs to itself, no external CDN
dependencies.

---

## Editing discipline

The same rules as the AIOV landing apply:

- **No emoji.** Period.
- **No external font CDNs.** System font stack only.
- **No JavaScript framework.** Inline JS only if absolutely necessary.
- **No tracking pixels.** No analytics. No third-party iframes.
- **No surface mention of "Caballerz Network LLC."** The entity is Swarm and Bee LLC.
- **No surface mention of "Marcus &amp; Millichap" / "M&amp;M."** Use "national platform" if the founder's prior firm context comes up.
- **Every page references `_shared.css` only.** Don't introduce per-page CSS files unless absolutely necessary.

---

## Style guide

The visual language matches the AIOV landing:

```
Palette
  Background      #0c1320  (midnight navy)
  Background-2    #111a2c  (sidebar / card backgrounds)
  Rules           #1c2a44  (subtle dividers)
  Ink             #f4ede0  (primary text · warm cream)
  Ink-2           #d6cfc1  (body text)
  Ink-mute        #8b8472  (captions · meta)
  Accent          #d4a850  (brass · headlines · links)
  Accent-3        #f0c878  (hover state)
  Teal            #6ab1ad  (note callouts)
  Warn            #d97757  (warning callouts)

Typography
  Headlines       Iowan Old Style → Palatino → Georgia → serif
  Body            -apple-system → BlinkMacSystemFont → system-ui → sans-serif
  Code            ui-monospace → SFMono-Regular → Menlo → Consolas → monospace

Layout
  Max content     760px (single column)
  Max nav         980px (slightly wider for navigation)
  Generous whitespace · institutional rhythm
  Section breaks via 1px horizontal rules at 56px vertical margin
```

---

## Cross-references

The docs link out to:
- The repo at `https://github.com/SudoSuOps/atlasOS` (deeper technical detail)
- The AIOV landing at `https://aiov.swarmandbee.ai` (marketing surface)
- The HACKER-PRO landing at `https://hackerpro.eth.link` (product order flow)
- The ENS surfaces at `atlasos.eth` and `defendable.eth` (network · receipts)

The repo links back to the docs at the README "Reach" section.
