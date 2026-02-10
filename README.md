# ptx - PortX Platform CLI

The command-line interface for the PortX platform.

## Features

- **Authentication** - OIDC device flow via Keycloak
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
echo "deb [trusted=yes] https://ptx-cli-releases.s3.amazonaws.com/apt stable main" | sudo tee /etc/apt/sources.list.d/portx.list
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

## Downloads

Binary releases are available on the [Releases](https://github.com/portx-labs/ptx-cli/releases) page.

## License

MIT License - see [LICENSE](LICENSE) for details.
