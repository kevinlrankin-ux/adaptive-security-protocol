# ASP Envelope Profile Selection Policy

## Status

Constitutional profile-selection policy for ASP envelope wrapping.

This document defines how ASP envelope wrapping profiles are selected.

It does not define ASP behavior.

It does not replace ASP Envelope.

It does not create legitimacy, authority, posture, signaling, or handling.

## Purpose

ASP Envelope remains the constitutional mechanism for validation, sealing, and movement of ASP-governed material.

This policy defines how wrapping profiles may be applied to ASP Envelope material without changing ASP meaning or functionality.

## Policy

### Default Wrapping Profile

The default wrapping profile for ASP Envelope movement is:

- `PQC Vault`

This means PQC Vault is the preferred wrapper when post-quantum wrapping is available and in scope.

### Compatibility Path

ASP Envelope material may also move using a non-PQC compatibility profile when:

- PQC wrapping is unavailable
- PQC wrapping is unnecessary for the specific movement context
- PQC wrapping is explicitly out of scope
- compatibility with existing systems requires non-PQC carriage

### Meaning of Default

Default does **not** mean:

- ASP Envelope is replaced
- non-PQC ASP Envelope movement is invalid
- ASP legitimacy changes
- ASP authority changes
- ASP posture changes
- ASP handling changes

Default means only that the preferred wrapping profile for envelope movement is PQC Vault where available and appropriate.

## Selection Rule

```yaml
profile_selection_policy:
  asp_envelope_semantics_changed: false
  default_wrapping_profile: pqc_vault
  compatibility_wrapping_profile: non_pqc_asp_envelope
  default_means: preferred_when_available_and_in_scope
  compatibility_means: supported_when_pqc_is_unavailable_unnecessary_or_out_of_scope
  profile_selection_is_not:
    - legitimacy_selection
    - authority_selection
    - posture_selection
    - handling_selection
```

## Boundary Rule

PQC Vault and non-PQC compatibility profiles are wrapping profiles for ASP Envelope movement.

They do not alter:

- ASP conceptual authority
- ASP constitutional identity
- ASP runtime handling semantics
- the meaning of the governed material

## Canonical Close

ASP Envelope remains ASP Envelope. Profile selection changes how governed material is wrapped for movement, not what ASP means or what authority ASP carries.