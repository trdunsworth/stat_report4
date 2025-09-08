# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a Python project called `stat-report4` using modern Python tooling with `pyproject.toml` configuration. The project is currently in early development stage with minimal structure.

## Development Environment

- **Python Version**: Requires Python 3.11+ (as specified in `pyproject.toml`)
- **Package Manager**: Uses `uv` for fast Python package management
- **Project Structure**: Standard Python project with `pyproject.toml` configuration

## Common Commands

### Environment Setup
```bash
# Create virtual environment using uv
uv venv

# Activate virtual environment
source .venv/bin/activate  # Linux/macOS
# or
.venv\Scripts\activate     # Windows

# Install project in development mode
uv pip install -e .
```

### Running the Application
```bash
# Run the main application
python3 main.py

# Or with uv
uv run main.py
```

### Development Workflow
```bash
# Install development dependencies (when added to pyproject.toml)
uv pip install -e ".[dev]"

# Run tests (when test framework is added)
uv run pytest

# Run linting (when linters are configured)
uv run ruff check
uv run ruff format

# Type checking (when mypy is added)
uv run mypy .
```

## Architecture

### Current Structure
- `main.py`: Entry point with basic hello world functionality
- `pyproject.toml`: Python project configuration
- `.python-version`: Python version specification (3.11)
- `.gitignore`: Standard Python gitignore patterns

### Development Patterns
- Use `pyproject.toml` for all project configuration
- Follow standard Python project structure as the codebase grows
- Consider adding these standard directories as the project develops:
  - `src/stat_report4/` - Main package code
  - `tests/` - Test files
  - `docs/` - Documentation

## Next Steps for Development

When expanding this project, consider adding:

1. **Testing Framework**: Add `pytest` to `[project.optional-dependencies]`
2. **Code Quality**: Add `ruff` for linting and formatting
3. **Type Checking**: Add `mypy` for static type analysis
4. **Pre-commit Hooks**: Set up `pre-commit` for automated code quality checks
5. **CI/CD**: Configure GitHub Actions or similar for automated testing

## Package Management with uv

This project uses `uv` for fast Python package management. Key benefits:
- Significantly faster than pip
- Better dependency resolution
- Built-in virtual environment management
- Compatible with existing Python ecosystem

### Adding Dependencies
```bash
# Add runtime dependency
uv add package-name

# Add development dependency
uv add --dev package-name

# Add optional dependency group
uv add --optional dev package-name
```

## Project Configuration

The `pyproject.toml` file is the single source of truth for:
- Project metadata
- Dependencies
- Build configuration
- Tool configurations (when tools are added)

When adding new tools, prefer configuring them in `pyproject.toml` rather than separate config files.
