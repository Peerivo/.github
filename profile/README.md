# Peerivo

**Infrastructure for a world where people, organizations and AI agents work together safely, verifiably and autonomously.**

Peerivo is an ecosystem of platforms, protocols and infrastructure for human and machine collaboration.

We build systems around a simple idea:

> Powerful agents need more than intelligence. They need identity, boundaries, evidence, accountability and trust.

## What we build

Peerivo spans several connected layers.

### Constitution & Governance

Executable rules and contracts that define how autonomous systems may act.

* **AI Constitution** — a machine-readable constitutional layer for AI systems
* **Agent Contracts** — identity, capabilities, scope, resources, policies and stop conditions
* **Approval Infrastructure** — explicit authorization for sensitive operations
* **Evidence & Outcome** — verifiable claims, actions, forecasts and results

### Safety & Control

Infrastructure for enforcing constraints in software and the physical world.

* **IronGate** — constitutional network and physical interlock infrastructure
* policy enforcement
* human override and emergency controls
* execution verification
* audit and provenance

### Identity & Network

A shared layer for people, companies and autonomous agents.

* **Peerivo ID**
* People
* Companies
* Agents
* Projects
* Jobs
* professional identity and reputation
* verified agent work

### Agent Infrastructure

Tools for creating, operating and supervising autonomous systems.

* Agent Factory
* Agent Manager
* Workbench
* Gateway
* execution environments
* permissions and resource capabilities
* observability and audit trails

### Knowledge & Learning

Systems that transform information, experience and evidence into reusable knowledge and individual development.

* Peerivo Learning
* AI Language
* Knowledge
* Genius
* adaptive learning systems

## Core principles

Our infrastructure is designed around several principles:

**Identity before authority**
Every actor should have a clear and verifiable identity.

**Explicit capabilities**
Agents receive specific permissions rather than implicit access.

**Least privilege**
Access is bounded by task, project, environment and resource.

**Evidence over assumption**
Material claims and outcomes should be supported by verifiable evidence.

**Human authority**
Human override and scoped approval remain available wherever required.

**Fail closed**
Missing authorization or evidence must not silently become permission.

**Auditable execution**
Important actions should leave a durable, attributable record.

**Interoperability**
Protocols and contracts should work across models, tools and execution environments.

## Architecture

Peerivo uses a hierarchy of executable contracts:

```text
Global Contract
    ↓
Project Contract
    ↓
Agent Contract
    ↓
Task / Run Contract
```

Each lower layer may make restrictions more specific or stronger, but cannot silently weaken the guarantees inherited from the layer above.

## Engineering

Our projects use technologies including:

`TypeScript` · `Next.js` · `Node.js` · `Go` · `PHP` · `.NET` · `PostgreSQL` · `Supabase` · `GitHub Actions` · `Vercel` · `Cloudflare`

The technology is secondary to the architectural goal: systems that are understandable, enforceable and verifiable.

## Open development

Peerivo contains both public infrastructure and product projects.

We use a review-first development process:

```text
main
  ↓
small branch
  ↓
implementation
  ↓
automated checks
  ↓
preview / verification artifact
  ↓
review
  ↓
approval
  ↓
merge
```

Unreviewed changes are not merged directly into `main`.

## Projects

Some of the systems being developed across Peerivo include:

* Mercy
* Living Menaion
* Symphony
* AI Constitution
* IronGate
* Peerivo Network
* Agent Factory
* Agent Manager
* Workbench
* Gateway
* Peerivo Learning
* Geo
* Origin

The ecosystem is evolving, and these projects increasingly share common protocols for identity, contracts, evidence, approvals and verification.

## Mission

Our goal is not simply to make AI agents more capable.

Our goal is to make increasingly capable autonomous systems **governable, understandable, interoperable and trustworthy enough to participate responsibly in the real world.**

🌐 **https://peerivo.net**
