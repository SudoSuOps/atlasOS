# Defendable · the receipt layer

Every output Atlas OS produces ships with a receipt. Every receipt has parents.
Every parent has provenance. Every provenance link traces to a source the seller actually signed.

That's what *Defendable* means.

---

## V/V/V — the trust standard

**Verified.** Every fact in every output traces to a source. sha256 + Hedera anchor.
A counsel can hash the source PDF and confirm it matches the parent_anchor on the deed.

**Vetted.** Every fact passes the Hack-Deed-Maker's seven-dimension drill before it ships.
Tenant story · building specs · market summary · lease terms · financials · comps · story hooks.
The Bookmaker never invents a number. The Rainmaker never matches blind.

**Virtu.** The standard isn't *good enough to ship*. The standard is *something I'd put my own
name on.* Thirty years of broker discipline runs through every output. We don't ship slop.

---

## The subdomain tree

Each Defendable document type lives at its own subdomain. Walking the tree:

```
defendable.eth (parent · receipt namespace)
│
├── deed.defendable.eth/<hash>
│       The Hack-Deed-Maker's underwriting work · the truth source
│       Parent of every other artifact in a deal
│
├── om.defendable.eth/<hash>
│       Rendered Offering Memorandum (Bookmaker / Gigi output)
│       Forward-gated by an NDA · back-link from any LOI that responds
│
├── nda.defendable.eth/<hash>
│       Confidentiality Agreement · forward-grants access to OM
│       access_grant.granted_documents[].doc_hash → OM render_pdf_sha256
│       Counsel verifies the OM signed-against matches the OM received
│
├── loi.defendable.eth/<hash>
│       Letter of Intent · buyer offer · back-link to OM
│       property_ref.parent_om_deed_hash → om.defendable.eth/<hash>
│
├── psa.defendable.eth/<hash>
│       Purchase & Sale Agreement · contract · back-link to LOI
│
├── aiov.defendable.eth/<session_id>
│       AI Opinion of Value · session metadata only
│       Hash of the request size + timestamp + TPM attestation
│       NEVER deal content
│
└── (future)
        psa.defendable.eth · t12.defendable.eth · rentroll.defendable.eth ·
        comp.defendable.eth · placer.defendable.eth · appraisal.defendable.eth
```

---

## How to verify a deal

Anyone with a hash and a browser:

```
1. Receive a document (e.g., om.defendable.eth/boa-murfreesboro-2026-04)
2. Compute the file's sha256 locally
3. Hit the URL · the resolver returns the receipt
4. Confirm the receipt's render_pdf_sha256 == your local hash
5. Walk parent_anchors:
       parent_hack_deed → the underwriting deed
       source_documents → rent roll, T-12, lease, title, ESA
       data_pulls → Placer, Esri, SEC EDGAR, comps
6. Each parent is its own receipt · keep walking until source PDFs
7. Hash any source PDF the seller produces · confirm it matches the chain

Total time: 30 seconds.
Total trust required in any third party: zero.
```

That's the audit. Mathematical, not relational.

---

## Anchoring

All Defendable receipts anchor to **Hedera Hashgraph topic 0.0.10291838**.

Hedera was chosen for:
- Sub-second finality
- Low fee per anchor (~$0.0008)
- aBFT consensus
- Public mirror nodes for verification
- HCS (Hedera Consensus Service) — purpose-built for this kind of message-anchoring

The bridge — `merkle.py → hedera_bridge.py` — batches deeds into Merkle trees and anchors
the root every block. Per-deed cost ~$0.0008. Per-deal cost (NDA + OM + LOI + PSA + AIOV
+ ~10 source-document anchors): under a penny.

---

## What's anchored vs. what's not

**Anchored on Hedera (publicly verifiable):**
- Document hashes (sha256)
- Parent-child link structure
- Timestamps
- Issuer wallet (e.g., `harvey.atlasos.eth` resolved address)
- Document type and version

**NEVER anchored:**
- Document content (the OM PDF stays in encrypted storage · only the hash anchors)
- Personal information
- Deal financials
- Tenant identities (except where the seller chose to publish in a teaser)
- Buyer identities for AIOV sessions
- Any data covered by an NDA

The chain proves the work happened. The content stays sovereign.

---

## A note on what this is NOT

Atlas OS is not a blockchain MLS. It is not a tokenized real estate marketplace.
It is not "Web3 CRE." It is not a DAO. It is not a smart-contract enforcement layer.

It is a brokerage doctrine — codified, automated, and provably trustworthy.
Hedera is plumbing, not the product. ENS is a directory, not the product.
The product is the work the boxes do, and the receipt that the work was done right.

Verified · Vetted · Virtu.

We don't ship slop.
