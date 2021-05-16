---
title: Overview
description: As a Polkadot parachain, Thales will use an on-chain governance system, allowing for a stake-weighted vote on public referenda.
---

# Governance in Thales

![Governance Thales Banner](/images/governance/governance-overview-banner.png)

## Introduction

Thales is a decentralized network that will be governed by a community of token holders, including core developers, application developers, collators, users, and other contributors. 

We aim to facilitate the engagement of token holders from each of these categories as part of launching the network.

## General Definitions

With great power comes great responsibility. Some important parameters to understand before engaging with Thales's governance include:

 - **Proposals** — actions or items being proposed by token holders. This need to be seconded by other users in order to move to referendum
 - **Referendum** — when the most seconded proposal is voted on by the community. There can be a maximum of five active referenda at a time unless there is an emergency referendum in progress
 - **Launch period** — how often new public referenda are launched
 - **Voting period** — time token holders have to vote for a referendum (duration of a referendum)
 - **Fast-Track Voting period** — duration for voting for emergency proposals that address critical issues
- **Voting** — referenda are voted on by token holders on a stake and conviction weighted basis. Convictions refer to the time that token holders wish to lock their tokens when voting: the longer they are locked, the more weight their vote has. Referenda that pass are subject to delayed enactment so that people who disagree with the direction of the decision have time to exit the network
 - **Enactment period** — time between a proposal being approved and enacted (make law). It is also the minimum period necessary to lock funds to propose an action
 - **Lock period** — time (after the proposal enactment) that the tokens of the winning voters are locked. Users can still use this tokens for staking or voting
 - **Cool-off period** - The duration a veto from the technical committee lasts before the proposal may be submitted again 
 - **Delegation** — act of transferring your voting power to another account for up to a certain conviction

## Principles

Guiding "soft" principles for engagement with Thales's governance process include:

 - Being inclusive to token holders that want to engage with Thales and that are affected by governance decisions.
 - Favoring token holder engagement, even with views contrary to our own, versus a lack of engagement.
 - A commitment to openness and transparency in the decision-making process.
 - Working to keep the greater good of the network ahead of any personal gain.  
 - Acting at all times as a moral agent that considers the consequences of action (or inaction) from a moral standpoint.
 - Being patient and generous in our interactions with other token holders, but not tolerating abusive or destructive language, actions, and behavior.


## On-Chain Governance Mechanics

The "hard" governance process for Thales will be driven by an on-chain process and will leverage the Democracy, Council, and Treasury [Substrate frame pallets](/resources/glossary/#substrate-frame-pallets), similar to how Kusama and the Polkadot Relay Chain are governed. The overall intent of these modules are to allow the majority of tokens on the network to determine the outcomes of key decisions around the network. These decision points come in the form of stake-weighted voting on proposed referenda.

Some of the main components of this governance model include:

 - **Referendum** — a proposal for a change to the Thales system including values for key parameters, code upgrades, or changes to the governance system itself
 - **Voting** — referenda will be voted on by token holders on a stake-weighted basis. Referenda which pass are subject to delayed enactment such that people that disagree with the direction of the decision have time to exit the network
 - **Council** — a group of elected individuals who have special voting rights within the system. Council members are expected to propose referenda for voting and have an ability to veto publicly-sourced referenda. There are rolling elections for council members where GLMR holders will vote on new or existing council members. The Council is also responsible for electing the technical committee
 - **Technical Committee** — a group of individuals elected by the Council who have special voting rights. As in Polkadot and Kusama, the Technical Committee has the ability to (along with the Council) fast-track emergency referenda voting and implementation in urgent circumstances. A fast-tracked referendum can be created alongside existing active referenda. That is to say, an emergency referendum does not replace currently active referenda
 - **Treasury** — A collection of funds that can be spent by submitting a proposal along with a deposit. Spending proposals must be approved by the council. Rejected proposals will result in the proposer losing their deposit

See [this overview on the Polkadot website](https://polkadot.network/a-walkthrough-of-polkadots-governance/) and [this wiki post](https://wiki.polkadot.network/docs/en/learn-governance) for more details on how these Substrate frame pallets implement on-chain governance.

## Voting Rights of the Council and the Technical Committee

This section covers some background information on voting and outlines voting parameters of the protocol as they are set currently. There is a limit to the amount of time in blocks that the technical committee and the council have to vote on motions. Motions may end in fewer blocks if there are already enough votes submitted to determine the outcome. A maximum of {{ networks.thalesbase.democracy.max_proposals}} proposals can be open each in the technical committee and in the council.

Voting parameters are currently set as follows:

|             Variable             |     |                         Value                         |
| :------------------------------: | :-: | :---------------------------------------------------: |
|     Voting Period     |     |     {{ networks.thalesbase.democracy.vote_period.blocks}} blocks ({{ networks.thalesbase.democracy.vote_period.days}} days)     |
|        Fast-Track Voting Period        |     |     {{ networks.thalesbase.democracy.fast_vote_period.blocks}} blocks ({{ networks.thalesbase.democracy.fast_vote_period.days}} day)     | | 
|          Enactment Period           |     |     {{ networks.thalesbase.democracy.enact_period.blocks}} blocks ({{ networks.thalesbase.democracy.enact_period.days}} day)  |
| Cool-off Period |     |     {{ networks.thalesbase.democracy.cool_period.blocks}} blocks ({{ networks.thalesbase.democracy.cool_period.days}} days)  |
|              Minimum Deposit               |     | {{ networks.thalesbase.democracy.min_deposit }} GLMR |

**Voting Rights to Cancel:**

 * The technical committee may cancel a proposal before it has been passed only by unanimous vote
 * A single technical committee member may veto an inbound council proposal, however, they can only veto it once, and it only lasts for the cool-off period ({{ networks.thalesbase.democracy.cool_period.days}} days)
 * The technical committee may cancel a proposal before it has been passed only by unanimous vote


## Try it on Thalesbase Alpha

Currently, in our Thalesbase Alpha TestNet, token holders can submit proposals and vote on referenda. To do so, check the following guides:

 - [Submit a proposal](/governance/proposals/)
 - [Vote on a proposal](/governance/voting/)

The Treasury component has yet to be implemented.
