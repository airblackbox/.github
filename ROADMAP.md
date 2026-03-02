# AIR Blackbox Roadmap

This document outlines the planned work for the AIR Blackbox platform. We're building the most comprehensive compliance scanning solution for AI/LLM applications ahead of the **August 2, 2026 EU AI Act enforcement deadline**.

## Q2 2026 (April - June)

### Documentation Site Launch
- Complete comprehensive documentation at https://docs.airblackbox.ai
- Interactive examples and tutorials
- API reference with code samples
- Best practices guide for compliance scanning

### CI/CD on Core Repos
- GitHub Actions workflows for all core repositories
- Automated testing on Python 3.11+ and Go 1.22+
- Code coverage enforcement (minimum 80%)
- Automated linting with Ruff (Python) and golangci-lint (Go)
- Security scanning integration (CodeQL, Dependabot)

### Tagged Releases & PyPI Polish
- Semantic versioning across all projects
- Release notes following Keep a Changelog format
- Optimized PyPI package structure
- Automated publishing from CI/CD

## Q3 2026 (July - September)

### v1.0 Stable Release (Target: August 2026)
- API stability guarantees
- Long-term support commitment
- Production-ready guarantees
- Migration guide for pre-1.0 users

### EU AI Act Compliance Push
- Full alignment with EU AI Act technical requirements
- Audit-ready configuration templates
- Risk assessment tooling
- Deadline support: August 2, 2026 enforcement

### Design Partner Program
- Onboard 3-5 design partners
- Regular feedback loops
- Early access to new features
- Case study development

### Enterprise Features
- SSO (OIDC/SAML) support
- Multi-tenancy and organization isolation
- Advanced RBAC
- Comprehensive audit logging
- API keys and service accounts

## Future Considerations

- Kubernetes integration (Helm charts, operators)
- SaaS hosted platform
- ML-based compliance prediction
- Custom rules engine
- Community marketplace for integrations

## How to Contribute

1. **Vote on features** through GitHub Discussions
2. **Propose new features** with detailed requirements
3. **Volunteer to implement** planned features
4. **Provide feedback** on released features

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Contact

- **GitHub Discussions:** https://github.com/airblackbox
- **Email:** jason@airblackbox.ai
- **Website:** https://airblackbox.ai
