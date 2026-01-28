# Probabilistic Settlement Protocol (PSP)
## Whitepaper v1.0

---

## Version & Scope Declaration

This document defines **Probabilistic Settlement Protocol (PSP) v1.0**.

This whitepaper is a **protocol-level specification**, not a business offering,
financial product, or application-layer implementation.

### Scope

PSP defines:

- Deterministic and verifiable probabilistic settlement rules
- Commit–reveal based randomness verification
- Protocol-level fee computation and non-retroactive governance constraints

PSP does **not** define:

- User interfaces
- Business logic
- Merchant policies
- Compliance, custody, or consumer protection mechanisms

Any application, platform, or service integrating PSP is solely responsible
for its own legal, regulatory, and operational compliance.

### Non-Endorsement

Use of PSP does not imply endorsement, approval, or partnership
by the PSP authors or contributors.

### Immutability of Finalized Outcomes

Once a settlement outcome is finalized under PSP rules,
it must not be altered retroactively by governance, operators, or integrators.

---

# Probabilistic Settlement Protocol (PSP)
Version 1.0

---

## Abstract

The Probabilistic Settlement Protocol (PSP) is a decentralized protocol specification for **verifiable, non-manipulable probabilistic settlement**.

PSP defines a deterministic, on-chain settlement primitive where the final settlement amount is selected from a predefined outcome distribution, using publicly verifiable randomness derived via commit–reveal mechanisms. Once finalized, settlement results are immutable and recomputable by any third party.

PSP is designed as a **protocol-level settlement primitive**, not an application, enabling integration across e-commerce, financial services, and digital marketplaces.

---

## 1. What PSP Is

PSP is:

- A **protocol**, not a platform  
- A **settlement-layer primitive**, not a product  
- A **verifiable probabilistic settlement standard**  
- Designed to be embedded into external systems  

PSP does **not** define:
- User interfaces
- Business logic
- Asset custody
- Application-specific workflows

It defines **how settlement outcomes are selected and finalized**.

---

## 2. Core Design Principles

### 2.1 Deterministic Recomputability

Given the same public inputs:
- Rule definition
- Committed randomness
- Settlement amount
- Protocol parameters

Any observer can recompute:
- Outcome index
- Final settlement amount
- Protocol fee

No trusted party is required.

---

### 2.2 Commit–Reveal Verifiability

Settlement randomness follows a commit–reveal flow:

1. A commitment hash is submitted on-chain
2. Inputs are revealed later
3. The revealed data must match the prior commitment

This prevents:
- After-the-fact manipulation
- Selective outcome bias
- Hidden randomness sources

---

### 2.3 Non-Retroactive Finality

Once a settlement is finalized:
- Outcomes cannot be changed
- Fees cannot be recalculated
- Rules cannot be retroactively modified

Protocol evolution is allowed **only for future settlements**.

> **The protocol may evolve, but it must never change past commitments.**

---

### 2.4 Minimal Trust Assumptions

PSP assumes:
- Public blockchain execution
- Transparent contract code
- No off-chain trust

PSP explicitly avoids reliance on:
- Trusted oracles
- Proprietary randomness providers
- Off-chain adjudication

---

## 3. Settlement Model

### 3.1 Rule Definition

A **Rule** defines a settlement distribution consisting of multiple **Outcomes**.

Each Outcome includes:
- A settlement behavior identifier
- A probability weight (basis points)
- A parameter field interpreted externally

All outcome weights must sum to **10,000 bps**.

---

### 3.2 Outcome Selection

Given:
- A finalized random value
- A rule's outcome distribution

The protocol deterministically maps the random value to a single outcome index using cumulative probability traversal.

This process is:
- Deterministic
- Recomputable
- Non-interactive

---

### 3.3 Settlement Amount Binding

Settlement computation binds:
- Declared settlement amount
- Selected outcome index
- Protocol fee parameters

The protocol does **not** transfer assets.  
It outputs **verifiable settlement metadata**.

---

## 4. Randomness Model

### 4.1 Why Commit–Reveal Instead of VRF

