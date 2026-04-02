<p align="center">
  <strong>AIR Blackbox</strong><br>
  Open-source compliance infrastructure for AI agents
</p>

<p align="center">
  Tamper-proof audit trails · PII tokenization · Policy enforcement · AI Bill of Materials
</p>

---

### What is AIR Blackbox?

AIR Blackbox is the compliance layer between your AI agents and production. It records every LLM call, tool invocation, and agent decision into tamper-evident audit chains — so you can prove what your AI did, when, and why.

Built for teams shipping AI agents that need to meet EU AI Act requirements by August 2026.

### Architecture

```
Your Agent Code
       │
       ▼
┌──────────────────┐
│   AIR Gateway    │  ← reverse proxy, records every LLM call
│   (Go binary)    │
└────────┬─────────┘
         │
    ┌────┴─────┬──────────────┬─────────────────┐
    ▼          ▼              ▼                 ▼
 Audit     PII            Policy           AI Bill of
 Chain     Tokenization   Engine           Materials
 (HMAC)    (DataVault)    (risk tiers)     (CycloneDX)
    │          │              │                 │
    └────┬─────┴──────────────┴─────────────────┘
         ▼
   Compliance Report
   (Articles 9–15)
```
### Get Started

```bash
pip install air-blackbox
```

**Framework trust layers** (drop-in, no code changes):

```bash
pip install air-langchain-trust     # LangChain / LangGraph
pip install air-crewai-trust        # CrewAI
pip install air-openai-trust        # OpenAI Agents SDK
pip install air-anthropic-trust     # Claude Agent SDK
pip install air-adk-trust           # Google ADK
pip install air-rag-trust           # RAG pipelines
```

**MCP server** (Claude Desktop, Claude Code, Cursor):

```bash
pip install air-blackbox-mcp
```

**Full stack** (Gateway + Episode Store + Policy Engine + Jaeger):

```bash
git clone https://github.com/airblackbox/air-platform
cd air-platform && make up
```
### Repositories

#### Core

| Repo | What it does |
|------|-------------|
| [**gateway**](https://github.com/airblackbox/gateway) | AI governance control plane — CLI scanner, reverse proxy, audit trails |
| [**air-platform**](https://github.com/airblackbox/air-platform) | Full stack Docker Compose deployment (Gateway + Episode Store + Policy Engine + Jaeger) |
| [**air-gate**](https://github.com/airblackbox/air-gate) | AI action firewall — HMAC-SHA256 audit chain with tool gating and PII redaction |
| [**air-blackbox-mcp**](https://github.com/airblackbox/air-blackbox-mcp) | MCP server — 14 compliance tools for Claude Desktop, Claude Code, and Cursor |
| [**compliance-action**](https://github.com/airblackbox/compliance-action) | GitHub Action — EU AI Act compliance checks on every PR |

#### Framework Trust Layers

| Repo | Framework |
|------|-----------|
| [**air-langchain-trust**](https://github.com/airblackbox/air-langchain-trust) | LangChain / LangGraph |
| [**trust-crewai**](https://github.com/airblackbox/trust-crewai) | CrewAI |
| [**air-adk-trust**](https://github.com/airblackbox/air-adk-trust) | Google Agent Development Kit |
| [**air-rag-trust**](https://github.com/airblackbox/air-rag-trust) | RAG pipelines |
#### Observability & Safety

| Repo | What it does |
|------|-------------|
| [**otel-collector-genai**](https://github.com/airblackbox/otel-collector-genai) | OTel Collector processor — PII redaction, cost metrics, loop detection |
| [**otel-prompt-vault**](https://github.com/airblackbox/otel-prompt-vault) | Encrypted prompt/completion storage with pre-signed URL retrieval |
| [**otel-semantic-normalizer**](https://github.com/airblackbox/otel-semantic-normalizer) | Normalizes gen_ai.* attributes to standard schema |
| [**runtime-aibom-emitter**](https://github.com/airblackbox/runtime-aibom-emitter) | AI Bill of Materials from runtime OTel traces (CycloneDX) |
| [**aibom-policy-engine**](https://github.com/airblackbox/aibom-policy-engine) | Policy-as-code for AI supply chain governance |
| [**mcp-security-scanner**](https://github.com/airblackbox/mcp-security-scanner) | Security scanner for MCP server configurations |
| [**mcp-policy-gateway**](https://github.com/airblackbox/mcp-policy-gateway) | Policy enforcement gateway for Model Context Protocol |

#### Evaluation & Testing

| Repo | What it does |
|------|-------------|
| [**eval-harness**](https://github.com/airblackbox/eval-harness) | Replay and score agent episodes against policies |
| [**trace-regression-harness**](https://github.com/airblackbox/trace-regression-harness) | Detect behavioral regressions across agent versions |
### PyPI Packages

| Package | Version | Install |
|---------|---------|---------|
| [air-blackbox](https://pypi.org/project/air-blackbox/) | 1.8.0 | `pip install air-blackbox` |
| [air-gate](https://pypi.org/project/air-gate/) | 0.2.0 | `pip install air-gate` |
| [air-blackbox-mcp](https://pypi.org/project/air-blackbox-mcp/) | 0.2.0 | `pip install air-blackbox-mcp` |
| [air-blackbox-sdk](https://pypi.org/project/air-blackbox-sdk/) | 0.1.1 | `pip install air-blackbox-sdk` |
| [air-compliance](https://pypi.org/project/air-compliance/) | 1.0.0 | `pip install air-compliance` |
| [air-langchain-trust](https://pypi.org/project/air-langchain-trust/) | 0.2.0 | `pip install air-langchain-trust` |
| [air-crewai-trust](https://pypi.org/project/air-crewai-trust/) | 0.1.0 | `pip install air-crewai-trust` |
| [air-openai-trust](https://pypi.org/project/air-openai-trust/) | 0.1.0 | `pip install air-openai-trust` |
| [air-anthropic-trust](https://pypi.org/project/air-anthropic-trust/) | 0.1.0 | `pip install air-anthropic-trust` |
| [air-adk-trust](https://pypi.org/project/air-adk-trust/) | 0.2.0 | `pip install air-adk-trust` |
| [air-rag-trust](https://pypi.org/project/air-rag-trust/) | 0.1.0 | `pip install air-rag-trust` |

### Links

- 🌐 [airblackbox.ai](https://airblackbox.ai)
- 📖 [Quickstart Guide](https://airblackbox.ai/quickstart.html)
- 📖 [Integration Guides](https://airblackbox.ai/guides.html)

---

<sub>EU AI Act enforcement begins August 2, 2026. Start now.</sub>