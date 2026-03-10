<p align="center">
  <img src="https://raw.githubusercontent.com/airblackbox/gateway/main/logo.png" alt="AIR Blackbox" width="200">
</p>

<h1 align="center">AIR Blackbox</h1>

<p align="center">
  <strong>AI governance control plane — compliance, inventory, incident response, and audit for AI agents.</strong>
</p>

<p align="center">
  <a href="https://pypi.org/project/air-blackbox/"><img src="https://img.shields.io/pypi/v/air-blackbox" alt="PyPI"></a>
  <a href="https://github.com/airblackbox/gateway/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Apache--2.0-blue.svg" alt="License"></a>
  <a href="https://opentelemetry.io"><img src="https://img.shields.io/badge/OpenTelemetry-enabled-blueviolet?logo=opentelemetry" alt="OTel"></a>
</p>

```bash
pip install air-blackbox
```

## Four Commands

```bash
air-blackbox comply      # EU AI Act compliance from live traffic (20 checks, 90% automated)
air-blackbox discover    # Shadow AI inventory + AI-BOM generation (CycloneDX 1.6)
air-blackbox replay      # Incident reconstruction from HMAC audit chain
air-blackbox export      # Signed evidence bundle for auditors and insurers
```

## 30-Second Demo

```bash
pip install air-blackbox
air-blackbox demo          # Zero config. No Docker. See compliance in action.
```

## How It Works

AIR Blackbox is a reverse proxy + Python SDK. Route AI traffic through the gateway and every call is recorded, analyzed, and compliance-checked.

```
Your AI Agent → AIR Blackbox Gateway → LLM Provider
                      │
                      ├── HMAC-signed audit records
                      ├── PII detection + injection scanning
                      ├── AI-BOM (models, tools, providers)
                      ├── EU AI Act compliance (Articles 9-15)
                      └── Evidence export for auditors
```

## EU AI Act Coverage

| Article | What It Covers | Detection |
|---------|---------------|-----------|
| **Art. 9** — Risk Management | Risk docs, active mitigations | HYBRID |
| **Art. 10** — Data Governance | PII in prompts, data vault | AUTO + HYBRID |
| **Art. 11** — Technical Docs | AI-BOM inventory, model cards | AUTO + HYBRID |
| **Art. 12** — Record-Keeping | HMAC audit chain, traceability | **100% AUTO** |
| **Art. 14** — Human Oversight | Kill switch, approval gates | AUTO + MANUAL |
| **Art. 15** — Robustness | Injection detection, resilience | AUTO + MANUAL |

## Framework Support

```bash
pip install "air-blackbox[langchain]"    # LangChain / LangGraph
pip install "air-blackbox[openai]"       # OpenAI SDK
pip install "air-blackbox[all]"          # Everything
```

## Repositories

| Repo | What It Is |
|------|-----------|
| **[gateway](https://github.com/airblackbox/gateway)** | The unified platform — proxy + SDK + compliance + AI-BOM + replay + export |
| **[VaultMind](https://github.com/airblackbox/VaultMind)** | Private AI OS — local-first RAG chatbot for law firms |
| **[air-blackbox-mcp](https://github.com/airblackbox/air-blackbox-mcp)** | MCP server + EU AI Act compliance scanner for Claude Desktop |

> **August 2, 2026** — EU AI Act high-risk enforcement deadline. Penalties up to €35M or 7% of global turnover.

---

Apache 2.0 · Built on OpenTelemetry · [airblackbox.ai](https://airblackbox.ai)
