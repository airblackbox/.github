# AIR Blackbox

**Open-source compliance infrastructure for AI agents — built for the EU AI Act.**

The August 2, 2026 enforcement deadline for high-risk AI systems is approaching. AIR Blackbox provides the audit trails, security controls, and compliance tooling that enterprises need to deploy AI agents legally in the EU.

## What We Do

Every AI agent decision gets recorded, every tool call gets gated, every prompt gets scanned — with tamper-evident HMAC-SHA256 audit chains that regulators can verify.

## Quick Start

```bash
pip install air-compliance        # Scan your project for EU AI Act gaps
air-compliance scan ./my-project  # Get a compliance report instantly
```

## Framework Trust Layers

Drop-in compliance for every major AI agent framework:

| Package | Framework | Install |
|---------|-----------|---------|
| [air-langchain-trust](https://github.com/airblackbox/air-langchain-trust) | LangChain / LangGraph | `pip install air-langchain-trust` |
| [air-crewai-trust](https://github.com/airblackbox/trust-crewai) | CrewAI | `pip install air-crewai-trust` |
| [air-openai-agents-trust](https://github.com/airblackbox/trust-openai-agents) | OpenAI Agents SDK | `pip install air-openai-agents-trust` |
| [air-autogen-trust](https://github.com/airblackbox/trust-autogen) | AutoGen / AG2 | `pip install air-autogen-trust` |
| [air-rag-trust](https://github.com/airblackbox/air-rag-trust) | RAG Knowledge Bases | `pip install air-rag-trust` |
| [openclaw-air-trust](https://github.com/airblackbox/trust-openclaw) | TypeScript / Node.js | `npm install openclaw-air-trust` |

## Compliance & Scanning

| Package | Purpose | Install |
|---------|---------|---------|
| [air-compliance](https://github.com/airblackbox/air-compliance-checker) | EU AI Act compliance scanner | `pip install air-compliance` |
| [Gateway](https://github.com/airblackbox/gateway) | Flight recorder reverse proxy | `docker pull ghcr.io/airblackbox/gateway:main` |
| [air-platform](https://github.com/airblackbox/air-platform) | Full stack (one command) | `docker compose up` |

## EU AI Act Coverage

Each trust layer provides controls mapped to specific articles:

- **Article 9** — Risk Management: ConsentGate classifies tool calls by risk level
- **Article 10** — Data Governance: DataVault tokenizes PII, ProvenanceTracker hashes KB documents
- **Article 11** — Technical Documentation: Structured audit logging with call graphs
- **Article 12** — Record-Keeping: HMAC-SHA256 tamper-evident chains
- **Article 14** — Human Oversight: Exception-based blocking, audit trail review
- **Article 15** — Robustness: InjectionDetector, WriteGate, DriftDetector

## Full Ecosystem (25 repos)

**Core Runtime:** Gateway, Agent-Episode-Store, Agent-Policy-Engine, Air-Platform

**Instrumentation:** Python-SDK, air-langchain-trust, air-crewai-trust, air-autogen-trust, air-openai-agents-trust, openclaw-air-trust, air-rag-trust

**Safety & Governance:** OTel-Collector-GenAI, OTel-Prompt-Vault, OTel-Semantic-Normalizer, Agent-Tool-Sandbox, Runtime-AIBOM-Emitter, AIBOM-Policy-Engine

**Evaluation & Testing:** Eval-Harness, Trace-Regression-Harness, Agent-VCR

**Security:** MCP-Security-Scanner, MCP-Policy-Gateway

**Compliance:** Air-Compliance-Checker

---

Apache 2.0 · Built on OpenTelemetry · [PyPI](https://pypi.org/search/?q=air+blackbox)
