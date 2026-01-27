# PSP Compliance Checklist (v1.1)

This checklist defines the **minimum requirements** for an implementation
to be considered **PSP-compliant**.

This document is **non-normative** and does not modify the PSP v1.0 protocol rules.
It exists to reduce integrator misuse and ambiguity.

---

## A. Mandatory Requirements (All Must Be Satisfied)

An implementation **MUST** satisfy all items below.

### A1. Deterministic Outcome Recomputation
- Settlement outcomes can be recomputed from public on-chain inputs
- No hidden or off-chain state is required to verify results

### A2. Pre-Commitment of Randomness
- A commit–reveal or equivalent pre-commitment mechanism is used
- Outcome-affecting randomness cannot be chosen after inputs are known

### A3. Single Finalization
- Each invocation is finalized exactly once
- Re-finalization or mutation of finalized results is impossible

### A4. Non-Retroactive Governance
- Parameter updates affect only future invocations
- Past finalized outcomes are never modified

### A5. Public Auditability
- All settlement-critical inputs and outputs are publicly observable
- Any third party can independently verify correctness

---

## B. Explicit Non-Requirements (Not Required for Compliance)

An implementation is **NOT required** to:

- Transfer assets on-chain
- Provide user interfaces or frontends
- Expose aggregate statistics per rule
- Implement dispute resolution
- Use a specific randomness provider (e.g. VRF)

---

## C. Prohibited Practices (Non-Compliant)

The following practices are **explicitly non-compliant**:

- Selecting or biasing outcomes after commitment
- Retroactively modifying settlement results
- Hiding settlement-critical logic off-chain
- Reinterpreting finalized outcomes via governance

---

## D. Recommended Best Practices (Optional)

The following practices are **recommended but optional**:

- Avoid exposing rule-level outcome aggregates
- Use domain separation or epochs to reduce inference
- Clearly disclose fee computation to integrators
- Separate protocol logic from application logic

---

## E. Compliance Declaration

Integrators may declare compliance by stating:

> “This system implements the Probabilistic Settlement Protocol (PSP) v1.0
> and satisfies the PSP Compliance Checklist v1.1.”

Such declarations are informational and non-binding.

---

**End of PSP Compliance Checklist v1.1**

