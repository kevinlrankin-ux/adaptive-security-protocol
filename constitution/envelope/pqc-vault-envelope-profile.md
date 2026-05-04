# PQC Vault Envelope Profile

## Status

Draft constitutional envelope profile for ASP.

This document adds a post-quantum-capable envelope profile to the Adaptive Security Protocol (ASP) without changing ASP core semantics.

## Evidence Boundary

This profile is based only on the current ASP repository structure and stated repo identity:

- ASP is a protocol, not a program.
- ASP defines non-removable invariants, constrained handling posture, bounded escalation logic, and governance rules for behavior under pressure.
- ASP already places Envelope, Stamp, Label / Validator, and OH-01 in the constitution layer.
- Existing ASP systems must remain unaffected by documentation and structure passes unless explicitly changed.

No runtime cryptographic implementation is introduced by this document.

## Purpose

PQC Vault is an optional ASP envelope profile for protecting portable artifacts that may move through systems that have not implemented post-quantum cryptography.

Examples of artifacts include:

- backups
- configuration bundles
- release packages
- industrial-control update packages
- signed manifests
- archived evidence objects
- system state exports

## Core Rule

PQC Vault MUST NOT become a hard dependency of ASP core.

Absence of PQC capability MUST NOT collapse ASP operation.

PQC envelopes MAY strengthen validation where post-quantum verification is available.

Where PQC verification is unavailable, ASP MUST continue to operate using its existing posture, label, validator, escalation, and safe-degradation logic.

## Design Position

PQC Vault is:

- an ASP-compatible envelope profile
- an artifact-protection boundary
- a portable package format
- an optional validation-strengthening mechanism

PQC Vault is not:

- a replacement for ASP
- a replacement for TLS, OAuth/OIDC, Zero Trust, or edge defenses
- a requirement for industrial or constrained-system operation
- a mandate that all local systems implement PQC
- an offensive security tool

## Boundary Model

The system carrying the artifact does not need to understand PQC.

Only the envelope creator and envelope verifier need PQC capability.

```text
legacy system / file share / historian / backup target / CI artifact store
        receives, stores, copies, or transmits
                    artifact.pqcv
```

The PQC-aware boundary performs:

```text
wrap -> store/transport -> inspect -> verify -> unwrap
```

## Envelope Classes

ASP may recognize multiple envelope profiles:

1. Baseline envelope
   - structural manifest
   - labels
   - validator expectations
   - no required cryptographic enhancement

2. Classical cryptographic envelope
   - conventional encryption and/or signatures
   - useful where PQC is unavailable

3. PQC Vault envelope
   - post-quantum-capable key wrapping and/or signatures
   - portable through non-PQC infrastructure

## Required PQC Vault Properties

A PQC Vault envelope MUST define:

- profile version
- envelope type
- payload type
- payload digest
- encryption status
- key-wrapping method
- signature status
- signer identity reference or key identifier
- validation posture
- creation timestamp
- declared unwrap requirements
- failure posture

A PQC Vault envelope MUST NOT expose plaintext payload contents in the manifest.

A PQC Vault envelope SHOULD support detached inspection so that a system can determine posture without unwrapping the payload.

## Validation Outcomes

A PQC Vault validator SHOULD return one of the following outcomes:

- valid
- invalid
- unsupported-profile
- unsupported-algorithm
- missing-key
- expired-policy
- ambiguous
- tampered
- malformed

These outcomes are inputs to ASP posture handling. They are not automatic authorization decisions.

## Runtime Posture Mapping

Suggested mapping:

```text
valid                 -> continuity
unsupported-profile   -> signal + bounded friction
unsupported-algorithm -> signal + bounded friction
missing-key           -> signal + bounded friction
ambiguous             -> signal + bounded friction
invalid               -> reject or quarantine
malformed             -> reject or quarantine
tampered              -> reject or quarantine
```

This mapping MAY be adjusted by domain-specific ASP policy.

## Industrial / Constrained-System Compatibility

PQC Vault MUST support boundary deployment.

For industrial motor controls, PLC-adjacent workflows, SCADA-adjacent workflows, historians, maintenance laptops, and constrained systems:

- the constrained device SHOULD NOT be required to perform PQC operations
- PQC operations MAY be performed by an engineering workstation, gateway, build server, verifier station, or recovery workstation
- the artifact may pass through non-PQC systems as opaque data
- failure to verify PQC MUST NOT imply failure of ASP core

## Security Notes

This profile defines an architecture and contract. It does not claim security of any specific implementation.

Implementation security depends on:

- vetted cryptographic libraries
- safe key generation
- safe key storage
- side-channel considerations
- algorithm agility
- deterministic manifest canonicalization
- test vectors
- reproducible validation behavior
- secure deletion policy where applicable
- recovery procedure discipline

## Non-Goals

This profile does not define:

- a complete cryptographic file format
- a production key-management system
- a certification claim
- a guarantee of regulatory compliance
- a mandate to modify existing industrial controllers

## Enterprise Acceptance Criteria

Before this profile is considered implementation-ready, the repository SHOULD include:

- CLI contract
- manifest schema
- test vector format
- threat model
- key-management notes
- algorithm-agility policy
- compatibility matrix
- recovery procedure
- validation failure matrix
- implementation review checklist

## Constitutional Invariant

PQC strengthens ASP at the artifact boundary; it must not burden ASP core.