PSP intentionally uses commit–reveal rather than external VRF systems.

Rationale:
- No dependency on third-party oracle networks
- Deterministic replay without oracle availability
- Lower systemic risk and surface area
- Suitable for protocol-layer primitives

Commit–reveal is sufficient because:
- The commitment is immutable
- The reveal is publicly verifiable
- Manipulation is detectable and rejectable

---

### 4.2 Trust Properties

Commit–reveal provides:
- **Unpredictability before reveal**
- **Verifiability after reveal**
- **Non-repudiation**

It does not attempt to provide:
- Perfect cryptographic randomness
- Entropy guarantees beyond adversarial detectability

This tradeoff is intentional.

---

## 5. Fee Model

### 5.1 Protocol-Level Fees

PSP defines protocol fees as:
- A fixed basis-point rate
- Subject to a hard fee cap
- Charged deterministically at settlement finalization

Fees are computed from:
- Settlement amount
- Current fee parameters

---

### 5.2 Fee Governance

Fee parameters may be updated only via:
- Explicit proposal
- Enforced timelock delay
- Non-retroactive application

Past settlements are never affected.

---
## Protocol Fee Model
## Protocol Fee Model

The Probabilistic Settlement Protocol (PSP) defines a protocol-level fee
mechanism that is deterministically bound to settlement finalization.

PSP does not charge for randomness generation or probability evaluation.
Instead, fees are assessed only when a settlement outcome is finalized
and verifiable on-chain.

### Fee Calculation

For each finalized invocation, the protocol computes a protocol fee
based on the declared settlement amount:

feeCharged = min(amount × feeBps / 10,000, feeCap)

Where:
- `amount` is the declared settlement amount provided by the invocation
- `feeBps` is the protocol fee rate in basis points
- `feeCap` is the maximum fee limit per invocation

Both `feeBps` and `feeCap` are protocol parameters subject to governance
constraints and timelocked updates.

### Deterministic Verifiability

The protocol fee is:
- Deterministic
- Publicly recomputable
- Bound to a specific settlement outcome

Any third party can independently recompute the charged fee using
on-chain data, ensuring transparency and non-manipulability.

### Fee Recipient

Each PSP deployment specifies a `feeRecipient` address, representing
the beneficiary of protocol-level fees.

The protocol itself does not enforce asset transfer semantics. Instead,
it provides an authoritative, on-chain computation of the fee obligation,
allowing integrators to settle fees according to their execution context.

### Non-Retroactive Guarantee

Protocol fee parameters apply only to invocations finalized after the
effective update time. No finalized settlement may be retroactively
affected by parameter changes.

## 6. Governance and Upgradability

### 6.1 Parameter Evolution

The protocol allows:
- Fee rate updates
- Fee cap updates
- Fee recipient updates

Only for future settlements.

---

### 6.2 What Cannot Be Changed

The protocol **explicitly forbids**:
- Recomputing finalized outcomes
- Altering historical settlement results
- Reinterpreting committed randomness

---

## 7. Integration Model

PSP is designed to be integrated by:
- Payment processors
- Marketplaces
- Financial applications
- Digital commerce systems

Integrators are responsible for:
- Asset custody
- User interaction
- Business logic

PSP provides:
- Verifiable settlement outcomes
- Deterministic fee computation
- Public auditability

---

## 8. Security Considerations

### 8.1 Threat Model

PSP defends against:
- After-the-fact manipulation
- Selective outcome bias
- Hidden settlement logic

It does not defend against:
- Incorrect integrator usage
- Malicious front-end behavior
- Off-chain fraud

---

### 8.2 Transparency Guarantees

All settlement-critical inputs are:
- Public
- On-chain
- Deterministically interpretable

---

## 9. Conclusion

PSP defines a new class of decentralized settlement primitive:
- Probabilistic
- Verifiable
- Non-manipulable
- Deterministically auditable

It is not an application.
It is not a business model.

It is a **settlement rule protocol**.

---

**End of Document**  
Probabilistic Settlement Protocol (PSP)  
Version 1.0
