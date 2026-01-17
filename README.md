# Agent Authority Protocol (AAP)

**Agent Authority Protocol (AAP)** is an open control-plane protocol that defines how autonomous agents may propose, justify, and commit **world-state transitions** under explicit, non-delegable **human authority**.

AAP addresses a fundamental problem emerging in agent-driven systems:

> When intelligent execution becomes faster than human governance,  
> authority must be made explicit — or control is lost.

---

## Why AAP Exists

Modern coding agents can generate, refactor, and deploy changes at speeds far exceeding human review.

Traditional governance mechanisms — pull requests, code reviews, CI gates — rely on an implicit assumption:

> The entity that executes changes is also the entity that authorizes them.

This assumption no longer holds.

As agent execution scales:
- Review becomes ceremonial
- Responsibility becomes implicit
- Control becomes ambiguous

AAP introduces a new abstraction:

> **Authority over world-state transitions**

It separates **execution capability** from **authorization power**, making control explicit, auditable, and enforceable.

---

## What AAP Is

AAP is:

- A **protocol**, not a product
- A **control plane**, not a workflow
- A **governance primitive**, not a policy checklist

AAP defines:
- Who may propose changes
- Under what constraints
- What evidence is required
- Who has final authority
- When a change becomes real

---

## What AAP Is Not

AAP is **not**:

- An agent communication protocol  
- An AI alignment framework  
- A developer productivity tool  
- A CI/CD replacement  
- A compliance checklist  

AAP governs **authority**, not intelligence.

For details, see:
- [`non-goals.md`](non-goals.md)

---

## Relationship to ICEP

AAP defines who is allowed to authorize world-state transitions.
ICEP defines how multiple agent intents are evaluated to select an accepted
world-state transition under constraints.

See the complementary ICEP specification in `../ICEP` (canonical) or
https://github.com/tokligence/ICEP.

---

## Core Concepts

AAP introduces several foundational concepts that replace legacy abstractions:

- **World-State**  
  The externally observable condition of a system (code, config, infra, data, behavior).

- **World-State Transition**  
  Any change that moves the system from one valid state to another.

- **Proposal**  
  A declarative request to perform a world-state transition.

- **Authority**  
  The legitimate power to approve or reject a proposed transition.

- **Human Final Authority**  
  A non-delegable role responsible for authorization.

These terms are defined normatively in:
- [`terminology.md`](terminology.md)

---

## Design Principles

AAP is built on the following non-negotiable principles:

1. **Authority precedes autonomy**  
2. **Explicit decisions over implicit trust**  
3. **Control plane over tooling**  
4. **Governance over velocity**  
5. **Traceability over convenience**

Any implementation that violates these principles is **not AAP-compliant**.

---

## Protocol Overview

AAP defines a minimal set of protocol primitives:

- **PROPOSE** — submit a world-state transition request  
- **CONSTRAIN** — apply invariants and policy rules  
- **EVIDENCE** — provide proof of compliance  
- **DECIDE** — human authorization or rejection  
- **COMMIT** — materialize the authorized transition  

AAP-compliant systems MUST enforce the following lifecycle:

DRAFT → PROPOSED → EVALUATED → ACCEPTED → COMMITTED
									↓
								REJECTED


Only transitions from **ACCEPTED → COMMITTED** may mutate the world-state.

---

## Security Model

AAP is designed to prevent:

- Unauthorized world-state mutation
- Agent privilege escalation
- Implicit or untraceable decisions
- Post-hoc justification of changes

Security in AAP is achieved through **authority enforcement**, not trust assumptions.

---

## Governance Model

AAP is an **open protocol**.

- This repository hosts the **specification** of AAP.
- **Tokligence** acts as the initial steward of the protocol.
- No single entity owns AAP.
- Protocol changes are proposed via RFCs and reviewed openly.

If adoption grows, AAP may transition to a neutral foundation model.

---

## Reference Implementation

AAP intentionally separates **specification** from **implementation**.

A reference implementation demonstrating AAP concepts is available in a
separate repository:

> https://github.com/tokligence/AAP-MVP (reference implementation)

The existence of an implementation does not define the protocol.

---

## RFCs

- RFC-0001: Agent Authority Protocol (AAP)

---

## Status

- **Current Status:** Draft
- **Initial RFC:** RFC-0001
- **License:** Apache 2.0

AAP is under active discussion. Feedback, critiques, and alternative designs are welcome.

---

## Contributing

AAP evolves through **clarity**, not velocity.

Before contributing:
1. Read [`terminology.md`](terminology.md)
2. Read [`non-goals.md`](non-goals.md)
3. Understand the authority model

Contributions that dilute or bypass the authority abstraction will not be accepted.

---

## Closing Note

AAP is not an attempt to make agents smarter.

It is an attempt to ensure that as intelligent execution scales,  
**human authority does not disappear by accident**.

When execution becomes cheap,  
**authority becomes everything**.
