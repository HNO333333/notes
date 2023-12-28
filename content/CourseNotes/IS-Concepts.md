---
title: Information Security Concepts
date: 2023-12-28
draft: false
author: HNO3
---

### information security
- protecting information from unauthorized
	- access
	- use
	- disclosure
	- disruption
	- modification
	- destruction
- essence (paraphrase): protect <font color="#f79646">information</font> & <font color="#f79646">system</font> from people who want to <font color="#f79646">misuse</font> it

### considerations about information security
- both consider security and "<font color="#f79646">productivity</font>" (should be usable and productive)
- level of security should be related to the <font color="#f79646">value</font> of information being secured

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

### characteristic of modern security model
- providing <font color="#f79646">limited access</font> to data in a <font color="#f79646">controlled</font> fashion

### 3 Ds security design principle
- *Defense*
	- reduce likelihood of compromise (lower risk)
- *Detection*
	- react to security incident
- *Deterrence*
	- reduce frequency of compromise

### security program components
authority ➡ framework ➡ assessment ➡ planning ➡ action ➡ maintenance

### risk analysis
- risk = probability(threat + exploit of vulnerability) $\times$ cost of damage
- objective of security program is <font color="#f79646">NOT eliminate</font> risks but <font color="#0070c0">mitigate</font> risks

### thread vector
- describe the *origin* and the *path* to reach *target*
- <font color="#f79646">how</font> to identify: create a *table* containing list of threats along with sources and targets

### security control for different threat vectors
- preventative
- detective
- deterrent
- corrective
- recovery
- compensation

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

### difference between active and passive attack
- *active attack* aims to <font color="#f79646">change data</font> and <font color="#f79646">harm system</font> (ex.: modification of message, replay, masquerade)
- *passive attack* aims to <font color="#f79646">obtain</font> information (hard to detect)

### fundamental principles of security design
- <font color="#f79646">economy</font> of mechanism
- fail-safe <font color="#f79646">default</font>
- least <font color="#f79646">privilege</font>
- isolation
- layering
- modularity

### attack surface and attack trees
- *attack surface*: <font color="#f79646">reachable</font> and <font color="#f79646">exploitable</font> **vulnerabilities** in a system
	- 3 types: network, software, human
	- larger & shallower ➡ higher risk
- *attack trees*: branching, hierarchical <font color="#f79646">data structure</font> that represents a set of potential <font color="#f79646">techniques</font> for exploiting security vulnerabilities
	- <font color="#00b050">root</font>: goal of attack
	- <font color="#00b050">leaf</font>: ways to initiate
	- <font color="#00b050">branch</font>: ways to reach goal

### 3 authentication components
- user <font color="#f79646">terminal</font> and user
- communication <font color="#f79646">channel</font>
- internet banking <font color="#f79646">server</font>

### 5 attack strategies
- user <font color="#f79646">credential compromise</font>
- <font color="#f79646">injection</font> of commands
- user <font color="#f79646">credential guessing</font>
- security policy <font color="#f79646">violation</font>
- use of known <font color="#f79646">authenticated session</font>

### 2 components of model for network security
- security-related transformation on the information to be sent (<font color="#f79646">encryption</font>)
- share secret information (key) and stay unknown to the opponent (<font color="#f79646">key distribution & maintenance</font>)

### 4 basic tasks for network security
- algorithm for <font color="#f79646">encryption</font> transformation
- algorithm for generating secret information (secret <font color="#f79646">key</font>)
- methods for secret information <font color="#f79646">distribution</font>
- <font color="#f79646">protocol specification</font> making use of algorithm and information

### symmetric encryption
- also called <font color="#00b050">conventional encryption</font> or <font color="#00b050">single-key</font> encryption
- only keep the key secret, NOT the algorithm

### 5 components of symmetric cipher model
- plaintext
- encryption algorithm
- secret key
- ciphertext
- decryption algorithm

