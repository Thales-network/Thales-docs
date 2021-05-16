---
title: Setting Up a Node
description: Follow this tutorial to learn how to set up your first Thales node. You’ll also learn how to connect it to and control it with the Polkadot JS GUI.
---

# Setting Up a Thales Node and Connecting to the Polkadot JS GUI

<style>.caption { font-family: Open Sans, sans-serif; font-size: 0.9em; color: rgba(170, 170, 170, 1); font-style: italic; letter-spacing: 0px; position: relative;}</style><div class='caption'>You can find all of the relevant code for this tutorial on the <a href="{{ config.site_url }}resources/code-snippets/">code snippets page</a></div>

## Introduction

This guide outlines the steps needed to create a development node for testing the Ethereum compatibility features of Thales.

!!! note
    This tutorial was created using the {{ networks.development.build_tag }} tag of [Thalesbase](https://github.com/Thales-network/thales/releases/tag/{{ networks.development.build_tag }}). The Thales platform and the [Frontier](https://github.com/paritytech/frontier) components it relies on for Substrate-based Ethereum compatibility are still under very active development.
    --8<-- 'text/common/assumes-mac-or-ubuntu-env.md'

A Thales development node is your own personal development environment for building and testing applications on Thales. For Ethereum developers, it is comparable to Ganache. It enables you to get started quickly and easily without the overhead of a relay chain. You can spin up your node with the `--sealing` option to author blocks instantly, manually, or at a custom interval after transactions are received. By default a block will be created when a transaction is received, which is similar to Ganache's instamine feature. 

If you follow to the end of this guide, you will have a Thales development node running in your local environment, with 10 [pre-funded accounts](#pre-funded-development-accounts), and will be able to connect it to the default Polkadot JS GUI.

## Getting Started with the Binary File

!!! note
    If you know what you are doing, you can directly download the precompiled binaries attached to each release on the [Thales-release page](https://github.com/Thales-network/thales/releases). These will not work in all systems. For example, the binaries only work with x86-64 Linux with specific versions of dependencies. The safest way to ensure compatibility is to compile the binary in the system where it will be run from.

First, start by cloning a specific tag of the Thales repo that you can find here:

[https://github.com/Thales-network/thales/](https://github.com/Thales-network/thales/)

```
git clone -b {{ networks.development.build_tag }} https://github.com/Thales-network/thales
cd thales
```

Next, install Substrate and all its prerequisites (including Rust) by executing:

```
--8<-- 'code/setting-up-node/substrate.md'
```

Once you have followed all of the procedures above, it's time to build the development node by running:

```
--8<-- 'code/setting-up-node/build.md'
```

If a _cargo not found error_ shows up in the terminal, manually add Rust to your system path (or restart your system):

```
--8<-- 'code/setting-up-node/cargoerror.md'
```

!!! note
    The initial build will take a while. Depending on your hardware, you should expect approximately 30 minutes for the build process to finish.


Then, you will want to run the node in dev mode using the following command:

```
--8<-- 'code/setting-up-node/runnode.md'
```

!!! note
    For people not familiar with Substrate, the `--dev` flag is a way to run a Substrate-bas

For more information on some of the flags and options used in the example, check out [Common Flags and Options](#common-flags-and-options). If you want to see a complete list of all of the flags, options, and subcommands, open the help menu by running:

```
./target/release/thales --help
```
## Connecting Polkadot JS Apps to a Local Thales Node

The development node is a Substrate-based node, so you can interact with it using standard Substrate tools. The two provided RPC endpoints are:

 - HTTP: `http://127.0.0.1:9933`
 - WS: `ws://127.0.0.1:9944` 

Start by connecting to it with Polkadot JS Apps. Open a browser to: [https://polkadot.js.org/apps/#/explorer](https://polkadot.js.org/apps/#/explorer). This will open Polkadot JS Apps, which automatically connects to Polkadot MainNet.

![Polkadot JS Apps](/images/setting-up-a-node/setting-up-node-5.png)

Click on the top left corner to open the menu to configure the networks, and then navigate down to open the Development sub-menu. In there, you will want to toggle the "Local Node" option, which points Polkadot JS Apps to `ws://127.0.0.1:9944`. Next, select the Switch button, and the site should connect to your Thales development node.

![Select Local Node](/images/setting-up-a-node/setting-up-node-6.png)

With Polkadot JS Apps connected, you will see the Thales development node waiting for transactions to arrive to begin producing blocks.


## Common Commands, Flags and Options

### Purging the Chain

When running a node via the binary file, data is stored in a local directory typically located in `~/.local/shared/thales/chains/development/db`. If you want to start a fresh instance of the node, you can either delete the content of the folder, or run the following command inside the `thales` folder:

```
./target/release/thales purge-chain --dev -y
```

This will remove the data folder, note that all chain data is now lost.

If you used Docker, the data folder is related to the Docker container itself.
### Node Flags

Flags do not take an argument. To use a flag, add it to the end of a command. For example:

```
--8<-- 'code/setting-up-node/runnode.md'
```

- `--dev`: Specifies the development chain
- `--no-telemetry`: Disable connecting to the Substrate telemetry server. For global chains, telemetry is on by default. Telemetry is unavailable if you are running a development (`--dev`) node.
- `--tmp`: Runs a temporary node in which all of the configuration will be deleted at the end of the process
- `--rpc-external`: Listen to all RPC interfaces
- `--ws-external`: Listen to all Websocket interfaces

### Node Options

Options accept an argument to the right side of the option. For example:

```
--8<-- 'code/setting-up-node/runnodewithsealinginterval.md'
```

- `-l <log pattern>` or `--log <log pattern>`: Sets a custom logging filter. The syntax for the log pattern is `<target>=<level>`. For example, to print all of the RPC logs, the command would look like this: `-l rpc=trace`.
- `--sealing <interval>`: When blocks should be sealed in the dev service. Accepted arguments for interval: `instant`, `manual`, or a number representing the timer interval in milliseconds (for example, `6000` will have the node produce blocks every 6 seconds). The default is `instant`.
- `--rpc-port <port>`: Sets the HTTP RPC server TCP port. Accepts a port as the argument.
- `--ws-port <port>`: Sets the WebSockets RPC server TCP port. Accepts a port as the argument.

For a complete list of flags and options, spin up your Thales development node with `--help` added to the end of the command.

## Advanced Flags and Options

--8<-- 'text/setting-up-node/advanced-flags.md'

For example, when running the binary:

```
./target/release/thales --dev --execution=Native --ethapi=debug,trace
```

## Pre-funded Development Accounts

Your Thales development node comes with ten pre-funded accounts for development. The addresses are derived from Substrate's canonical development mnemonic: 

```
bottom drive obey lake curtain smoke basket hold race lonely fit walk
```

--8<-- 'code/setting-up-node/dev-accounts.md'

Checkout the [Using MetaMask](/getting-started/local-node/using-metamask/) section to get started interacting with your accounts.

Also, included with the development node is a prefunded account used for testing purposes:

--8<-- 'code/setting-up-node/dev-testing-account.md'
