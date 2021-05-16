---
title: Overview
description: Thales provides staking features where token holders nominate collators with their tokens and earn rewards
---

# Staking in Thales

![Staking Thales Banner](/images/staking/staking-overview-banner.png)

## Introduction

Thales uses a block production mechanism based on [Polkadot's Proof-of-Stake model](https://wiki.polkadot.network/docs/en/learn-consensus) where there are collators and validators. [Collators](https://wiki.polkadot.network/docs/en/learn-collator) maintain parachains (in this case, Thales) by collecting transactions from users and producing state transition proofs for the Relay Chain [validators](https://wiki.polkadot.network/docs/en/learn-validator).

The collators' set (nodes that produce blocks) are selected based on their stake in the network. And here is where staking comes in.

Collators (and token holders if they nominate) have a stake in the network from which they get slashed if they misbehave. Therefore, the higher the stake, the higher the network security. The higher the stake, the more likely the collator will get selected to produce a block and earn rewards, which they share with their nominators. In such a way, network members are incentivized to stake tokens to improve the overall security.

## General Definitions

--8<-- 'text/staking/staking-definitions.md'

Currently, for Thalesbase Alpha:

|             Variable             |     |                                                  Value                                                  |
| :------------------------------: | :-: | :-----------------------------------------------------------------------------------------------------: |
|     Minimum nomination stake     |     |                          {{ networks.thalesbase.staking.min_nom_stake }} tokens                           |
|        Minimum nomination        |     |                          {{ networks.thalesbase.staking.min_nom_amount}} tokens                           |
| Maximum nominators per collators |     |                             {{ networks.thalesbase.staking.max_nom_per_col }}                             |
| Maximum collators per nominator  |     |                             {{ networks.thalesbase.staking.max_col_per_nom }}                             |
|              Round               |     | {{ networks.thalesbase.staking.round_blocks }} blocks ({{ networks.thalesbase.staking.round_hours }} hours) |
|          Bond duration           |     |                            {{ networks.thalesbase.staking.bond_lock }} rounds                             |

## Reward Distribution

At the end of every round ({{ networks.thalesbase.staking.round_blocks }} blocks), collators are rewarded for their work from {{ networks.thalesbase.staking.bond_lock }} rounds ago.

When collators join the set of collators, they establish a commission to charge their nominators for the service they provide. Therefore, the reward distribution goes as follows:

 - The commission is taken out of the reward to be distributed
 - The collator gets the rewards corresponding to their stake in the network, plus the commission
 - The rest of the rewards are distributed among nominators by stake

Mathematically speaking, for collators, the reward would look like this:

![Staking Collator Reward](/images/staking/staking-overview-1.png)

Where the stake corresponds to the amount of tokens bonded by the collator in respect to the total stake of that collator (accounting nominations).

For each nominator, the reward would look like this:

![Staking Nominator Reward](/images/staking/staking-overview-2.png)

Where the stake corresponds to the amount of tokens bonded by each nominator in respect to the total stake of that collator.

## Try it on Thalesbase Alpha

In the Thalesbase Alpha TestNet, token holders can stake and earn rewards (to get familiar with the system as the token doesn't have any actual value).

To do so, you can check [this guide](/staking/stake/).
