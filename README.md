# ptx - PortX Platform CLI

The command-line interface for the PortX platform.

## Features

- **Authentication** - Secure login via OIDC device flow
- **Cluster Access** - Connect to EKS clusters and manage kubeconfig
- **Port Forwarding** - SSM-based port forwarding to databases and services
- **Project Management** - Provision and manage applications

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

## Downloads

Binary releases are available on the [Releases](https://github.com/portx-labs/ptx-cli/releases) page.

## License

MIT License - see [LICENSE](LICENSE) for details.
