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
pip install air-langchain-trust   # LangChain
pip install air-adk-trust         # Google ADK
pip install air-crewai-trust      # CrewAI
```

**Full stack** (Gateway + Jaeger + Dashboard):

```bash
git clone https://github.com/airblackbox/air-platform
cd air-platform && make up
```

### Repositories

| Repo | What it does |
|------|-------------|
| [**gateway**](https://github.com/airblackbox/gateway) | AI governance control plane — CLI, reverse proxy, audit trails |
| [**air-platform**](https://github.com/airblackbox/air-platform) | Full stack deployment (Docker Compose) |
| [**compliance-action**](https://github.com/airblackbox/compliance-action) | GitHub Action — EU AI Act compliance checks on every PR |
| [**air-blackbox-mcp**](https://github.com/airblackbox/air-blackbox-mcp) | MCP server for Claude Desktop and Cursor |
| [**air-gate**](https://github.com/airblackbox/air-gate) | HMAC-SHA256 audit chain engine with tool gating |
| [**air-adk-trust**](https://github.com/airblackbox/air-adk-trust) | Trust layer for Google Agent Development Kit |

### PyPI Packages

| Package | Version | Install |
|---------|---------|---------|
| [air-blackbox](https://pypi.org/project/air-blackbox/) | — | `pip install air-blackbox` |
| [air-langchain-trust](https://pypi.org/project/air-langchain-trust/) | 0.2.0 | `pip install air-langchain-trust` |
| [air-adk-trust](https://pypi.org/project/air-adk-trust/) | 0.3.0 | `pip install air-adk-trust` |
| [air-crewai-trust](https://pypi.org/project/air-crewai-trust/) | 0.1.0 | `pip install air-crewai-trust` |

### Links

- 🌐 [airblackbox.ai](https://airblackbox.ai)
- 📖 [Quickstart Guide](https://airblackbox.ai/quickstart.html)
- 📖 [Integration Guides](https://airblackbox.ai/guides.html)

---

<sub>EU AI Act enforcement begins August 2, 2026. Start now.</sub>
