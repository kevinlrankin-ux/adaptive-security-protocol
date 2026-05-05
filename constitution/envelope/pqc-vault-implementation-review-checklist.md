# PQC Vault Implementation Review Checklist

## Status

Draft implementation review checklist for PQC Vault.

This document provides a conservative review checklist for any future implementation effort.

It does not itself implement PQC Vault.

It does not certify readiness.

It does not define ASP behavior.

## Purpose

This checklist exists so future implementation work can be reviewed against the current constitutional boundaries without overstating repository maturity.

## Review Checklist

```yaml
implementation_review_checklist:
  boundary_and_scope:
    - pqc_vault_role_still_limited_to_wrapping_and_unwrapping
    - asp_meaning_not_modified
    - legitimacy_authority_posture_handling_not_assigned_by_wrapper
  wrap_unwrap_contract:
    - wrap_inputs_defined
    - wrap_outputs_defined
    - unwrap_inputs_defined
    - unwrap_outputs_defined
    - failure_boundaries_defined
  manifest:
    - minimal_boundary_manifest_present
    - profile_identifier_preserved
    - governed_material_identifier_preserved
    - boundary_product_class_preserved
  compatibility:
    - non_pqc_fallback_path_documented
    - compatibility_impact_stated
    - no_false_claim_that_all_carrier_systems_require_pqc
  algorithm_agility:
    - algorithm_family_note_present_if_needed
    - no_silent_cryptographic_drift
    - compatibility_or_rotation_note_present_if_needed
  implementation_honesty:
    - no_claim_of_production_readiness_without_runtime_evidence
    - no_claim_of_certification_without_external_basis
    - no_claim_that_documentation_alone_equals_operational_realization
```

## Review Outcome Classes

```yaml
review_outcome_classes:
  conceptually_aligned:
    meaning: constitutional_boundaries_preserved_but_runtime_realization_not_shown
  implementation_candidate:
    meaning: enough_contract_manifest_and_review_structure_exists_to_begin_bounded_build_work
  operationally_demonstrated:
    meaning: runtime_evidence_exists_and_has_been_reviewed_separately
```

## Non-Meaning

```yaml
non_meaning:
  - checklist_presence_is_not_implementation
  - checklist_completion_is_not_authority
  - checklist_completion_is_not_certification
  - checklist_completion_is_not_production_readiness
```

## Canonical Close

A good checklist should keep implementation ambition honest. It should make future build work easier to review without letting review scaffolding pretend the build is already done.