# Trezu

## What is it?

**Trezu** is a **non-custodial, multi-chain treasury management platform** that enables teams to collaboratively manage crypto assets through a shared wallet system and collective control.

Unlike an individual wallet, in Trezu **no single member can act unilaterally**: every action requires team consensus. It is designed for organizations that need transparency, traceability, and security in the management of digital funds.

> "A treasury is a shared wallet that allows teams to securely manage crypto assets across multiple blockchains." — Trezu Docs

---

## What is it for?

Trezu solves the problem of **managing crypto funds as a team without sacrificing security or decentralization**:

- **Consolidate multi-chain assets** in a single interface (no need for separate wallets per network)
- **Require multiple approvals** before executing any transaction
- **Separate responsibilities** between who proposes payments, who approves them, and who manages configuration
- **Record and audit** every proposal, vote, and executed action
- **Delegate without losing control**: members operate within the limits of their role

### Supported operations

| Operation | Description |
|---|---|
| Single payments | Transfer tokens to an external wallet |
| Batch payments | Send funds to multiple recipients in a single proposal |
| Asset swaps | Exchange tokens across blockchains directly from the treasury |
| Staking | Propose staking of treasury assets |
| Member management | Add, remove, or modify member roles |

---

## Target users

Trezu is aimed at any **team or organization that manages crypto funds collectively**:

- **DAOs**: decentralized on-chain treasury governance
- **Web3 startups**: shared control of operational funds among co-founders
- **Crypto investment funds**: multisig oversight with role separation between analysts and approvers
- **Protocol teams**: management of reserves and contributor payments
- **Companies paying in crypto**: payment flows with internal approvals before execution

---

## Governance model and roles

Trezu implements a system of **intentionally separated roles**. Each member has their own wallet and signs independently. Roles can be combined.

### Available roles

**Requestor**
- Creates payment, staking, or swap proposals
- Can delete their own pending proposals
- **Cannot vote** or approve proposals

**Finance**
- Approves or rejects proposals created by Requestors
- Executes approved transactions
- **Cannot create proposals** or modify configuration

**Governance**
- Manages treasury configuration: members, roles, voting thresholds, voting duration
- **Cannot create financial proposals** (intentional separation of powers)
- High-risk role: recommended only for high-security wallets (e.g. hardware wallets)

> The design principle is **least privilege**: each role does exactly what it needs and nothing more.

### Permission matrix

| Action | Requestor | Finance | Governance |
|---|:---:|:---:|:---:|
| Create payment proposal | ✅ | ❌ | ❌ |
| Approve / reject proposal | ❌ | ✅ | ❌ |
| Manage members and roles | ❌ | ❌ | ✅ |
| Configure voting thresholds | ❌ | ❌ | ✅ |
| Combine with other roles | ✅ | ✅ | ✅ |

---

## Payment proposal flow

1. **Requestor** navigates to Payments, enters recipient wallet, token, and amount
2. Adds an optional comment for approvers and reviews before submitting
3. The proposal enters **pending** status and is visible to the Finance team
4. Finance members **vote** for or against during the configured period
5. Once the **approval threshold** is reached, the transaction executes automatically

> ⚠️ Payments are **irreversible**. Once submitted, a proposal cannot be edited — only deleted before being approved.

---

## Security

### Multisig model
Every transaction requires multiple members to sign with their individual wallets. No centralized key controls the funds.

### Non-custodial
Trezu does not custody assets. Funds remain under the team's control at all times.

### Configurable thresholds
The team defines how many signatures are required to approve a proposal (e.g. 3 out of 5 Finance members).

### Configurable voting duration
You can set how long a vote remains open before it expires.

### Least privilege
Roles are designed so that no one has more access than necessary. Governance cannot move funds; Finance cannot change configuration.

### Hardware wallet compatibility
Support for **Ledger** as an additional security layer for critical signers.

### Trezu-recommended best practices
- Assign Governance only to hardware wallets shared among trusted members
- Review memberships periodically
- Set voting thresholds intentionally (do not use minimum default values)
- Maintain separation of duties: do not assign Requestor + Finance to the same members

---

## Supported blockchains

Trezu supports **30+ networks**, including:

`Ethereum` · `NEAR` · `Solana` · `Bitcoin` · `Polygon` · `Sui` · `TON` · `Cardano` · `Avalanche` · `BNB Chain`

Multi-chain management allows holding assets across different networks and operating from a single interface, eliminating the need for separate wallets per blockchain.

---

## Address Book

Trezu includes an **address book** where frequently-used wallets associated with multiple blockchains can be saved. It reduces errors by avoiding manual copy/paste of addresses in every proposal.

---

## Resources

- Official documentation: https://docs.trezu.org
- Use case example: [[Trezu - DAO Use Case]]

---

## Tags

#crypto #treasury #multisig #web3 #dao #non-custodial #trezu #security #governance
