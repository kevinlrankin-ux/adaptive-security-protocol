# PQC Vault CLI Contract

## Status

Draft contract. This document defines intended command behavior before implementation.

No command described here should be treated as implemented until runtime code and tests exist.

## Design Goals

The CLI should be:

- deterministic
- scriptable
- explicit about failure
- safe by default
- suitable for CI and operator workflows
- compatible with non-PQC transport and storage systems
- independent from ASP core operation

## Command Principles

Every command MUST:

- return a stable exit code
- emit machine-readable output when requested
- avoid silent failure
- preserve original payloads unless explicitly instructed otherwise
- avoid exposing plaintext in logs
- distinguish validation failure from unsupported capability

## Commands

### wrap

Wrap a payload into a PQC Vault envelope.

```bash
pqc-vault wrap <input> --recipient <recipient-public-key> --out <artifact.pqcv>
```

Minimum behavior:

- read input payload
- create manifest
- encrypt payload where encryption is selected
- wrap payload key for recipient
- write envelope
- optionally sign manifest or full envelope

### unwrap

Recover a payload from a PQC Vault envelope.

```bash
pqc-vault unwrap <artifact.pqcv> --key <private-key> --out <output>
```

Minimum behavior:

- parse envelope
- validate manifest structure
- verify integrity
- attempt key recovery
- decrypt payload
- write output only after successful validation unless policy permits otherwise

### inspect

Inspect envelope metadata without unwrapping payload.

```bash
pqc-vault inspect <artifact.pqcv>
```

Minimum behavior:

- show profile version
- show envelope class
- show algorithms declared
- show payload digest reference
- show signature status if present
- show validation requirements
- never expose plaintext payload

### verify

Verify an envelope against a trust policy.

```bash
pqc-vault verify <artifact.pqcv> --trust <trust-policy>
```

Minimum behavior:

- parse trust policy
- validate envelope structure
- verify signature if required
- verify digest/integrity fields
- return a posture-oriented result

### sign

Create a signed envelope or signed manifest.

```bash
pqc-vault sign <input> --key <signing-key> --out <signed-artifact.pqcv>
```

Minimum behavior:

- canonicalize manifest
- sign manifest or envelope according to profile
- write signed artifact

### rotate

Rotate recipient access without changing payload plaintext.

```bash
pqc-vault rotate <artifact.pqcv> --recipient <new-recipient-public-key> --out <rotated.pqcv>
```

Minimum behavior:

- validate existing envelope
- recover or rewrap envelope key according to policy
- create new recipient wrapping material
- preserve audit-relevant manifest lineage

## Output Modes

The CLI SHOULD support:

```bash
--format text
--format json
```

JSON output SHOULD be stable across minor versions.

## Exit Codes

Suggested exit codes:

| Code | Meaning |
|---:|---|
| 0 | success |
| 1 | general failure |
| 2 | invalid arguments |
| 3 | malformed envelope |
| 4 | validation failed |
| 5 | unsupported profile |
| 6 | unsupported algorithm |
| 7 | missing key |
| 8 | trust policy failed |
| 9 | unsafe output target |
| 10 | internal implementation error |

## Validation Result Vocabulary

Commands that inspect or verify envelopes SHOULD use the shared vocabulary:

- valid
- invalid
- unsupported-profile
- unsupported-algorithm
- missing-key
- expired-policy
- ambiguous
- tampered
- malformed

## Safety Requirements

The CLI MUST NOT:

- overwrite files unless explicitly allowed
- log plaintext payload material
- treat unsupported PQC capability as successful validation
- treat signature absence as valid when policy requires signature
- treat encryption absence as valid when policy requires encryption

## Deferred Decisions

The following are intentionally not fixed in this contract yet:

- implementation language
- concrete cryptographic library
- final envelope binary format
- final manifest schema
- key-storage backend
- certification claims
