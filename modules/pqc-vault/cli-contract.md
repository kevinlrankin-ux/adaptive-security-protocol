# PQC Vault CLI Contract

## Status

Draft contract. This document defines intended command behavior before implementation.

No command described here should be treated as implemented until runtime code and tests exist.

## Scope

The PQC Vault CLI is limited to wrapping and unwrapping ASP-governed material under post-quantum cryptographic protection.

The CLI does not define ASP behavior, validate legitimacy, authorize action, assign posture, interpret system meaning, or determine handling.

## Design Goals

The CLI should be:

- deterministic
- scriptable
- explicit about failure
- safe by default
- suitable for CI and operator workflows
- limited to preserving the Portable Post-Quantum Boundary
- independent from ASP core behavior

## Command Principles

Every command MUST:

- return a stable exit code
- avoid silent failure
- preserve original payloads unless explicitly instructed otherwise
- avoid exposing plaintext in logs
- avoid defining ASP posture or legitimacy outcomes

## Commands

### wrap

Wrap ASP-governed material inside a Portable Post-Quantum Boundary.

```bash
pqc-vault wrap <input> --recipient <recipient-public-key> --out <artifact.pqcv>
```

Minimum behavior:

- read input material
- protect input material under post-quantum cryptographic wrapping
- write wrapped artifact
- avoid changing ASP meaning, posture, legitimacy, or handling semantics

### unwrap

Recover ASP-governed material from a Portable Post-Quantum Boundary.

```bash
pqc-vault unwrap <artifact.pqcv> --key <private-key> --out <output>
```

Minimum behavior:

- read wrapped artifact
- open the Portable Post-Quantum Boundary using authorized key material
- write recovered material
- avoid assigning ASP meaning, posture, legitimacy, or handling semantics

## Exit Codes

Suggested exit codes:

| Code | Meaning |
|---:|---|
| 0 | success |
| 1 | general failure |
| 2 | invalid arguments |
| 3 | unable to read input |
| 4 | unable to wrap |
| 5 | unable to unwrap |
| 6 | missing key material |
| 7 | unsupported cryptographic capability |
| 8 | unsafe output target |
| 9 | internal implementation error |

## Safety Requirements

The CLI MUST NOT:

- overwrite files unless explicitly allowed
- log plaintext payload material
- define ASP behavior
- assign ASP posture
- determine legitimacy
- authorize action
- expand beyond wrap and unwrap without a separate constitutional review

## Deferred Decisions

The following are intentionally not fixed in this contract yet:

- implementation language
- concrete cryptographic library
- final boundary container format
- final minimal manifest format
- key-storage backend
- certification claims
