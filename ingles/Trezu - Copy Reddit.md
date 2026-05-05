# Trezu — Reddit Copy

---

## Post 1: r/web3 / r/CryptoCurrency — General introduction

**Title:** We built a cross-chain multisig treasury for teams

---

Managing shared crypto funds in a team is still a mess.

Most teams end up with one of these setups:
- One person holds the keys and everyone just... trusts them
- A basic multisig where approvals are coordinated through DMs and ignored messages
- Spreadsheets tracking who approved what, manually

We built **Trezu** to fix this. It's a non-custodial treasury platform that lets teams manage crypto across 30+ blockchains with role separation and on-chain traceability.

**How it works:**
- **Requestors** propose payments or swaps — they can't approve their own requests
- **Finance** votes to approve or reject — they can't touch treasury configuration
- **Governance** manages members and voting rules — they can't move funds

Every action requires collective approval. Nothing executes until the configured threshold is met.

We support Ethereum, NEAR, Solana, Bitcoin, Polygon, Sui, TON, Cardano and more — all from a single interface. Cross-chain swaps included.

If you're running a DAO, a Web3 startup, or any team managing shared crypto funds — we'd love your feedback.

👉 https://docs.trezu.org

---

## Post 2: r/ethereum / r/nearprotocol — Technical

**Title:** We built a role-based multisig treasury with cross-chain support — here's how the permission model works

---

What's missing from most multisig setups is **role separation**.

Standard multisig: N-of-M signers. Anyone can propose, anyone can approve. Fine for personal use, but in teams it creates problems: no traceability, no separation of duties, easy to bypass informally.

**Trezu** solves it like this:

```
Requestor  → can propose payments/swaps, cannot vote
Finance    → can approve/reject proposals, cannot create them
Governance → controls configuration (members, thresholds, duration), cannot move funds
```

Roles are additive — they can be combined. But the separation is intentional: whoever requests a payment is never the one who approves it (unless you consciously combine roles).

On the technical side:
- Non-custodial — funds remain on-chain under team control
- Configurable voting thresholds (e.g. 3 of 5 Finance members)
- Configurable voting duration
- Ledger support for critical signers
- Address book for frequent recipients (reduces copy/paste errors)
- 30+ chains: Ethereum, NEAR, Solana, Bitcoin, Polygon, Sui

We're in the documentation phase and gathering feedback from DAOs and Web3 teams. Happy to answer technical questions.

👉 https://docs.trezu.org

---

## Post 3: r/DAO — Use case

**Title:** How to structure a DAO treasury with real role separation (using Trezu)

---

Most DAOs I've seen have one of two problems:

1. Treasury controlled by 2-3 founders with full access — single point of failure and trust
2. Full on-chain governance for every payment — so slow that operations grind to a halt

Here's a middle ground that works well:

**Team structure:**
- 2-3 Governance wallets on hardware (Ledger) — rarely used, only for configuration changes
- 3-5 Finance members for approvals — threshold at 2/3 or 3/5
- All operational contributors as Requestors — they propose, Finance approves

**Day-to-day flow:**
1. An ops contributor submits a payment proposal with a comment/justification
2. Finance reviews asynchronously (voting window: 24-48h)
3. If threshold is met → executes automatically on-chain
4. If rejected → funds never move, rejection is recorded with reason

**What you gain:**
- Full audit trail on-chain
- No single person can move funds unilaterally
- Governance changes (adding members, changing thresholds) are separate from financial operations
- Cross-chain ops from one interface — no juggling wallets per chain

We're building this with [Trezu](https://docs.trezu.org). Still early, happy to hear how others are structuring their treasury ops.

---

## Post 4: r/CryptoCurrency — Community

**Title:** How our team stopped relying on one person to move crypto funds

---

We work on a Web3 project and for a long time we had a problem I think many teams share: the project's funds sat in a wallet managed by 2 people. No records, no traceability, and the frustration that if either of them was unavailable, nothing could be moved.

We tried different solutions until we found **Trezu**, a non-custodial multisig treasury platform that lets you manage team funds with separated roles.

The key difference from a standard multisig:

- There are distinct roles for whoever **proposes** a payment and whoever **approves** it
- Whoever manages configuration (adding members, changing rules) **cannot move funds**
- Everything is recorded on-chain: who proposed, who approved, when it executed

For us it was a significant change. Now any team member can propose a payment, but it always requires at least 2 of the 3 financial approvers to sign off before anything executes.

Works across 30+ blockchains (NEAR, Ethereum, Solana, Bitcoin, and more) with built-in cross-chain swaps.

If you're managing funds as a team and still doing it with a single wallet or basic multisig, it's worth a look.

👉 https://docs.trezu.org

---

## Suggested tags per post

- Post 1: `web3` `crypto` `multisig` `dao` `treasury`
- Post 2: `ethereum` `near` `defi` `security` `multisig`
- Post 3: `dao` `governance` `treasury` `web3` `crypto`
- Post 4: `crypto` `bitcoin` `ethereum` `web3` `finance`
