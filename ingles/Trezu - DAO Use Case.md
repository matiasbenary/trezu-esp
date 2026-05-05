# Trezu — Use Case: DeFi Protocol DAO

## Context

**NovaDeFi DAO** is a decentralized organization managing a lending protocol on NEAR and Ethereum. The team has 12 members distributed globally and manages a treasury of ~$2M in assets (NEAR, ETH, USDC).

Before Trezu, funds were controlled by a single multisig wallet managed informally, with shared access among the founders. The problem: lack of traceability, dependency on 2 people to approve everything, and no role separation.

---

## Team structure in Trezu

| Member | Role in the DAO | Role in Trezu |
|---|---|---|
| Alice (CTO) | Technical co-founder | Governance + Finance |
| Bob (CEO) | Operational co-founder | Governance |
| Carol (CFO) | Finance lead | Finance |
| Dave (Ops) | Operations | Requestor |
| Eve (Marketing) | Growth | Requestor |
| Frank (Dev) | Contributor | Requestor |

**Voting configuration:** 2 out of 3 Finance members must approve before any payment executes.
**Voting duration:** 48 hours.

---

## Scenario 1: Monthly contributor payments

### Situation
Dave (Ops) needs to process monthly payments to 8 contributors totaling 15,000 USDC on NEAR.

### Flow

```
Dave (Requestor)
  └── Creates proposal "Contributor Payments - May 2025"
        ├── Recipient 1: wallet-contributor-1.near → 2,000 USDC
        ├── Recipient 2: wallet-contributor-2.near → 1,500 USDC
        └── ... (8 payments in a single batch proposal)
              └── Adds comment: "Per spreadsheet approved in Discord"

Carol (Finance)
  └── Reviews proposal, verifies amounts against spreadsheet
        └── Votes ✅ APPROVE

Alice (Finance)
  └── Confirms with Carol, checks recipient wallets
        └── Votes ✅ APPROVE → threshold reached (2/3)

System
  └── Executes all 8 payments automatically on-chain ✅
```

**Result:** All 8 contributors receive their payments without any individual having had unilateral control. The entire process is recorded on-chain.

---

## Scenario 2: Cross-chain asset rebalancing

### Situation
The treasury has excess ETH on Ethereum and needs liquidity in NEAR for the month's operational expenses.

### Flow

```
Dave (Requestor)
  └── Creates swap proposal: 5 ETH → equivalent NEAR
        └── Comment: "Rebalancing to cover Q2 opex"

Carol + Alice (Finance)
  └── Approve the swap (2/2 within 6 hours)

Trezu
  └── Executes cross-chain swap directly from the treasury
        └── Funds available in NEAR without manually moving between wallets ✅
```

---

## Scenario 3: Onboarding a new Finance member

### Situation
The DAO votes to bring in Grace as a new Finance team member to decentralize approvals.

### Flow

```
Bob (Governance)
  └── Creates governance proposal: add Grace's wallet with Finance role

Alice (Governance)
  └── Approves the configuration change

Trezu
  └── Adds Grace as Finance
        └── Voting threshold updates to: 2 out of 4 Finance ✅
```

> ⚠️ This change is handled by Governance, completely separate from financial operations. Dave, Carol, and Eve (Requestors/Finance) have no involvement in configuration.

---

## Scenario 4: Rejected proposal

### Situation
Eve (Marketing) proposes a payment of 50,000 USDC for an influencer campaign without prior team approval.

### Flow

```
Eve (Requestor)
  └── Creates proposal: 50,000 USDC → wallet-agency.eth
        └── Comment: "Q3 campaign - see brief in Notion"

Carol (Finance)
  └── Reviews: amount was not in the approved budget
        └── Votes ❌ REJECT with comment: "Not approved in Q3 budget"

Alice (Finance)
  └── Votes ❌ REJECT

System
  └── Proposal rejected. Funds never moved. ✅
```

**Result:** The approval system acted as an internal control. The rejection is recorded with justification.

---

## Observed benefits vs. previous situation

| Aspect | Before (informal multisig) | With Trezu |
|---|---|---|
| Traceability | Manual, in spreadsheets | Automatic, on-chain |
| Approvals | 2 founders with full access | Separated roles, 2 of 3 Finance |
| Error risk | High (copy/paste wallets) | Low (Address Book + review) |
| Payment time | 2-3 days (manual coordination) | ~6-48 hours (async voting) |
| Onboarding new approvers | Complex and risky | Controlled by Governance |
| Audit trail | Nonexistent | Full on-chain record |

---

## Recommended setup for similar DAOs

```
Treasury NovaDeFi
├── Governance: 2-3 hardware wallets (Ledger)
├── Finance: 3-5 members, threshold 2/3 or 3/5
├── Requestors: all operational contributors
├── Voting duration: 24-48h (balance between agility and security)
└── Address Book: all recurring wallets pre-registered
```

---

## Tags

#trezu #dao #use-case #multisig #defi #near #governance #treasury
