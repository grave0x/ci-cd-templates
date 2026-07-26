# Python CI Templates

Two variants:
- [`ci-python.yml`](../.github/workflows/ci-python.yml) — pip-based (standard)
- [`ci-python-uv.yml`](../.github/workflows/ci-python-uv.yml) — uv-based (faster, lockfile)

## Which one to use

| Use `ci-python.yml` (pip) | Use `ci-python-uv.yml` (uv) |
|---------------------------|-----------------------------|
| `requirements.txt` | `uv.lock` |
| `setup.py` / `setup.cfg` | `pyproject.toml` with `[tool.uv]` |
| No lockfile | Has lockfile |
| Poetry / Pipenv projects | uv-managed projects |

## What they check

| Step | Tool | Fails on |
|------|------|----------|
| Lint | `ruff check` | Style/lint violations |
| Format | `ruff format --check` | Unformatted code |
| Types | `mypy` (optional) | Type errors |
| Tests | `pytest` | Test failures |
| Build | `python -m build` / `uv build` | Packaging errors |

## Customization

- **Python version matrix**: Edit `python-version` in the matrix strategy.
- **Linter**: Replace `ruff` with `flake8`, `pylint`, or `black` by changing the CI step.
- **mypy**: Remove the type-check step if your project doesn't use it.
- **Test framework**: Replace `pytest` with `unittest` (`python -m unittest`).

## Prerequisites

- A `pyproject.toml`, `setup.py`, or `setup.cfg` at the repo root
- For the release template (pip): a `PYPI_API_TOKEN` secret, or trusted publishing configured on PyPI
