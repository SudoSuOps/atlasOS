# Atlas OS · Architecture

The full technical map of what runs where, who talks to whom, and where the receipts land.

---

## The four layers

```
┌──────────────────────────────────────────────────────────────────────┐
│                      LAYER 1 · IDENTITY                              │
│                                                                      │
│  atlasos.eth — the parent ENS namespace                              │
│  Every HACKER box gets one subdomain at provisioning:                │
│                                                                      │
│      harvey.atlasos.eth          (a Hack on a brokerage desk)        │
│      familyoffice.atlasos.eth    (a 1031 buyer's desk)               │
│      gigi.atlasos.eth            (the Bookmaker persona)             │
│      rainmaker.atlasos.eth       (the matchmaker service)            │
│      aiov.atlasos.eth            (the AIOV ordering surface)         │
│      atlas70b.atlasos.eth        (back-end doctrine model)           │
│                                                                      │
│  Each subdomain resolves to: a wallet · a live HACKER endpoint       │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│                      LAYER 2 · COMPUTE                               │
│                                                                      │
│  HACKER         · Jetson Orin Nano 8GB   · 67 TOPS  · $250           │
│      Granite-4.1-3B Q4 (Hack-Deed-Maker) · 13.5 tok/s                │
│      Granite-Docling-258M (eyes)                                     │
│      Whisper STT · Piper TTS · Honey ledger mirror                   │
│                                                                      │
│  HACKER-PRO     · Jetson Orin NX 16GB    · 100 TOPS · $599           │
│      Granite-4.1-8B Q4 (Bookmaker / family office)                   │
│      Plus all HACKER components                                      │
│                                                                      │
│  HACKER-AGX     · AGX Orin 64GB          · 275 TOPS · $2,000         │
│      Granite-4.1-30B Q4 (branch-tier · multi-deal concurrent)        │
│                                                                      │
│  ATLAS-70B      · datacenter · 2× RTX PRO 6000 Blackwell             │
│      Llama-3.3-70B-Instruct + Atlas Block-0 LoRA                     │
│      The doctrine model · cracks the hardest deals                   │
│      Runs in EPHEMERAL containers for AIOV (no persistence)          │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│                      LAYER 3 · WORK                                  │
│                                                                      │
│  Skill catalog · ~60 tools across 7 categories:                      │
│                                                                      │
│    1. Data-pull        Placer · Esri · SEC · county GIS · FEMA       │
│    2. Doc-abstract     Docling-powered: lease · T-12 · rent roll …   │
│    3. Math             cap · DSCR · IRR · 1031 · rent-to-sales       │
│    4. Drafting         OM · landing · e-blast · LOI · NDA · social   │
│    5. Verify           Merkle · Hedera · cross-firm resolve          │
│    6. Market intel     news · employers · CMBS · supply pipeline     │
│    7. Visual           drone brief · trade-area polygon · callouts   │
│                                                                      │
│  Each skill response is sha256+anchored · becomes parent_anchor      │
│  Skills compose into workflows · workflows become deeds              │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│                      LAYER 4 · RECEIPTS                              │
│                                                                      │
│  defendable.eth — the parent ENS namespace for receipts              │
│  Every Defendable document type gets a subdomain:                    │
│                                                                      │
│      deed.defendable.eth/<hash>     · the Hack-Deed-Maker work       │
│      om.defendable.eth/<hash>       · the rendered booklet           │
│      nda.defendable.eth/<hash>      · gates OM access · forward-link │
│      loi.defendable.eth/<hash>      · buyer offer · back-links to OM │
│      psa.defendable.eth/<hash>      · contract · back-links to LOI   │
│      aiov.defendable.eth/<id>       · session metadata only          │
│                                                                      │
│  Anchored on Hedera topic 0.0.10291838                               │
│  Counsel verifies the full chain in 30 seconds, any browser          │
└──────────────────────────────────────────────────────────────────────┘
```

---

## Deal-flow lineage

```
HACK-DEED (root · the underwriting work)
   │
   ├── OM (rendered booklet)
   │     ↑ gated by NDA
   ├── NDA (forward-grants OM access)
   ├── LOI (back-responds to OM with buyer offer)
   └── PSA (back-responds to LOI with contract terms)

Side branch:
HACK-DEED → AIOV (session metadata only · no content stored)
```

