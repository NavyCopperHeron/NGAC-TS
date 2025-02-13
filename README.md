# NGAC TypeScript

## Introduction

`ngac-ts` is a TypeScript library based on **NGAC (Next-Generation Access Control)** that implements the core components of NGAC:

- **PAP (Policy Administration Point)** - Responsible for managing and defining policies.
- **PDP (Policy Decision Point)** - Evaluates access requests and makes decisions.
- **PEP (Policy Enforcement Point)** - Enforces access control decisions.
- **PIP (Policy Information Point)** - Provides environmental information required for policy decisions.

This toolkit is published on [npm](https://www.npmjs.com/) and can be used to develop NGAC-based access control systems.

---

## Installation

Install via npm:

```bash
npm install ngac-ts
```

---

## Quick Start

### 1. Define Policies (PAP)

```typescript
import { PolicyAdministrationPoint } from 'ngac-ts';
const pap = new PolicyAdministrationPoint();
const node1 = new Node(1, "user1", "user");
const node2 = new Node(2, "object1", "object");
// Test addNode
pap.addNode(node1);
// Test adding nodes and edge separately
pap.addNode(node2);
pap.addEdge(1, 2, new Set(["read"]));
// Test updateNode
pap.updateNode(1, { name: "updatedUser" });
// Test deleteNode
pap.deleteNode(1);
```

### 2. Evaluate Access Requests (PDP & PEP)

```typescript
import { PolicyDecisionPoint, PolicyEnforcementPoint } from 'ngac-ts';

const pdp = new PolicyDecisionPoint();
const pep = new PolicyEnforcementPoint(pdp);
// Test access requests
const decision = await pep.requestAccess(user, object, "read");
```

### 3. Query Environmental Information (PIP)

```typescript
import { PolicyInformationPoint } from 'ngac-ts';

const graph = new Graph({ directed: true });
graph.setNode("1", { name: "UserNode", type: "user" });
graph.setNode("2", { name: "ResourceNode", type: "object" });
graph.setEdge("1", "2", { permission: "read" });
const graphJson = JSON.stringify(graphlibJson.write(graph));
const pip = new PolicyInformationPoint();
pip.storeGraph(graphJson);
const retrievedGraph = pip.retrieveGraph();
```

---


## Contribution Guidelines

We welcome contributions!

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes (`git commit -m "Add new feature"`).
4. Push your branch (`git push origin feature-branch`).
5. Submit a Pull Request.

---

## License

This project is licensed under the [Apache-2.0 license](LICENSE). Feel free to use and modify it.

