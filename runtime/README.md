# ASP Runtime Layer

This directory holds runtime behavior and operational handling semantics.

Examples:
- legitimacy
- degradation
- signaling
- friction escalation

Runtime behavior enforces ASP; it does not define ASP.

ASP governs runtime handling posture when actor legitimacy cannot be immediately established.

ASP does not collapse uncertain conditions into binary acceptance or refusal.
Instead, it signals handling posture and applies bounded friction while preserving system continuity.

verified   → continuity
unverified → friction & signal
uncertain  → signal & friction
never      → silent failure

When actors cannot be verified or attested, ASP does not allow silent failure.
