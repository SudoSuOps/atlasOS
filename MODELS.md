# Atlas OS · Models

The full model stack. Every brain that runs on every node.

Documentation only. Cooked weights are proprietary to Swarm and Bee LLC and ship
inside customer-held HACKER hardware. Base models cited here are publicly available
under their respective licenses.

---

## The fleet

| Model | Base | Params | Role | Lives on |
|---|---|---|---|---|
| **Atlas-70B** | Llama-3.3-70B-Instruct | 70B | Doctrine model · IC memos · final verdicts · AIOV cracker | Datacenter (swarmrails · 2× PRO 6000 96GB) |
| **Bookmaker-8B** | IBM Granite-4.1-8B | 8B | OS-tier reasoner · OM rendering · senior-desk Bookmaker | HACKER-PRO ($599 box) · datacenter for batch |
| **Hack-Deed-Maker-3B** | IBM Granite-4.1-3B | 3B | Desk-edge underwriter · live calc · LOI drafting | HACKER ($250 box) |
| **Branch-30B** *(future)* | IBM Granite-4.1-30B | 30B | Branch-tier · multi-deal concurrent | HACKER-AGX ($2K box) |
| **Granite-Docling-258M** | Granite-Docling | 258M | Eyes · reads any rent roll · T-12 · lease · OM | Every HACKER tier |
| **Whisper-base** | OpenAI Whisper | 74M | Ears · transcribes seller calls · meeting notes | Every HACKER tier |
| **Piper TTS** | Piper | ~60M | Mouth · broker-voice synthesis | Every HACKER tier |

---

## Atlas-70B · the doctrine model

```
Base model     meta-llama/Llama-3.3-70B-Instruct
Base license   Meta Llama 3.3 Community License (commercial-permitted with terms)
Architecture   Dense decoder · 80 layers · 8192 hidden · GQA 64:8 · SwiGLU · 128K ctx
Cook recipe   Gold Standard (see recipes/atlas-70b.yml)
                LoRA r=64 α=32 · LR 1e-5 cosine · eff batch 32 · max_steps 1177
                bf16 LoRA · target = q_proj/k_proj/v_proj/o_proj/gate_proj/up_proj/down_proj
Training data  Royal Jelly CRE Block-0 corpus (see CORPUS.md)
                125,651 train records · 996 fingerprint-disjoint eval
Hardware       2× RTX PRO 6000 Blackwell 96GB · FSDP_FULL_SHARD
Cook time      ~73 hours
Final loss     train ~0.54 · eval projected ~0.55-0.65
Defendable     issuer swarmandbee.eth · category atlas.defendable.eth
                anchor topic 0.0.10291838
                subdomains: corpus · recipe · weights · eval
```

**What it does.** Cracks the hardest deals. Writes IC memos. Issues final pass-or-proceed
verdicts. Powers AIOV. Runs in *ephemeral containers* — TPM-attested, no persistent volumes,
session-only — so customer data never persists server-side.

**Where it runs.** Datacenter only (swarmrails · `atlas70b.atlasos.eth`). Never on a
desk-edge HACKER. Customer's HACKER calls into Atlas-70B for hard problems and AIOV
sessions; Atlas-70B answers and self-destructs the session.

---

## Bookmaker-8B · the senior-desk reasoner

```
Base model     ibm-granite/granite-4.1-8b
Base license   Apache 2.0
Architecture   Dense decoder · 40 layers · 4096 hidden · GQA 32:8 · SwiGLU ·
                tied embeddings · 128K ctx · BF16
Cook recipe   Gold Standard (see recipes/bookmaker-8b.yml)
                LoRA r=64 α=32 · LR 1e-5 cosine · eff batch 32 · max_steps 1177
                bf16 LoRA · target = standard 7-module list
                single-GPU, no FSDP, no QLoRA (8B fits cleanly on a 5090)
Training data  Royal Jelly CRE Block-0 corpus (same as Atlas-70B · apples-to-apples)
Hardware       1× RTX 5090 32GB
Cook time      ~9-10 hours
Eval (step 400) eval_loss 0.5615 · token_acc 85.79% · within striking range of 70B
Quantization   Q4_K_M for HACKER-PRO deployment (~4 GB on disk · 16K ctx feasible)
                BF16 for datacenter batch (~16 GB)
Defendable     issuer swarmandbee.eth · category bookmaker.defendable.eth
                compares_to atlas.defendable.eth (apples-to-apples corpus + recipe)
```

**What it does.** Renders OMs. Drafts pitch decks and e-blasts. Computes complete rent
ladders. Does the Bookmaker (Gigi) work. Stronger reasoning than the 3B for Bookmaker-class
deliverables that need narrative depth and cross-section coherence.

**Where it runs.** HACKER-PRO ($599) for senior desks · family office · institutional buyers.
Also runs in the datacenter as the Bookmaker batch service for OM production at volume.

---

## Hack-Deed-Maker-3B · the desk-edge underwriter

