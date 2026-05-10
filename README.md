# UVP Tools

uvp is a uv-based (mini) project management suite focused though not limited to lightweight Python projects.

Think "I want to create and experiment with a quick Python tool with a few dependencies. A full project setup seems overblown for what I need."

## Environment Variables

- `UVP_PROJECTS_DIR` - Directory where uv environments are stored (default: `$HOME/tmp/uvp-projects`)
- `UVP_DEFAULT_PYTHON_VERSION` - Default Python version for new environments (default: 3.14)
- `UVP_DESCRIPTION_FILE` - File used to store environment descriptions

## Installation

Clone this repository.

Copy and rename the file 'dot_zshrc_uvp' to ~/.zshrc_uvp.

Add the following to your shell configuration file (e.g., `.zshrc`):

```bash
source ~/.zshrc_uvp
```

## Functions

### `uvp_is_installed`
Check if the `uv` command is installed. Returns true/false.

### `uvp_venv_is_present`
Check if a `.venv` directory exists in the current directory.

### `uvp_projects_dir_is_present`
Verify that the `UVP_PROJECTS_DIR` environment variable points to an existing directory.

### `uvpn [env_name] [python_version]`
Create a new uv environment with an optional name and Python version (default: `$UVP_DEFAULT_PYTHON_VERSION`). Creates the environment in `UVP_PROJECTS_DIR`.

### `uvplast`
Get the most recently created uv environment and activate it.

### `uvpls`
List all uv environments stored in `UVP_PROJECTS_DIR`.

### `uvpgo [env_name]`
Go to a specific uv environment or the most recent one if no argument is given. Activates the environment upon arrival.

### `uvprm [env_name]`
Remove a specific uv environment or the most recent one if no argument is given.

### `uvpl [options]`
Lock the current uv environment with optional arguments passed to `uv lock`.

### `uvpp [python_version]`
Create a new uv environment for the current project with an optional Python version (default: `$UVP_DEFAULT_PYTHON_VERSION`). Uses existing `.venv` if present.

### `uvpa`
Activate the virtual environment in the current directory's `.venv`.

### `uvpd`
Deactivate the currently active virtual environment.

### `uvpstatus`
Show the status of the current uv environment, including whether a venv is active and how it was managed.

### `uvphelp`
Display help information for all uvp functions.

## Usage Examples

```bash
# Create a new named environment with Python 3.12
uvpn myproject 3.12

# List available environments
uvpls

# Switch to an existing environment
uvpgo myproject

# Work in current directory, create env if needed
uvpp

# Activate/deactivate current venv
uvpa
uvpd

# Lock dependencies
uvpl

# Check status
uvpstatus
```

## Notes

- Each new environment created with `uvpn` or `uvpp` generates a description file at `$UVP_DESCRIPTION_FILE`. Update this file to document your environment.
- The `uvpgo` and `uvprm` commands default to the most recent environment if no name is provided.
