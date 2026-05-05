# PQC Vault Minimal Boundary Manifest Schema

## Status

Draft minimal boundary manifest schema for PQC Vault-wrapped ASP-governed material.

This document defines a minimum manifest shape for continuity and boundary preservation.

It does not define ASP behavior.

It does not create legitimacy, authority, posture, signaling, or handling.

## Purpose

The manifest exists so wrapped material can carry enough boundary identity to remain inspectable and continuity-preserving across systems, including systems that have not implemented PQC.

## Minimal Manifest Shape

```yaml
pqc_vault_boundary_manifest:
  manifest_version: 0.1-draft
  profile_identifier: pqc_vault
  governed_material_identifier: <required>
  governed_material_type: <required>
  boundary_product_class: portable_post_quantum_boundary
  wrapping_state: wrapped
  wrapping_context_identifier: <required>
  source_system_identifier: <required_if_known>
  created_at: <required_if_known>
  compatibility_note: <optional>
```

## Required Minimum Fields

```yaml
required_minimum_fields:
  - manifest_version
  - profile_identifier
  - governed_material_identifier
  - governed_material_type
  - boundary_product_class
  - wrapping_state
  - wrapping_context_identifier
```

## Optional Fields

```yaml
optional_fields:
  - source_system_identifier
  - created_at
  - compatibility_note
  - algorithm_family_note
  - recovery_reference
```

## Schema Rules

```yaml
schema_rules:
  profile_identifier_must_equal: pqc_vault
  boundary_product_class_must_equal: portable_post_quantum_boundary
  wrapping_state_allowed_values:
    - wrapped
    - unwrapped_reference_only
  manifest_must_not:
    - assign_legitimacy
    - assign_authority
    - assign_posture
    - interpret_system_meaning
```

## Non-Meaning

```yaml
non_meaning:
  - manifest_presence_is_not_authority
  - manifest_presence_is_not_legitimacy
  - manifest_presence_is_not_runtime_posture
  - minimal_schema_is_not_final_cryptographic_format
  - minimal_schema_is_not_production_readiness
```

## Canonical Close

A minimal manifest should carry just enough boundary identity to preserve continuity, without pretending that metadata alone decides trust or authority.