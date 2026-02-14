# {{ project_name }}

{{ project_description }}

## Quick Start

### Installation
```bash
# Clone the repository
git clone <your-repo-url>
cd {{ project_name }}

# Set up the development environment
just setup
```

### Usage
```python
from {{ module_name }} import CONF, hello

# Access configuration
print(CONF.workspace.data_dir)

# Use module functions
print(hello())
```

## Development

### Available Commands
```bash
just              # List all available commands
just setup        # Install dependencies
just test         # Run tests
just format       # Format code
just lint         # Lint code
just typecheck    # Type check
just check        # Run all checks
just build        # Build package
```

### Configuration

The project can be configured via TOML files in the following locations (in priority order):

1. `/etc/{{ project_slug }}/config.toml` (system-wide)
2. `~/.{{ project_slug }}/config.toml` (user-specific)
3. `{{ project_slug }}.toml` (project-specific)

Example configuration:
```toml
project_name = "{{ project_name }}"
debug = false

[workspace]
data_dir = "data"
output_dir = "outputs"
models_dir = "models"
cache_dir = ".cache"
```

{% if use_remote_sync %}
### Remote Development

Deploy code to {{ remote_cluster_name }}:
```bash
just sync-remote
```
{% endif %}

### Running Tests
```bash
# Run all tests
just test

# Run with pytest directly
uv run pytest

# Run specific test file
uv run pytest tests/test_settings.py
```

### SLURM Scripts

#### Interactive Session
```bash
./scripts/srun.sh
```

This will prompt you for:
- Partition selection
- CPU count
- Memory allocation
- Time limit
- GPU requirements

#### Batch Job
```bash
sbatch scripts/example.sbatch
```

Edit `scripts/example.sbatch` to customize your job parameters and execution commands.

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
├── pyproject.toml             # Project configuration
├── justfile                   # Task automation
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