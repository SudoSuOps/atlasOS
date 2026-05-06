# Atlas OS

> The operating system for the brokerage desk.
>
> Thirty years on a national platform. Eight billion in transacted deals.
> I sat in the pit. Every output Defendable.
>
> **Verified · Vetted · Virtu.**

---

## What this is

Atlas OS is what runs on the **HACKER** — a $250 silver box that sits on a Hack's desk and works.
Same OS runs on the family office's box. Same OS runs on the sponsor's. Same OS runs on the Rainmaker's.

Every box is a node on a network. Every deed it ships gets a receipt. Every receipt is anchored.

This isn't a SaaS dashboard. It isn't a search engine. It isn't an MLS replacement.
It's the brokerage desk — staffed.

---

## The thesis · in one sentence

> *Stop renting a search engine. Hire the work. Plug in the box.*

The data companies — the ones with the listings feeds and the dashboards and the $500/month seats —
they're a search index your team has to log into. They charge by the seat. Their model is to extract
your listings and rent them back.

Atlas OS sells labor. Two AI roles per desk, priced like the humans they replace:

```
Hack-Deed-Maker     $60,000 / yr   the analytical hire — drills the deal
Bookmaker (Gigi)    $60,000 / yr   the marketing hire — ships the booklet
                    ─────────
Combined desk       $108,000 / yr  + a one-time $250 box per Hack
```

Same total cost as one junior analyst plus one marketing coord on payroll.
Three to four times the volume because the box doesn't sleep.

The senior broker stays on the dial floor. The box stays at the desk. The deals close.

---

## What runs on the box

| Layer | Component | Notes |
|---|---|---|
| Brain | Granite-4.1-3B (cooked) — Hack-Deed-Maker | Underwriting · cap rate · DSCR · IRR · LOI drafting |
| Eyes | Granite-Docling-258M | Reads any rent roll · T-12 · lease · OM · ESA |
| Ears | Whisper-base | Transcribes seller calls · meeting notes |
| Mouth | Piper TTS | Broker-voice synthesis · Discord channel speech |
| Memory | Honey ledger SQLite mirror | 18 months of comparable trades, on disk, queryable in milliseconds |
| Receipts | Defendable verification module | Every output anchored to Hedera · counsel-verifiable |
| Network | AtlasOS mesh | Speaks to other HACKERs at `<persona>.atlasos.eth` |

All four AI models concurrent on 8 GB. No cloud round-trip. Sovereign by design.

---

## The product line

| Product | Hardware | Brain | Customer | Seat at AtlasOS |
|---|---|---|---|---|
| **HACKER** | Jetson Orin Nano 8GB · $250 | Granite 3B cooked | Brokerage Hack desk | `harvey.atlasos.eth` |
| **HACKER-PRO** | Jetson Orin NX 16GB · $599 | Granite 8B cooked | Family office · senior desk | `familyoffice.atlasos.eth` |
| **HACKER-AGX** | AGX Orin 64GB · $2,000 | Granite 30B cooked | Brokerage HQ · sponsor branch | `<entity>.atlasos.eth` |

Same OS. Same protocol. Same network. The bigger the role, the bigger the brain.

---

## What the personas do

### Hack-Deed-Maker — `<broker>.atlasos.eth`
The analytical hire. Drills the seven dimensions of every deal:
tenant story · building specs · market summary · lease terms · financials · comps · story hooks.
Owns the work. Owns the accountability. Builds the deed.

### Bookmaker (Gigi) — `gigi.atlasos.eth`
The creative hire. Class A office. 20th floor. Skyview window seat.
Receives the deed from the Hack-Deed-Maker. Ships the 10-deliverable bundle:
OM PDF · landing page · e-blast · CoStar copy · social cards · 1-pager · packet TOC ·
map captions · comp callouts · photographer brief.

**Bookmaker never computes a number.** Numbers come from the Hack. Gigi polishes the trophy.

### Rainmaker — `rainmaker.atlasos.eth`
The matchmaker service. Family office has a 1031 timeline; Rainmaker pulls inventory across
the network and ships timeline-fit candidates to their HACKER. Charges per matched close,
0.25–0.50%, against a broker industry standard of 3%.

### AIOV — `aiov.atlasos.eth`
The AI Opinion of Value. Family office drops docs into their HACKER-PRO inbox.
30–60 minutes later, a defensible value opinion is rendered on-box.

> *We can't see your deal even if we wanted to.*

That's not a policy. It's the architecture. Documents never leave the family office's hardware.
A small encrypted brief travels to Atlas-70B in an ephemeral container, gets processed,
returns encrypted, and the container destroys itself. Hedera anchors only the session metadata —
never the deal.

Receipts at `aiov.defendable.eth/<id>`. The buyer's counsel can audit the chain in 30 seconds
without ever seeing the underlying numbers.

---

## The Defendable layer

Every artifact ships with a receipt. Every receipt has parents. Every parent has provenance.

```
HACK-DEED         deed.defendable.eth/<hash>          the underwriting work
   │
   ├── OM         om.defendable.eth/<hash>             rendered booklet · gated by NDA
   ├── NDA        nda.defendable.eth/<hash>            grants OM access · forward-link
   ├── LOI        loi.defendable.eth/<hash>            buyer offer · back-links to OM
   ├── PSA        psa.defendable.eth/<hash>            contract · back-links to LOI
   └── AIOV       aiov.defendable.eth/<id>             value opinion · session-only metadata
```

A buyer's counsel walks the chain end to end in 30 seconds. Booklet → underwrite → seller's
signed rent roll. Three documents, sixty seconds, full audit.

