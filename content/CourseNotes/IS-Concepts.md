---
title: Information Security Concepts
date: 2023-12-26
draft: false
author: HNO3
---
## definitions

### information security
- protecting information from unauthorized
	- access
	- use
	- disclosure
	- disruption
	- modification
	- destruction

### CIA(AA) Triad
- *Confidentiality*
	- no permissionless disclosure
- *Integrity*
	- no permissionless change
- *Availability*
	- no denial to authorized user
- *Authenticity*
	- can be trusted and verified
- *Accountability*
	- requirement for actions to be traced

### 3 Ds security design principle
- *Defense*
	- reduce likelihood of compromise
- *Detection*
	- react to security incident
- *Deterrence*
	- reduce frequency of compromise

### security program components
authority ➡ framework ➡ assessment ➡ planning ➡ action ➡ maintenance

### risk analysis
- risk = proba(threat + exploit of vulnerability) * cost of damage

### thread vector
- describe the *origin* and the *path* to reach *target*
- how to identify: create a *table* containing list of threats along with sources and targets

### types of attacks
- *virus*: self-replicating program, execute host file will execute virus
- *worm*: use its own code to replicate, do NOT directly modify other host file
- *trojan horse*: activate legitimate program by unsuspecting users

### OSI security architecture
- for *who*: managers to organize task of providing security
- 3 aspects
	- *security attack*: action that compromise security of information
	- *security mechanism*: process designed to detect, prevent and recover from attack
	- *security service*: service that enhance the security of system, making use of security mechanism

### active and passive attack
- difference
	- *active attack* aims to change the data and harm the system (ex.: modification, replay)
	- *passive attack* aims to obtain information

### fundamental principles of security design
- economy of mechanism
- fail-safe default
- least privilege
- isolation
- layering
- modularity

### attack surface and attack trees
- *attack surface*: reachable and exploitable vulnerabilities in a system
	- 3 types: network, software, human
	- larger & shallower ➡ higher risk
- *attack trees*: branching, hierarchical data structure that represents a set of potential techniques for exploiting security vulnerabilities
	- <font color="#00b050">root</font>: goal of attack
	- <font color="#00b050">leaf</font>: ways to initiate
	- <font color="#00b050">branch</font>: ways to reach goal

### 3 authentication components
- user terminal and user
- communication channel
- internet banking server

### 5 attack strategies
- user credential compromise
- injection of commands
- user credential guessing
- security policy violation
- use of known authenticated session

### 4 basic tasks for network security
- algorithm for encryption transformation
- algorithm for generating secret information (secret key)
- methods for secret information distribution
- protocol specification making use of algorithm and information

### 5 components of symmetric cipher model
- plaintext
- encryption algorithm
- secret key
- ciphertext
- decryption algorithm

### requirement of security
- strong *encryption algorithm*
- secure key *distribution* and *maintenance*

### 3 dimensions to characterize cryptographic system
- type of operations for encryption transformation
- number of keys
- way to process ciphertext / plaintext

### unconditionally secure scheme
- ciphertext does not contain enough information to determine plaintext
	- no encryption algorithm (except one-time pad) is unconditionally secure

### computationally secure
- cost of breaking > value of encrypted information OR
- time of breaking > useful lifetime of information

### techniques for encryption transformation
- substitution
- transposition
### block cipher & stream cipher
- *block*: a block of plaintext is treated as a whole and used to produce ciphertext block of equal length
- *steam*: continuous encrypting digital data one bit or one byte at a time

### monoalphabetic cipher
- one plaintext letter randomly correspond to another letter
- attack: frequency comparison / repeated pattern (why: frequency information retains in the ciphertext)

### polyalphabetic cipher
- use a set of monoalphabetic substitution rules
- one plaintext letter can correspond to multiple ciphertext letter

### singular & non-singular transformation
- non-singular == reversible: 1 to 1 mapping, no loss of information
- singular == irreversible

### basic idea of Feistel cipher
- *confusion*: complicate relationship between <font color="#00b050">statistics of ciphertext</font> and <font color="#00b050">value of encryption key</font> (via: determine one ciphertext by multiple plaintext)
- *diffusion*: statistical structure of plaintext is dissipated (by complex substitution)

### why Feistel cipher
- approximate ideal block cipher (block size $\infty$, safest)
- how: stack multiple ciphers in sequence

### design features / parameters of Feistel cipher
- *block size*
- *key size*
- *number of rounds*
- *subkey generation algorithm*
- *round function*

### avalanche effect
- small change in plaintext or key should produce a significant change in ciphertext

### 3 critical aspects of block cipher design
- number of rounds
- design of function
- key scheduling

### criteria for randomness
- uniform distribution
- independence

### how to test randomness of PRF / PRNG
- uniformity
- scalability
- consistency

### 2 forms of unpredictability
- forward unpredictability
- backward unpredictability

### 3 cryptographic algorithms to generate PRNGs
- symmetric block cipher
- asymmetric cipher
- hash functions and message authentication codes

### pros and cons of linear congruential generator
- *pros*: resulting sequence is <font color="#00b050">statistically indistinguishable</font> from a sequence drawn from (1,m-1)
- *cons*: 1) once seed determined, sequence is determined. 2) knowledge of small part of sequence is sufficient to determine the parameter of the algorithm
	- alleviation: periodically restart; add current clock value

