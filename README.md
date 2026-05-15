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

## Prerequisites

To use `ptx cluster --access` with `kubectl`, you need:

- **AWS CLI v2** — used by the generated kubeconfig to fetch EKS auth tokens (`aws eks get-token`)
- **kubectl** — for interacting with the cluster

Install AWS CLI:

| OS | Command |
|----|---------|
| macOS | `brew install awscli` |
| Linux (deb) | `sudo apt install awscli` |
| Windows | `winget install Amazon.AWSCLI` |

Without AWS CLI installed, `kubectl` will fail with `exec: executable aws not found`.

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

## Examples

### Connect to a cluster and list pods

After running `ptx cluster --access`, your kubeconfig is automatically merged and the context is set to the selected cluster:

```bash
ptx cluster --access            # interactive cluster picker
kubectl get pods -A             # list pods across all namespaces
kubectl get pods -n my-app      # list pods in a specific namespace
kubectl get nodes               # list cluster nodes
```

### Forward a VPC endpoint (core banking, RDS proxy, internal API)

Use `--host` and `--port` to forward an arbitrary VPC endpoint through the tenant's bastion:

```bash
# Start a forward to a VPC endpoint on port 443
ptx port-forward --start --host vpce-034cf664.us-west-2.vpce.amazonaws.com --port 443

# In another terminal, hit the service via localhost
curl https://localhost:443/healthcheck

# See what sessions are running
ptx port-forward --list

# Stop a session when you're done
ptx port-forward --stop          # interactive picker
ptx port-forward --stop-all      # stop everything
```

## Downloads

Binary releases are available on the [Releases](https://github.com/portx-labs/ptx-cli/releases) page.

## License

MIT License - see [LICENSE](LICENSE) for details.
