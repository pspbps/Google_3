# PSP Protocol Roadmap

This document defines the **official evolution roadmap** of the  
**Probabilistic Settlement Protocol (PSP)**.

The roadmap follows a strict principle:

> **The protocol may evolve, but it must never alter past commitments or finalized outcomes.**

All versions below are designed with explicit compatibility guarantees.

---

## Versioning Policy

- **v1.x** — Backward-compatible upgrades  
  - No breaking changes to finalized outcomes
  - Existing integrations remain valid

- **v2.0** — Breaking upgrade  
  - New canonical contracts
  - v1.x remains usable but no longer the latest standard

---

## PSP v1.0 — Protocol Definition Release (Completed)

**Status:** ✅ Released

PSP v1.0 establishes the core settlement primitive.

### Included
- Deterministic probabilistic settlement via outcome distributions
- Commit–reveal based verifiable randomness
- Invocation finalization with immutable results
- Deterministic fee computation with fee cap
- Timelocked governance for fee parameter updates
- Clear separation between protocol logic and application logic

### Explicitly Out of Scope
- Asset custody or transfer
- Business logic or application workflows
- E-commerce, listing, or marketplace semantics
- Dispute resolution or off-chain enforcement

PSP v1.0 serves as the **canonical protocol specification**.

---

## PSP v1.1 — Specification & Integration Enhancements (Planned)

**Compatibility:** Fully backward-compatible with v1.0

### Goals
Improve integrator clarity and interoperability without modifying core protocol guarantees.

### Planned Enhancements

#### 1. Specification Clarification
- Formal glossary and domain model
- Clear definition of PSP compliance requirements
- Integrator responsibility checklist

#### 2. Interface & Event Standardization
- Stable protocol interfaces (e.g. `IRuleRegistry`, `IInvocationManager`)
- Canonical event definitions for indexing and analytics
- Deterministic output schemas

#### 3. Result Privacy & Observability Controls (Optional)
- Best-practice guidance to avoid revealing rule-level progress
- Optional epoch or commitment-domain separation to reduce inference
- No protocol-level aggregation of outcome statistics

#### 4. Governance Policy Formalization
- Explicit non-retroactivity guarantees in documentation
- Recommended governance patterns (e.g. multisig fee recipients)

PSP v1.1 does **not** introduce new trust assumptions.

---

## PSP v2.0 — Modular Execution & Value Capture (Future)

**Compatibility:** Breaking upgrade (new canonical deployment)

### Goals
Enable stronger execution guarantees, optional value capture enforcement,
and modular randomness sources while preserving auditability.

### Planned Modules

#### 1. Modular Randomness Providers
- Pluggable randomness interface
- Support for:
  - Commit–reveal (default / fallback)
  - External VRF providers
  - Chain-native randomness (where applicable)

All randomness sources must remain publicly verifiable and auditable.

---

#### 2. Fee Capture Modes

Two standardized fee modes may coexist:

- **Soft Enforcement**
  - Protocol emits verifiable fee quotes
  - Applications execute transfers externally
  - Lowest integration friction

- **Hard Enforcement**
  - Protocol-level escrow or allowance-based fee collection
  - Stronger guarantees, higher integration requirements

Applications may declare supported fee modes.

---

#### 3. Standard Invocation Manager
- Canonical execution-layer component
- Responsible for:
  - Asset handling
  - Invocation orchestration
  - Settlement execution
- Keeps core protocol contracts minimal and composable

---

#### 4. Canonical Registry & Ecosystem Signaling
- Registry of canonical PSP deployments
- Versioned contract address registry
- “PSP-compliant” signaling for integrations and tooling

---

## Long-Term Vision

PSP aims to become a **settlement-layer primitive**
that can be safely embedded into diverse real-world systems,
while maintaining strict guarantees:

- Verifiability over trust
- Determinism over discretion
- Evolution without retroactive modification

---

**End of Roadmap**
