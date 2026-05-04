# PQC Vault Threat Model

## Status

Draft threat model. This document defines security concerns for the PQC Vault module before implementation.

It does not claim that any implementation currently satisfies these requirements.

## Scope

This threat model covers a PQC Vault envelope used to wrap, transport, store, inspect, verify, and unwrap portable artifacts.

In scope:

- payload confidentiality
- payload integrity
- manifest integrity
- signature validation
- key wrapping
- recipient handling
- validation posture
- non-PQC infrastructure transit
- recovery workflows

Out of scope for this draft:

- full enterprise key-management implementation
- hardware security module integration
- regulatory certification
- device firmware security
- network authentication
- user identity lifecycle management

## Assets

Protected assets include:

- plaintext payload
- payload encryption key
- recipient private keys
- signing private keys
- trust policies
- manifest integrity
- validation results
- audit-relevant envelope metadata

## Actors

Expected actors:

- authorized producer
- authorized verifier
- authorized recipient
- recovery operator
- CI/build system
- archive or backup system
- non-PQC transport/storage system

Potential adversarial actors:

- unauthorized reader
- unauthorized modifier
- replay actor
- downgrade actor
- confused-deputy actor
- malicious insider
- compromised transport/storage system
- compromised local workstation

## Trust Boundaries

Primary trust boundaries:

1. Payload before wrapping
2. Envelope creation
3. Non-PQC transport/storage
4. Envelope inspection
5. Envelope verification
6. Envelope unwrapping
7. Restored plaintext handling

The non-PQC transport/storage environment is not trusted with plaintext.

## Threats

### Payload Disclosure

An attacker obtains the `.pqcv` artifact and attempts to recover plaintext.

Required controls:

- payload encryption when confidentiality is required
- safe key wrapping
- no plaintext leakage in manifest or logs
- careful output handling

### Payload Tampering

An attacker modifies ciphertext, manifest fields, or attached metadata.

Required controls:

- payload digest or authenticated encryption
- manifest canonicalization
- signature verification where policy requires it
- clear tamper result

### Manifest Confusion

An attacker changes envelope metadata to alter validation behavior.

Required controls:

- canonical manifest
- signed manifest or signed envelope
- strict parser
- explicit unsupported-profile and unsupported-algorithm outcomes

### Downgrade

An attacker attempts to force a weaker envelope profile or weaker algorithm.

Required controls:

- explicit profile version
- trust-policy enforcement
- algorithm-agility rules
- refusal when policy requires stronger protection

### Replay

An attacker presents an old but valid envelope as current.

Required controls:

- timestamps
- optional policy expiration
- optional artifact lineage
- optional external freshness checks

### Key Substitution

An attacker tricks a producer into wrapping for the wrong recipient or verifier into trusting the wrong signer.

Required controls:

- stable key identifiers
- trust policy
- explicit recipient display
- key provenance documentation

### Unsupported Capability Confusion

A system that cannot verify PQC treats the envelope as valid.

Required controls:

- unsupported-profile and unsupported-algorithm outcomes
- no silent success
- posture mapping through ASP

### Unsafe Restore

A valid envelope restores dangerous or misplaced content.

Required controls:

- safe output defaults
- no overwrite unless explicit
- optional destination policy
- clear user/operator intent

## ASP Posture Integration

Threat outcomes should feed ASP posture handling. Cryptographic validation is not automatic authorization.

Suggested posture examples:

- valid -> continuity
- unsupported-profile -> signal + bounded friction
- missing-key -> signal + bounded friction
- ambiguous -> signal + bounded friction
- invalid -> reject or quarantine
- tampered -> reject or quarantine
- malformed -> reject or quarantine

## Enterprise Review Questions

Before implementation, reviewers should answer:

1. What payloads are allowed?
2. What metadata may be exposed?
3. What keys are used and where are they stored?
4. What signatures are mandatory?
5. What algorithms are allowed by policy?
6. What happens when the verifier lacks PQC support?
7. What is the restore policy?
8. What audit trail is required?
9. What is the break-glass recovery process?
10. What test vectors prove compatibility?

## Non-Claims

This document does not claim resistance to every attack.

This document establishes the minimum threat surface that must be addressed before PQC Vault becomes executable software.
