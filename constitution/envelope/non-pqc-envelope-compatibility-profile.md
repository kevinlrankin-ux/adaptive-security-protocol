# Non-PQC Envelope Compatibility Profile

## Status

Constitutional compatibility profile for ASP Envelope movement when PQC wrapping is unavailable, unnecessary, or out of scope.

This document defines compatibility carriage for ASP Envelope material.

It does not define ASP behavior.

It does not replace ASP Envelope.

It does not compete with PQC Vault.

## Purpose

ASP-governed material may need to move through environments where PQC wrapping is unavailable, unnecessary, or not yet adopted.

This compatibility profile exists so ASP Envelope movement can remain supported in those contexts without semantic drift and without pretending that compatibility carriage changes ASP meaning.

## Scope

This profile is limited to non-PQC carriage of ASP Envelope material.

It does not:

- define ASP behavior
- define legitimacy
- authorize action
- assign posture
- determine handling
- claim post-quantum protection where none is present

## Compatibility Rule

Non-PQC ASP Envelope movement remains supported when required by compatibility, adoption stage, or context.

Support for this profile does **not** mean:

- non-PQC becomes the preferred wrapping profile
- PQC Vault is invalidated
- ASP Envelope semantics split into separate meanings

## Profile Role

```yaml
compatibility_profile:
  profile_name: non_pqc_asp_envelope
  role: compatibility_wrapping_profile
  supported: true
  preferred_by_default: false
  changes_asp_meaning: false
  changes_legitimacy_authority_posture_or_handling: false
```

## Relationship to PQC Vault

PQC Vault may be the default wrapping profile for ASP Envelope movement.

This compatibility profile remains the supported fallback path where PQC wrapping is unavailable, unnecessary, or out of scope.

Neither profile changes ASP meaning.

## Canonical Close

Compatibility support should preserve movement without creating semantic confusion. Non-PQC carriage is a supported wrapping path, not a second ASP.