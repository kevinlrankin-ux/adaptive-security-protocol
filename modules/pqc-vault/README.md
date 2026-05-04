# PQC Vault

PQC Vault is an ASP-compatible module for wrapping portable artifacts in a post-quantum-capable envelope.

It is designed to protect files, backups, configuration bundles, manifests, and other packages as they move through infrastructure that may not itself implement post-quantum cryptography.

## Relationship to ASP

ASP remains protocol-first.

PQC Vault does not replace ASP, modify ASP core semantics, or require all ASP systems to implement PQC.

PQC Vault provides an optional envelope profile that can strengthen validation at artifact boundaries.

## Operating Principle

The artifact can be post-quantum protected even when the surrounding system is not.

```text
producer / verifier: PQC-aware
transport / storage: may be non-PQC
payload: protected by envelope
```

## Intended Use Cases

- backup wrapping
- release package sealing
- configuration bundle protection
- portable recovery packages
- industrial maintenance package verification
- CI artifact protection
- long-term archive sealing
- signed evidence object transport

## Non-Goals

PQC Vault is not:

- a replacement for ASP
- a replacement for system authentication
- a replacement for network transport security
- a requirement for industrial controllers or constrained devices
- an offensive security tool
- a claim of certified cryptographic compliance

## CLI Contract Preview

The expected CLI shape is:

```bash
pqc-vault wrap <input> --recipient <recipient-public-key> --out <artifact.pqcv>
pqc-vault unwrap <artifact.pqcv> --key <private-key> --out <output>
pqc-vault inspect <artifact.pqcv>
pqc-vault verify <artifact.pqcv> --trust <trust-policy>
pqc-vault sign <input> --key <signing-key> --out <signed-artifact.pqcv>
pqc-vault rotate <artifact.pqcv> --recipient <new-recipient-public-key> --out <rotated.pqcv>
```

This is a contract preview only. It is not yet an implementation.

## Enterprise Build Gates

Before runtime code is added, this module should define:

1. Threat model
2. Envelope manifest schema
3. CLI contract
4. Test vector format
5. Key-management policy
6. Algorithm-agility policy
7. Compatibility matrix
8. Recovery and break-glass procedure
9. Validation failure matrix
10. Implementation review checklist

## Compatibility Commitment

PQC Vault must preserve ASP compatibility with non-PQC systems.

A non-PQC system may store, copy, transmit, archive, or route a `.pqcv` artifact without understanding its contents.

PQC operations should occur at producer, verifier, gateway, archive, build, recovery, or operator-workstation boundaries.

## Current Status

Draft module definition. No cryptographic implementation has been committed.
