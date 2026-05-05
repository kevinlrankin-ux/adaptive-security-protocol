# Adaptive Security Protocol (ASP)

**Protocol-level security governance for cost asymmetry, bounded defender work, and safe degradation under stress.**

ASP is a **protocol**, not a program.

It defines:
- non-removable invariants
- constrained handling posture
- bounded escalation logic
- governance rules for behavior under pressure

ASP complements existing security systems by governing **how systems behave under stress**, even when actors or requests are otherwise structurally valid.

---

## What ASP Is

- A protocol-first security governance system
- A boundary and handling discipline for adversarial or uncertain conditions
- A framework for preserving continuity while increasing friction on unverified or unattested actors
- A concept that may be expressed through constitutional and runtime mechanisms

## What ASP Is Not

- Not an authentication product
- Not a surveillance layer
- Not a drop-in plugin
- Not an offensive toolkit
- Not a replacement for TLS, OAuth/OIDC, Zero Trust, or edge defenses

---

## Core Principle

Unverified or unattested actors experience higher friction, while continuity-verified actors experience near-zero overhead.

---

## Layering

ASP has three layers:

1. **Concept**
   - identity
   - invariants
   - governance boundary
   - escalation posture

2. **Constitution**
   - Envelope
   - Stamp
   - Label / Validator
   - OH-01

3. **Runtime**
   - legitimacy
   - degradation
   - signaling
   - friction escalation

**Important:** constitutional and runtime mechanisms express ASP operationally, but they do not replace ASP's conceptual authority.

---

## Runtime Posture

ASP governs runtime handling posture when actor legitimacy cannot be immediately established.

ASP does not collapse uncertain conditions into binary acceptance or refusal.
Instead, it signals handling posture and applies bounded friction while preserving system continuity.

verified   → continuity  
unverified → friction & signal  
uncertain  → signal & friction  
never      → silent failure

When actors cannot be verified or attested, ASP does not allow silent failure.

---

## Compatibility Note

This realignment restores conceptual authority at the repository root.
It does **not** alter the operational semantics of:
- Envelope
- Stamp
- Label / Validator
- OH-01

Existing systems using those operational constructs should remain unaffected by this documentation and structure pass.

---

## Repository Structure

- `concept/` - protocol identity, invariants, governance, escalation
- `constitution/` - operational constitutional mechanisms
- `runtime/` - handling posture, signaling, degradation, friction
- `modules/asp/` - module/pointer surface where applicable

---

## Status

ASP is a protocol-first repository.
Mechanism documents express the protocol; they do not replace it.
