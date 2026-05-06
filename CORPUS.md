# Royal Jelly CRE Corpus

The proprietary CRE training corpus. Curated under the Royal Jelly Protocol. Powers
every Atlas brain — Atlas-70B, Bookmaker-8B, Hack-Deed-Maker-3B — and every future
vertical Hack.

**Documentation only.** Corpus content is proprietary to Swarm and Bee LLC and
never committed to this repository. Hashes and structure are anchored on Hedera for
verification.

---

## What it is

A high-quality, multi-source, fingerprint-deduplicated corpus of CRE underwriting
exchanges in the canonical chat format:

```
{
  "messages": [
    {"role": "system",    "content": "<broker persona + 2026 market environment>"},
    {"role": "user",      "content": "<deal sheet · property facts · financials>"},
    {"role": "assistant", "content": "<broker-grade analysis · math · pass-or-proceed>"}
  ]
}
```

Every record passed the **Royal Jelly Protocol (RJP-1)** quality gate before inclusion.

---

## Block-0 stats (the slice all current cooks train on)

```
Total train records         125,651
Eval records (holdout)      996
Fingerprint-disjoint        YES (no train-eval leakage)
Unique system prompts       37
System-prompt buckets       5 (underwriting_calc · ic_memo · distress_workout ·
                                macro_capital · comp_market)
Avg record size             ~6,200 chars (~1,500 tokens)
Range                       799 → 15,889 chars

Dropped during build        38,038 fingerprint duplicates
                            Sub-min-message records discarded
                            jelly_threshold_verification_score < 75 discarded

Build seed                  42
Build elapsed               26.2 seconds
Build date                  2026-05-03

train.jsonl sha256          d63b05d9e36b0e0d1113ee2fcf9c4681dbb95133a44889319bf1df2f7ad90f39
eval.jsonl sha256           7f025a264210174a75c5bad30c5f255011e133272ed33a1917798b3085f075cc
```

---

## Source mix (provenance per row)

```
Label                            Records   Notes
────────────────────────────────────────────────────────────────────
canonical_cre_volume             59,523    capped @ 60K of 651K available
                                            base CRE language · property types · markets · structures
capital_markets_neweconomy       19,754    modern capital stack · RWA · debt fund · special servicing
atlas_v1_foundation              16,938    original Atlas DNA · pass/proceed mental model
macro_energy                     13,965    energy-aware CRE · cold storage · data center · EV charging
capital_markets_stamped           8,871    Defendable-stamped institutional debt deals
streams                           4,224    multi-shard signal · live market chatter
maturity_wall_workflow            2,376    distressed refi path planning (2026 vintage)
────────────────────────────────────────────────────────────────────
TOTAL                          125,651
```

Each source has its own sha256, anchored to the corpus manifest.

---

## The five buckets (what skills the corpus teaches)

```
1. underwriting_calc      "Show all steps · round money to dollar · ratios to 2 decimals"
                          The junior-analyst-doing-the-math voice.

2. ic_memo                Executive Summary / Property Overview / Market / Financial /
                          Risk / Recommendation structure.
                          The senior-broker IC memo voice.

3. distress_workout       DSCR compression · A/B note splits · debt-fund vs CMBS path
                          modeling · sponsor equity tracking.
                          The 2026-vintage debt-wall voice.

4. macro_capital          Sector-level moves · cap rate spreads · CMBS delinq trends ·
                          lender appetite shifts.
                          The capital markets strategist voice.

5. comp_market            Submarket analysis · comp selection rationale · adjustments ·
                          trends.
                          The data-driven comp voice.
```

After ~37,000 samples seen at gold-standard recipe (1177 steps × 32 effective batch),
a Granite-4.1-3B-class brain absorbs enough variety in each bucket to produce
broker-grade output without prompt babysitting. Same recipe scales cleanly through 8B
and 70B sizes.

---

## Royal Jelly Protocol (RJP-1)

The CRE corpus is graded under the Royal Jelly Protocol — the same quality framework
that classifies every Hive Honey artifact in the broader Swarm pipeline.

```
Tier         Verification score  Use
─────────────────────────────────────────────────────────────
Royal Jelly  ≥ 95                top-tier · seeds future synthetic
Honey        ≥ 85                production training corpus
Pollen       ≥ 75                experimentation · candidate
Propolis     < 75                discarded (gate floor)
```

