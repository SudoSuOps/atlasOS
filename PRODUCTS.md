# Atlas OS · Products

Five SKUs. Three boxes. Two services. One network.

---

## The boxes

### HACKER · $250

```
Hardware    NVIDIA Jetson Orin Nano 8GB Super Developer Kit
Compute     67 TOPS · 1024-core Ampere GPU · 32 Tensor Cores
Memory      8 GB LPDDR5 unified (102 GB/s)
CPU         6-core ARM Cortex-A78AE @ 1.51 GHz
Power       7-25W
Storage     234 GB NVMe
I/O         Gigabit Ethernet · WiFi · 2× CSI camera · USB audio · HDMI

OS          Atlas OS (a SwarmOS distribution)
Brain       Granite-4.1-3B cooked Q4_K_M (Hack-Deed-Maker)
Throughput  ~13.5 tok/s sustained · ~500ms TTFT
```

**Customer.** Brokerage Hack on a dial floor. One per desk.

**Daily job.** Runs the desk-edge underwriter. Live cap-rate / DSCR / IRR during seller
calls. Drafts LOIs in 30 seconds. Pre-stamps deeds. Joins Discord channels with voice and
camera. Wax on, wax off — drill every deal, every day.

**Persona.** `<broker-firstname>.atlasos.eth` (one per box, registered at provisioning).

---

### HACKER-PRO · $599

```
Hardware    NVIDIA Jetson Orin NX 16GB
Compute     100 TOPS
Memory      16 GB
Power       10-25W

Brain       Granite-4.1-8B cooked Q4_K_M (Bookmaker / family office)
Throughput  ~10 tok/s sustained
```

**Customer.** Family office · 1031 buyer · institutional seller · senior brokerage desk
that needs richer narrative production (full Bookmaker rendering on-box).

**Daily job.** Hosts the Bookmaker-class brain. Runs AIOV. Receives inventory matched
by Rainmaker. Inbox-style UX at `familyofficexyz.atlasos.eth/inbox`.

**Persona.** `<office-name>.atlasos.eth`.

---

### HACKER-AGX · $2,000

```
Hardware    NVIDIA AGX Orin 64GB
Compute     275 TOPS
Memory      64 GB
Power       15-60W

Brain       Granite-4.1-30B cooked Q4_K_M (branch-tier · multi-deal concurrent)
```

**Customer.** Brokerage HQ · fund sponsor · multi-vertical Rainmaker.

**Daily job.** Concurrent inference for an entire branch. Hosts the heavyweight brain
when you need maximum reasoning depth.

**Persona.** `<entity>.atlasos.eth` (firm-level).

---

## The services

### AIOV · AI Opinion of Value

A defensible, sub-hour value opinion for any property. Family office drops docs into
their HACKER-PRO inbox; the AIOV report renders on-box, encrypted round-trip to the
Atlas-70B doctrine model, no data persisted server-side.

```
Single AIOV       $499 / deal
Subscription      $4,999 / yr · 12 AIOVs / yr
Enterprise        Custom · multi-billion family office · full portfolio coverage
```

**Why it kills the BOV (Broker Opinion of Value).** A BOV is "free" because it costs you
market exposure — every broker who runs one starts pitching for the listing. AIOV
costs $499 and zero exposure. *We can't see your deal even if we wanted to.*

Receipt at `aiov.defendable.eth/<session_id>`. Counsel verifies you got a defensible
value opinion without ever seeing what was analyzed.

---

### Rainmaker · Inventory matching

Across the AtlasOS network, Rainmaker matches inventory to buyers' timelines.
A family office facing a 1031 deadline queries Rainmaker; their HACKER-PRO returns
five timeline-fit candidates, each with full Defendable receipts.

```
Per matched close   0.25–0.50% of deal value
                    (vs broker industry standard 3%)
```

**Where the inventory comes from.** Other HACKERs on the network — broker desks listing
their pipeline, sponsors listing direct, sellers listing direct. The Rainmaker doesn't
create inventory; it surfaces what's already on the network.

**Persona.** `rainmaker.atlasos.eth` (or vertical-specific: `rainmaker.stnl.atlasos.eth`,
`rainmaker.industrial.atlasos.eth`, etc.)

---

## SKU bundles

| Customer | Recommended bundle | Annual cost |
|---|---|---|
| Single brokerage Hack | HACKER + Hack-Deed-Maker labor | $108K + $250 capex |
| Senior brokerage desk | HACKER-PRO + Bookmaker labor | $108K + $599 capex |
| Family office (active buyer, 5+ acquisitions/yr) | HACKER-PRO + AIOV subscription + Rainmaker | $4,999 + $599 + per-close |
| Family office (occasional, 1-3 deals/yr) | HACKER-PRO + AIOV per-deal | $599 + $499/deal |
| Sponsor / seller | HACKER-PRO + listing | $599 + per-listed-deed |
| Brokerage HQ | HACKER-AGX + 5-10× HACKER + labor stack | varies |

---

## What's not for sale

- **Data feeds.** We don't sell listings. We don't sell comps. We don't sell market reports.
- **Per-seat dashboards.** No web app. No login portal. The product is the box, the persona, the work.
- **Listing platform fees.** Sellers list direct, no commission per listing.
- **Cooked weights as standalone files.** Atlas-70B / Bookmaker-8B / Hack-Deed-Maker-3B
  weights are proprietary and run only on customer-held HACKER hardware on the network.
- **Customer data.** Ever. By architecture.
