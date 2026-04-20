# AIR Blackbox

**The open-source trust infrastructure for autonomous AI agents.**
Record. Replay. Enforce. Audit. With post-quantum signed evidence.

[![airblackbox.ai](https://img.shields.io/badge/airblackbox.ai-00D4AA?style=for-the-badge)](https://airblackbox.ai)
[![Apache 2.0](https://img.shields.io/badge/license-Apache%202.0-blue?style=for-the-badge)](https://www.apache.org/licenses/LICENSE-2.0)
[![EU AI Act](https://img.shields.io/badge/EU%20AI%20Act-Aug%202%2C%202026-red?style=for-the-badge)]()
[![Post-Quantum](https://img.shields.io/badge/ML--DSA--65-FIPS%20204-purple?style=for-the-badge)](https://csrc.nist.gov/pubs/fips/204/final)

---

## The problem

On August 2, 2026, EU AI Act enforcement begins. Fines reach €35M or 7% of global annual turnover. Every AI agent in production needs three things regulators will ask for:

1. **Proof the code is built to standard** — before it ships
2. **Control over what agents are allowed to do** — at runtime
3. **A tamper-evident record of what they actually did** — that survives the arrival of quantum computers

## The stack

AIR Blackbox is seven open-source packages that compose. Install one. Install all of them. Same keys, same signatures, same evidence format across the entire stack.

```
         ┌──────────────────────────────────────────────────┐
         │              YOUR AI AGENT                       │
         │  (OpenAI · Anthropic · LangChain · CrewAI · …)   │
         └───────────────────────┬──────────────────────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │                  │                  │
              ▼                  ▼                  ▼
      ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
      │  air-blackbox │  │     Gate      │  │   air-gate    │
      │  scan + CLI   │  │ covenants +   │  │ human-in-the- │
      │  51+ checks   │  │  receipts     │  │ loop + PII    │
      └───────┬───────┘  └───────┬───────┘  └───────┬───────┘
              │                  │                  │
              └──────────────────┼──────────────────┘
                                 ▼
                         ┌───────────────┐
                         │   air-trust   │
                         │  HMAC + Ed25519 + ML-DSA-65 │
                         └───────┬───────┘
                                 ▼
                         ┌───────────────┐
                         │   .air-evidence  │
                         │  self-verifying  │
                         │   audit bundle   │
                         └───────────────┘
```

## The packages

### Core

**[airblackbox](https://github.com/airblackbox/airblackbox)** · *Start here*
EU AI Act scanner (51+ checks across Articles 9–15), audit gateway, Gate policy engine with bilateral receipts. The flight recorder and the brain.
`pip install air-blackbox`

**[air-trust](https://github.com/airblackbox/air-trust)**
Cryptographic primitives. HMAC-SHA256 audit chains, Ed25519 signed handoffs, ML-DSA-65 post-quantum signatures (FIPS 204). Every signing operation across the stack routes through here.
`pip install air-trust`

**[air-gate](https://github.com/airblackbox/air-gate)**
Human-in-the-loop tool gating with Slack approvals, PII redaction across 25+ categories (HIPAA, PCI-DSS, GDPR), and framework wrappers for LangChain and OpenAI function tools. Runs as a library or FastAPI server.
`pip install air-gate`

### Deployment

**[air-platform](https://github.com/airblackbox/air-platform)**
Full stack in one command. Docker Compose starts Gateway + Episode Store + Policy Engine + Jaeger + Prometheus in ~8 seconds.
`git clone && make up`

**[air-controls](https://github.com/airblackbox/air-controls)** · **[air-controls-mcp](https://github.com/airblackbox/air-controls-mcp)**
Policy controls runtime and its MCP server. Expose AIR's governance primitives to any MCP-compatible client.

### Integrations

**[air-blackbox-mcp](https://github.com/airblackbox/air-blackbox-mcp)**
MCP server with 10 tools. Works with Claude Desktop, Cursor, Claude Code, or any MCP client. `scan_code`, `classify_risk`, `check_injection`, `suggest_fix`, and more.

**[air-blackbox-plugin](https://github.com/airblackbox/air-blackbox-plugin)**
Claude Code plugin. Four slash commands (`/air-discover`, `/air-comply`, `/air-replay`, `/air-export`) plus a skill that teaches Claude Code how to interpret scan output against specific EU AI Act articles.

```
/plugin marketplace add airblackbox/air-blackbox-plugin
/plugin install air-blackbox@air-blackbox
```

### Observability

**[otel-collector-genai](https://github.com/airblackbox/otel-collector-genai)**
OpenTelemetry Collector processor for GenAI workloads. Redact prompts, detect loops, emit compliance metrics. Drop it into any existing OTel pipeline.

**[otel-prompt-vault](https://github.com/airblackbox/otel-prompt-vault)**
Content-addressed vault for prompts and completions. Traces reference content by hash — sensitive data never hits your observability backend.

## Quickstart — pick your entry point

**I want to scan my Python AI code right now.**
```bash
pip install air-blackbox
air-blackbox comply --scan . -v
```

**I want to add an audit gateway in front of my existing OpenAI calls.**
```python
client = OpenAI(
    base_url="http://localhost:8080/v1",
    default_headers={"X-Gateway-Key": "your-key"},
)
# everything else in your code stays identical
```

**I want to run the whole stack.**
```bash
git clone https://github.com/airblackbox/air-platform.git
cd air-platform && make up
```

**I want AI governance inside my editor.**
```
/plugin marketplace add airblackbox/air-blackbox-plugin
/plugin install air-blackbox@air-blackbox
```

## Why post-quantum today

Every other "AI audit trail" on the market signs with HMAC or RSA. Both will be breakable by quantum computers within the retention window of records you're generating right now. EU AI Act Article 12 requires logs kept for at least six months, often years.

AIR Blackbox signs with **ML-DSA-65 (FIPS 204 / Dilithium3)** — NIST's standardized post-quantum signature. Keys generated locally, never leave your machine. Evidence produced today still verifies in 2035.

## Validated by

- **Julian Risch** (deepset / Haystack) — public validation, 38-minute response time on GitHub
- **Piero Molino** (Ludwig) — merged compliance changes driven by AIR scan results
- **arXiv AEGIS** (Mar 2026) — independent research published the same interception architecture
- **McKinsey State of AI Trust 2026** — trust infrastructure named as the critical agentic AI category
- Listed in [awesome-ai-regulation](https://github.com/EthicalML/awesome-artificial-intelligence-regulation) and [awesome-eu-ai-act](https://github.com/GenAI-Gurus/awesome-eu-ai-act)

## Philosophy

AIR is a witness, not a gatekeeper — until you tell it to be. Recording never breaks production flow. Dropped audit records are acceptable; dropped user requests are not. You cannot trust what you cannot prove.

## License

Everything is Apache 2.0. Use it in commercial products. Fork it. Sell services around it. Keep the attribution.

---

**[airblackbox.ai](https://airblackbox.ai)** · [Documentation](https://airblackbox.ai/docs) · [Demo](https://airblackbox.github.io/air-platform/hosted-demo.html) · [Star the core repo](https://github.com/airblackbox/airblackbox) to help other teams find us.

*Not legal advice. A linter, not a lawyer. AIR Blackbox checks technical requirements; full EU AI Act compliance also requires organizational processes, documentation, and — depending on your risk classification — external conformity assessment.*
