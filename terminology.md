# Terminology

This document defines the core terminology used by the **Agent Authority Protocol (AAP)**.

The purpose of this terminology is not academic precision, but **conceptual clarity**.
AAP intentionally introduces new terms to replace legacy abstractions that no longer hold in agent-driven systems.

---

## World-State

**World-State** refers to the externally observable condition of a system.

This includes, but is not limited to:

* Source code
* Configuration files
* Infrastructure definitions
* Data schemas
* Runtime behavior
* Deployment topology
* Authorization boundaries

AAP treats code as a *projection* of the world-state, not the world-state itself.

---

## World-State Transition

A **World-State Transition** is any change that moves the system from one valid world-state to another.

Examples include:

* Modifying a database schema
* Changing an authentication rule
* Introducing retry logic into a payment flow
* Altering deployment or release behavior

AAP governs *transitions*, not code diffs.

---

## Agent

An **Agent** is an autonomous or semi-autonomous system capable of proposing or executing actions that may affect the world-state.

In AAP:

* Agents are assumed to be **high-speed execution entities**
* Agents are **not trusted** by default
* Agents do **not possess authority**

---

## Proposal

A **Proposal** is a declarative request to perform a world-state transition.

A proposal MUST include:

* Intent (what change is requested)
* Scope (what parts of the system are affected)
* Constraints (what must not be violated)
* Evidence (why the change is safe)

A proposal is not executable by itself.

---

## Authority

**Authority** is the legitimate power to approve or reject a proposed world-state transition.

Authority is:

* Explicit
* Non-delegable
* Auditable

In AAP, **authority belongs exclusively to humans**.

---

## Human Final Authority

**Human Final Authority** refers to the role responsible for authorizing world-state transitions.

This role:

* Cannot be assumed by agents
* Cannot be automated
* Cannot be bypassed

Human Final Authority is the ultimate safeguard against uncontrolled execution.

---

## Constraint / Invariant

A **Constraint** (or **Invariant**) is a rule that MUST hold before and after any world-state transition.

Examples:

* “No direct modification of authentication logic”
* “No schema changes without migration approval”
* “No production access by agents”

Violating a constraint invalidates a proposal.

---

## Evidence

**Evidence** is any artifact that supports the claim that a proposal satisfies all constraints.

Examples:

* Test results
* Static analysis reports
* Formal proofs
* Simulation outcomes

Evidence precedes authorization.

---

## Commit

A **Commit** is the irreversible act of materializing an authorized world-state transition.

In AAP:

* Commits are effects, not decisions
* Commits occur only after authorization
* Commits must be traceable to a specific authority decision

---

## Control Plane

The **Control Plane** is the system responsible for enforcing AAP.

It evaluates proposals, applies constraints, records decisions, and permits or denies commits.

The control plane is **not optional**.

---

## Execution Plane

The **Execution Plane** consists of agents and tools that perform work.

The execution plane:

* Proposes changes
* Produces evidence
* Never authorizes outcomes

---

# Terminology Stability

Terminology defined in this document is considered **normative** for AAP.

Any implementation or discussion of AAP MUST adhere to these definitions to remain compatible with the protocol.

---
