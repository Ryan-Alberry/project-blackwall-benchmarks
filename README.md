# Project Blackwall (`v1.1.1`)

**Air-Gapped, Zero-Trust Rust Sidecar Proxy for AI Agents & Model Context Protocol (MCP)**

Project Blackwall is a high-performance, local-first security sidecar built in Rust to secure the bidirectional execution boundary between autonomous AI agents, LLMs, and enterprise tools. Designed around aerospace limit-switch and precision tolerance principles, Blackwall intercepts, inspects, and sandboxes JSON-RPC MCP payloads inside the Kubernetes pod—eliminating cloud guardrail latency and third-party data exposure.

---

## Verified `v1.1.1` Benchmarks

| Audit Metric | Result | Scope |
| :--- | :--- | :--- |
| **Adversarial Red-Team Gauntlet** | **32 / 32 Blocked (100%)** | OWASP/MITRE ATLAS, AST parser bombs, parser differentials, homoglyphs, encoding obfuscation, DLP leaks |
| **Enterprise False-Positive Audit** | **50 / 50 Passed (0.0% FP)** | Healthcare, Energy Grid/Metrology, FinTech, DevSecOps, SQL Analytics |
| **Deterministic Block Latency** | **< 450 µs** | Stage A & Stage B-0 structural, schema, entropy, and heuristic blocks (1–144 µs Stage A) |
| **p99 End-to-End SLA** | **< 15 ms** | Verified under 500x concurrent burst load with embedded ONNX neural inference |
| **External Cloud Dependencies** | **Zero (Air-Gapped)** | 100% local execution; zero outbound API calls |

---

## Tri-Stage Defense Architecture

### Stage A — Structural & Differential Shield (The Limit Switch)
* **Pre-Parse AST Depth Clamping:** Drops deeply nested JSON parser bombs before deserialization.
* **Parser-Differential Protection:** Rejects duplicate keys to enforce the `Inspected == Executed` invariant.
* **Strict Schema & Tolerance Clamping:** Enforces whitelisted tool schemas, approved database tables, and hard numeric bounds for critical infrastructure.
* **SHA-256 Tool Metadata Pinning:** Detects and blocks silent tool-description poisoning.
* **Recursive Payload Unpacking:** Unwraps nested Base64, Hex, URL, and ASCII byte-array encodings prior to inspection.

### Stage B — De-Cloaking, Entropy & Local Neural Engine
* **Unicode De-Cloaking:** Strips zero-width characters and applies Fullwidth/NFKC canonicalization to defeat homoglyph smuggling.
* **Shannon Entropy Shield:** Sliding-window entropy detection catches GCG adversarial suffixes and high-entropy obfuscation.
* **Local ONNX Micro-Classifier (`ort`):** Embedded DeBERTa model evaluates semantic prompt injections and intent hijacking on-device.
* **Tenant-Isolated Session Tracking & DLP:** Isolates state by `tenant_id` and blocks outbound credential/secret exfiltration.
* **Tamper-Evident Audit Ledger:** SHA-256 hash-chained logging for cryptographic verification (`/verify-audit`).

### Stage C — Ephemeral Execution Vault (`Wasmtime`)
* **Deterministic CPU Fuel Metering:** Hard instruction-count ceiling terminates infinite loops and DoS payloads.
* **Strict Memory Ceiling:** Hard 16 MB linear RAM cap per execution instance.
* **Zero Host Syscalls:** Complete isolation from the host filesystem, environment variables, and network stack.

---

## Request a 30-Day Technical Sandbox Evaluation
Project Blackwall is distributed as a stripped, air-gapped OCI container for B2B OEM evaluation. 
To request a time-limited evaluation binary or schedule a 15-minute live terminal walkthrough, contact the founding team:
* **Ryan Alberry** — Co-Founder & Head of R&D
* **Michael Corley** — Co-Founder & Head of Operations
