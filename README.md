# 🛡 ClusterShield – Kubernetes Attack Path Visualizer

Graph-Based Security Analysis for Cloud-Native Infrastructure

ClusterShield is a security analysis tool that detects **multi-hop privilege escalation attack paths in Kubernetes clusters**. Instead of auditing permissions individually, ClusterShield models the entire cluster as a **directed graph** and uses graph algorithms to discover hidden attack chains.

Built for **Hack2Future 2.0 – IIIT Dharwad (Cloud Security Track)**.

---

# 🚨 Problem

Modern Kubernetes clusters contain many interconnected entities:

- Pods
- ServiceAccounts
- Roles
- RoleBindings
- Secrets
- External Services

Attackers rarely compromise privileged resources directly. Instead they follow **chains of permissions**, where each step appears harmless individually.

Example attack path:

```
Attacker → Pod → ServiceAccount → Secret → Production Database
```

Each step looks safe in isolation but together creates a **privilege escalation chain**.

Traditional RBAC audits cannot detect these multi-hop relationships.

---

# 💡 Proposed Solution

ClusterShield builds a **graph model of the Kubernetes cluster** and applies graph algorithms to detect attack paths.

Workflow:

1. Extract cluster data using `kubectl`
2. Convert cluster entities into nodes
3. Map permissions as directed edges
4. Run graph algorithms to discover attack paths
5. Generate a security kill-chain report

---

# 🧠 Key Features

- Kubernetes RBAC attack path discovery
- Graph-based security model
- Privilege escalation detection
- CVSS weighted risk scoring
- Attack path visualization
- Kill-chain report generation

---

# 🏗 System Architecture

```
Kubernetes Cluster
        │
        ▼
kubectl Data Extraction
        │
        ▼
Cluster Graph Builder (Python + NetworkX)
        │
        ▼
Security Analysis Engine
│        │        │
BFS    Dijkstra   DFS
        │
        ▼
Kill Chain Report
        │
        ▼
Interactive Attack Graph (D3.js / Cytoscape.js)
```

---

# 🛠 Tech Stack

## Backend
- Python
- NetworkX
- Click CLI Framework

## Frontend
- D3.js
- Cytoscape.js

## Database
- JSON
- Neo4j (optional)

## APIs
- Kubernetes API
- NIST NVD API

## Tools
- kubectl
- Docker

---

# 📂 Planned Repository Structure

```
cluster-shield
│
├── cli
│   └── main.py
│
├── graph
│   └── graph_builder.py
│
├── analysis
│   ├── bfs.py
│   ├── dijkstra.py
│   └── dfs.py
│
├── visualization
│   └── attack_graph.js
│
├── reports
│   └── report_generator.py
│
├── docs
│
└── README.md
```

---

# 🚧 Development Status

Project under development for **Hack2Future 2.0 Hackathon**

Planned milestones:

- [ ] Kubernetes cluster data ingestion
- [ ] Graph construction
- [ ] Attack path detection algorithms
- [ ] Risk scoring engine
- [ ] Interactive attack graph visualization
- [ ] Kill chain report generation

---

# 👥 Team

**Team Name:** ClusterShield

- Rakshita — Graph Algorithms
- Vinod — Backend Development
- Sharada — Security Analysis
- Sanskurti — Frontend & Visualization

---

# 🚀 Future Scope

- CI/CD integration for automated attack path detection
- Multi-cluster security analysis
- Temporal attack path tracking
- GitHub Actions integration
- Real-time Kubernetes monitoring

---

# 📜 License

MIT License

---

# ⭐ Hackathon

Project built for **Hack2Future 2.0 – National Level Hackathon at IIIT Dharwad**
