# PQC Vault

PQC Vault provides a Portable Post-Quantum Boundary wrapper for ASP-governed material.

PQC Vault wraps and unwraps ASP-governed material under post-quantum cryptographic protection.

## Relationship to ASP

PQC Vault does not define ASP behavior.

PQC Vault does not replace ASP.

PQC Vault does not compete with ASP or with existing security systems.

PQC Vault does not validate legitimacy, authorize action, assign posture, interpret system meaning, or determine handling.

Access, legitimacy, posture, signaling, escalation, and handling remain outside the scope of PQC Vault.

## Operating Principle

The purpose of PQC Vault is to preserve the Portable Post-Quantum Boundary while protected material moves through systems that have not implemented post-quantum cryptography.

Systems interacting with PQC Vault-wrapped material are not required to implement PQC in order for the boundary to remain preserved.

## Intended Use Cases

- backup wrapping
- release package wrapping
- configuration bundle wrapping
- portable recovery package wrapping
- industrial maintenance package wrapping
- CI artifact wrapping
- long-term archive wrapping
- signed evidence object wrapping

## Non-Goals

PQC Vault is not:

- a replacement for ASP
- a definition of ASP behavior
- a validation system
- an authorization system
- a posture engine
- a replacement for system authentication
- a replacement for network transport security
- a requirement for industrial controllers or constrained devices
- an offensive security tool
- a claim of certified cryptographic compliance

## Minimal CLI Contract Preview

The expected minimal CLI shape is:

```bash
pqc-vault wrap <input> --recipient <recipient-public-key> --out <artifact.pqcv>
pqc-vault unwrap <artifact.pqcv> --key <private-key> --out <output>
```

This is a contract preview only. It is not yet an implementation.

## Enterprise Build Gates

Before runtime code is added, this module should define:

1. Wrap/unwrap contract
2. Minimal boundary manifest schema
3. Threat model limited to boundary preservation
4. Key-management policy
5. Algorithm-agility policy
6. Compatibility notes
7. Recovery and break-glass procedure
8. Implementation review checklist

## Compatibility Commitment

PQC Vault must preserve the Portable Post-Quantum Boundary.

PQC Vault must remain limited to wrapping and unwrapping ASP-governed material under post-quantum cryptographic protection.

## Current Status

Draft module definition. No cryptographic implementation has been committed.
