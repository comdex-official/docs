# Installation

This is for setting up a comdex **full node**.

## Hardware Requirements

We recommend the following for running Comdex Core:

- **2 or more** CPU cores
- At least **1TB** of disk storage
- At least **16GB** of memory
- At least **100mbps** network bandwidth

## Building Comdex Core

### Step 1. Install Golang

**Go v1.17.1 or higher is required for Comdex Core.**

If you haven't already, install Golang by following the [official docs](https://golang.org/doc/install). Make sure that your `GOPATH` and `GOBIN` environment variables are properly set up.

### Step 2: Get Comdex Core source code

Use `git` to retrieve Comdex Core from the [official repo](https://github.com/comdex-official/comdex/), and checkout the `main` branch, which contains the latest stable release. That should install the `comdex` binaries.

```bash
git clone https://github.com/comdex-official/comdex
cd comdex
git fetch --tags
git checkout v0.0.1
```

### Step 3: Build from source

You can now build Comdex Core. Running the following command will install executables `comdex` (Comdex node daemon) and `comdex` (CLI for interacting with the node) to your `GOPATH`.

```bash
make install
```

### Step 4: Verify your installation

Verify that everything is OK. If you get something like the following, you've successfully installed Comdex Core on your system.

```bash
comdex version --long
name: comdex
server_name: comdex
client_name: comdex
version: 
commit: 
build_tags: netgo,ledger
go: go version go1.17.1 darwin/amd64
```

## Production Environment

::: warning NOTE
This guide only covers general settings for a production-level full node. You can find further details on considerations for operating a validator node in our [Validator Guide](Validator_Guide.md)

For the moment, this guide has only been tested against RPM-based Linux distributions. 
:::


### Increase Maximum Open Files

`comdex` can open more than 1024 files (which is default maximum) concurrently.
You wil want to increase this limit.

Modify `/etc/security/limits.conf` to raise the `nofile` capability.

```
*                soft    nofile          65535
*                hard    nofile          65535
```

### Create a Dedicated User

`comdex` does not require the super user account. We **strongly** recommend using a normal user to run `comdex`. However, during the setup process you'll need super user permission to create and modify some files.

### Firewall Configuration

`comdex` uses several TCP ports for different purposes.

- `26656` is the default port for the P2P protocol. This port is opened in order to communicate with other nodes, and must be open to join a network. **However,** it does not have to be open to the public. For validator nodes, we recommend configuring `persistent_peers` and closing this port to the public.

- `26657` is the default port for the RPC protocol. This port is used for querying / sending transactions. In other words, this port needs to be opened for serving queries from `comdex`. It is safe to _NOT_ to open this port to the public unless you are planning to run a public node.

- `1317` is the default port for (LCD), which can be executed by `comdex rest-server`. LCD provides HTTP RESTful API layer to allow applications and services to interact with your `comdex` instance through RPC. Check the [Comdex REST API]() for usage examples. You don't need to open this port unless you have use of it.

- `26660` is the default port for interacting with the [Prometheus](https://prometheus.io) database which can be used for monitoring the environment. This port is not opened in the default configuration.

### Running Server as a Daemon

It is important to keep `comdex` running at all times. There are several ways to achieve this, and the simplest solution we recommend is to register `comdex` as a `systemd` service so that it will automatically get started upon system reboots and other events.

### Register Comdex as a service

First, create a service definition file in `/etc/systemd/system`.

#### Sample file: `/etc/systemd/system/comdex.service`

```
[Unit]
Description=Comdex Daemon
After=network.target

[Service]
Type=simple
User=ubuntu
ExecStart=/home/ubuntu/go/bin/comdex start
Restart=on-abort

[Install]
WantedBy=multi-user.target

[Service]
LimitNOFILE=65535
```

Modify the `Service` section from the given sample above to suit your settings.
Note that even if we raised the number of open files for a process, we still need to include `LimitNOFILE`.

After creating a service definition file, you should execute `systemctl daemon-reload` and `systemctl enable comdex`

### Controlling the service

Use `systemctl` to control (start, stop, restart)

```bash
# Start
systemctl start comdex
# Stop
systemctl stop comdex
# Restart
systemctl restart comdex
```

### Accessing logs

```bash
# Entire log
journalctl -t comdex
# Entire log reversed
journalctl -t comdex -r
# Latest and continuous
journalctl -t comdex -f
```
