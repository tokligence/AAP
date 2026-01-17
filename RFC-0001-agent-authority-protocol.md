# RFC-0001: Agent Authority Protocol (AAP)

**Status:** Draft  
**Category:** Standards Track  
**Version:** 1.0  
**Author:** Tokligence (Initial Steward)

---

## 1. Abstract

Agent Authority Protocol (AAP) defines a control-plane protocol that governs how autonomous agents may propose, justify, and commit **world-state transitions** under explicit, non-delegable **human authority**.

AAP addresses the governance gap introduced when intelligent execution scales faster than human oversight, rendering traditional code-centric approval models insufficient.

---

## 2. Motivation

Software systems are increasingly modified by autonomous or semi-autonomous agents capable of generating, refactoring, and deploying changes at speeds far exceeding human review.

Existing governance mechanisms—such as pull requests, code reviews, and CI gates—implicitly assume that the entity executing a change is also the entity authorizing it. This assumption no longer holds.

As intelligent execution accelerates:

- Review becomes ceremonial rather than authoritative
- Responsibility becomes implicit rather than explicit
- Control becomes ambiguous rather than enforceable

AAP introduces a new abstraction: **authority over world-state transitions**, decoupling execution capability from authorization power.

---

## 3. Terminology

The following terms are normative within AAP.  
Detailed definitions are provided in `terminology.md`.

- **World-State**  
- **World-State Transition**  
- **Agent**  
- **Proposal**  
- **Authority**  
- **Human Final Authority**  
- **Constraint / Invariant**  
- **Evidence**  
- **Commit**  
- **Control Plane**  
- **Execution Plane**

Any implementation claiming AAP compliance MUST adhere to these definitions.

---

## 4. Design Principles

AAP is governed by the following non-negotiable principles:

1. **Authority precedes autonomy**  
2. **Explicit decisions over implicit trust**  
3. **Control plane over tooling**  
4. **Governance over velocity**  
5. **Traceability over convenience**

These principles take precedence over implementation convenience or performance optimizations.

---

## 5. Authority Model

AAP enforces a strict separation between execution and authorization:

- Autonomous agents MAY propose world-state transitions.
- Autonomous agents MUST NOT authorize transitions.
- Human authority MUST be explicit, attributable, and auditable.
- Human authority MUST NOT be delegated to agents or automated systems.

This separation is fundamental to preventing unauthorized or implicit world-state mutation.

---

## 6. Protocol Primitives

AAP defines the following minimal set of primitives:

- **PROPOSE**  
  Submit a declarative request for a world-state transition.

- **CONSTRAIN**  
  Apply invariants and policy rules that must not be violated.

- **EVIDENCE**  
  Provide artifacts demonstrating compliance with constraints.

- **DECIDE**  
  An explicit authorization or rejection issued by human authority.

- **COMMIT**  
  The irreversible materialization of an authorized transition.

These primitives are conceptual and normative.  
AAP intentionally does not prescribe wire-level representations in RFC-0001.

---

## 7. State Machine

AAP-compliant implementations MUST enforce the following lifecycle:

DRAFT → PROPOSED → EVALUATED → ACCEPTED → COMMITTED
							   	↓
							  REJECTED


Only transitions from **ACCEPTED → COMMITTED** may mutate the world-state.

### 7.1 Lifecycle Semantics

AAP mandates the existence and enforcement of the state machine but does not prescribe:

- Cancellation or revocation semantics
- Retry or timeout policies
- Concurrent proposal resolution strategies

These behaviors are considered **control-plane policy** and are implementation-defined.

---

## 8. Authority Binding (Normative)

AAP requires that every **DECIDE** and **COMMIT** action be cryptographically and logically bound to a specific human authority decision.

An AAP-compliant implementation MUST ensure that:

- Every authorization decision is attributable to a human authority
- Every commit is traceable to a unique prior decision
- Replay, substitution, or reuse of decisions is prevented

The concrete mechanisms used to achieve this binding—such as identity providers, digital signatures, hardware-backed keys, or secure logs—are **implementation-defined**.

---

## 9. Transport and Encoding (Non-Normative)

AAP intentionally does not mandate a specific transport, encoding, or message schema in RFC-0001.

The protocol defines **authority semantics and state transitions**, not communication mechanics.

Future RFCs may specify:

- Reference message schemas
- Recommended transports (e.g. HTTP+JSON, gRPC)
- Compatibility profiles for existing agent protocols

This separation is intentional to avoid premature ossification and to allow AAP to be embedded into diverse control planes.

---

## 10. Constraints and Evidence (Normative Scope)

AAP requires that proposals declare constraints and provide evidence,
but does not define a canonical policy language or evidence format
in RFC-0001.

Constraints and Evidence are abstract categories in AAP.
Their concrete representations are intentionally left undefined
to allow domain-specific policy systems.

Their concrete representations, validation methods, and provenance
requirements are implementation-defined and may be standardized
in future RFCs.

---

## 11. Security Considerations

AAP is designed to mitigate the following risks:

- Unauthorized world-state mutation by agents
- Implicit authority escalation
- Post-hoc justification of changes
- Non-attributable system modifications

### 11.1 Threat Model (Informative)

AAP addresses:

- Untrusted or over-privileged agents
- Accidental authority leakage
- Governance bypass through automation

AAP does not address:

- Model hallucination
- Malicious human authorities
- Insider threats

These risks must be handled by organizational, legal, or operational controls.

---

## 12. Non-Goals

AAP explicitly does NOT:

- Define agent communication protocols
- Specify policy DSLs
- Replace CI/CD systems
- Optimize developer productivity
- Guarantee correctness or safety

AAP governs **authority**, not intelligence.

---

## 13. Versioning and Extensibility

AAP follows a versioned RFC model.

- RFC-0001 defines the core authority abstraction.
- Extensions MUST NOT violate the authority model.
- Wire-level bindings, policy languages, and compliance profiles are expected to be defined in future RFCs.

---

## 14. Conformance

An implementation may claim AAP compliance if and only if it:

- Enforces the authority model
- Implements the state machine
- Prevents unauthorized commits
- Provides auditable decision records

---

## 15. References

(To be populated in future revisions)

---

## 16. Closing Statement

AAP does not attempt to make autonomous systems smarter.

It ensures that as intelligent execution scales,  
**human authority does not disappear by accident**.

When execution becomes cheap,  
**authority becomes everything**.