That's what *Defendable* means. Not a logo. Not a label. A chain you can verify yourself.

---

## The two-tree ENS architecture

```
atlasos.eth     →  WHO   ·   identity · persona · live HACKER endpoint
defendable.eth  →  WHAT  ·   certified document · receipt · anchored hash
```

They compose. `harvey.atlasos.eth` ships an underwrite, lands at `deed.defendable.eth/<hash>`,
parent-anchored to harvey's wallet. The actor and the artifact are both addressable, both
verifiable, both portable across firms.

---

## The unit economics

A traditional brokerage desk:

```
Senior broker        $562K / yr   (~25 closes / yr · pure dialer)
Junior analyst       $60–90K
Marketing coord      $60K
Data subs            ~$60K        (Crexi · CoStar · Buildout · CRM)
                     ─────────
Cost to staff        ~$760K / yr
Volume ceiling       ~25 deals
```

An Atlas-augmented desk:

```
Senior broker        $562K / yr   (still on the dials)
Hack-Deed-Maker      $60K / yr    (AI · 24/7)
Bookmaker (Gigi)     $60K / yr    (AI · 24/7)
Data substrate       $0           (baked into the AI roles)
                     ─────────
Cost to staff        ~$682K / yr
Volume ceiling       75–100 deals
```

Same senior. ~$80K less. Three to four times the volume.
The senior never leaves the dials. That's the unlock.

---

## What's running today

```
2026-05-06

Atlas-70B (Llama 3.3 doctrine model)         finishing on swarmrails (~step 1130 / 1177)
Bookmaker-8B (Granite 4.1 · Atlas corpus)    cooking on smash (step 400 · eval 0.5615 · 86%)
Underwriter-3B (Granite 4.1 · Atlas corpus)  cooking on rig 99 (step ~50 / 1177)
Granite-Docling-258M                         deployed · eyes · TEDS 0.97 on financial tables
HACKER reference unit                        signal-edge-01 · stock 3B benchmarked at 13.5 tok/s

Compute fleet                                186 GPUs · ~14 TB VRAM · sovereign · owned
                                             126× RTX PRO 6000 Blackwell (96GB ea)
                                              48× RTX 4500 (32GB ea · 24/7 inference fleet)
                                              12× RTX 5090 (32GB ea)

Schemas locked                               LOI · NDA · OM · AIOV  (PSA next)
Doctrine locked                              Hack-Deed-Maker · Bookmaker · Rainmaker
                                             Wax-on-Wax-off · Labor-not-Data · V/V/V
```

---

## V/V/V — the trust standard

**Verified.** Every fact in every output traces to a source. sha256 + Hedera anchor.

**Vetted.** Every fact passes the Hack-Deed-Maker's seven-dimension drill before it ships.
The Bookmaker never invents a number. The Rainmaker never matches blind.

**Virtu.** The Italian word for craftsmanship as a virtue. Every deliverable carries
the polish of someone who has closed eight billion in deals over thirty years.
The standard isn't *good enough to ship*. The standard is *something I'd put my own
name on*. Every output, every box, every desk.

We don't ship slop.

---

## Provenance

**Caballerz Network LLC** · DBA **Swarm & Bee** · Florida LLC.
Dun & Bradstreet **D-U-N-S 138652395**.

Founder background: thirty years in commercial real estate on a national platform.
Eight billion in closed transactions. Industrial STNL · cold storage · supply chain
logistics · economic development. Sat in the pit. Knows what a deal looks like
on the way to close, and what a deal looks like on the way to dead.

Atlas OS is the firm's brokerage doctrine, automated. Same lifecycle. Same discipline.
Same standard. The receipts make it portable.

---

## License

Apache 2.0 for the OS components and schemas in this repository.

The cooked model weights — Atlas-70B, Bookmaker-8B, Hack-Deed-Maker-3B — are proprietary
to Caballerz Network LLC. Available to customers who hold a HACKER box on the network.

---

## Repository layout

```
atlasOS/
├── README.md              this file
├── ARCHITECTURE.md        full technical map
├── PRODUCTS.md            HACKER · HACKER-PRO · HACKER-AGX · AIOV · Rainmaker
├── PERSONAS.md            atlasos.eth subdomain registry · how identities work
├── DEFENDABLE.md          the receipt layer · subdomain tree · audit walkthroughs
├── MODELS.md              full model stack — Atlas-70B · Bookmaker-8B · Hack-Deed-Maker-3B · Docling
├── CORPUS.md              Royal Jelly CRE corpus — provenance · RJP grading · cook auditor
├── ROADMAP.md             what's running · what's next · cooks calendar
├── recipes/               cook recipes (declarative · per-model spec) — atlas-70b · bookmaker-8b · hack-deed-maker-3b
├── schema/                JSON schemas for every Defendable document
│   ├── loi.schema.json
│   ├── nda.schema.json
│   ├── om.schema.json
│   ├── aiov.schema.json
│   └── deed.schema.json
├── boxes/                 hardware specs and AtlasOS provisioning
│   ├── hacker.yml         $250 · Orin Nano 8GB
│   ├── hacker-pro.yml     $599 · Orin NX 16GB
│   └── hacker-agx.yml     $2,000 · AGX Orin 64GB
├── personas/              ENS registration templates
└── docs/                  doctrine · brand language · sales motion
```

---

## Reach

- Network: `atlasos.eth`
- Box page: `hackerpro.eth`
- Receipts: `defendable.eth`
- Founder: build@swarmandbee.ai

---

*The 3% commission is optional now.*
