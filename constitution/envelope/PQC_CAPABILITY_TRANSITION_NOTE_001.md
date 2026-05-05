# PQC Capability Transition Note 001

## Status

Transition note for relocating PQC protected-envelope implementation gravity out of ASP.

## Purpose

ASP remains the governing meaning layer.

PQC protected-envelope capability may align to ASP without redefining ASP.

This note records that the dedicated implementation-capability home for Portable Post-Quantum Boundary work is:

- `kevinlrankin-ux/portable-post-quantum-object-boundary`

## Role Split

```yaml
role_split:
  asp_repo:
    role:
      - protocol_identity
      - invariants
      - constitutional_meaning
      - runtime_handling_semantics
    not_role:
      - primary_pqc_cli_home
      - primary_crypto_implementation_home
      - primary_key_management_home

  ppqob_repo:
    role:
      - pqc_protected_envelope_capability_layer
      - wrap_unwrap_behavior
      - manifest_shape
      - algorithm_agility_details
      - cli_or_operator_surface
      - implementation_review_and_runtime_evidence
    vendor_source_of_truth:
      - adaptive_security_protocol
```

## Reading Rule

Capability repos aligned to ASP may cite ASP as their governing vendor or meaning repo.

ASP does not need to become the capability home in order for the capability to remain ASP-aligned.

## Canonical Close

ASP stays strongest when it remains the meaning layer. Capability repos may align to ASP without asking ASP to carry their implementation gravity.