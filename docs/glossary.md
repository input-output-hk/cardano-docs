# Glossary

Glossary of terms related to Cardano SL.

## Core Concepts

### Cryptocurrency

Computer system which uses cryptographic protocols to generate a ledger.

### Cardano SL

Hybrid decentralized cryptocurrency.

### Ledger

A collection of data that keeps track of value assigned to individuals.

### Transaction

Data that represents the act of transferring value.

### Decentralization

A notion of a computer system operating through interaction of independent
nodes. In case of maintaining a shared data collection such as ledger, a
consensus is required for consistency and thus reliability of data.

### Consensus Algorithm

A way for a decentralized system to reach a consistent view on shared
collections of data. Cardano SL uses the [Ouroboros Consensus
Algorithm](/cardano/proof-of-stake/), which is an algorithm based on
Proof of Stake.

### Proof of Stake

To generate data in a decentralized environment, election of a temporary
authority is required. This temporary authority will tell which data should
be included into the shared collection. In case of cryptocurrencies, the data
included is transactions Proof of Stake approach is to say that the more value
someone has, the more inclined they are to maintain the ledger. Thus, the
probability of a user (_Alice_) having right to add a group of transactions
(called _block_) to the collection of data from which the ledger can be
derived (called _blockchain_) is determined by the percentage of the total
value (the money Alice has is called _stake_, and Alice herself is
called _stakeholder_) in the system she owns (see [Follow the
Satoshi](#follow-the-satoshi)).

### Node

A computer that runs a computer program that participates in a decentralized
protocol system.

## Protocol Basics

### Slot

A small period of time that is significantly larger than the expected
difference in clocks on different nodes.

### Epoch

A bigger period of time for which we know in advance who will have the right
to generate a block in each slot.

### Follow The Satoshi

A mechanism whereby stakeholders are selected at random to forge a new block
in the blockchain, with proportional chance to get elected depending on their
amount of stake in the protocol.

### Leader Selection

A process of picking who will generate blocks in the next epoch. Leaders are
selected with probability proportional to their stake (see
[Proof of Stake](#proof-of-stake), [Follow the Satoshi](#follow-the-satoshi)).


