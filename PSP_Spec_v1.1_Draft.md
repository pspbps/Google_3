# PSP Specification v1.1 (Draft)

This document defines **clarifications and non-breaking enhancements**
to the Probabilistic Settlement Protocol (PSP) v1.0.

PSP v1.1 is **fully backward-compatible** with v1.0.
No changes in this document alter finalized outcomes or past commitments.

---

## Scope of v1.1

PSP v1.1 focuses on:

- Reducing integrator misuse
- Improving interoperability
- Clarifying observability and privacy tradeoffs
- Formalizing compliance expectations

PSP v1.1 does **not** mandate new trust assumptions
and does **not** introduce breaking changes.

---

## 1. Terminology Clarifications

### Invocation
A single settlement attempt bound to:
- RuleId
- Commitment
- Settlement amount
- Finalized outcome index

An invocation is **finalized exactly once**.

### Finalization
The on-chain act that permanently records:
- Outcome index
- Bound inputs
- Deterministic fee result

Finalization is irreversible.

---

## 2. PSP Compliance (Minimum Requirements)

An implementation is considered **PSP-compliant** if it satisfies:

1. Deterministic outcome recomputation from public inputs
2. Commit–reveal or equivalent pre-commitment mechanism
3. Non-retroactive governance (future-only parameter updates)
4. Public auditability of finalized outcomes
5. Explicit separation between protocol logic and application logic

---

## 3. Observability vs. Privacy Guidance

### 3.1 Invocation-Level Verifiability

PSP guarantees that each invocation can be individually verified.

The protocol does **not** require:
- Public aggregation of outcomes per rule
- Disclosure of progress toward expected distribution

---

### 3.2 Avoiding Rule-Level Leakage (Best Practices)

Integrators are encouraged to:

- Avoid exposing rule-level outcome statistics on-chain
- Avoid deterministic ordering that enables inference
- Use commitment domain separation or epochs where applicable

These are **recommendations**, not protocol requirements.

---

## 4. Interface & Event Stability Guidance

To ensure interoperability, PSP v1.1 recommends:

- Stable interfaces for core protocol contracts
- Event fields that fully encode settlement-critical data
- No reliance on off-chain hidden state for outcome computation

---

## 5. Governance & Parameter Updates

v1.1 formalizes the following governance expectations:

- All parameter updates must be timelocked
- No parameter update may affect finalized invocations
- Fee recipients should be transparent and auditable

---

## 6. Forward Compatibility

This draft intentionally preserves compatibility with
future PSP v2.0 modules, including:

- Modular randomness providers
- Optional fee enforcement modes
- Canonical deployment registries

---

## Status

- Version: Draft
- Compatibility: Backward-compatible with PSP v1.0
- Implementation impact: None required

---

**End of PSP Specification v1.1 (Draft)**
