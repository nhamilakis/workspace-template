# Python Data Science Project Template

A modern, opinionated Copier template for Python data science projects with best practices baked in.

## Features

- 🚀 **Modern Python tooling**: Uses `uv` for fast dependency management and command execution
- 📦 **Proper package structure**: Source layout with `src/` directory
- ✅ **Quality tools**: Ruff for formatting/linting, mypy for type checking, pytest for testing
- 📚 **Documentation**: MkDocs with Material theme pre-configured
- 🔧 **Task automation**: Justfile for common development tasks
- 🎯 **SLURM support**: Pre-configured scripts for HPC job scheduling
- 🪝 **Pre-commit hooks**: Automated code quality checks
- 🔄 **Template updates**: Built on Copier for easy project updates

## Prerequisites

- Python 3.11 or higher
- [uv](https://github.com/astral-sh/uv) (`curl -LsSf https://astral.sh/uv/install.sh | sh`)
- [Copier](https://github.com/copier-org/copier) (`uvx copier` or `uv tool install copier`)
- [just](https://github.com/casey/just) (optional, for task automation)

## Quick Start

### Create a new project
```bash
uvx copier copy gh:nhamilakis/workspace-template .
```

```bash
uv tool run copier copy gh:nhamilakis/workspace-template .
```


### Set up the generated project

```bash
cd your-new-project

# Set up the development environment
just setup

```

## Available Just Commands

The generated project includes a `justfile` with common development tasks:

```bash
just setup          # Install dependencies and set up the environment
just test           # Run pytest
just format         # Format code with ruff
just lint           # Lint code with ruff
just typecheck      # Run mypy type checking
just docs-serve     # Serve documentation locally
just build          # Build the package with uv
just clean          # Clean build artifacts
```


## SLURM Scripts

### Interactive Session (`scripts/srun.sh`)

Start an interactive SLURM session with GPU/CPU resources:

```bash
./scripts/srun.sh
```

The script will prompt you for:
- Partition selection
- Number of CPUs
- Memory allocation
- Time limit
- GPU requirements

### Batch Job (`scripts/example.sbatch`)

Example SLURM batch script that you can customize for your specific jobs.

```bash
sbatch scripts/example.sbatch
```


## Project Structure
```
{{ project_name }}/
├── src/{{ module_name }}/     # Main package code
│   ├── __init__.py
│   ├── settings.py
│   └── utils.py
├── tests/                      # Test files
├── scripts/                    # SLURM scripts
│   ├── srun.sh
│   └── example.sbatch
├── docs/                       # Documentation
├── notebooks/                  # Jupyter notebooks
├── libs/                       # External libraries
├── pyproject.toml              # Project configuration
├── justfile                    # Task automation
└── README.md
```


## Documentation

Build and serve documentation locally:
```bash
just docs-serve
```

Then visit http://127.0.0.1:8000

## Contributing

1. Create a feature branch
2. Make your changes
3. Run checks: `just check`
4. Run tests: `just test`
5. Submit a pull request

## License

[Your License Here]

## Authors

- {{ author_name }} <{{ author_email }}>