```
Base model     ibm-granite/granite-4.1-3b
Base license   Apache 2.0
Architecture   Dense decoder · 40 layers · 2560 hidden · GQA 40:8 · SwiGLU ·
                tied embeddings · 128K ctx · BF16
Cook recipe   Gold Standard mirrored from Atlas-70B (see recipes/hack-deed-maker-3b.yml)
                Same hyperparameters · single-GPU bf16 LoRA
Training data  Royal Jelly CRE Block-0 corpus (apples-to-apples vs 8B and 70B)
Hardware       1× RTX 5090 32GB
Cook time      ~5-6 hours
Eval (step 200) eval_loss 1.102 · token_acc 75.17% · tracks within 3pts of 8B
Quantization   Q4_K_M for HACKER deployment (~2.1 GB on disk · runs on Orin Nano 8GB)
                Sustained throughput 13.5 tok/s on Jetson Orin Nano
Defendable     issuer swarmandbee.eth · category hack-deed-maker.defendable.eth
```

**What it does.** Daily underwriting. Live cap rate / DSCR / IRR sensitivity during phone
calls. LOI drafting in 30 seconds. Pre-stamps deeds. Acts as the on-desk analytical brain.

**Where it runs.** HACKER ($250 box) — every Hack desk. The smallest brain in the family
that still produces broker-grade output. Q4_K_M quantization fits comfortably alongside
Docling, Whisper, and Piper on a single 8GB Jetson.

---

## Granite-Docling-258M · the eyes

```
Model          ibm-granite/granite-docling-258M
License        Apache 2.0
Architecture   Idefics3-based · siglip2-base-patch16-512 vision encoder +
                Granite 165M language model + pixel-shuffle connector
Capabilities   Equations · code · charts · tables (OTSL) · layout · OCR · doc QA
Languages      English (primary) · Japanese · Arabic · Chinese (experimental)
Performance    TEDS 0.97 / 0.96 on FinTabNet (financial tables · the line that matters)
                OCR F1 0.84 · OCRBench 500 · Equation F1 0.968
Quantization   INT8 for HACKER deployment (~700 MB on disk)
Output         DocTags XML → markdown / JSON via docling-core
```

**What it does.** Parses any document the broker tosses over. Rent roll PDF →
tenant-by-tenant JSON. T-12 PDF → normalized income/expense. Lease PDF → structured
terms. OM PDF → DocTags + structured sections. Phase-1 ESA, title commitment,
appraisal — anything PDF-shaped.

**Where it runs.** Every HACKER tier. Always on-box. **The PDFs never leave the customer's
hardware** — Docling parses them locally, sovereign by default.

---

## The voice and ear stack

| | Model | Size | Runtime |
|---|---|---|---|
| Whisper-base (STT) | OpenAI Whisper | 74M | INT8 ~500 MB on-box |
| Piper TTS | rhasspy/piper | ~60M | ONNX runtime · ~100 MB on-box |

**Whisper transcribes** seller calls, Discord meetings, in-room recordings.
The transcript feeds the underwriter on-box. **Audio never leaves the desk.**

**Piper speaks** in broker voice when the HACKER joins a Discord channel or answers
a verbal query. Pre-trained voices, locally rendered — no cloud TTS.

---

## Future Hack-fleet (vertical specialists)

The Hack-fleet is the per-vertical specialization layer. All future Hacks cook on
Granite-4.1-8B base, with QLoRA adapters trained on vertical-specific corpora.

| Hack | Vertical | Base | Status | Corpus |
|---|---|---|---|---|
| Hack-STNL-DG | Dollar General STNL | Granite-4.1-8B | Planned · first Hack | DG-WIKI-GRAPH (74 pairs seeded · expand to 5K) |
| Hack-QSR | Quick-service restaurant | Granite-4.1-8B | Planned | TBD |
| Hack-Auto | Automotive parts (O'Reilly · AutoZone · etc) | Granite-4.1-8B | Planned | TBD |
| Hack-Entertainment | Entertainment / leisure | Granite-4.1-8B | Planned · Harvey doctrine prototype | TBD |
| Hack-Cold-Storage | Industrial cold storage | Granite-4.1-8B | Planned · Donovan's specialty | TBD |
| Hack-Medical-Office | Medical office | Granite-4.1-8B | Planned | TBD |

Each Hack is a thin LoRA adapter on top of the same Granite-4.1-8B base. The Bookmaker-8B
deployment on a HACKER-PRO can hot-swap adapters per vertical query — same hardware, many
specializations, all governed by the same Defendable receipt chain.

---

## Provenance and license summary

```
Atlas-70B base                Llama 3.3 Community License (Meta)
Bookmaker-8B base             Apache 2.0 (IBM)
Hack-Deed-Maker-3B base       Apache 2.0 (IBM)
Branch-30B base (future)      Apache 2.0 (IBM)
Granite-Docling-258M          Apache 2.0 (IBM)
Whisper                       MIT (OpenAI)
Piper TTS                     MIT (rhasspy)

Cooked LoRA adapters          PROPRIETARY — Swarm and Bee LLC
Royal Jelly CRE corpus        PROPRIETARY — Swarm and Bee LLC (see CORPUS.md)
Atlas OS infrastructure       Apache 2.0 (this repository)
```

The OS is open. The brains are proprietary. The corpus is proprietary. The receipts are public.
That's the right shape for a labor business with a sovereign-data trust claim.
