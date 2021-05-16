---
title: Technology
description: Thales is built using Rust and the Substrate framework, enabling rich tools for implementation, but also allowing for specialization and optimization.
---

# Technology

## The Thales Development Stack

Thales is a smart contract blockchain platform built in the Rust programming language using the Substrate framework.  

### Rust Programming Language

Rust is a good language for implementing a blockchain, as it is highly performant like C and C++, but has built-in memory safety features that are enforced at compile time, which prevents many common bugs and security issues that can arise from C and C++ implementations.

### Substrate Framework

Substrate provides a rich set of tools for creating blockchains, including a runtime execution environment that enables a generic state transition function, and a pluggable set of modules that provide implementations of various blockchain subsystems.

Thales leverages multiple existing Substrate frame pallets to provide key blockchain services and functionality, including core blockchain data structures, peer-to-peer networking, consensus mechanisms, accounts, assets, and balances.  Custom pallets and logic in the runtime implement Thales-specific behavior and functionality, such as cross-chain token integration.  For leveraged pallets, Thales will strive to stay as close as possible to the upstream Substrate codebase and incorporate Substrate bug fixes, enhancements, and new features on an ongoing basis.

## Blockchain Runtime

The core Thales runtime specifies the state transition function and behavior of the Thales blockchain.  The Thales runtime is built using [FRAME](/resources/glossary/#substrate-frame-pallets). It includes several standard pallets as well as several custom ones. The runtime is compiled to a [WebAssembly (Wasm)](/resources/glossary/#webassemblywasm) binary as well as a native binary. These compiled versions will be executed in the Polkadot Relay Chain and Thales node environments.  

!!! note
    Substrate Frame Pallets are a collection of Rust-based modules providing functionality that is required when building a blockchain.  WebAssembly is an open standard that defines a portable binary code format. It is supported by different programming languages, compilers, and browsers. Find more definitions [in our glossary](/resources/glossary/).

Some of the key Substrate Frame Pallets used in the Thales runtime include:

 - **Balances** — Support for accounts, balances, and transfers.
 - **EVM** — Full Rust-based EVM implementation based on SputnikVM.  Provides the state transition logic for Thales-based smart contracts.
 - **Ethereum** — Provides emulation of Ethereum block processing for the EVM.
 - **RPC-Ethereum** — Web3 RPC implementation in Substrate.
 - **Council** — Includes governance mechanics around the council and proposals.
 - **Democracy** — Functionality for public stake-weighted token holder voting.
 - **Executive** — Orchestration layer that dispatches calls to other runtime modules.
 - **Indices** — Support for user-friendly shortnames for account addresses.
 - **System** — Provides low-level types, storage, and blockchain functions.
 - **Treasury** — On-chain treasury that can be used to fund public goods such as a parachain slot.

Thales also uses the Cumulus library to provide integration to the Polkadot relay chain.

In addition to these Substrate Frame Pallets, we will be implementing modules with Thales-specific functionality, including collator mechanics and rewards and other developer building blocks.

## Ethereum Compatibility Architecture

Smart contracts on Thales can be implemented using Solidity, Vyper, and any other language which can compile smart contracts to EVM-compatible bytecode.  Thalesbean aims to provide a low-friction and secure environment for the development, testing, and execution of smart contracts that is compatible with the existing Ethereum developer toolchain.  

The execution behavior and semantics of Thales-based smart contracts will strive to be as close to Ethereum Layer 1 as possible.  Thales is a single shard, so cross-contract calls have the same synchronous execution semantics as on Ethereum Layer 1.

![Diagram showing the interactions made possible through Thales's Ethereum compatibility](/images/technology-diagram.png)

A high-level interaction flow is shown above.  A Web3 RPC call from a DApp or existing Ethereum developer tool, such as Truffle, is received by a Thales node.  The node will have both Web3 RPCs and Substrate RPCs available, which means that you can use Ethereum or Substrate tools when interacting with a Thales node.  These RPC calls are handled by associated Substrate runtime functions.  The Substrate runtime checks signatures and handles any extrinsics.  Smart contract calls are ultimately passed to the EVM to execute the state transitions.

By basing our EVM implementation on the Substrate Pallet-EVM, we get a full Rust-based EVM implementation and support from the Parity engineering team.
