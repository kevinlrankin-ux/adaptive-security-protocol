# PQC Vault Validation Failure Matrix

## Status

Draft matrix. This document defines expected validation outcomes and ASP posture guidance.

Validation results are not automatic authorization decisions. They are inputs into ASP posture handling.

## Matrix

| Result | Meaning | Suggested ASP posture | Notes |
|---|---|---|---|
| valid | Envelope satisfies required structure, integrity, and trust policy | continuity | Does not by itself authorize payload execution |
| invalid | Envelope fails validation | reject or quarantine | Treat as unsafe until reviewed |
| unsupported-profile | Verifier does not support this envelope profile | signal + bounded friction | Do not treat as valid |
| unsupported-algorithm | Verifier does not support declared algorithm | signal + bounded friction | May require upgraded verifier |
| missing-key | Required recipient, verification, or trust key unavailable | signal + bounded friction | May be recoverable |
| expired-policy | Envelope or trust policy is outside allowed time/policy window | signal + bounded friction or reject | Domain policy decides severity |
| ambiguous | Verifier cannot reach a clear determination | signal + bounded friction | Avoid silent success |
| tampered | Envelope appears modified or integrity check fails | reject or quarantine | High-severity result |
| malformed | Envelope cannot be parsed as a valid structure | reject or quarantine | High-severity result |

## Required Behavior

A verifier MUST distinguish between:

- unsupported capability
- missing key material
- malformed envelope
- failed integrity validation
- failed trust policy

A verifier MUST NOT collapse these outcomes into generic success or generic failure when machine-readable reporting is requested.

## Operator Guidance

Suggested operator responses:

- valid: proceed according to local policy
- unsupported-profile: route to a compatible verifier
- unsupported-algorithm: update verifier or apply approved fallback policy
- missing-key: initiate key retrieval or recovery process
- expired-policy: request policy review
- ambiguous: escalate for human review
- invalid/tampered/malformed: quarantine and preserve evidence

## CI / Automation Guidance

Automation SHOULD fail closed for:

- invalid
- tampered
- malformed

Automation MAY fail with actionable signal for:

- unsupported-profile
- unsupported-algorithm
- missing-key
- expired-policy
- ambiguous

## Enterprise Requirement

Any implementation MUST expose validation results in a stable machine-readable form.
