# Python Best Practices 2024

*Compiled on 2026-03-12*

This repository collects the most recent recommendations for modern Python development as of 2024. It is organized into four main sections.

## Code Style
- Use **Black** (or **Ruff formatter**) for automatic code formatting. Black 23.x supports the latest syntax (including pattern matching, type union `|`).
- Run **Ruff** as a linter; it combines flake8, pycodestyle, and isort functionality and is extremely fast.
- Enforce *import sorting* with **isort** (or let Ruff handle it).
- Prefer **f‑strings** over `%` or `str.format`.
- Keep line length at *88* (Black default) or configure to *120* if the project warrants it.

## Type Hints
- Adopt **PEP 484/PEP 585** style annotations. Use native collection types (`list[int]`, `dict[str, Any]`).
- Enable **strict** mode in **mypy** (`--strict`, `warn_unused_ignores`, `warn_unused_configs`).
- Consider **pyright** or **ruff**'s type‑checking mode for faster feedback in CI.
- Add **type‑guarded** stubs (`*.pyi`) only for external libraries lacking type info.

## Testing
- Use **pytest** as the primary test runner; its rich plugin ecosystem (e.g., `pytest-cov`, `pytest-asyncio`).
- Keep tests in a `tests/` package mirroring the source layout.
- Aim for *>90%* coverage, measured with `pytest --cov`.
- Leverage **hypothesis** for property‑based testing of edge cases.
- Run tests in isolated environments via **tox** or **nox**, targeting multiple Python versions (3.9‑3.12).

## Package Management
- Prefer **Poetry** for dependency management and packaging. It creates a deterministic lock file (`poetry.lock`).
- For CI/CD, use **uv** for fast virtual‑env creation and package installation.
- Publish wheels built with **cibuildwheel** for broad platform support.
- Keep `setup.cfg`/`pyproject.toml` minimal; declare build system using `setuptools>=68` or `flit` if appropriate.
- Use **dependabot** or **renovate** to keep dependencies up‑to‑date.

---
*This README will be expanded with deeper guides, configuration examples, and tooling recommendations.*