### requirement of security
- strong *encryption algorithm* (with ciphertext can't know key or plaintext)
- secure key *distribution* and *maintenance*

### 3 dimensions to characterize cryptographic system
- type of <font color="#f79646">operations</font> for encryption transformation
- number of <font color="#f79646">keys</font>
- way to <font color="#f79646">process</font> ciphertext / plaintext

### unconditionally secure scheme
- ciphertext does not contain enough information to determine plaintext, no matter with how much time, it's impossible to decrypt
- no encryption algorithm (except one-time pad) is unconditionally secure

### computationally secure
- <font color="#00b050">cost</font> of breaking > <font color="#00b050">value</font> of encrypted information OR
- <font color="#00b050">time</font> of breaking > useful lifetime of information
- problem: cost/time to break is hard to estimate

### techniques for encryption transformation
- substitution
- transposition

### formulas, pros and cons for different cipher

*Caesar*
- $C = E(p+k)mod\:26$, $P=D(c-k)mod\:26$
- cons: easy to break, there is limited possibility

*playfair*
- procedure
	- filling $5\times 5$ matrix with key first then remaining letters in alphabetic order
	- same row: right
	- same column: down
- pros: better than monoalphabetic, difficult to conduct frequency analysis
- cons: easy to break (leaves much of structure of plaintext)

*Hill*
- $C=PK\:mod\:26$, $P=CK^{-1}\:mod\:26$, where $C$ and $P$ are row vectors, and $K$ is matrix

*Vigenère*
- $C_i=(p_i+k_{i\:mod\:m})\:mod\:26$, $p_i=(C_i-k_{i\:mod\:m})\:mod\:26$, key is repeating keyword
- pros: frequency information is obscured
- cons: 1) considerable <font color="#00b050">frequency</font> information retains, 2) <font color="#00b050">keyword length</font> may be found
- cryptanalysis: 1) test for monoalphabetic cipher, 2) find repeated pattern, 3) find keyword length by common factors of repeated pattern interval, 4) take ciphertext letter according to the keyword length, and break it like a sequence of Caesar cipher
- how to improve: <font color="#00b050">autokey</font>, concatenate keyword with plaintext itself

*Vernam*
- work on binary data: $c_{i}=p_{i}\oplus k_{i}$, $p_{i}=c_{i}\oplus k_{i}$, $k_i$ is NOT key: it's a bit stream (output of key stream generator) that determined by the key
- cryptanalysis: break with sufficient ciphertext and the use of known probable plaintext sequence

*one-time pad*
- using a random key that is as long as the message to decrypt single message then discard
- pros: 1) can't determine which result of cryptanalysis is correct, 2) security is due to <font color="#00b050">randomness</font> of the key
- cons: 1) <font color="#00b050">large quantities</font> of random key, 2) <font color="#00b050">key</font> distribution and protection

*steganography*
- pros: hide in object, no <font color="#00b050">suspicion</font> (encrypted information will be considered as important)
- cons: 1) limited <font color="#00b050">capacity</font>, 2) large <font color="#00b050">overhead</font>, 3) once system is discovered, whole system is destroyed

*DES*
- pros: 1) no effective attack found; 2) fast
- cons: key size (56 bits too small)

### block cipher & stream cipher
- *block*: a block of plaintext is treated as a whole and used to produce ciphertext block of equal length
- *steam*: continuous encrypting digital data one bit or one byte at a time

### monoalphabetic cipher
- one plaintext letter randomly correspond to another letter ($n!$ permutations make it harder to break)
- attack: frequency comparison / repeated pattern (why: <font color="#f79646">frequency information</font> retains in the ciphertext)

### polyalphabetic cipher
- use a set of monoalphabetic substitution <font color="#00b050">rules</font>, choice of which rule to use is determined by key
- one plaintext letter can correspond to multiple ciphertext letter

### singular & non-singular transformation
- non-singular == reversible: 1 to 1 mapping, no loss of information
- singular == irreversible

