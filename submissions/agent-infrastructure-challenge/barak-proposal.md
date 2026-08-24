--- /dev/null
+++ b/submissions/agent-infrastructure-challenge/barak-proposal.md
@@ -0,0 +1,18 @@
+# Agent Infrastructure Challenge - Proposal Submission
+
+**Author:** Barak  
+**Challenge:** Agent Infrastructure Challenge  
+
+## Overview
+This proposal introduces **Native Tool-Calling support** within the GaiaNet/LlamaEdge API server (Rust). This upgrade transforms GaiaNet nodes from passive knowledge bases into active, autonomous agents capable of structured decision-making and tool execution within the secure WasmEdge sandbox.
+
+## Key Features
+- **Native Tool Detection:** Middle-layer implementation for parsing model-generated function calls.
+- **Active Agentic RAG:** Enabling agents to decide when to perform vector lookups vs. external actions.
+- **Base Network Integration:** A working PoC demonstrating on-chain operations (balance checks, smart contract interaction) directly from the node.
+
+## PoC Repository
+[Technical Architecture and PoC Code](https://github.com/bmnaorpop-spec/gaianet-agent-infrastructure)