---
title: Vision
description: Thales is designed to enable a multi-chain future, where users and assets can move freely across many specialized and heterogenous chains.
---

# Our Vision for Thales

We believe in a multi-chain future with many chains, and many users and assets on those chains. In this context, we have created Thales: a smart contract platform that provides an Ethereum-compatible environment for building decentralized applications. Thales was designed to serve these new kinds of assets and users that exist across two or more chains.

Existing smart contract platforms are designed to service the users and assets on a single, specific chain.  By providing cross-chain smart contract functionality, Thales allows developers to shift existing workloads and logic to Thales and extend the reach of their applications to new users and assets on other chains.

Thales's cross-chain integration is accomplished by becoming a [parachain](/resources/glossary/#parachains) on the Polkadot network.  The [Polkadot network](/resources/glossary/#polkadot) provides integration and connectivity between parachains that are connected to the network and to other non-Polkadot-based chains, such as Ethereum and Bitcoin, via bridges.

## Who Benefits From Thales

There are three main audiences who can most benefit from Thales's cross-chain functionality:

### Existing Ethereum-Based Projects

Projects that are struggling with cost and scalability challenges on Ethereum can use Thales to: 

 - Move portions of their existing workloads and state off of Ethereum Layer 1 with minimal required changes.  
 - Implement a hybrid approach, where applications live on both Ethereum and Thales simultaneously.  
 - Extend their reach to the Polkadot network and other chains that are connected to Polkadot.  

### Polkadot Ecosystem Projects

Ecosystem projects that need smart contract functionality can use Thales to:  

 - Augment their existing parachains and parathreads.  
 - Add new functionality that is needed but not included on the main [Polkadot Relay Chain](/resources/glossary/#relay-chain). For example, they could create a place where teams can crowdfund their projects, implement lockdrops, and process other, more complex financial transactions than are provided by base [Substrate](/resources/glossary/#substrate) functionality.  
 - Leverage the mature and extensive Ethereum development toolchain.  

### Developers of New DApps

Individuals and teams that want to try building on Polkadot can use Thales to: 

 - Leverage the specialized functionality from Polkadot parachains while reaching users and assets on other chains.  
 - Compose functionality from Polkadot parachains by using Thales as a lightweight integration layer that aggregates network services before presenting them to end users. Implementing a composed service using pre-built integrations on a smart contract platform will be a lot faster and easier (in many cases) than building a full Substrate runtime and performing the integrations yourself in the runtime.  

## Key Features and Functionality

Thales achieves these goals with the following key features:  

 - **Decentralized and Permissionless** , providing a base requirement for censorship resistance and support for many existing and future DApp use cases.  
 - **Contains a Full EVM Implementation** , enabling Solidity-based smart contracts to be migrated with minimal change and with expected execution results.  
 - **Implements the Web3 RPC API** so that existing DApp front-ends can be migrated with minimal change required, and so existing Ethereum-based tools, such as Truffle, Remix, and MetaMask, can be used without modification against Thales.  
 - **Compatible with the Substrate Ecosystem Toolset** , including block explorers, front-end development libraries, and wallets, allowing developers and users to use the right tool for what they are trying to accomplish.  
 - **Native Cross-Chain Integration** via the Polkadot network and via token bridges, which allows for token movement, state visibility, and message passing with Ethereum and other chains.  
 - **On-Chain Governance** to allow stakeholders to quickly and forklessly evolve the base protocol according to developer and community needs.  

This unique combination of elements fills a strategic market gap, while allowing Thales to address future developer needs as the Polkadot network grows over time.  Building your own chain with Substrate is powerful, but also comes with a number of additional responsibilities, such as learning and implementing the chain’s runtime in Rust, creating a token economy, and incentivizing a community of node operators.

For many developers and projects, an Ethereum-compatible smart contract approach will be much simpler and faster to implement.  And by building these smart contracts on Thales, developers can still integrate with other chains and get value from Polkadot-based network effects.
