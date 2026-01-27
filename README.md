# Probabilistic Settlement Protocol (PSP)

This repository contains the **official specification and whitepaper**
for the **Probabilistic Settlement Protocol (PSP)**.

PSP is a decentralized protocol for **verifiable, non-manipulable probabilistic settlement**
designed for real-world commerce and financial workflows.

---

## 📄 Whitepaper

- **PSP Whitepaper v1.0**  
  👉 [`whitepaper/PSP_Whitepaper_v1.0.md`](whitepaper/PSP_Whitepaper_v1.0.md)

---

## 🧭 Specification & Drafts

- **PSP Specification v1.1 (Draft)**  
  Clarifications and non-breaking enhancements to v1.0.  
  👉 [`PSP_Spec_v1.1_Draft.md`](PSP_Spec_v1.1_Draft.md)

> Draft documents do not modify or override finalized protocol rules.


## What is PSP?

PSP is:

- A **protocol**, not a platform
- A **settlement-layer primitive**, not an application
- A **verifiable probabilistic settlement standard**
- Designed to be embedded into e-commerce, financial, and service systems

Settlement outcomes (e.g. full settlement, zero settlement, proportional settlement)
are determined by deterministic on-chain logic combined with verifiable randomness.

---

## Core Properties

- **Commit–Reveal Verifiability**  
  Settlement inputs are committed before outcome revelation, preventing after-the-fact manipulation.

- **Deterministic Recomputation**  
  Any third party can independently recompute settlement outcomes and protocol fees from public inputs.

- **Non-Retroactive Governance**  
  Protocol parameters may evolve only via timelocked governance and never affect finalized settlements.

- **Protocol-Level Fee Model**  
  Fees are computed deterministically and bound to settlement finalization.

---

## Repository Scope

This repository contains:

- Protocol definition
- Formal whitepaper
- Design rationale

Reference implementations and deployments live in separate repositories.

---

## Status

- Whitepaper: **v1.0 (published)**
- Specification: **stable**
- Reference implementation: **in progress**