### requirement for public-key cryptography
- easy to generate key pair
- easy to encrypt
- easy to decrypt
- infeasible for adversary knowing public key to determine private key or decrypt ciphetext

### network access control managing
- <font color="#00b050">authenticate</font> users to log in
- <font color="#00b050">data</font> access
- <font color="#00b050">actions</font> to be performed
- examine the <font color="#00b050">health</font> of users' device

### NAC deal with 3 components
1. access router
2. policy server
3. network access server

### digital ledger technology
- *ledger*: records of maintenance (transaction + ownership) of property
- *digital*: managed by computer
- *distributed*: record kept on multiple computers
- *decentralized*: record managed in a decentralized way (no central entity management)

### classification of DLT
- in terms of identity of nodes
	- permissioned
	- permissionless
- in terms of reading data
	- public
	- private

### 3 data structure for DLT
- linear linked list of blocks
- directed acyclic graph
- tree-like

### blockchain definition
- data is **read only**, cannot be modified once entered into the blockchain, and new data can only be appended at the end of blockchain

### key feature of blockchain
- eliminate third party involvement in maintaining the blockchain network

### 3 components of blockchain
- block
- chain
- transaction

### features of blockchain system
- decentralization
- transparency
- immutability
- availability
- pseudonymity
- security
- non-repudiation
- auditability

### classification of blockchain system
- in terms of network
	- *public*: any node can join/leave/mine
	- *private*: node can join/leave with permission from central entity, miner is selected
	- *consortium*: node can join/leave with permission from consortium of nodes
- in terms of access permission
	- permissioned
	- permissionless

### issue of public blockchain
- limited transactions
- scalability (node/transaction)
- pseudonymity
- limited block size
- energy consumption

### comparison between blockchain system and database management system
|  | blockchain | DBMS |
| ---- | ---- | ---- |
| hashing | critical role | not applied |
| public/private key | essential requirement | not applied |
| sequence of records | placed sequentially and linked together | not sequentially |
| consenus | essential | not applied |
| immutability | characteristic | not present |
| ledger dissemination | essential | not applied  |

### 3 types of nodes in blockchain network
| behavior/types of nodes | full node | lightweight node | miner node |
| ---- | ---- | ---- | ---- |
| copy of ledger | complete copy locally | partial copy locally | complete copy locally |
| transaction generation | yes | yes |  |
| consensus participation |  |  | yes |
| routing for message dissemination and verification | yes | yes | yes |
| transaction validation |  |  | yes |


### 6 layers in blockchain
- application
- visualization and smart contract
- consensus
- network and OS
- data organization and topology
- hardware

### working sequence of blockchain
1. user creates account
2. user creates transaction (Tx)
3. transaction signed
4. transaction broadcast to validating nodes
5. transaction validated
6. transactions gathered in the pool
7. miner node gathers Txs and creates block
8. miner node start mining
9. block validation carried out
10. successful miner adds block to the blockchain
11. added block information broadcast to blockchain network
12. blockchain node adds the broadcast block to their local copy of blockchain (block confirmation)
13. block becomes part of global blockchain (block published)

### composition of a block
- hash pointer
- merkle tree
- nonce
- confirmation
- timestamp
- block version
- transaction

### 3 type of blockchain platform
- suitable only for cryptocurrency
- smart contract
- available over cloud

### examples of applications of blockchain
- asset management & tracking
- own assets in terms of token
- cryptocurrency
- smart contract based new business logic

### features of BitCoin blockchain system
- p2p network architecture
- hashing algorithm
- public/private key encryption
- distributed storage
- logically centralized
- consensus algorithm
- time stamping of transactions

### block component of BitCoin
- outer header
- block header
- block body

### 3 types of users in Ethereum
- contract account
- miners
- externally owned account

### properties of blockchain system
- *smart contract*
	- classification: deterministic (dependent on external data/event)
- *scalability issues*
	- nodes/transactions/size of ledger/storage capacity of nodes
- *transaction capacity*
	- limiting factors: Tx/block, Tx speed, interval between blocks
- *interoperability*

### definition of smart contract
- self-executing program that automate actions required in an agreement
### sharding
- blockchain nodes are divided into multiple smaller groups (shards) and each shard handle some transactions in parallel
- issue: <font color="#00b050">communication</font> between different shards; how all nodes keep the complete ledger

### definition of consensus
- reach a common agreement
- once decision of consensus is reached, it will be communicated to other parties and system will be updated

### responsibility of consensus protocol
- *maintain data* (ordering, originality, tamper-resistance)
- *reach agreement* among nodes

### 2 types of failure
- *crash*: legitimate nodes can't work properly (send or receive data)
- *Byzantine*: malicious nodes arbitrarily send fault information

### main idea of PoW
- higher hash rate means higher chance to solve PoW cryptography puzzle, and the first node to solve the puzzle will be winner, which is able to add block and win award

### issue of PoW
- double spending problem
- probabilistic nature: two or more nodes might solve the puzzle at the same time, resulting in the creation of fork
- long latency
- computational expensive

### false tolerant of PoW
- susceptible to 51% attack
- fault-tolerant to Byzantine attack
- attack resistant to Sybil attack (creating pseudo identities to launch attack)