### basic idea of Feistel cipher
- *confusion*: complicate relationship between <font color="#00b050">statistics of ciphertext</font> and <font color="#00b050">value of encryption key</font> (via: determine one ciphertext by multiple plaintext) (from ciphertext can't determine key)
- *diffusion*: statistical structure of plaintext is dissipated (by complex substitution) (from ciphertext can't determine plaintext)
![[IS notes-20231212-13.png|450]]

### why Feistel cipher
- approximate ideal block cipher (block size $\infty$, safest)
- how: stack multiple ciphers in sequence
- example: DES

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

### AES
![[IS-Concepts-20231228-1.png|600]]
- not Feistel structure, 1 permutation and 3 substitution
- decryption algorithm is NOT identical to encryption algorithm

### where we need generation of random bit stream
- key generation
- encryption

### criteria for randomness
- uniform distribution
- independence

### TRNG/PRNG/PRF
![[IS-Concepts-20231228-2.png|200]]![[IS-Concepts-20231228-3.png|200]]![[IS-Concepts-20231228-4.png|200]]

### 3 aspects to test randomness of PRF / PRNG
- uniformity
- scalability
- consistency

### 3 tests of randomness
- *frequency test*: (if 1/0 have same proportion)
- *runs test*: if runs with various length is expected
- *Maurer's universal statistical test*: if the sequence can be compressed significantly

### 2 forms of unpredictability
- forward unpredictability
- backward unpredictability

### 2 categories of PRNG algorithms
- purpose-built algorithm
- algorithms based on existing cryptographic algorithms

### 3 cryptographic algorithms to generate PRNGs
- <font color="#00b050">symmetric</font> block cipher
- <font color="#00b050">asymmetric</font> cipher
- <font color="#00b050">hash</font> functions and message authentication codes

### Linear Congruential Generators
-  $m$: modulus, $m>0$ (chosen very large)
- $a$: multiplier, $0<a<m$
- $c$: increment, $0\le c <m$
- $X_0$: starting value or <font color="#00b050">seed</font>, $0\le X_0 < m$
- $$ \begin{aligned}X_{n+1}\:=\:(aX_n\:+\:c)\bmod m\end{aligned}$$
- range: $0\le X_m \le m$
- tests for Linear Congruential Generator
	- if it's <font color="#00b050">full-period generating</font> function (generate all numbers of the range before repeating)
	- if sequence appear <font color="#00b050">random</font>
	- if can be <font color="#00b050">implemented</font> efficiently with 32-bit arithmetic
- pros: statistically indistinguishable
- cons: 1) if known algorithm, once a single number is discovered, all subsequent numbers are known; 2) knowledge of a small part of the sequence is sufficient to determine the parameters of the algorithm
- improve: 1) restart sequence periodically, 2) add current clock value