Every link in the chain is a deed. Every deed has a hash. Every hash has parents.
Walk from a closed PSA back to the seller's signed rent roll in three hops.

---

## Privacy architecture for AIOV

The "we don't whisper your deal" claim is structural, not promised.

```
Family office HACKER-PRO (familyoffice.atlasos.eth)
    │
    │ (1) Local Docling parses PDFs
    │ (2) Local 8B underwriter computes prelim cap/DSCR/IRR
    │ (3) HACKER encrypts a small JSON brief with a one-time session key
    │     [Raw PDFs NEVER leave the office]
    │
    │  encrypted brief →→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→
    ▼                                                      ▼
                                          Atlas-70B ephemeral container
                                              · TPM-attested boot
                                              · no persistent volumes
                                              · decrypts in-memory
                                              · runs the underwrite
                                              · encrypts response with same key
                                              · container self-destructs
                                          └──→ encrypted response back

    │ (4) HACKER-PRO decrypts with session key
    │ (5) Renders AIOV report on-box
    │     "you got mail" at familyofficexyz.atlasos.eth/inbox
    ▼
Family office reads it · their data, their disk

Hedera anchors:
  ✓ session_id (uuid · random)
  ✓ timestamp_start / end
  ✓ request_size_bytes / response_size_bytes
  ✓ TPM attestation of ephemeral container
  ✗ NEVER deal data, address, tenant, financials
```

---

## Network protocol (high level)

HACKERs talk to each other over the AtlasOS mesh.

```
Persona A (e.g., harvey.atlasos.eth) wants to query persona B (rainmaker.atlasos.eth):

  1. A resolves rainmaker.atlasos.eth → wallet + endpoint
  2. A signs the request with its wallet
  3. Request travels (HTTPS over LAN/WAN · or direct mesh on local network)
  4. B verifies A's signature against the ENS registration
  5. B processes (e.g., Rainmaker matches inventory to A's criteria)
  6. B returns signed response
  7. A verifies B's signature
  8. Both anchor a session record at <interaction_type>.defendable.eth/<id>
```

No central broker. No platform middleman. ENS is the directory; Hedera is the receipt log;
each HACKER carries its own sovereignty.

---

## Compute fleet (datacenter side)

```
swarmrails       Xeon w9-3475X · 256GB DDR5 · 2× RTX PRO 6000 Blackwell 96GB
                 Atlas-70B doctrine model (training + AIOV ephemeral inference)

smash            Ryzen 9 9950X3D · 60GB · 1× RTX 5090 32GB
                 Bookmaker-8B production rendering · cooks for 8B-class models

192.168.0.99     Ryzen + 1× RTX 5090 32GB
                 Hack-Deed-Maker-3B cooks · the underwriter LoRA factory

48× RTX 4500     200W · 32GB ea · 24/7 inference fleet
                 Document parsing (Docling) · Bookmaker batch jobs ·
                 Rainmaker matching workloads

12× RTX 5090     32GB ea
                 Burst capacity · cook scheduling

126× RTX PRO 6000 Blackwell  96GB ea
                 The reserve · sovereign compute moat
                 ~14 TB VRAM total fleet capacity
```

---

## Why this architecture wins

**Sovereign by default.** Customer data lives on the customer's hardware. The server-side
work is ephemeral and TPM-attested.

**Provable, not promised.** Every claim ("we don't store data") is structurally enforced
and Hedera-attested. Counsel can verify without trusting the firm.

**Composable.** Every persona is an ENS subdomain. Every artifact is a Defendable receipt.
Adding a new role (e.g., a new vertical Rainmaker) is one ENS registration plus a HACKER box.

**Portable.** A receipt at `om.defendable.eth/<hash>` resolves anywhere. No CRM lock-in.
No platform dependency. Counsel at any firm verifies in 30 seconds.

**Owned compute.** The model behind every persona runs on owned GPUs. ~14 TB of VRAM,
180+ accelerators, no cloud margin baked in. The marginal cost of a HACKER box answer is
electricity.

That's the moat. Architecture, not pricing.
