--- /dev/null
+++ b/submissions/agent-infrastructure-challenge/barak-native-tool-calling.md
@@ -0,0 +1,86 @@
+# Bounty Submission: Agent Infrastructure Challenge — Native Tool-Calling & Base Integration
+
+## Submitter
+**Name:** Barak  
+**GitHub:** bmnaorpop-spec  
+**Submission Date:** 2024  
+**Proposal Repository:** https://github.com/bmnaorpop-spec/gaianet-agent-infrastructure
+
+---
+
+## Summary
+
+This submission proposes introducing **Native Tool-Calling support** within the
+GaiaNet/LlamaEdge API server (Rust). The goal is to transform GaiaNet nodes
+from passive knowledge bases into active, autonomous agents capable of
+structured decision-making and tool execution within the secure WasmEdge
+sandbox.
+
+## Proposed Key Features
+
+### 1. Native Tool Detection
+A middle-layer implementation for parsing model-generated function calls.
+This involves intercepting model output, detecting structured tool-call
+intent, and routing the call to the appropriate handler.
+
+### 2. Active Agentic RAG
+Enabling agents to decide when to perform vector lookups (passive knowledge
+retrieval) versus when to take external actions (active tool execution). This
+replaces the current always-RAG pipeline with a conditional routing layer.
+
+### 3. Base Network Integration
+A working proof-of-concept demonstrating on-chain operations — specifically
+balance checks and smart contract interaction — directly from the GaiaNet
+node via the tool-calling infrastructure.
+
+## Technical Architecture (as described)
+
+```
+User Request
+    │
+    ▼
+┌──────────────────────────┐
+│  GaiaNet API Server (Rust)│
+│  ┌────────────────────┐  │
+│  │ LlamaEdge Infer     │  │
+│  │ (model generates    │  │
+│  tool-call JSON)       │  │
+│  └────────┬───────────┘  │
+│           │               │
+│  ┌────────▼───────────┐  │
+│  │ Tool-Call Parser   │  │
+│  │ (middle layer)     │  │
+│  └────────┬───────────┘  │
+│           │               │
+│  ┌────────▼───────────┐  │
+│  │ Router: RAG vs Tool │  │
+│  └───┬────────────┬───┘  │
+│      │            │       │
+│  ┌───▼───┐  ┌────▼────┐ │
+│  │ Vector │  │ Tool     │ │
+│  │ Store  │  │ Executor │ │
+│  │ (RAG)  │  │ (Wasm)   │ │
+│  └───────┘  └────┬────┘ │
+│                   │      │
+│  ┌────────────────▼───┐ │
+│  │ Base Network Plugin │ │
+│  │ (balance, contract) │ │
+│  └────────────────────┘ │
+└──────────────────────────┘
+    │
+    ▼
+Response to User
+```
+
+## Review Checklist
+
+- [ ] Submission repo is accessible
+- [ ] PoC code compiles (Rust)
+- [ ] Tool-calling parser correctly extracts function calls from model output
+- [ ] Router distinguishes RAG vs tool execution paths
+- [ ] Base network integration: balance check works
+- [ ] Base network integration: smart contract interaction works
+- [ ] Solution runs within WasmEdge sandbox
+- [ ] No unnecessary dependencies introduced
+- [ ] Documentation is clear and complete
+- [ ] License compatibility verified
+
+## Review Notes
+
+| Criterion | Status | Notes |
+|---|---|---|
+| Repo accessible | Pending | |
+| Native tool detection | Pending | |
+| Active agentic RAG | Pending | |
+| Base network integration | Pending | |
+| WasmEdge sandboxed | Pending | |
+| Code quality | Pending | |
+
+---
+
+## Bounty Details
+
+- **Challenge:** Agent Infrastructure Challenge
+- **Repository:** GaiaNet-AI/bounties
+- **Submission PR/Issue:** #3
+
+## Status
+
+**Under Review**
+
+This submission has been received and is pending technical evaluation by the
+GaiaNet team. The review will assess code quality, correctness of the
+tool-calling implementation, security of the Base network integration, and
+compatibility with the existing GaiaNet/LlamaEdge architecture.
