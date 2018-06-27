# kodebox-code-chain-connect

## Table of Contents

* [kodebox\-code\-chain\-connect](#kodebox-code-chain-connect)
  * [Table of Contents](#table-of-contents)
  * [Introduction to Codechain](#introduction-to-codechain)
    * [Market status](#market-status)
    * [Codechain](#codechain)
  * [Blockchain games and GoCryptobot](#blockchain-games-and-gocryptobot)
    * [Blockchain games](#blockchain-games)
    * [Blockchain games today](#blockchain-games-today)
    * [GoCryptobot](#gocryptobot)
    * [Market status](#market-status-1)
    * [GoCryptobot](#gocryptobot-1)
    * [Things to consider](#things-to-consider)
  * [CodeChain Deep Dive](#codechain-deep-dive)
    * [Table Of Contents](#table-of-contents-1)
    * [PoW vs BFT](#pow-vs-bft)
    * [CodeChain Consensus](#codechain-consensus)
    * [Sharding](#sharding)
    * [Storage](#storage)
    * [Transactions](#transactions)
    * [Scripting](#scripting)
    * [Sync](#sync)
    * [Network (P2P)](#network-p2p)
  * [CodeChain Open Source and Roadmap](#codechain-open-source-and-roadmap)
    * [How to contribute](#how-to-contribute)
    * [CodeChain projects](#codechain-projects)

## Introduction to Codechain

### Market status

#### Blockchain Technologies Today

No codes!

It doesn't even need software engineers?

#### How to build high performance blockchain

##### Bitcoin

* we don't need it. security first.

##### Ethereum

* sharding
* ...
* try to solve the performance issues

##### Fork EOS and reduce # of BP to 11

* EOS uses 21 BP
* reduce it using lessen central concentration

#### What about Other Projects?

#### Blockchain is a new OS?

#### Current Status

* Everyone uses Ethereum to issue tokens
* No one builds applications on Ethereum
  * High transaction cost
  * Low performance (10-20 TPS)
  * Slow block confirmation time

#### Solution

* Issue tokens first and wait until Ethereum solves problems.

### Codechain

open-source blockchain project

service specification (can change algorithm, network, performance, security...)

* Game
* Finance
* Entertainment
* Commerce

#### Key features

built-in multi-asset management solution

* issue, transfer and manage currencies, tokens...

pluggable consensus model

* choose the consensus model optimzal for the business: PoW, Tendermint, Hot-stuff, and PoA

programmability

* make use of CodeChain's support for programmable transactions
* asset evolution, fusion, random item generation, escrow, payment channels and atomic swap
* not turing complete. (Ethereum = turing complete, it has a lot of issues)

scalability via sharding

* achieve higher transaction speed through horizontal scaling
* transaction should be only one sharding. (assumption)

## Blockchain games and GoCryptobot

### Blockchain games

ERC20

ERC721

ex) crypto kitties

* unique cat
* first service not in commerce business. (game)

#### CryptoKitties

speculator leaves

price is getting low.

a lot of copies came out

### Blockchain games today

* Collectibles (highly speculative)
* Gambling
* Pyramids, Hot potatoes
* Browser-based
* not sustainable

### GoCryptobot

* not gambling, and pyramids
* mobile target
* use blockchain

### Market status

#### Blockchain games market

* Tiny
* Failed to bring in gamers
* Unsustainable business model
* Concept of digital asset ownership

#### Blockchain gaming platforms

* Virtual goods marketplace
* ERC721 market - artificial scarcity
* Incentives linked with ad, UGC, Twitch, etc
* No contents, no transactions, no code
* ex) WAX, EN JIN COIN, Dmarket
* No incentives to game development company.
* scarce items only?
  * cannot explain which one is scarce.

### GoCryptobot

World's first mobile blockchain game for both iOS and Android

* based on Ethereum
* ERC20/ERC721
* ... including everything related to Ethereum

#### Take-away

* User experience is valuable more than 30%.
* Players' core incentive is not in earning cash
* Items trading outside the game is pointless
* Blockchain is way more expensive than what you may think
  * gas fee
  * ethereum node
  * Tx may even be rejected

#### is blockchain useless?

No, but current blockchain game projects are.

* Poor game/service development expertise
* Non-existent service core value what gamer wants?
* Token economy but no business model
* Poor blockchain technology knowledge
* Better without blockchain

### Things to consider

Decentralized network

* that issues and transfers digital assets
* that works without a central authority
* will never be faster

Which part of the service does really have to be decentralized?

* no central control
* costs

Does the digital asset enough value for leveraging blockchain?

* scarcity
* price
* traceability

## CodeChain Deep Dive

### Table Of Contents

* Consensus
* Sharding
* Storage
* Transaction
* Script
* Sync
* P2P

### PoW vs BFT

PoW - bitcoin, ethereum (Proof of Work)

### CodeChain Consensus

Pluggable consensus architecture

* PoW
* PoA ( Proof of Authority)
* Tendermint
* Hot-stuff

Separation between beacons and replicas

* Beacon: a cechanism for triggering proposals
* eg. PoW(Beacon) + Wendy(Replicas)

### Sharding

* One of Scalability Solution candidates
* Global root has only the root of the shards
* all assets are stored in the shards (separated, distributed)

#### verification in same shard => how?

Participants

Gateway (service manager)

* collect transactions
* create parcel
* collect signatures from validators
* hand over these signatures to beacon 

Mental model

* not two level distribution
* validators (centralized)

#### Shard Validator

Allocate validators every epoch(term - 1 day?)

### Storage

#### Bitcoin vs Ethereum

choose Ethereum method

#### Merkleized UTXO

* UTXO set embedded in Merkle Trie (header?)
* Piggy-back "undo" feature from Merkle Trie
* Asset Transfer in Merkleized UTXO 3/3

### Transactions

only Asset related job.

#### type

* Mint (publication) => asset itself
* Transfer => one of asset (transfer info)

#### actions

1. collect transaction
2. gateway
3. parcel
4. network (nodes)

### Scripting

Native support for P2SH

Guaranteed termination (not turing complete)

* no loops
* no backjump allowed

separation between **lock script** and **parameters**

* script identification without original script
* required for implementing wallet

multiple return types

* success, fail, burn...

#### Burn

Eliminate asset permanently

* transaction is invalid if burnt asset is used

Programmable control of asset circulation

* automatic disposal of single-use objects

smaller state size

#### Asset transfer

* Lockscript + unlockscript
* lockscript hash check
* unlockscript verification
* state => unlockscript => parameter => lockscript => return

### Sync

Full block synchronization

pull gossip for block propagation (after mining)

* requester have full control on bandwidth
* small message duplication
* header first style block request

fully parallel header fetching

* fast catch up for best peer

#### Snapshot synchronization

block validation without history

* faster startup time
* reduced storage requirement

verifiable snapshot header

* use "head" of state trie as manifest

Compressed subtree as state chunk

### Network (P2P)

#### Network extensions

* Pluggable extension mechanism
* Multiple extensions can perform the same task in different ways
* UDP for Session Initiator (fixed protocol)
* TCP for P2P connection

#### Peer discovery

* Discovery is one of extensions
* network formation and policy can be changed
* Unstructured and Kademlia discovery is implemented (customized)

#### Session initiation

* ECDH
* Share session without network

#### Authentication

* Each connection has a unique session key
* all messgaes have signature field
* header - version, extension/name,version
* body - ase256/or not
* signature - black2b

#### Extension API

can contribute easily

## CodeChain Open Source and Roadmap

### How to contribute

* [github](https://github.com/CodeChain-io/codechain)
* [gitter](https://gitter.im/CodeChain-io/codechain)

### CodeChain projects

* rust based
* rustup
* javascript sdk