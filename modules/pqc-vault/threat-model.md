# PQC Vault Threat Model

## Status

Draft threat model. This document is limited to threats against the Portable Post-Quantum Boundary wrapper.

It does not claim that any implementation currently satisfies these requirements.

## Scope

This threat model covers PQC Vault only as a wrapper and unwrapper for ASP-governed material.

In scope:

- confidentiality of wrapped material
- integrity of the Portable Post-Quantum Boundary
- key wrapping
- authorized unwrap
- preservation of the Portable Post-Quantum Boundary across non-PQC systems

Out of scope:

- ASP behavior
- ASP validation
- ASP posture
- ASP signaling
- ASP authorization
- system authentication
- network transport security
- full enterprise key-management implementation
- hardware security module integration
- regulatory certification
- device firmware security
- user identity lifecycle management

## Assets

Protected assets include:

- wrapped material
- recovered plaintext material
- payload encryption key
- recipient private keys
- boundary metadata required for wrap and unwrap

## Threats

### Boundary Disclosure

An attacker obtains the wrapped artifact and attempts to recover protected material.

Required controls:

- post-quantum cryptographic wrapping where required
- safe key wrapping
- no plaintext leakage in metadata or logs
- careful output handling during unwrap

### Boundary Mutation

An attacker modifies the wrapped artifact.

Required controls:

- boundary integrity protection
- refusal to unwrap when boundary integrity cannot be established by the implementation
- no silent recovery from altered boundary material

### Key Substitution

An attacker causes material to be wrapped for the wrong recipient or unwrapped with unauthorized key material.

Required controls:

- explicit recipient key handling
- key provenance documentation
- safe key-storage policy before production implementation

### Downgrade

An attacker attempts to force non-PQC or weaker protection while representing the artifact as PQC Vault-wrapped.

Required controls:

- explicit boundary format version
- algorithm-agility policy before production implementation
- refusal to represent weaker wrapping as a preserved Portable Post-Quantum Boundary

### Unsafe Unwrap

A wrapped artifact is opened into an unsafe output location or overwrites existing material.

Required controls:

- safe output defaults
- no overwrite unless explicit
- clear operator intent for unwrap destination

## Non-Claims

PQC Vault does not define ASP behavior.

PQC Vault does not validate legitimacy, authorize action, assign posture, interpret system meaning, or determine handling.

This document does not claim resistance to every attack.

This document establishes the minimum threat surface for preserving the Portable Post-Quantum Boundary while wrapping and unwrapping ASP-governed material.
