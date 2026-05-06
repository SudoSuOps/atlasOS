# Personas

## The subdomain comes with the box

When you buy a HACKER, you don't just get hardware. You get a seat on the network.

```
HACKER ($250)        ── ships with ──   <name>.atlasos.eth     (one subdomain · one wallet)
HACKER-PRO ($599)    ── ships with ──   <client>.atlasos.eth   (one subdomain · one wallet)
HACKER-AGX ($2,000)  ── ships with ──   <entity>.atlasos.eth   (one subdomain · one wallet)
```

The ENS subdomain is your **identity on the AtlasOS network** and your **confidentiality
boundary**. No subdomain, no node. Every box has its own.

That's not bundled marketing. It's how the network knows who is talking.

---

## Why the ENS subdomain matters

It does four things:

**1 · Identity.** Other HACKERs resolve `<name>.atlasos.eth` to a wallet address. When
your HACKER ships an LOI, the network verifies the signature against your subdomain's
wallet. There's no impersonating you on this network.

**2 · Endpoint discovery.** Your subdomain also resolves to your live HACKER endpoint
(or the gateway that proxies it). When `rainmaker.atlasos.eth` matches inventory to your
1031 timeline, it routes the response to *your* box, not a cloud mailbox.

**3 · Confidentiality boundary.** Every NDA, OM, AIOV, and LOI is encrypted to your
wallet. Your subdomain is the public key that unlocks them. Without your wallet, no one
else — not even Atlas-70B, not even Swarm and Bee LLC — can decrypt your deals.

**4 · Cross-firm portability.** A receipt at `om.defendable.eth/<hash>` carries the
issuer subdomain in its parent_anchors. Counsel at any firm, in any state, in any
country, resolves the chain in 30 seconds. No login. No platform onboarding.

---

## Subdomain naming patterns

```
Brokerage Hack desk        harvey.atlasos.eth
                           alec.atlasos.eth
                           (first name · matches the human Hack)

Brokerage firm (HQ)        ackermangroup.atlasos.eth
                           northwood.atlasos.eth
                           (firm name · for HACKER-AGX deployments)

Family office              acmecapital.atlasos.eth
                           lakeshorefamily.atlasos.eth
                           (firm name · matches the LP/family)

Sponsor / seller           kerco.atlasos.eth
                           prizm.atlasos.eth
                           (sponsor name · for direct listings)

Service personas           rainmaker.atlasos.eth
                           aiov.atlasos.eth
                           atlas70b.atlasos.eth
                           gigi.atlasos.eth
                           (network-resident services · provisioned by Atlas)

Vertical Rainmakers        rainmaker.stnl.atlasos.eth
                           rainmaker.industrial.atlasos.eth
                           rainmaker.coldstorage.atlasos.eth
                           (vertical-specific matchmakers)
```

---

## The wallet pairing

Every subdomain resolves to a deterministically generated wallet at provisioning.
The HACKER's secure element holds the private key; the public key is the ENS resolver
target.

```
Provisioning flow:
  1. Customer orders HACKER (or PRO / AGX)
  2. Customer chooses a subdomain at checkout (subject to availability)
  3. Box ships pre-flashed with AtlasOS
  4. Customer powers on · enters seed phrase or generates new wallet
  5. ENS subdomain registered to the new wallet
  6. Box now has a network identity · ready to ship and verify receipts
```

The seed phrase never leaves the box during the initial generation flow. Customer
can choose to back it up to their own cold storage — that's their call, not ours.

---

## Subdomain tiers and pricing

```
Standard subdomain (any first name · firm name · service name)    $0 · bundled with box
Two-word subdomain (e.g., midtown-cre.atlasos.eth)                $0 · bundled with box
Premium one-word (e.g., harvey.atlasos.eth · alec.atlasos.eth)    $0 · first-come basis
Reserved one-word (specific names: jpmorgan, blackstone, etc)     priced per request
Multi-tenant office (5+ subdomains for one firm)                  bulk discount available
```

Donovan's reference subdomains (`harvey · alec · aj`) are reserved internally as
**operating personas** — they're the Hack roster the firm trains its people against.
They're not for sale; they're the lineage.

---

## The confidentiality claim made plain

When we say *"we can't see your deal even if we wanted to,"* this is what makes that
true at the architecture level:

```
1. The OM, NDA, LOI, AIOV report — all encrypted to YOUR subdomain's wallet
2. Atlas-70B (the doctrine model) gets a one-time session key per request
3. Atlas-70B runs in an ephemeral container · destroys the session key on completion
4. Hedera anchors metadata only (timestamps · sizes · attestation)
5. Your HACKER decrypts results locally with your wallet
6. We never hold a key that decrypts your deal · ever
```

The subdomain is the front of this whole structure. **Without your subdomain's wallet,
no piece of Swarm and Bee LLC infrastructure can read your deal.**

That's the confidentiality model. It's structural, not contractual.

---

## What happens if you sell your box

The subdomain stays with the box (or transfers to a new wallet at the new owner's
choosing). HACKER provisioning records are anchored at `provisioning.atlasos.eth`,
so chain of custody is auditable.

If the box is lost or destroyed, the subdomain can be re-bound to a new wallet only
if the customer has retained the seed phrase. **This is the customer's responsibility —
sovereign data also means sovereign key management.** We can't reset what we don't hold.

---

## What happens if you stop being a customer

Nothing. Your box keeps working. Your subdomain stays bound. Past receipts at
`<type>.defendable.eth/<hash>` remain verifiable forever — they're on Hedera.

Subscription products (AIOV, Rainmaker matching) lapse on non-renewal, but the box
itself is yours, the OS is yours, and the cooked weights you have are yours. We don't
brick boxes. The customer relationship is term-bounded; the property rights aren't.

That's the non-extractive part of the model. Once you've bought the box and earned
your receipts, those don't go away when the contract does.