Block-0 entered training only with **jelly_threshold_verification_score ≥ 75**
(Pollen-grade or higher). Honey-grade and Royal-Jelly-grade subsets are weighted
heavier in future cooks.

The protocol enforces:
- **Mechanism present** (the answer explains *why*, not just *what*)
- **Tradeoff acknowledged** (real-world CRE never has only upside)
- **Density floor** (no filler · every sentence carries weight)
- **Numerical accuracy** (math passes deterministic verifiers)
- **Schema validity** (system/user/assistant chat format)
- **De-duplication** (fingerprint-based)
- **No degenerate output** (no "as an AI language model" leak)

Every dropped record is logged with reason. Every kept record carries its Jelly score
in the manifest.

---

## Cook auditor protocol

The corpus is *re-validated continuously during training*, not trusted blind.

Every 3 hours during a cook:
- Sample N records from active checkpoints
- Run contamination scan (chat-template leakage · think-tag leakage · "I cannot help" leakage)
- Compute Jelly distribution drift
- Merkle-stamp the audit
- **Kill switch: if contamination > 1%, the cook stops.**

This is locked doctrine. *Validate the validator.* No model ships from a cook the auditor
didn't sign off on.

---

## Defendable provenance

```
Manifest issuer              swarmandbee.eth
Manifest category            data.atlas.defendable.eth
Hedera anchor topic          0.0.10291838
Anchor target                anchor.atlas.defendable.eth

Subdomain receipts:
  corpus.atlas.defendable.eth     · the corpus build manifest
  recipe.atlas.defendable.eth     · the cook recipe used per build
  weights.atlas.defendable.eth    · the trained adapter hashes
  eval.atlas.defendable.eth       · the eval results
```

Every cook produces a manifest at `MANIFEST_SLICE.json` with:
- per-source sha256 + raw count + label
- filter parameters (jelly threshold · fingerprint dedup · min messages)
- drop counts per reason
- final train/eval sha256
- system_prompt diversity stats
- Defendable issuer + category + anchor target

The manifest itself is hashed and Hedera-anchored. Three-document audit chain:
deed → manifest → source hashes. Counsel verifies in 30 seconds.

---

## Future expansion

Block-0 is the first slice. Next slices in queue:

- **Block-1 · Vertical-Hack pairs.** STNL-DG · QSR · Auto · Entertainment · Cold Storage.
  Synthetic + real pairs scored against Royal Jelly. ~5K-15K per Hack.
- **Block-2 · Distress-cycle 2026-2027.** Live deals as they hit watchlist · special servicing
  decisions · workout outcomes. Anchored by closing date. The maturity-wall living dataset.
- **Block-3 · Bookmaker creative production.** 100% creative-only pairs (NO analytical work).
  OM teasers · landing pages · e-blasts · listing copy from public CoStar/LoopNet/Crexi/REIT
  decks. For Bookmaker v2 cook on Granite-4.1-8B (per locked Bookmaker doctrine).

Each new block ships with its own manifest, its own RJP grading, its own anchor.
The corpus compounds. The brains compound with it.

---

## What this corpus is *not*

- **Not the corpus M&M / CBRE / JLL train on.** Theirs are private, untrained on a model
  this scale, and never anchored. We're not competing for the same ground.
- **Not scraped from public listings.** Curated, multi-source, RJP-graded. The 38,038
  duplicates dropped during the Block-0 build came from public-listing redundancy —
  precisely the kind of low-signal data that hurts a cook.
- **Not synthetic-only.** Mix of real-deal records (atlas_v1_foundation) and synthetic-
  but-graded pairs. Every synthetic record had to pass RJP to be kept.
- **Not static.** New blocks land continuously. Models retrain on a quarterly cadence,
  Defendable-anchored each time. Living dataset, not frozen training set.

---

## License

The Royal Jelly CRE Corpus is **proprietary** to Swarm and Bee LLC.

**Not licensed for redistribution.** Available indirectly through cooked Atlas brains
that ship inside customer-held HACKER hardware. Customers don't license the corpus —
they license the work the corpus enables.

That's the labor business in action: pay for the analyst, not the database.
