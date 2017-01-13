# Technical Specification

[//]: # (<2017-01-15>)

## Block Headers

### Block Versions

There's two types of blocks:

#### Genesis Blocks

Genesis blocks are composed of

- Header
    - Hash of previous block header
    - Body proof:
        - Hash of the slot leader list
    - Consensus data:
        - Epoch, chain difficulty
- Body
    - List of slot leaders for an epoch

#### Main Blocks

- Header
    - Hash of previous block header
    - Body proof
        - Amount of transactions and AVL+ tree root
        - Hash of witness list
        - Hash of MPC data
    - Consensus data
        - Epoc, slot, chain difficulty
        - Public key and signature of slot leader
- Body
    - Merkle tree of transactions
    - List of transaction witnesses
    - MPC data (commitments and openings)

### AVL+ Trees

Cardano SL Block Headers use [an improved authenticated dynamic data
structure](https://eprint.iacr.org/2016/994.pdf). The improvements to the
design of authenticated dictionaries reduce proof size and speed up
verification.

### Segregated Witness

_Pending_

## Transactions

_Pending_

### Addresses

An address is composed the following components: a version and type, a
hash, and a checksum. The corresponding sizes and desciptions are:

- Version and type: `1 byte`
    - 0: Pay to public key
    - 128: Pay to script hash

- Hash: `28 bytes`

Is calculated by `BLAKE2s-224(SHA3-256(x))` where `x` is either a public
key or the a script.

- Checksum: `4 bytes`

Is calculated as a `CRC32` of `(version || hash)`

### Raw Transaction Format

## P2P Network

### Initial Peers

The list of initial peers is below:

- `someip` (_Pending_)
- `anotherip` (_Pending_)
- `thatotherip` (_Pending_)

### Peer Discovery

### Connecting To Peers

### Initial Block Download

### Block Broadcasting

### Transaction Broadcasting
