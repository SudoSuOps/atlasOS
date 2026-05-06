# Infrastructure · we own the compute

> *Not a cloud provider. Not a data harvester. We own the compute.*

This is the infra-side of the labor business thesis. The boxes ship to customer
desks; the back-end inference runs on hardware Swarm and Bee LLC owns and operates.
There is no AWS line item. There is no Azure line item. There is no GCP line item.
There is no "data partner" agreement that gives a third party access to your deals.

---

## The fleet (as of 2026-05)

```
Sovereign GPU inventory                  186 GPUs · ~14 TB VRAM total
                                          7 active rigs · datacenter + edge

Datacenter compute
  swarmrails  · Xeon w9-3475X · 2× RTX PRO 6000 Blackwell 96GB · Atlas-70B doctrine
  smash       · Ryzen 9950X3D · 1× RTX 5090 32GB                · Bookmaker-8B production
  rig 99      · Ryzen      · 1× RTX 5090 32GB                · Hack-Deed-Maker-3B cooks

24/7 inference fleet                     48× RTX 4500 32GB · 200W cards
                                          (purpose-built for batch inference at scale)
                                          (Docling parsing · Bookmaker batch · Rainmaker match)

Burst + cook scheduling                  12× RTX 5090 32GB

Reserve capacity                         126× RTX PRO 6000 Blackwell 96GB
                                          ~12 TB VRAM
                                          (the moat · provisioned for production rollout)

Edge reference unit                      signal-edge-01 · Jetson Orin Nano 8GB
                                          (the canonical HACKER deployment target)
```

These are owned, racked, and operated by Swarm and Bee LLC. Not leased capacity.
Not committed cloud spend. Not "AI cloud" credits.

---

## What this means commercially

**No AWS / Azure / GCP / Cloudflare AI / Together / Replicate margin baked in.**
Customers do not subsidize a cloud provider's data center business through us.

**No data-residency uncertainty.** Your data either stays on your HACKER (sovereign
edge) or moves to our owned servers in our facilities (sovereign datacenter). It doesn't
get routed through a hyperscaler's queueing system or a model-serving startup's
shared inference cluster.

**No "your prompts may be used to improve our models" clause.** This is the standard
clause every cloud LLM provider has. We don't have it because we don't need it: our
training data comes from the curated Royal Jelly CRE corpus, not from customer prompts.
The infrastructure architecturally cannot do prompt-as-training, because production
inference runs in ephemeral containers with no persistent volumes.

**No third-party data resale.** Your deals do not become a Crexi listing, a CoStar comp,
a Reonomy record, or a SafeGraph foot-traffic data point. They stay yours.

---

## How AIOV inference actually works (the architecture, not the promise)

Family office runs AIOV. The flow:

```
1. Family office HACKER-PRO encrypts a small JSON brief with a fresh session key
   (the original PDFs never leave the office)

2. The encrypted brief is sent to Atlas-70B's endpoint at atlas70b.atlasos.eth

3. Atlas-70B's gateway:
   - spins up a fresh ephemeral container per session
   - container is TPM-attested (boot integrity verified before secret release)
   - no persistent volumes mounted · only RAM
   - decrypts the brief in memory only
   - runs the underwriting via vLLM-served Atlas-70B weights
   - encrypts the response with the same session key
   - flushes container memory · destroys the container

4. Encrypted response returns to the family office HACKER-PRO

5. Hedera anchors:
     ✓ session_id (uuid · random)
     ✓ timestamp_start / timestamp_end
     ✓ request_size_bytes / response_size_bytes
     ✓ TPM measurement of the ephemeral container
     ✗ NEVER deal data, address, tenant, financials

6. The session key never persists anywhere except the family office's wallet
```

**This is structural.** The atlas70b.atlasos.eth endpoint cannot retain customer data
because the inference container itself does not have writable persistent storage.
Architecture, not policy.

---

## The big-models-on-our-compute principle

Atlas-70B is the doctrine model. It's the brain that cracks the hardest deals — full
IC memos, AIOV reports, distress workouts, multi-property portfolio analyses.
Running a 70B at production quality requires real compute. We provide it.

**Not as a SaaS endpoint. As infrastructure for our own labor product.**

When you buy a HACKER-PRO and subscribe to AIOV, you're paying for an analyst's
output, not for inference time. The Atlas-70B back-end is *how the analyst thinks*,
not what you're billed for. Per-call overhead is on us.

This is the same model as a brokerage that owns its office building rather than renting
desks at WeWork. The compute is the office. Owning it changes the customer experience,
the cost structure, and the trust story all at once.

---

## What we are NOT

This list is not modesty. It's positioning.

**We are not a cloud provider.** AWS, Azure, GCP — those are infrastructure-as-a-service
companies. We don't sell compute by the hour. We sell labor outputs that happen to run
on infrastructure we own.

**We are not a data harvester.** Crexi, CoStar, Reonomy, Placer, SafeGraph — those
companies' business model is to aggregate market data and rent it back via subscriptions.
We use some of those data layers (Placer specifically · see other docs) as *input
substrates inside our hires*, not as products we resell.

**We are not a SaaS platform.** Salesforce, Buildout, Dealpath — those are workflow
software with monthly per-seat fees. We don't sell seats. We sell roles (the AI
analyst, the AI marketing coord) priced like the humans they replace.

**We are not a marketplace operator extracting fees from listing volume.** LoopNet,
Crexi-as-marketplace — those companies make money on listing fees and commission
overrides. We make money on labor SKUs and per-match Rainmaker fees that are
fundamentally smaller than broker commissions.

**We are not a DAO. We are not Web3. We are not tokenizing real estate.** Hedera is
the cryptographic settlement layer for our receipts. ENS is the directory for our
personas. That's it. There is no governance token. There is no fundraise. There are
no founders' allocations. We're a Florida LLC selling labor and hardware.

**We are not an AI lab.** We don't sell access to language models. We don't publish
foundation model checkpoints for general use. We cook proprietary adapters on a
proprietary corpus and ship them inside a proprietary product. The OS is open
(Apache 2.0); the brains and the data are not.

---

## What we ARE

A real estate brokerage doctrine company that owns its compute, sells its labor as
roles (not seats), anchors its work in cryptographic receipts, and stays out of every
data-extraction model the rest of the industry runs on.

Swarm and Bee LLC · Florida LLC · D-U-N-S 138652395.

The compute is the office. The boxes are the desks. The receipts are the work.
The customer pays for the work.

---

## How customers verify this isn't BS

Three ways:

1. **Audit the architecture.** This repository documents how AIOV works. The
   ephemeral-container claim is testable: any customer with a TPM verification stack
   can confirm the container measurement matches what's anchored on Hedera per session.

2. **Audit the receipts.** Every AIOV session has a Hedera-anchored record at
   `aiov.defendable.eth/<session_id>`. The metadata is public. The container TPM
   measurement is public. The deal content is not — and never will be — anchored.

3. **Audit the LLC.** Swarm and Bee LLC is a Florida-registered legal entity with
   a public D-U-N-S number. State-licensed brokers operate the firm's brokerage
   activities. Real address, real entity, real liability. Not an offshore wrapper.

That's what makes the *Verified · Vetted · Virtu* trust standard real instead of
marketing. You can check our work without taking our word.
