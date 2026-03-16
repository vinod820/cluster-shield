🛡 ClusterShield – Kubernetes Attack Path Visualizer

Graph-Based Security Analysis for Cloud-Native Infrastructure

ClusterShield is a security analysis tool that discovers multi-hop attack paths inside Kubernetes clusters.
Instead of analyzing permissions individually, ClusterShield models the entire cluster as a directed graph and uses graph algorithms to detect potential privilege escalation chains.

This project is being built for Hack2Future 2.0 – IIIT Dharwad (Cloud Security Track).

🚨 Problem

Modern Kubernetes clusters contain many interconnected entities:

Pods

Service Accounts

Roles / RoleBindings

Secrets

External services

Security tools typically analyze these permissions individually, which makes it difficult to detect multi-step attack chains.

Example attack path:

Attacker → Pod → ServiceAccount → Secret → Production Database

Each step appears harmless individually, but together they create a privilege escalation chain.

ClusterShield identifies these hidden paths.

💡 Proposed Solution

ClusterShield builds a graph model of the Kubernetes cluster and applies graph algorithms to detect attack paths.

Core workflow

1️⃣ Extract cluster data

kubectl get pods
kubectl get roles
kubectl get rolebindings
kubectl get secrets

2️⃣ Convert entities into a directed graph

Nodes

Pods

ServiceAccounts

Roles

Secrets

Edges

Permission relationships

3️⃣ Run security analysis algorithms

Algorithm	Purpose
BFS	Find blast radius of a compromised node
Dijkstra	Find shortest exploit path
DFS	Detect circular privilege escalation

4️⃣ Generate a Kill Chain Security Report

attack path list

risk scores

recommended remediation

🧠 Key Features

✔ Kubernetes RBAC attack path discovery
✔ Graph-based security model
✔ Privilege escalation detection
✔ CVSS weighted risk scoring
✔ Attack path visualization
✔ Kill-chain report generation

🏗 System Architecture
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
Interactive Attack Graph (D3.js / Cytoscape)
🛠 Tech Stack

Backend

Python

NetworkX

Click CLI

Frontend

D3.js / Cytoscape.js

Database

JSON

Neo4j (optional)

APIs

Kubernetes API

NIST NVD API

Tools

kubectl

Docker

## 📂 Planned Repository Structure

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
└── docs
```
👥 Team

Team Name: ClusterShield

Members

Rakshita — Graph Algorithms

Vinod — Backend Development

Sharada — Security Analysis

Sanskurti — Frontend & Visualization

🚀 Status

Project under development for Hack2Future 2.0 Hackathon.

Implementation will begin during the hackathon.
