# ptx - PortX Platform CLI

The command-line interface for the PortX platform.

## Features

- **Authentication** - Secure login via OIDC device flow
- **Cluster Access** - Connect to EKS clusters and manage kubeconfig
- **Port Forwarding** - SSM-based port forwarding to databases and services
- **Project Management** - Provision and manage applications
- **Multi-Org Support** - `--org` flag and `PTX_ORG` env var for per-command tenant override

## Installation

### macOS / Linux (Homebrew)

```sh
brew tap portx-labs/portx-tap
brew install ptx
```

### Linux (apt)

```sh
echo "deb [trusted=yes] https://portx-labs.github.io/ptx-cli stable main" | sudo tee /etc/apt/sources.list.d/portx.list
sudo apt update
sudo apt install ptx
```

### Windows (Chocolatey)

```powershell
choco install ptx
```

### Windows (winget)

```powershell
winget install PortX.ptx
```

## Quick Start

```bash
# Configure your organization
ptx config add --org <your-org>

# Authenticate
ptx login

# Connect to a cluster
ptx cluster --access

# Forward a database port
ptx port-forward --start
```

## Usage

### Organization Override

Use `--org` or `PTX_ORG` to target a specific organization without changing your saved config:

```bash
# Per-command override (does NOT modify config.yaml):
ptx --org myorg cluster --access
ptx --org myorg port-forward --start

# Via environment variable:
PTX_ORG=myorg ptx cluster --access

# Login with --org persists it as the active org:
ptx login --org myorg
```

Priority: `--org` flag > `PTX_ORG` env var > `config.yaml` current_org_id.

## Downloads

Binary releases are available on the [Releases](https://github.com/portx-labs/ptx-cli/releases) page.

## License

MIT License - see [LICENSE](LICENSE) for details.
