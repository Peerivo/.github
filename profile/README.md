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

## Core Projects

### [AI Constitution](https://github.com/Peerivo/constitution)

Executable governance and contract layer for AI agents and autonomous systems.

AI Constitution defines the rules under which agents operate: identity, authority, capabilities, resources, approvals, evidence requirements, network policies, stop conditions and runtime constraints.

It establishes the common contract hierarchy used across Peerivo:

```text
Global Contract
    ↓
Project Contract
    ↓
Agent Contract
    ↓
Task / Run Contract
```

Lower-level contracts may make restrictions more specific or stronger, but cannot silently weaken inherited constraints.

---

### [IronGate](https://github.com/Peerivo/irongate)

Safety and enforcement infrastructure for AI agents, autonomous systems and physical-world execution.

IronGate turns constitutional rules into enforceable runtime controls. It provides the boundary between an agent and the resources it is trying to access or control.

Its scope includes:

* identity and capability enforcement
* runtime authorization
* network restrictions
* human approvals
* stop conditions
* fail-closed execution
* human override
* emergency controls and interlocks
* physical agent safety
* execution evidence and verification

AI Constitution defines what is allowed. IronGate helps enforce those rules in practice.

---

### [Peerivo Network](https://github.com/Peerivo/network)

Identity, relationship and coordination layer for people, organizations, projects and AI agents.

Peerivo Network is the shared network foundation of the Peerivo ecosystem.

It is designed to connect:

* People
* Companies
* AI Agents
* Projects
* Jobs
* identities
* permissions
* professional relationships
* verified work and reputation

The long-term goal is a network where both human and autonomous actors can have explicit identities, roles, relationships and verifiable histories of work.

---

### [Factory](https://github.com/Peerivo/factory)

Infrastructure for creating, configuring, packaging and operating AI agents.

Factory provides the lifecycle layer for agents and agent-based systems.

Its responsibilities include:

* agent creation
* Agent Contracts
* identity assignment
* capabilities
* tools and resources
* execution environments
* policies
* configuration
* packaging and versioning
* deployment preparation
* runtime metadata
* observability
* evidence collection

Factory does not define global governance itself. It consumes the rules and contract model defined by AI Constitution and prepares agents to operate within them.

---

### [Workbench](https://github.com/Peerivo/workbench)

Development and operational workspace for building, testing and running agent-based systems.

Workbench is where developers and operators interact with agents, projects, tools and execution environments.

It is designed to support workflows such as:

* creating and modifying applications
* working with repositories
* running development tasks
* testing agents
* inspecting execution results
* managing project context
* using tools and connected services
* preparing deployments
* reviewing generated changes

Workbench is the interactive workspace, while Factory manages the agent lifecycle and IronGate controls sensitive execution.

---

### [Geo](https://github.com/Peerivo/geo)

Web discovery, indexing and machine-readable visibility infrastructure for Peerivo projects.

Geo helps projects become discoverable not only through traditional search engines, but also through AI systems, agents and emerging machine-consumption channels.

Its scope includes:

* IndexNow integration
* search engine discovery
* structured metadata
* sitemap infrastructure
* canonical URLs
* schema.org
* robots and crawler policies
* AI crawler visibility
* machine-readable project information
* entity and content discovery
* GEO / Generative Engine Optimization
* Answer Engine Optimization
* shared discovery standards across Peerivo projects

Geo acts as a common discovery layer rather than each Peerivo project implementing indexing and machine visibility independently.

The ecosystem is evolving, and these projects increasingly share common protocols for identity, contracts, evidence, approvals and verification.

## Mission

Our goal is not simply to make AI agents more capable.

Our goal is to make increasingly capable autonomous systems **governable, understandable, interoperable and trustworthy enough to participate responsibly in the real world.**

🌐 **https://peerivo.net**
