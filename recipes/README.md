# Recipes

Cook recipes for every Atlas brain. Declarative, reproducible, anchored.

Each recipe is a **complete description** of how a model was trained:
- base model + license
- LoRA configuration
- training hyperparameters
- hardware
- corpus reference (sha256-anchored)
- Defendable issuer + category + anchor topic
- deployment target

**This is documentation, not executable.** The actual training scripts live on the
cook rigs and are not committed (paths and tokens redacted, environment-specific).
The recipes here are the *spec*; the scripts are the *implementation*.

## Files

| Recipe | Model | Box deployment |
|---|---|---|
| `atlas-70b.yml` | Atlas doctrine model · 70B dense | Datacenter · powers AIOV ephemeral sessions |
| `bookmaker-8b.yml` | Bookmaker / OS-tier reasoner · 8B dense | HACKER-PRO + datacenter batch |
| `hack-deed-maker-3b.yml` | Desk-edge underwriter · 3B dense | HACKER ($250 box) |

## Future recipes

- `branch-30b.yml` — branch-tier · runs on HACKER-AGX
- `hack-stnl-dg.yml` — first vertical Hack · Granite-4.1-8B + DG-WIKI-GRAPH adapter
- `hack-qsr.yml` · `hack-auto.yml` · `hack-cold-storage.yml` · `hack-medical-office.yml`
- `bookmaker-v2-creative.yml` — creative-only Bookmaker cook (per locked doctrine)

## Why publish recipes

Three reasons.

1. **Reproducibility for our own builders.** When we re-cook on Block-1 or Block-2,
   the recipe is the spec we lift from. Drift-proof.

2. **Auditability for customers.** A counsel inspecting an AIOV receipt can pull
   `recipe.atlas.defendable.eth/<id>`, see exactly what hyperparameters trained the
   brain that produced their value opinion, and verify the recipe sha256 matches what
   was anchored. Trust the math, not the firm.

3. **Brand alignment.** *Verified · Vetted · Virtu.* The recipes are part of what
   makes the work Defendable. Hide the corpus, hide the weights, but publish the recipe —
   that's the right shape.

## What's NOT in the recipes

- **Cook rig hostnames or IPs in raw form** (redacted to relative paths)
- **HuggingFace tokens** (env-only, never committed)
- **Internal storage paths** beyond what's needed for spec
- **Customer-specific overrides** (per-tenant Hack adapters etc · live in customer-private
  configuration, not this public repo)
