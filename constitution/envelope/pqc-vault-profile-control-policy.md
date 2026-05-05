# PQC Vault Profile Control Policy

## Status

Constitutional control policy for selecting PQC Vault as a protected-envelope mode for ASP Envelope movement.

This document defines operator and policy control over protected-envelope selection.

It does not define ASP behavior.

It does not replace ASP Envelope.

It does not create legitimacy, authority, posture, signaling, or handling.

## Purpose

ASP Envelope remains the baseline constitutional mechanism for validation, sealing, and movement of ASP-governed material.

PQC Vault is the standard protected-envelope capability for ASP Envelope movement.

This policy defines how that protected mode may be enabled, disabled, preferred, or bypassed without changing ASP meaning.

## Control Model

```yaml
profile_control_policy:
  baseline_envelope_mode: asp_envelope
  protected_envelope_mode: pqc_vault_wrapped_asp_envelope
  pqc_vault_standard_protected_capability: true
  preferred_when_enabled: true
  operator_selectable: true
  policy_selectable: true
  disableable: true
  presumed_for_all_asp_material: false
  non_pqc_asp_carriage_remains_valid: true
```

## Selection Meaning

Selection of protected-envelope mode means only that ASP Envelope material is wrapped with PQC Vault for protected carriage.

It does not mean:

- ASP Envelope is replaced
- all ASP-governed material must be PQC-wrapped
- ASP legitimacy changes
- ASP authority changes
- ASP posture changes
- ASP handling changes

## Explicit State Rule

PQC-protected status must be explicit.

ASP-governed material MUST NOT be presumed PQC-wrapped unless protected-envelope mode has been explicitly applied by operator choice, policy, or another declared control surface.

## Radio-Dial Reading

A local system may expose envelope mode as a policy or operator dial, for example:

```yaml
envelope_mode_examples:
  - asp_envelope
  - pqc_vault_wrapped_asp_envelope
```

The existence of a dial does not split ASP meaning into separate systems.
It only changes the selected wrapping mode for movement.

## Canonical Close

ASP Envelope remains the baseline. PQC Vault is the standard protected-envelope capability. Protected status must be explicitly selected, not silently presumed.