### Blum Blum Shub generator
$$ \begin{array}{rcl}\mathrm{X}_0&=&\mathrm{s}^2\mod\:n\\\mathrm{for}\quad\mathrm{i}&=&1\:\textsf{to}\:\infty\\\mathrm{X}_i&=&(\mathrm{X}_{i-1})^2\mod\:n\\\mathrm{B}_i&=&\mathrm{X}_i\mod\:2\end{array}$$
where $p\equiv q\equiv3(\operatorname{mod}4)$ and $n=p\times q$
- BBS pass cryptographically secure (next-bit test: can't predict next bit with probability higher than 0.5)

### concepts in public-key cryptography
- *asymmetric key*: two related keys used to perform complementary operations
- *public key certificate*: a digital <font color="#00b050">document</font> <font color="#f79646">issued</font> and digitally <font color="#f79646">signed</font> by the private key of an authority that <font color="#f79646">binds</font> the name of a <font color="#f79646">subscriber</font> to a public key, indicating that the subscriber identified in the certificate has sole <font color="#f79646">control</font> and <font color="#f79646">access</font> to the corresponding private key

### requirement for public-key cryptography
- easy to <font color="#00b050">generate</font> key pair
- easy to <font color="#00b050">encrypt</font>
- easy to <font color="#00b050">decrypt</font>
- infeasible for adversary knowing public key to determine private <font color="#00b050">key</font> or decrypt <font color="#00b050">ciphetext</font>

### essential steps for public-key cryptography
1. generate a pair of keys
2. place one key in public while the other in private
3. encrypt message with one key
4. decrypt with the other key

### 3 usages of public-key cryptosystems
- encryption & decryption
- digital signature
- key exchange

### Diffie-Hellman algorithm & man in the middle attack
![[IS-Concepts-20231228-5.png|500]]

![[IS notes-20231212-30.png|500]]
- why vulnerable: participants are not <font color="#00b050">authenticated</font>
- how to overcome: <font color="#00b050">digital signatures</font> & <font color="#00b050">public-key certificates</font>
### network access control managing
- <font color="#00b050">authenticate</font> users to log in
- determine <font color="#00b050">data</font> access, <font color="#00b050">actions</font> to be performed
- examine the <font color="#00b050">health</font> of users' device

### NAC deal with 3 components
1. *access router*: node attempts to access network, also called *supplicant* or *client*
2. *policy server*: determine what access to be granted
3. *network access server*: access control point, also called *media gateway* or *remote access server*

### procedure of NAC
1. authenticate AR, verify <font color="#00b050">identity</font>
2. <font color="#00b050">enable</font> secure <font color="#00b050">communication</font> by establishment of <font color="#00b050">session key</font>
3. <font color="#00b050">check</font> on AR to determine if <font color="#00b050">permitted</font> for remote access

### digital ledger technology
- *ledger*: records of <font color="#00b050">maintenance</font> (transaction + ownership) of property
- *digital*: managed by <font color="#00b050">computer</font>
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

### why blockchain secure
- strong public/private <font color="#00b050">keys</font>
- <font color="#00b050">hashing</font> algorithm
- digital <font color="#00b050">signature</font>
- <font color="#00b050">encryption</font> techniques

### issue of public blockchain
- limited <font color="#00b050">transactions</font>
- <font color="#00b050">scalability</font> (node/transaction)
- <font color="#00b050">pseudonymity</font> (double spending)
- limited <font color="#00b050">block size</font>
- <font color="#00b050">energy</font> consumption

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
- *outer header* (block size, block identification)
- *block header* (block version, time stamp, hashing target, nonce, previous hash, Merkle Tree root)
- *block body* (all transactions)

### 3 types of users in Ethereum
- contract account
- miners
- externally owned account

### properties of blockchain system
- *smart contract*
	- classification: <font color="#00b050">deterministic</font> (dependent on external data/event) and <font color="#00b050">non-deterministic</font>
- *scalability issues*
	- nodes/transactions/size of ledger/storage capacity of nodes
	- how to improve: 1) offload to side chain (main chain only store hash); 2) [[#sharding]]
- *transaction capacity*
	- limiting factors: # of Tx in block, Tx speed, interval between blocks
- *interoperability*

### definition of smart contract
- self-executing program that automate actions required in an agreement

### sharding
- blockchain nodes are <font color="#00b050">divided</font> into multiple smaller groups (shards) and each shard handle some transactions in <font color="#00b050">parallel</font>
- issue: <font color="#00b050">communication</font> between different shards; how all nodes keep the complete ledger

### definition of consensus
- reach a common agreement
- once decision of consensus is reached, it will be communicated to other parties and system will be updated

### metrics of consensus
- performance
	- transaction throughput (number of transactions per second a blockchain can process, $throughput=\dfrac{block\:size}{transaction\:size\times block\:time}$)
- scalability

### responsibility of consensus protocol
- *maintain data* (ordering, originality, tamper-resistance)
- *reach agreement* among nodes

### 2 types of failure
- *crash*: legitimate nodes can't work properly (send or receive data)
- *Byzantine*: malicious nodes <font color="#00b050">arbitrarily</font> send fault information

### main idea of PoW
- higher <font color="#00b050">hash rate</font> means higher chance to solve PoW cryptography puzzle, and the first node to solve the puzzle will be winner, which is able to add block and win award

### issue of PoW
- <font color="#00b050">double spending</font> problem
- probabilistic nature: two or more nodes might solve the puzzle simultaneously, resulting in the<font color="#00b050"> creation of fork</font>
- long <font color="#00b050">latency</font>
- <font color="#00b050">computational</font> expensive

### fault tolerant of PoW
- susceptible to 51% attack
- fault-tolerant to Byzantine attack
- attack resistant to Sybil attack (creating pseudo identities to launch attack)

### difficulty of PoW
- higher difficulty ➡ more computing resources required ➡ harder to attack

### main idea of PoS
- selection of miners depends on amount of stakes each node carries

### pros and cons of PoS
- pros
	- less <font color="#00b050">energy</font> consumption
	- lower <font color="#00b050">computational</font> power requirement
	- <font color="#00b050">faster transaction</font> confirmation speed
- cons
	- subject to <font color="#00b050">dominance</font> by the most significant token holders
	- <font color="#00b050">positive feedback</font> loop
	- message transmission loss and <font color="#00b050">delay</font>
	- <font color="#00b050">reward</font> incentivization

### comparison between PoW & PoS
| aspect of comparison | PoW | PoS |
| ---- | ---- | ---- |
| mining/validating a block | amount of computational work | amount of stake |
| distribution of reward | mines the block first wins | validator doesn't receive a block award since paid by network fee |
| competition | use computer processing power to solve puzzles | algorithm determines winner based on the size of stake |
| centralization | centralized in nature | algorithm determines winner based on the size of stake |
| specialized equipment | GPU | standard server-grade service is sufficient for PoS system |
| efficiency | less energy efficient, less expensive, more reliable | cost and energy efficient, less reliable |
| adding a malicious block | need more than 50% of computing power | hackers should have more than 51% of all cryptocurrency |
| security | greater the hash, more secure the work | stake helps lock crypto assets to secure the network for the reward |
| forking | naturally prevent constant forkng | forking is not automatically discouraged by PoS |

### main idea of PAXOS
- allow consensus over a value under unreliable communications. "<font color="#00b050">majority</font> represents the whole"
![[IS notes-20231218-1.png|600]]

phases
- *prepare*
	- <font color="#00b050">proposer</font> receive request from client
	- <font color="#00b050">proposer</font> sends <font color="#00b0f0">prepare (n)</font>
	- <font color="#00b050">acceptor</font> stores highest proposal number (<font color="#00b0f0">n</font>) and send promise message (with/without full proposal)
- *accept*
	- <font color="#00b050">proposer</font> waits until gets responses from majority of acceptors for <font color="#00b0f0">n</font>
	- <font color="#00b050">proposer</font> sends an accept message <font color="#00b0f0">accpet(n,v)</font>
	- <font color="#00b050">acceptors</font> accept and reply with <font color="#00b0f0">accepted(n,v)</font>
	- if majority of <font color="#00b050">acceptors</font> accept v, then consensus is reached

### main idea of RAFT
- enable state machine replication with a persistent log, allow cluster reconfiguration, enabling cluster membership changes without service interruption
![[IS-Concepts-20231226-1.png]]

phases
- *leader election*
	- all nodes start as followers, once not receive heartbeats from leader, follower node undertakes candidate role and attempt to become leader by election process
	- if a candidate receive majority of votes, then it become leader. Otherwise, if no one wins ➡ election timeout
- *log replication*
	- client sends <font color="#00b0f0">request</font>/command to leader (to be executed by replicated state machine)
	- leader <font color="#00b0f0">assigns</font> a <font color="#00b0f0">term</font> <font color="#a5a5a5">(to ascertain time of entry of command)</font> and <font color="#00b0f0">index</font> <font color="#a5a5a5">(identify position of entry in log of node)</font> to command, then appends this command to log
	- leader sends out request to replicate (copy) this command to follower nodes
	- when leader is able to replicate (copy) command to <font color="#00b0f0">majority</font> of follower nodes, which acknowledge that the entry is <font color="#00b050">committed</font> on cluster
	- leader <font color="#00b0f0">execute</font> the command and <font color="#00b0f0">returns result</font> to client, also <font color="#00b0f0">notify followers</font> that entry is committed. followers execute committed commands in their state machine

### main idea of PBFT
- designed to provide consensus in the presence of Byzantine faults
![[IS notes-20231218-6.png|650]]

phases
- *pre-prepare*
	- leader <font color="#00b0f0">accepts request</font>
	- leader <font color="#00b0f0">assigns</font> sequence number
	- leader <font color="#00b0f0">broadcasts</font> information to all backup replicas
- *prepare*
	- backups <font color="#00b0f0">accept</font> pre-prepare message (if never accepted this with same view or sequence number before)
	- backups <font color="#00b0f0">send</font> prepare message to all replicas
- *commit*
	- replicas <font color="#00b0f0">wait</font> for 2f+1 prepare message with same view, sequence number and request
	- replicas <font color="#00b0f0">send</font> commit messages to all replicas
	- replicas <font color="#00b0f0">wait</font> for 2f+1 commit message arrive
	- replicas <font color="#00b0f0">execute</font> received request
	- replicas <font color="#00b0f0">send</font> a reply with execution result to client

### 3 subprotocols of PBFT
- normal operation
- view change
- checkpointing

### licensed & unlicensed spectrum
- *licensed*: managed by governments and telecom operators needs to buy it then provides communication service to customers
- *unlicensed*: used free of charge by anyone at any time

### why cognitive radio
- wireless radio spectrum is underutilized (due to <font color="#00b0f0">static allocation</font> of spectrum). CR uses <font color="#00b0f0">dynamic spectrum access</font> (DSA) paradigm, which can utilize wireless radio spectrum efficiently

### 2 types of nodes in CR
- *primary radio node*: licensed users, can only use licensed spectrum
- *secondary users*: can only use licensed spectrum when it's <font color="#00b0f0">not</font> being used by primary users and do <font color="#00b0f0">not</font> cause harmful <font color="#00b0f0">inference</font> to primary radio node. When primary radio node requires, it has to leave the frequency band.

### if not collision-free communication
- <font color="#00b0f0">lose</font> packets
- <font color="#00b0f0">re-transmission</font> required
- energy and time <font color="#00b0f0">consumption</font>

### medium access control protocols classification
in terms of "channels"
- single channel
- multiple channel

in terms of "contention"
- contention based
- contention free

in terms of access
- random access
- controlled access

### advantage of sharing spectrum
- enable to use LTE and 5G <font color="#00b0f0">simultaneously</font> in the same frequency band
- determine the <font color="#00b0f0">demand</font> of different radios in real-time
- (<font color="#a5a5a5">how: available bandwidth is divided into independent parts and dynamically assigns different standard)</font>

### issue of DSS in CR
- self-aware
- self-configuration
- self-healing
- self-optimizing
- self-protecting

### how blockchain help CR
- blockchain provides <font color="#f79646">verification</font> and <font color="#f79646">validation</font> schemes to ensure security
- decentralized validation algorithm of blockchain enable medium access <font color="#f79646">protocol</font> of CR more <font color="#f79646">accessible</font> and <font color="#f79646">implementation</font> be easier
- lacking centralized node makes overall system more <font color="#f79646">robust</font> against <font color="#f79646">single-point failure</font>

### procedure for collision-free communication with blockchain
- each group reach <font color="#f79646">local consensus</font> to allocate resources
- <font color="#f79646">broadcast</font> information to all CR nodes
- CR nodes will not use these resources
- result in <font color="#f79646">collision avoidance</font> in CR network

### pros & cons of using blockchain in CR
pros
- lack of central entity
- immutability 
- availability
- DoS resillient
- non-repudiation
- smart contract integration

cons
- high computational <font color="#00b0f0">overhead</font>
- <font color="#00b0f0">ownership</font> of ledger
- <font color="#00b0f0">capacity</font>
- <font color="#00b0f0">storage</font> requirement of nodes



