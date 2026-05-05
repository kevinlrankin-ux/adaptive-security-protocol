# PQC Vault Envelope Profile

## Status

Draft constitutional envelope profile for ASP.

This document defines PQC Vault only as a Portable Post-Quantum Boundary wrapper for ASP-governed material.

No runtime cryptographic implementation is introduced by this document.

## Evidence Boundary

This profile is based only on the current ASP repository structure and stated repo identity:

- ASP is a protocol, not a program.
- ASP already places Envelope, Stamp, Label / Validator, and OH-01 in the constitution layer.
- Existing ASP systems must remain unaffected by documentation and structure passes unless explicitly changed.

This document does not define ASP behavior.

## Purpose

PQC Vault wraps and unwraps ASP-governed material under post-quantum cryptographic protection.

The purpose of the wrapper is to preserve the Portable Post-Quantum Boundary while protected material moves through systems that have not implemented post-quantum cryptography.

Examples of wrapped material include:

- backups
- configuration bundles
- release packages
- industrial-control update packages
- signed manifests
- archived evidence objects
- system state exports

## Scope

PQC Vault is limited to wrapping and unwrapping ASP-governed material under post-quantum cryptographic protection.

PQC Vault does not:

- define ASP behavior
- replace ASP
- compete with ASP
- replace or compete with existing security systems
- validate legitimacy
- authorize action
- assign posture
- interpret system meaning
- determine handling
- require all systems carrying wrapped material to implement PQC

## Portable Post-Quantum Boundary

PQC Vault provides a Portable Post-Quantum Boundary wrapper for ASP-governed material.

PQC Vault does not define ASP behavior.

PQC Vault does not replace ASP.

PQC Vault does not compete with existing security systems.

PQC Vault does not validate legitimacy, authorize action, assign posture, interpret system meaning, or determine handling.

PQC Vault wraps and unwraps ASP-governed material using post-quantum cryptographic protection.

The purpose of the wrapper is to preserve the Portable Post-Quantum Boundary while the protected material moves through systems that have not implemented post-quantum cryptography.

Systems interacting with PQC Vault-wrapped material are not required to implement PQC in order for the boundary to remain preserved.

Access, legitimacy, posture, signaling, escalation, and handling remain outside the scope of PQC Vault.

## Boundary Preservation

PQC Vault-wrapped material must preserve the Portable Post-Quantum Boundary until an authorized unwrap operation occurs.

This profile does not prescribe carrier-system behavior beyond preserving the Portable Post-Quantum Boundary.

## Non-Goals

This profile does not define:

- ASP behavior
- ASP validation
- ASP posture
- ASP signaling
- a complete cryptographic file format
- a production key-management system
- a certification claim
- a guarantee of regulatory compliance
- a mandate to modify existing industrial controllers

## Enterprise Acceptance Criteria

Before this profile is considered implementation-ready, the repository SHOULD include:

- wrap/unwrap contract
- minimal boundary manifest schema
- threat model limited to boundary preservation
- key-management notes
- algorithm-agility policy
- compatibility notes
- recovery procedure
- implementation review checklist

## Constitutional Invariant

PQC Vault MUST preserve the Portable Post-Quantum Boundary.

PQC Vault MUST NOT define, replace, or compete with ASP behavior.

PQC Vault MUST remain limited to wrapping and unwrapping ASP-governed material under post-quantum cryptographic protection.
