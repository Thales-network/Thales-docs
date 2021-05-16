---
title: Code Snippets
description: In order to make it easier to get started with Thales, here are code snippets for each of the tutorials we’ve created.
---

# Code Snippets

## Setting up a Local Thales Node

**Clone thales-tutorials repo:**

```
git clone -b {{ networks.development.build_tag }} https://github.com/Thales-network/thales
cd thales
```

**Install substrate and its pre-requisites:**

```
--8<-- 'code/setting-up-node/substrate.md'
```

**Add Rust to system path:**

```
--8<-- 'code/setting-up-node/cargoerror.md'
```

**Build the development node:**

```
--8<-- 'code/setting-up-node/build.md'
```

**Run node in dev mode:**

```
--8<-- 'code/setting-up-node/runnode.md'
```

**Purge chain, clean up any old data from running a ‘dev’ node in the past:**

```
./target/release/thales-development purge-chain --dev
```

**Run node in dev mode suppressing block information but prints errors in console:**

```
./target/release/thales-development --dev -lerror
```

## Genesis Account

--8<-- 'text/metamask-local/dev-account.md'

## Development Accounts

--8<-- 'code/setting-up-node/dev-accounts.md'

--8<-- 'code/setting-up-node/dev-testing-account.md'

## MetaMask

**Thales Development node details:**

--8<-- 'text/metamask-local/development-node-details.md'

**Thalesbase TestNet:**

--8<-- 'text/testnet/testnet-details.md'
