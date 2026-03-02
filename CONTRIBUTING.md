# Contributing to AIR Blackbox

Thank you for your interest in contributing to AIR Blackbox! We welcome contributions from developers, researchers, and security professionals.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally
3. **Create a feature branch** from `main`

## Code Style

### Python Projects
We use **Ruff** for linting and formatting:

```bash
pip install ruff
ruff format .
ruff check --fix .
```

### Go Projects
We use **golangci-lint**:

```bash
golangci-lint run ./...
```

## Testing

### Python
```bash
pytest --cov=. --cov-report=term-missing
```

### Go
```bash
go test -race -coverprofile=coverage.out ./...
```

## Pull Request Process

1. Push to your fork
2. Create a Pull Request with a clear title
3. Reference related issues (e.g., `Fixes #123`)
4. Address review feedback

## Commit Messages

- Use clear, descriptive messages
- Start with a verb (Add, Fix, Update, Remove, Refactor)
- Keep the first line under 70 characters

## Reporting Issues

1. Check existing issues to avoid duplicates
2. Include steps to reproduce, expected vs actual behavior, and environment details

## Code of Conduct

This project adheres to the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md).

## License

All contributions are licensed under the Apache License 2.0.
