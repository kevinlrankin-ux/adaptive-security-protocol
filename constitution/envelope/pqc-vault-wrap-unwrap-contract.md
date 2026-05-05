# PQC Vault Wrap/Unwrap Contract

## Status

Draft constitutional contract for PQC Vault wrap and unwrap operations.

This document defines a minimal contract for wrap and unwrap behavior around ASP-governed material.

It does not define ASP behavior.

It does not create runtime legitimacy, authority, posture, signaling, or handling.

It does not by itself prove production readiness.

## Purpose

PQC Vault is a wrapping profile for ASP Envelope movement.

This contract defines the minimum expected inputs, outputs, preserved properties, and failure boundaries for:

- wrap
- unwrap

The goal is to make the Portable Post-Quantum Boundary operationally legible without claiming more implementation maturity than currently exists.

## Contract Scope

This contract is limited to:

- wrapping ASP-governed material
- unwrapping ASP-governed material
- preserving boundary identity through carriage
- exposing minimum boundary metadata needed for continuity

This contract does not define:

- ASP legitimacy
- ASP authority
- ASP runtime posture
- policy decisions about whether unwrap should be allowed in a local system
- production key management
- final cryptographic file format

## Wrap Contract

### Inputs

```yaml
wrap_inputs:
  - governed_material
  - profile_identifier
  - boundary_manifest
  - wrapping_context_identifier
  - key_reference_or_key_material_placeholder
```

### Required Wrap Properties

```yaml
required_wrap_properties:
  preserves_governed_material_identity: true
  preserves_boundary_manifest_linkage: true
  preserves_profile_identifier: true
  indicates_wrapped_state: true
  does_not_change_asp_meaning: true
  does_not_assign_legitimacy_or_authority: true
```

### Wrap Output

```yaml
wrap_output:
  wrapped_material_object: required
  boundary_manifest_reference: required
  profile_identifier: pqc_vault
  wrapped_state: true
```

## Unwrap Contract

### Inputs

```yaml
unwrap_inputs:
  - wrapped_material_object
  - boundary_manifest_reference
  - unwrap_context_identifier
  - key_reference_or_key_material_placeholder
```

### Required Unwrap Properties

```yaml
required_unwrap_properties:
  verifies_expected_profile_before_unwrap: true
  preserves_boundary_identity_through_unwrap: true
  does_not_assign_legitimacy_or_authority: true
  exposes_failure_cleanly_if_unwrap_cannot_proceed: true
```

### Unwrap Output

```yaml
unwrap_output:
  recovered_governed_material: required_if_successful
  boundary_manifest_reference: required
  unwrap_status:
    - success
    - blocked
    - failed
```

## Failure Boundaries

```yaml
failure_boundaries:
  wrap_failure_must_not:
    - silently_strip_boundary_identity
    - silently_change_profile_identifier
  unwrap_failure_must_not:
    - silently_emit_material_as_if_successful
    - silently_claim_boundary_preservation_if_verification_failed
```

## Non-Meaning

```yaml
non_meaning:
  - wrap_success_is_not_legitimacy
  - wrap_success_is_not_authority
  - unwrap_success_is_not_authority
  - boundary_manifest_is_not_runtime_posture
  - contract_presence_is_not_production_readiness
```

## Canonical Close

A wrap/unwrap contract should make boundary-preserving movement inspectable without pretending that movement alone decides meaning, trust, or authority.