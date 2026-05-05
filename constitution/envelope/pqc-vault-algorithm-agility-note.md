# PQC Vault Algorithm Agility Note

## Status

Draft constitutional note for algorithm agility in PQC Vault wrapping.

This document defines an algorithm-agility posture for PQC Vault.

It does not mandate a final cryptographic suite.

It does not define ASP behavior.

It does not create legitimacy, authority, posture, signaling, or handling.

## Purpose

If PQC Vault is to function as a Portable Post-Quantum Boundary wrapper across changing environments, algorithm choice cannot be treated as permanently fixed at the constitutional level.

This note establishes that the boundary-preservation role is stable even if the underlying cryptographic suite later changes.

## Agility Principle

```yaml
algorithm_agility_principle:
  boundary_role_stable: true
  cryptographic_suite_may_evolve: true
  profile_identifier_stable: pqc_vault
  final_algorithm_set_fixed_here: false
```

## Allowed Reading

Algorithm agility means:

- the PQC Vault profile may later specify one or more concrete algorithm families
- those choices may evolve without changing ASP meaning
- those choices may evolve without changing the Portable Post-Quantum Boundary role

Algorithm agility does not mean:

- arbitrary silent cryptographic drift
- silent incompatibility with carried material
- change to ASP legitimacy or authority semantics

## Minimum Documentation Expectation

When concrete algorithm families are later introduced, the repository SHOULD record:

```yaml
minimum_documentation_expectation:
  - algorithm_family_identifier
  - reason_for_selection
  - compatibility_impact
  - recovery_or_rotation_note
  - any_required_manifest_extension
```

## Non-Meaning

```yaml
non_meaning:
  - agility_note_is_not_algorithm_implementation
  - agility_note_is_not_key_management
  - agility_note_is_not_runtime_authority
  - agility_note_is_not_production_readiness
```

## Canonical Close

Algorithm agility should let the wrapper evolve without forcing ASP meaning to drift with it.