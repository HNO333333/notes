---
title: Information Security Notes
date: 2023-12-12
draft: false
author: HNO3
---

## Lecture 1 Information Security Fundamentals

### Definitions

- Definition of Information Security
	- protecting information and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction
- cost of security should NOT greater than the value of what it is protecting
- Definition of Security
	- <span style="background:rgba(160, 204, 246, 0.55)">"CIA"</span>: confidentiality, integrity and availability
		- <font color="#00b050">confidentiality</font>
			- data confidentiality: not available or disclosed to unauthorized individuals
			- privacy: control by whom and to whom that information may be disclosed
		- <font color="#00b050">integrity</font>
			- data integrity: information or programs are changed only in a specific and authorized manner
			- system integrity: system performs its intended function, free from deliberate or unauthorized manipulation
		- <font color="#00b050">availability</font>
			- system work promptly and service is not denied to authorized users
		- CIA(AA) model
			- authenticity: property of being genuine and able to be trusted and verified
			- accountability: requirement for actions to be traced uniquely.

### Evaluation of Information Security

<span style="background:rgba(3, 135, 102, 0.2)">Design Principles</span>
- "3Ds": defense, detection, deterrence
- <font color="#00b050">Defense</font>
	- reduce the likelihood of compromise
- <font color="#00b050">Detection</font>
	- react to security incident
- <font color="#00b050">Deterrence</font>
	- reduce frequency of compromise

<span style="background:rgba(3, 135, 102, 0.2)">How to Build a Secure System</span>
- authority
- framework
- assessment
- planning
- action
- maintenance
- ![[IS notes-20231212-1.png|500]]

<span style="background:rgba(3, 135, 102, 0.2)">Risk Analysis</span>
- formula: $Risk = Probability(Threat + Exploit \space of \space Vulnerability) \times Cost \space of \space Damage$
- Threat
	- threat vector
		- describe <font color="#00b050">origin</font> and the <font color="#00b050">path</font> to reach <font color="#00b050">target</font>
		- identify: create <font color="#00b050">table</font> containing lists of threats along with sources and targets
	- threat sources and targets
	- <span style="background:#d3f8b6">types of attacks</span>
		- **virus**: self-replicating programs, every time host file is executed, virus executed, too
		- **worm**: use its own code to replicate, does not directly modify other host code to replicate
		- **Trojan horse**: pose legitimate programs that are activated by unsuspecting user
	- malicious mobile code
	- advanced persistent threats
	- manual attacks

<span style="background:rgba(3, 135, 102, 0.2)">OSI security architecture</span>
- useful to <font color="#00b050">managers</font> as a way of organizing the task of providing security
- OSI architecture focuses on three aspects:
	- **security attack**: any action that <font color="#00b050">compromises security of information</font> owned by an organization
	- **security mechanism**: process that designed to <font color="#00b050">detect</font>, <font color="#00b050">prevent</font> or <font color="#00b050">recover</font> from attack
	- **security service**: service <font color="#00b050">enhances security</font> of system and information transfer, making use of security mechanisms to provide service

<span style="background:rgba(3, 135, 102, 0.2)">Active and Passive Attack</span>

- **Passive**: the goal is to <font color="#00b050">obtain information</font>
- **Active**: goal: may <font color="#00b050">change</font> the data or <font color="#00b050">harm</font> the system
	- example: modification, masquerading, replaying, repudiation, denial of service
	- masquerading
		- take place when: pretending to be another entity
	- replay
		- passive capture of data unit and its subsequent retransmission to produce an unauthorized effect
	- modification
		- message altered
	- denial of service
		- prevent normal use
		- may have specific target, may disrupt entire network


### Fundamentals of Secure Design

- economy of mechanism
	- simple and small as possible
- fail-safe default
	- default: lack of access
- complete mediation
	- <font color="#00b050">every access must be checked</font> against access control mechanism
- open design
	- mechanism should be open
- separation of privilege
	- multiple attributes required to achieve access to restricted resources. (multifactor user authentication)
- least privilege
- least common mechanism
	- minimize functions shared by different users
- psychological acceptability
	- mechanism should not interfere users
- isolation
	- public system isolated from critical resources
	- files of different users should be isolated from each other
	- security mechanism should be isolated
- encapsulation
	- specific form of isolation, based on object-oriented functionality
- modularity
	- refer to both the development of security functions as separate, protected modules and to the use of modular architecture for mechanism design and implementation
- layering
	- use of multiple overlapping protection approaches addressing different aspects of information system
- least astonishment
	- interface should respond the way that least likely to astonish users

<span style="background:rgba(3, 135, 102, 0.2)">Attack Surfaces & Attack Trees</span>
- *attack surfaces*
	- consists of the <font color="#00b050">reachable</font> and <font color="#00b050">exploitable</font> vulnerabilities in a system
	- examples
		- open ports facing web
		- services available inside firewall
		- code process incoming data
		- interfaces
		- employee with access to sensitive information
	- <span style="background:#d3f8b6">categories of attack surfaces</span>
		- <font color="#00b050">Network</font> attack surface
		- <font color="#00b050">Software</font> attack surface
		- <font color="#00b050">Human</font> attack surface
- defense in depth and attack surfaces
	- ![[IS notes-20231212-2.png|253]]
	- <font color="#00b050">larger & shallower</font> the surface is, higher the risk is
	- attack surface analysis: useful to assess the scale and severity of threats
	- analysis of vulnerability: useful for developers aware of where security mechanism required
	- defined attack surfaces -> find ways to make surface smaller -> less risk
	- attack surface provides guidance on setting priorities for testing

- Attack Trees
	- definition: branching, hierarchical <font color="#00b050">data structure</font> that represents a set of potential techniques for <font color="#00b050">exploiting security vulnerabilities</font>
	- <font color="#00b050">root</font> node: security incident as the <font color="#00b050">goal</font> of attack
	- branches and sub-nodes: ways to reach goal
	- <font color="#00b050">leaf</font> node: ways to <font color="#00b050">initiate</font> attacks
	- each node other than a leaf is either an **AND**-node or an **OR**-node
		- goal represented by **AND**-node: all subgoals must be achieved
		- goal represented by **OR**-node: a least one subgoal must be achieved
	- branches can be labelled by values (difficulty, cost or others)
	- example ![[IS notes-20231212-3.png]]


<span style="background:rgba(3, 135, 102, 0.2)">3 Components Involved in Authentication</span>
- User terminal and <font color="#00b050">user</font> (UT/U)
	- attack target the user equipment
- Communication <font color="#00b050">channel</font> (CC)
	- focus on communication link
- Internet banking <font color="#00b050">server</font> (IBS)
	- offline attacks against server host the banking application

<span style="background:rgba(3, 135, 102, 0.2)">5 Attack Strategies</span>
- **User Credential Compromise**
	- against any elements of attack surface
- **Injection of Commands**
	- intercept communication between UT and IBS
- **User Credential Guessing**
	- brute force attack authentication scheme by sending random username and passwords
- **Security Policy Violation**
	- violate may expose weak access control to outside
- **Use of Known Authenticated Session**

<span style="background:rgba(3, 135, 102, 0.2)">Model for Network Security</span>

- ![[IS notes-20231212-4.png|450]]
- message transferred by internet service
- security is to protect information transmission
- techniques for providing security
	- information transformation
	- secret information shared by two principals
	- trusted third party may be needed

<span style="background:rgba(3, 135, 102, 0.2)">4 Basic Tasks</span>
- <font color="#00b050">algorithm</font> for performing the security-related <font color="#00b050">transformation</font>
- Generate the secret information (<font color="#00b050">key-generation</font>) to be used with the algorithm.
- methods for the distribution and sharing of the secret information (<font color="#00b050">key-distribution</font>)
- Specify a <font color="#00b050">protocol</font> to be used that makes use of algorithm and information to achieve particular security service

## Lecture 3-5 Encryption Techniques

### Symmetric Cipher Model

- other names: conventional encryption, single-key encryption
- definitions of basic concepts
	- *plaintext*: original information
	- *ciphertext*: coded message
	- *enciphering / encryption*: plaintext -> ciphertext
	- *deciphering / decryption*: ciphertext -> plaintext
	- *cryptography*
	- *cipher / cryptographic system*: scheme for encryption
	- *cryptanalysis*: techniques used to decipher
	- *cryptology*: cryptography + cryptanalysis
- <span style="background:#d3f8b6">5 components of symmetric cipher model</span>
	- plaintext
	- encryption algorithm
	- secret key
	- ciphertext
	- decryption algorithm
- <span style="background:#d3f8b6">requirement of security</span> (加密算法+密钥分发保管)
	- strong encryption <font color="#00b050">algorithm</font>
	- sender and receiver should obtain copies of secret key in a secure way and must keep key secure
- model
	- ![[IS notes-20231212-5.png|500]]
	- Y = E(K,X)
	- X = D(K,Y)
- how to <span style="background:#d3f8b6">characterize cryptographic system</span> (3 dimensions)
	- type of <font color="#00b050">operations</font> used for encryption transformation
		- two types: <font color="#00b050">substitution</font> + <font color="#00b050">transposition</font>
		- fundamental requirement: no information lost OR operation reversible
		- "*product system*": system involves <font color="#00b050">multiple stages</font> of substitution and transposition
	- number of <font color="#00b050">keys</font> used
		- types: asymmetric, two-key, public-key encryption...
	- way to <font color="#00b050">process</font> cipher plaintext
		- types: <font color="#00b050">block</font> cipher (in 1 block, out 1 block), <font color="#00b050">stream</font> cipher (continuous processing input and output one element at a time)
- <span style="background:#d3f8b6">unconditionally secure scheme</span>
	- *definition*: ciphertext does not contain enough <font color="#00b050">information</font> to determine plaintext
	- no encryption algorithm is unconditionally secure (except one-time pad)
- criteria of encryption algorithm (*computationally secure*)
	- cost of breaking > value of encrypted information OR
	- time of breaking > useful lifetime of information


<span style="background:rgba(3, 135, 102, 0.2)">Substitution Techniques</span>
- basic building block: 1) substitution 2) transposition

### Caesar Cipher
- circular rotate alphabet
	- C = E(k,p) = (p+k) mod 26 %% p here is each plaintext letter %%
	- p = D(k, C) = (C - k) mod 26
- easy to decrypt: only 25 possible keys

### Monoalphabetic Cipher
- cipher can be any permutation of 26 alphabetic characters (one plaintext letter randomly correspond to another letter)
- way to attack
	- compare relative frequency of letters with natural distribution in English
	- look for repeated patterns to determine the whole cipher map
- easy to break: ciphertext contains the frequency information of plaintext

### Playfair Cipher
- ![[IS notes-20231212-6.png|397]]
- how to encrypt
	- break plain text into pairs, and filled with "filler letter". balloon -> ba lx lo on
	- two plaintext letter at the same row: replaced by letter to the right: ar -> RM (circularly right)
	- two plaintext letter at the same column: replaced by letter to the letter beneath: mu -> CM
	- otherwise, each plaintext in a pair is replaced by the letter lies in its own row and column occupied by the other plaintext letter: hs -> BP
- analysis
	- hard to identify individual diagram
	- encrypt by pair, frequency information is wiped
	- but still easy to break: leaves much of structure of plaintext language intact

### Hill Cipher
- $\mathbf{A}=\begin{pmatrix}5&8\\17&3\end{pmatrix}$, $\mathbf{A^{-1}}mod26=\begin{pmatrix}9&2\\1&15\end{pmatrix}$,
  $\mathbf{AA^{-1}}=\begin{pmatrix}53&130\\156&79\end{pmatrix}mod26 = \begin{pmatrix}1&0\\0&1\end{pmatrix}$
- how to calculate inverse matrix
	- determinant: ![[IS notes-20231212-7.png]]
	- $$ [\mathbf{A}^{-1}]_{ij}=(\det\mathbf{A})^{-1}(-1)^{i+j}(\mathbf{D}_{ji})$$
- Hill algorithm
	- take m successive plaintext letters and substitute with m ciphertext letters, and the process of substitution is determined by m linear equations: $$ \begin{aligned}c_1&=(k_{11}p_1+k_{21}p_2+k_{31}p_3)\bmod26\\c_2&=(k_{12}p_1+k_{22}p_2+k_{32}p_3)\bmod26\\c_3&=(k_{13}p_1+k_{23}p_2+k_{33}p_3)\bmod26\end{aligned}$$
	  or in a matrix form: $$ (c_1\:c_2\:c_3)=(p_1\:p_2\:p_3)\begin{pmatrix}k_{11}&k_{12}&k_{13}\\k_{21}&k_{22}&k_{23}\\k_{31}&k_{32}&k_{33}\end{pmatrix}\mathrm{mod}\:26$$
	  $\mathbf{C} = \mathbf{PK}mod26$
	- decryption use $\mathbf{K^{-1}}$

### Polyalphabetic Cipher
- to improve simple monoalphabetic techniques: use different monoalphabetic substitutions as one proceed
- characteristics
	- set of monoalphabetic substitution rules is used
	- key determine rule to be used

<span style="background:rgba(3, 135, 102, 0.2)">Vigenère cipher</span>
- contains Caesar ciphers, each cipher denoted by a key letter
- plaintext: $P=p_0, p_1, ..., p_n$, key: $K=k_0, k_1, ..., k_m$. ($n>m$)
- $$ \begin{aligned}&C=E(K,P)=(p_0+k_0)\bmod26,\:(p_1+k_1)\bmod26,\:\ldots\:,(p_{m-1}+k_{m-1})\bmod26,\\&(p_m+k_0)\bmod26,\:(p_{m+1}+k_1)\bmod26,\:\ldots\:,(p_{2m-1}+k_{m-1})\bmod26,\:\ldots\end{aligned}$$ $$C_{i}=(p_i + k_{i\space mod \space m})mod \space 26$$
- Decryption: $p_{i} = (C_i-k_{i\space mod \space m})mod \space 26$
- strength: multiple ciphertext letters for each plaintext letter, one for each unique letter of keyword
- letter frequency is obscured, but still some frequency information remains
- cryptanalysis of Vigenere cipher
	- determine length of keyword
	- attack by frequency technique for each of the monoalphabetic cipher
- autokey system
	- keyword concatenated with the plaintext itself to provide a running key

<span style="background:rgba(3, 135, 102, 0.2)">Vernam Cipher</span>
- choose keyword that as long as the plaintext and has no statistical relationship to it
- works on binary data
- encryption: $c_i = p_i \oplus k_i$, decryption: $p_i = c_i \oplus k_i$

<span style="background:rgba(3, 135, 102, 0.2)">One-Time Pad</span>
- key is as long as the message, used one-time then discarded
- no way to attack (attack may result in multiple plausible results, can't determine which one is correct)
- challenges
	- problem of generating large quantities of random keys
	- key distribution and protection

<span style="background:rgba(3, 135, 102, 0.2)">Transposition Techniques</span>
- Rail Fence: ![[IS notes-20231212-8.png|300]]
- ![[IS notes-20231212-9.png|400]]
	- write plaintext row-by-row, and cipher according to the column number from key and encrypt it column by column
	- by more than 1 stage of transposition, it will become less easy to reconstruct

<span style="background:rgba(3, 135, 102, 0.2)">Steganography</span>
- 藏头诗（？）
- form
	- character marking
	- invisible ink
	- pin puncture
	- typewriter correction ribbon
- drawbacks
	- overhead to hide relatively few bit of information (capacity is low)
	- once system is discovered, it will become worthless
- advantage
	- can be used to secretly send messages without the transmission being detected. (encryption will flag traffic as secret/important, steganography will not draw attention)

## Lecture 6 Block Cipher

### Stream Cipher
- encrypts a digital data one bit or one byte at a time
- example: Vigenere cipher, Vernam cipher
- limitation: (distribution) keystream must be provided to both users in advance via some independent and secure channel
- introduce insurmountable logistical problems
- ![[IS notes-20231212-10.png]]

### Block Cipher
- ![[IS notes-20231212-11.png]]
- definition: a block of plaintext is treated as a whole and used to produce ciphertext block of equal length
- compared with stream cipher: block cipher share same key

<span style="background:rgba(3, 135, 102, 0.2)">Feistel Cipher Structure</span>
- motivation
	- same length of plaintext and ciphertext
	- plaintext must generate unique ciphertext ("reversible" or "nonsingular")
- Nonsingular and singular transformation
	- 1 to 1 mapping -> nonsingular
- idea to approximate ideal block cipher
	- for block cipher: larger the block size (n) & more arbitrary substitution ➡ more secure, but n can't be impractically large
	- utilizing execution of <font color="#00b050">multiple ciphers in sequence</font> so that the result will be stronger


<span style="background:rgba(3, 135, 102, 0.2)">General n-bit-n-bit Block Substitution</span>
- ![[IS notes-20231212-12.png|300]]
- vulnerable to frequency attack
	- small block size will result this problem

### Feistel Cipher
- Basic concepts
	- substitution
		- each plaintext element uniquely replaced by a corresponding ciphertext element
	- permutation
		- each plaintext element uniquely replaced by a permutation of that sequence
	- basic idea: <font color="#00b050">confusion and diffusion</font>
- confusion and diffusion
	- ideal: all statistics of the ciphertext are independent of the particular key used
	- *diffusion*: statistical structure of plaintext is dissipated into long-range statistics of the ciphertext (avoid finding plaintext from ciphertext)
		- how to realize: one ciphertext is affected by multiple plaintext digits
		- example: $$ y_n=\left(\sum_{i=1}^km_{n+i}\right)\mathrm{mod}26$$
	- *confusion*: make relationship between the statistics of ciphertext and the value of the encryption key as complex as possible (avoid finding key from ciphertext)
		- how to realize: complex substitution algorithm

#### Feistel Cipher Structure
- ![[IS notes-20231212-13.png|450]]
- *encryption*
	- divide into two parts LE & RE
	- different rounds have different keys, any round can be implemented
	- all rounds have the same structure
- *decryption*
	- same process, reverse order keys
	- no need to different algorithms
- realization of Feistel network depends on these parameters (<font color="#00b050">design features</font>)
	- *block size*: larger -> more secure
	- *key size*: larger -> more secure, lower speed
	- *number of rounds*: more -> more secure
	- *subkey generation algorithm*: greater complexity -> harder to cryptanalysis
	- *round function F*: greater complexity -> more secure
- detailed analysis of encryption and decryption
	- encryption side
	  $LE_{16} = RE_{15}$
	  $RE_{16}=LE_{15} \oplus F(RE_{15}, K_{16})$
	- decryption side ![[IS notes-20231212-14.png|221]]
	  $LD_1 = RD_0 = LE_{16}=RE_{15}$
	  $RD_1=LD_0 \oplus F(RD_0,K16)=RE_{16} \oplus F(RD_0,K16)=[LE_{15}\oplus F(RE_{15},K_{16})]\oplus F(RE_{15},K_{16})$
	- XOR properties
		- $$[A\oplus B]\oplus C = A \oplus [B\oplus C] $$ $$D \oplus D = 0 $$ $$E \oplus 0 = E$$
	- each iteration encryption: $LE_i = RE_{i-1}$, $RE_i=LE_{i-1}\oplus F(RE_{i-1},K-i)$
	- ![[IS notes-20231212-15.png|292]] ![[IS notes-20231212-16.png|351]]



## Lecture 7 Block Cipher & AES

### DES: Data Encryption Standard
- encrypt 64-bit input with a 56-bit key
- encryption
	- ![[IS notes-20231212-17.png|450]]
	- 64-bit key input, but last 8 bits used as parity bits or set arbitrary
	- exact structure of Feistel cipher
	- <span style="background:#d3f8b6">Avalanche Effect</span>
		- small change in plaintext or key should produce a significant change in ciphertext
		- this effect happens in DES
- strength of DES
	- key size
		- needs to be larger to make it hard to attack by brute force
	- nature of algorithm
		- robust so far
- timing attacks
	- information about the key or plaintext is obtained by observing how long it takes a given implementation to perform decryption on various ciphertext

### Block Cipher Design Principles
- 3 critical aspects of block cipher design
	- **number of rounds**
		- criteria: known cryptanalysis require greater effort than brute-force key search attack
		- more than 16 rounds will make the cryptanalysis method less efficient than brute-force search
	- **design of function $F$**
		- non-linear
		- hard to approximate $F$ by a set of linear equations
		- should have good avalanche properties
		- strict avalanche criterion (SAC): any output bit will change with probability 0.5 when any single input bit is inverted
		- bit independence criterion (BIC): output bots j and k should change independently when any single input bit is inverted
	- **key scheduling**
		- select subkeys to maximize the difficulty of deducing individual subkeys and the difficulty to work back to the main key

## Lecture 8 AES

<span style="background:rgba(3, 135, 102, 0.2)">Introduction</span>
- symmetric block cipher, <font color="#00b050">not</font> a Feistel structure
- operate on 8-bit bytes
- XOR: addition of two bytes
- multiplication: in finite field GF, with $m(x)=x^8+x^4+x^3+x+1$
	- irreducible polynomial: can't be expressed by product of lower degree polynomials

### general structure of AES
- ![[IS notes-20231212-18.png|550]]
- input: 128bits, key length: 16/24/32 bytes
- input converted into 4\*4 matrix, copied into state array which is modified at each stage.
- key is also depicted as a square matrix of bytes
- each word is 4 bytes, total key schedule is 44 words for 128-bit key
- ordering of key matrix is by column ![[IS notes-20231212-19.png|600]]
- number of rounds
	- 10 for 16-byte key, 12 for 24-byte key, 14 for 32-byte key
- N-1 rounds functions
	- *SubBytes*
		- ![[IS notes-20231212-20.png|450]]
		- essentially: table look-up
			- leftmost 4 bits of the byte are used as a row value and the rightmost 4 bits are used as a column value
			- example: {95} -> row 9, col 5 ![[IS notes-20231212-21.png]]![[IS notes-20231212-22.png]]
			- how to construct S-box
				- initialize: row y col x has value {yx}
				- map each byte in S-box to its multiplicative inverse in the field GF($2^8$)
				- each byte consist 8 bits, apply transformation: $$ b'_i=b_i\oplus b_{(i+4)\bmod8}\oplus b_{(i+5)\bmod8}\oplus b_{(i+6)\bmod8}\oplus b_{(i+7)\bmod8}\oplus c_i$$
				- ![[IS notes-20231212-23.png]]
	- *ShiftRows*
		- ![[IS notes-20231212-24.png]]
		- 1st row: not altered
		- 2nd row: circular left shift 1 byte
		- 3rd row: circular left shift 2 byte
		- 4th row: circular left shift 3 byte
	- *MixColumns*
		- ![[IS notes-20231212-25.png]]
	- *AddRoundKey*
		- ![[IS notes-20231212-26.png]]
		- state (1st matrix) XOR round key
- final round
	- only three transformation (no MixColumns)
- before first round
	- only AddRoundKey operation
- detail structure
	- ![[IS notes-20231212-27.png|475]]
	- not Feistel structure
		- not modify half: every round process the whole block
	- key expanded into an array of 44 32-bit words, 4 distinct words serve as a round key
		- RotWord: one-byte circular left shift
	- 4 stages each round: <font color="#00b050">1 permutation, 3 substitution</font>
		- SubBytes: Uses an S-box to perform a byte-by-byte substitution of the block
		- ShiftRows: A simple <font color="#00b050">permutation</font>
		- MixColumns: A substitution that makes use of arithmetic over GF(2^8)
		- AddRoundKey: A simple bitwise XOR of the current block with a portion of the expanded key
	- only AddRoundKey stage uses key, other stage is reversible and can be done without knowing the key
	- decryption process is not identical as the encryption
	- state is the same for both encryption and decryption


## Lecture 9 Random Bit Generation and Stream Ciphers

### introduction
- usage: key generation, encryption
- two strategies to generate random bits
	1. compute bits deterministically using algorithm, called <font color="#548dd4">pseudorandom number generators</font> (PRNGs) or <font color="#548dd4">deterministic random bit generators</font> (DRBGs)
	2. produce bits <font color="#e36c09">non-deterministically</font> using physical sources that produce some random output, called <font color="#e36c09">true random number generators</font> (TRNGs) or <font color="#e36c09">non-deterministic random bit generators</font> (NRBGs)
- network security algorithms that makes use of random binary numbers
	- key distribution and mutual authentication scheme
	- session key generation
		- secret key for symmetry encryption is generated for particular session and is valid for a short period of time
- randomness
	- <span style="background:#d3f8b6">criteria</span>
		- uniform distribution
		- independence
	- unpredictability
	- inefficiency
		- enhance: pretend to generate random number
- TRNGs, PRNGs, and PRFs
	- use algorithms to generate is not statistically random
	- *TRNG*
		- input: source of true randomness (ex.: instantaneous value of system clock)
		- conversion to binary -> random bit stream
	- *PRNG*
		- input: a fixed value (seed) + (maybe) previous output
		- can be reproduced if the adversary knows the algorithm and the seed
	- *PRF* (Pseudo-Random Function)
		- used to produce a pseudo-random string of bits of fixed length
		- input: seed, <font color="#00b050">context-specific value</font> and previous output
		- no difference between PRF and PRNG

### PRNG requirements
- adversary who doesn't know the seed is unable to determine the pseudorandom string
- normally 128-bit key, but PRF does not generate effectively random 128-bit output values, it may be possible to narrow the possibilities and use brute-force
- how to <span style="background:#d3f8b6">test randomness</span>
	- *uniformity*: any point in generation, the occurrence of 0 and 1 is equally likely
	- *scalability*: test can also be applied to subsequence extracted at random from the original sequence
	- *consistency*: behavior of generator must be consistent across starting value (seed)
- examples of tests
	- <font color="#e36c09">frequency test</font>: number of zeros should be approximately the same as that of ones
	- <font color="#e36c09">runs test</font>: focus on total number of run (an uninterrupted sequence of identical bits bounded before and after with a bit of the opposite value)
	- <font color="#e36c09">Maurer's universal statistical test</font>: focus on the number of bits between matching patterns, in order to detect whether the sequence can be compressed without loss of information (if can compress: not random)
- <span style="background:#d3f8b6">two forms of unpredictability</span>
	- <font color="#0070c0">forward unpredictability</font>: seed unknown, next output should be unpredictable in spite of any knowledge of previous bits
	- <font color="#0070c0">backward unpredictability</font>: can't determine the seed from knowing generated values
- seed requirement
	- must be unpredictable
	- typically, seed is generated by TRNG

### PRNG algorithms (2 types)
- purpose-built algorithms
	- only designed for generating pseudo-random bit stream
- algorithms based on existing cryptographic algorithms
	- Cryptographic algorithms randomising input data
		- <span style="background:#d3f8b6">3 cryptographic algorithms to generate PRNGs</span>
			1. <font color="#00b050">symmetric</font> block ciphers
			2. <font color="#00b050">asymmetric</font> ciphers
			3. <font color="#00b050">hash</font> functions and message authentication codes

### Linear Congruential Generators
- parameterized with four numbers
	1. $m$: modulus, $m>0$
	2. $a$: multiplier, $0<a<m$
	3. $c$: increment, $0\le c <m$
	4. $X_0$: starting value or seed, $0\le X_0 < m$
- $$ \begin{aligned}X_{n+1}\:=\:(aX_n\:+\:c)\bmod m\end{aligned}$$
	- range: $0\le X_m \le m$
- selection of $a,c,m$ is critical (if wrongly selected, it will be periodic)
	- $m$: <font color="#00b050">very large</font> to produce long sequence of random numbers (usually chosen to be maximum representable non-negative number of a computer)
- test for evaluation of random number generator
	1. function should be a full-period generating function (all number from 0 to m-1 should be generated before repeating)
	2. generated sequence should appear random
	3. function should implement efficiently with 32-bit arithmetic
- to meet this criteria:  $X_{n+1}=(aX_n)\mathrm{~mod~}(2^{31}-1)$
- strength of this algorithm
	- resulting sequence is statistically indistinguishable from a sequence drawn from (1,m-1)
- drawback
	- once the value of seed is chosen, the sequence is determined
	- knowledge of small part of the sequence is sufficient to determine the parameters of the algorithm (known $X_0, X_1, X_2, X_3$, then $a,c,m$ can be solved)
- to alleviate this drawback
	- make actual sequence used <font color="#00b050">nonreproducible</font>: use <font color="#00b050">internal system clock</font> to modify random number stream
		- <font color="#00b050">restart sequence</font> after $N$ numbers using the current clock value as the new seed
		- <font color="#00b050">add current clock value</font> and mod $m$

### Blum Blum Shub (BBS) Generator
- procedure
	- choose two large prime number $p$, $q$ that both have a remainder 3 when divided by 4: $p\equiv q\equiv3(\operatorname{mod}4)$
	- let $n = p \times q$
	- choose number $s$ that relatively prime to $n$ (so that $p$ and $q$ aren't factor of $s$)
	- then a sequence of bits $B_i$ can be generated by: 
	  $$ \begin{array}{rcl}\mathrm{X}_0&=&\mathrm{s}^2\mod\:n\\\mathrm{for}\quad\mathrm{i}&=&1\:\textsf{to}\:\infty\\\mathrm{X}_i&=&(\mathrm{X}_{i-1})^2\mod\:n\\\mathrm{B}_i&=&\mathrm{X}_i\mod\:2\end{array}$$
- pros
	- cryptographically secure pseudo-random bit generator
- "CSPRBG"
	- definition: pass next-bit test
		- <font color="#0070c0">next-bit test</font>: find if there is a polynomial-time algorithm that on input of the first k bits of an output sequence, can predict the (k+1) bit with probability significantly higher than 0.5

### Public-key Cryptography
- based on <font color="#0070c0">mathematical functions</font> rather than substitution and permutation
- asymmetric, need two separate keys
- correct some common misconceptions
	- public-key encryption is NOT more secure from cryptanalysis
	- public-key encryption is NOT a general-purpose technique
- terminologies
	- asymmetric key
		- private key & public key are used to perform complementary operations
	- public key certificate
		- a document that issued and signed by private key of a certification authority.
		- indicates subscriber identified in the certificate has sole control and access to the corresponding private key
	- public key cryptographic algorithm
		- algorithm uses two related key: public key and private key
		- it's impossible to derive private key from public key
	- public key infrastructure (PKI)
		- policies, processes, platforms, software and workstations for administration of certificates and public-private key pairs
- evolved from two problems associated with symmetric encryption
	- key distribution
		- requirement for symmetric encryption
			- either two parties share a key that has been distributed
			- use of key distribution center
		- total secrecy over communication
	- digital signatures
		- motivation: can a message be identified to be sent by a particular person?
- characteristic of asymmetric encryption algorithm
	- computationally infeasible to determine the decryption key given <font color="#0070c0">cryptographic algorithm</font> & <font color="#0070c0">encryption key</font>
	- some other characteristics shown in certain algorithms
		- either one related key can be used for encryption with the other for decryption
- procedures
	- ![[IS notes-20231212-28.png|550]]
	- ![[IS notes-20231212-29.png|550]]
	- essential steps
		1. each user generates a pair of keys
		2. each user place one of the keys to public access, while the other keep private
	- entire encrypted message serves as a digital signature.
- classification of public-key cryptosystem
	- encryption/decryption
	- digital signature
	- key exchange
- requirement for public-key cryptography
	- computationally easy for each party to generate a key pair
	- computationally easy for sender to encrypt message
	- computationally easy for receiver to decrypt ciphertext
	- computationally infeasible for adversary knowing public key to determine private key or decrypt the ciphertext

### Comparison of Symmetric Encryption and Public-Key Encryption

| Conventional Encryption                                                                                                                                                                                                                                                      | Public-Key Encryption |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| *Needed to work*:<br>1. same algorithm and same key used for encryption and decryption<br>2. sender and receiver share the algorithm and key<br>*Needed for security*:<br>1. key must keep secret<br>2. not knowing key can't decrypt, knowing ciphertext can't determine key | *Needed to work*:<br>1. a pair of keys, one for encryption and the other for decryption<br>2. sender and receiver have one of the matched pair of keys<br>*Needed for security*:<br>1. one of the keys must keep secret<br>2. not knowing the other key can't decrypt, knowing public key, algorithm and ciphertext can't determine private key                     |

## Lecture 10 PKCS & Network Security

### Diffie-Hellman Algorithm
- [Reference: Wikipedia](https://zh.wikipedia.org/wiki/%E8%BF%AA%E8%8F%B2-%E8%B5%AB%E7%88%BE%E6%9B%BC%E5%AF%86%E9%91%B0%E4%BA%A4%E6%8F%9B), scenario: <font color="#00b050">key exchange</font>
- based on the effectiveness on the difficulty of computing discrete logarithms
	- basis: for any integer $b$ and $a$, and prime number $p$, we can find a unique exponent $i$ such that 
	  $$ b\equiv a^i\left(\operatorname{mod}p\right)\quad\text{where}\:\:0\leq i\leq(p-1)$$
- steps
	1. A and B share a prime number $q$ and an integer $\alpha$, such that $\alpha < q$ and $\alpha$ is a primitive root of $q$ ($\alpha^k = n \: mod \: q$)
	2. A generates private key $X_A$ such that $X_A < q$, and also B generates private key $X_B$
	3. A calculates public key $Y_A = \alpha^{X_A}\:mod\:q$, so do B generates $Y_B = \alpha^{X_B}\:mod\:q$
	4. A receives $Y_B$ and B receives $Y_A$
	5. A calculates shared secret key $K=(Y_B)^{X_A}\:mod\:q$, B calculates shared secret key $K=(Y_A)^{X_B}\:mod\:q$
- mathematical equation of this algorithm:
  $$ \begin{aligned}K&=(Y_B)^{X_A}\operatorname{mod}q\\&=(\alpha^{X_B}\operatorname{mod}q)^{X_A}\operatorname{mod}q\\&=(\alpha^{X_B})^{X_A}\operatorname{mod}q\\&=\alpha^{X_BX_A}\operatorname{mod}q\\&=(\alpha^{X_A})^{X_B}\operatorname{mod}q\\&=(\alpha^{X_A}\operatorname{mod}q)^{X_B}\operatorname{mod}q\\&=(Y_A)^{X_B}\operatorname{mod}q\end{aligned}$$
- symmetry property: $a\equiv b\mathrm{~(mod~}q)\mathrm{~if~}b\equiv a\mathrm{~(mod~}q)$
- Man in the Middle Attack
	- ![[IS notes-20231212-30.png|500]]
	- A and B thought they share a secret key but their future communication will be monitored and changed by Darth.
	- key exchange protocol is vulnerable because it does not authenticate the participants.
		- how to overcome: digital signatures, public-key certificates

### Network Access Control (NAC) and Security
- <span style="background:#d3f8b6">NAC</span>: umbrella term for managing access to a network
	- <font color="#00b050">authenticate</font> users logging in
	- data <font color="#00b050">access</font>
	- <font color="#00b050">actions</font> to be performed
	- <font color="#00b050">examine</font> the health of users' devices
-  Components NAC Deal With
	- <font color="#548dd4">access router</font> (AR)
		- node attempts to access the network
		- can be any device managed by NAC system
		- referred to as <font color="#548dd4">supplicants</font>, or <font color="#548dd4">clients</font>
	- <font color="#fac08f">policy server</font>
		- determine what access should be granted
		- rely on backend system to help determine host's condition
	- <font color="#92cddc">network access server</font> (NAS)
		- access control point for users
		- also called <font color="#92cddc">media gateway</font>, or <font color="#92cddc">remote access server</font> (RAS)
	- ![[IS notes-20231212-31.png|400]]
- Procedure
	- different ARs seek access
	- authenticate AR
		- involving secure protocol and cryptographic keys
		- may be performed by NAS, or mediated by NAS
			- between supplicant and authentication server: policy server
				- policy server will perform checks, verify compliance with requirements from secure configuration baseline
		- purposes of authentication
			- verify <font color="#00b050">identity</font> (determine privilege)
			- result in <font color="#00b050">establishment of session keys</font> to enable future communication
	- once authenticate: NAS enable AR to interact with resources in the network
- NAC enforcement methods
	- IEEE802.1X & VLAN
		- IEEE802.1X: link layer protocol: enforces authorization before assigning IP address
		- make use of Extensible Authentication Protocol for authentication
		- VLAN: logical subgroup within LAN created by software
			- combine user station and network devices into 1 unit
			- more efficiently to flow
			- network segmented logically into virtual LANs
			- NAC decides which VLANs will direct AR
			- VLAN can be created dynamically and VLAN membership may overlap.
	- Fire wall & DHCP management
		- firewall
			- a form of NAC by allowing or denying network traffic
		- Dynamic Host Configuration Protocol (DHCP)
			- protocol enables dynamic allocation of IP address to hosts
			- intercepts DHCP requests and assigns IP address
			- easy to install and configure but subject to various IP spoofing, limited security
	- Extensible Authentication Protocol (EAP)
		- framework for network access and authentication protocol
		- provides a set of protocols between a client and an authentication server
		- operate over variety of network and facilities, accommodate authentication needs of various networks
		- ![[IS notes-20231212-32.png|425]]
		- components of EAP
			- EAP peer: client computers
			- EAP authenticator: access point or NAS requires EAP authentication before granting access to network
			- authentication server: negotiate use of EAP method with EAP peer, validate EAP peer's credentials, authorize access to network
				- usually a Remote Authentication Dial-In User Service (RADIUS) server
			- ![[IS notes-20231212-33.png|425]]
	- Authentication Methods
		- authenticator decisions involves
			- authentication
			- authorization

## Lecture 1-10 Review

- definition of information security
- how to ensure appropriate security
- secure design principles
- threat definition
- threat vector
- types of attacks
- security model: CIA triad
- model of network security
- symmetric cipher model
- unconditionally secure scheme
- ciphers
	- substitution
	- caesar cipher
	- monoalphabetic cipher
	- playfair cipher
	- hill cipher
	- vigenere cipher
	- vernam cipher
	- one-time pad
	- transposition technique
	- stream cipher
	- block cipher
	- feistel cipher structure
	- DES
	- AES
- Randomness
	- TRNG, PRNG, PRF
	- Linear Congruential Generator
	- Blum Blum Shub Generator
- Public-key cryptosystem

## Lecture 11 Distributed Ledger Technology (DLT) & Block Chain

### DLT
- ledger: records of maintenance of property
	- maintenance: transactions/ownership
- <span style="background:#d3f8b6">classification</span>
	1. in terms of identity of nodes
		- permissioned
		- permissionless
	2. in terms of reading data
		- public
		- private
- comparison with database management system (DBMS)
	- DLT
		- <font color="#00b050">no central</font> entity
		- <font color="#00b050">consensus</font> through mining nodes
		- data kept by every node
		- has common records, global view and is <font color="#00b050">distributed</font>
	- DBMS: centralized management, consensus through central entity

### Blockchain
- <span style="background:#d3f8b6">data structure for DLT</span>
	- linear linked list of blocks (blockchain)
	- directed acyclic graph (DAG)
	- tree-like data structures
- blockchain is NOT essentially chain of blocks, it can be DAG as well
- <span style="background:#d3f8b6">definition of blockchain</span>
	- data is read only and cannot be modified once it is entered into the blockchain and new data can only be appended at the end of blockchain, making blockchain highly immutable
- <span style="background:#d3f8b6">key feature of blockchain</span>
	- eliminate third party involvement in maintaining the blockchain network
- <span style="background:#d3f8b6">components of blockchain</span>
	- *block*: basic component, where transactions are assembled in blocks
	- *chain*: each of these blocks is <font color="#00b050">linked</font> together to form blockchain
	- *transactions*: store <font color="#00b050">information</font>

#### Features of Blockchain System
- *decentralization*
	- no central entity or intermediary to control or validate the transactions
	- users have data control capability
- *transparency*
	- anyone can track transaction history
- *immutability*
	- once transaction added to blockchain can validated by the participating nodes, it can't be changed
- *availability*
	- ledger can be accessed by all nodes
- *pseudonymity*
	- identity is partially revealed, making blockchain system privacy aware
- *security*
	- strong public & private keys
	- hashing algorithms
	- digital signatures
	- encryption techniques
- *non-repudiation*
	- once transaction was added and validated, it can't be disowned by the blockchain node
- *auditability*
	- public blockchain: one can audit whole ledger itself
	- private blockchain: only authorized entity can perform audit
- *data tampering*
	- blockchain store the hash of the previous block

## Lecture 12 Overview of Blockchain System

### Blockchain Classifications
- from <span style="background:#d3f8b6">network perspective</span>
	- public
	- private
	- consortium
- from <span style="background:#d3f8b6">access permission perspective</span>
	- permissioned
		- consortium blockchain
		- private blockchain
	- permissionless
		- public blockchain

#### Public Blockchain Network—Permissionless
- any blockchain node can join or leave at any time
- any node can participate in mining process
- completely decentralized
- example: bitcoin
- general issues of public blockchain
	- limited transactions
		- less than 10 transactions/second (Tps) can be handled for Bitcoin
	- scalability
		- amount of participating blockchain nodes will increase exponentially
	- pseudonymity
		- trigger privacy attacks & exploited by malicious nodes
	- limited block size
	- energy consumption
		- reliance of public blockchain system on PoW cryptographic puzzle, huge amount of energy is consumed
#### Private Blockchain Network—Permissioned
- node can join or leave with the permission from central entity
- completely centralized
- miners are selected a priori

#### Consortium Blockchain Network—Permissioned
- not completely centralized nor decentralized (partially centralized)
- nodes can join or leave with the permission from the <font color="#00b050">consortium</font> of nodes
- not all the nodes can validate transactions

### Blockchain and Database Maintenance
- database system
	- centralized
		- maintenance is the responsibility of the central entity, which requires it to be reliable and trusted
	- distributed
		- multiple designated nodes are responsible for database maintenance
- blockchain system
	- public blockchain
		- maintained by all nodes
		- an entity needed to resolve any conflicts or makes protocols
	- consortium blockchain
		- consortium of nodes is responsible for updating and maintaining the blockchain system
	- private blockchain
		- single node is responsible for blockchain maintenance
		- resemble centralized system
- Public Verifiability
	- allow system to be verified by the public
- Comparison between blockchain system and DBMS
	- hashing
		- DBMS: not applied
		- blockchain: critical role and applied to different stages
	- public/private key
		- DBMS: not applied
		- blockchain: essential requirement
	- sequence of records
		- DBMS: not maintained sequentially
		- blockchain: placed sequentially and linked each other
	- consensus
		- DBMS: not required
		- blockchain: essential
	- immutability
		- DBMS: not present
		- blockchain: a characteristic
	- ledger dissemination
		- DBMS: not required
		- blockchain: essential

### User/Nodes in a Blockchain Network
- user/node must generates public/private key pairs for authentication
- user/node has to establish minimum number of peer connection with other nodes

| behavior/types of nodes                            | full node             | lightweight node     | miner node            |
| -------------------------------------------------- | --------------------- | -------------------- | --------------------- |
| copy of ledger                                     | complete copy locally | partial copy locally | complete copy locally |
| transaction generation                             | yes                   | yes                  |                       |
| consensus participation                            |                       |                      | yes                   |
| routing for message dissemination and verification | yes                   | yes                  | yes                   |
| transaction validation                             |                       |                      | yes                      |

- classification of nodes
	- common classification
		- *full*
			- keep full copy of ledger
			- participate in transaction verification without reference to external nodes
			- participate in routing
		- *lightweight*
			- keep header of each block then reference to external node when required
			- participate in routing
		- *miner* (functionality)
			- carry consensus, responsible for publishing block
			- most powerful nodes, can change state of blockchain network
	- in terms of transaction
		- leader
			- nodes create blocks
			- can be elected and serves during a specific time
		- validator
			- nodes validate blocks
			- called as miner nodes
	- or
		- sender
			- creating transaction and issue transaction to multiple nodes
			- sign transactions with their private keys
		- receiver
			- receive transaction issued by sender nodes

### 6-Layers in Blockchain
- *Application*
	- directly interacts with user
- *Virtualization and Smart Contract*
	- interact with user machine and responsible to <font color="#00b050">compile</font> blockchain node & <font color="#00b050">visualize</font>
- *Consensus*
	- <font color="#00b050">manage</font> and <font color="#00b050">reach</font> consensus in P2P network
	- operate at <font color="#00b050">network level</font>
	- dictate which <font color="#00b050">protocol</font> to be used and how to follow protocol to achieve consensus
- *Network and OS*
	- managing underlying network services and operation over blockchain network
	- manage: communication mechanism, peer discovery, routing and peer-to-peer network
- *Data Organization and Topology*
	- data organization and topology management
	- tasks of this layer: hashing, data storage, cryptographic algorithms, data ordering, side chain, sharding and off-chain issues
	- issues of this layer: transaction models and Merkle Tree management
- *Hardware*

## Lecture 13-14 Working Principle of Blockchain

### General Process of Blockchain

>[!info] Working Sequence
>1. user creates account
>2. user creates transaction (Tx)
>3. transaction signed
>4. transaction broadcast to validating nodes
>5. transaction validated
>6. transactions gathered in the pool
>7. miner node gathers Txs and creates block
>8. miner node start mining
>9. block validation carried out
>10. successful miner adds block to the blockchain
>11. added block information broadcast to blockchain network
>12. blockchain node adds the broadcast block to their local copy of blockchain (block confirmation)
>13. block becomes part of global blockchain (block published)

### Blockchain Governance System

- Composition of a Block
	- hash pointer
		- point out the previous hash
		- used to verify the integrity of the blockchain
	- merkle tree
		- verify the set of all transaction quickly within a block
		- binary tree represent transactions in a block
		- detailed explanation: each <font color="#00b050">transaction</font>, a separate <font color="#00b050">hash</font> value is calculated. Then, the two hash values are <font color="#00b050">combined</font> to generate a new hash going upward toward the root. Then at the root, all the hash values are combined to create a new hash value. This hash value is then used for integrity and verification purpose. Now, if this hash value has been modified, it means, some transactions within the block have been modified
	- nonce
	- confirmation
	- time stamp
	- block version
	- Tx
- Ownership of Blockchain
	- different companies can operate in a consortium blockchain
	- if single organization involved, then considered as private blockchain
- Confidentiality in Blockchain
	- public blockchain system doesn't provide confidentiality except users and their actual identity are not disclosed using pseudonymity
	- consortium and private blockchain provide more confidentiality to users, however, nodes need more trust in such environment, and the identity should be known within the network

### Blockchain Platforms

types
1. suitable only for <font color="#00b050">cryptocurrency</font>
2. supports <font color="#00b050">smart contract</font>
3. available over the <font color="#00b050">cloud</font>

- examples of applications of blockchain
	- asset management & tracking
	- own assets in terms of token
	- cryptocurrency
	- smart contract based new business logic
- BitCoin Blockchain
	- consensus mechanism uses Proof of Work (PoW)
	- partially support smart contracts using UTXO
	- some nodes can keep the copy of ledger
	- virtual currency
		- transfer assets value
		- paid for mining process
	- features
		- cryptography
		- p2p network architecture
		- hashing algorithm
		- public/private key encryption
		- distributed storage
		- logically centralized
		- consensus algorithm
		- time stamping of transactions
	- working principle of BitCoin
		1. A participating node <font color="#548dd4">send a transaction</font> to neighboring nodes
		2. Neighboring nodes <font color="#548dd4">check</font> this transaction
		3. All the nodes including miners <font color="#548dd4">add</font> this transaction to the unverified <font color="#548dd4">transaction pool</font>.
		4. Miner node <font color="#548dd4">gathers</font> few transactions and <font color="#548dd4">starts mining</font> the block
		5. <font color="#548dd4">Informs</font> a block (including set of transactions) to the whole network.
		6. Full nodes (including miners) check different fields of the block and its <font color="#548dd4">validity</font>.
		7. The nodes <font color="#548dd4">add</font> correct block to their <font color="#548dd4">copy</font> of the ledger
	- block components
		- outer header
			- block size
			- block identification information
		- block header
			- information: block version, time stamp, hashing target, nonce, parent block hash, Merkle Tree root
		- block body
			- all transactions are assembled along with transaction counter
- Ethereum Blockchain
	- another public cryptocurrency
	- incorporate business logic to blockchain network in the form of smart contracts
	- Ethash: PoW, Ethereum 2.0 uses PoS
	- participate nodes need to install Ethereum Virtual Machine (EVM) to execute smart contracts
	- built on P2P network and require virtual P2P wire protocol
	- three types of users
		- contract account (CA)
			- normal users, make transactions
		- miners
		- externally owned account (EOA)
			- perform transactions to another EOA
			- can call the function of CA and they can also make a new smart contract

### Properties of Blockchain System

- smart contracts
	- classification
		- deterministic smart contracts
			- execution not dependent on external data or event
		- non-deterministic smart contracts
			- execution dependent on external data (called as oracles)
			- encourages innovative applications and business models
- scalability issues in blockchain system
	- considered in these aspects
		- How much <font color="#548dd4">scalable</font> the blockchain system is when we <font color="#548dd4">increase</font> the number of blockchain <font color="#548dd4">nodes</font>?
		- How blockchain system behave when there is an <font color="#548dd4">increase</font> in <font color="#548dd4">number of transactions</font>?
		- How blockchain system behaves when the <font color="#548dd4">size of the ledger</font> increases in terms of storage?
	- full copy of ledger will definitely keep increasing, thus it's problematic for nodes without high storage capacity
- transaction capacity
	- <font color="#548dd4">measurement</font> of blockchain system <font color="#548dd4">performance</font>: number of transaction handled per second by the blockchain
	- factors limit transaction handling capacity
		- transactions included in each block
		- transaction speed
		- interarrival time of blocks
	- how to increase transaction capacity
		- higher number of transactions included in each block
		- efficient and quick responding consensus algorithms required
		- fast interarrival time of blocks
		- offload transactions from the main blockchain to side chain
			- *off-chain transactions*: offload the transactions from the main blockchain to the side chain
			- only <font color="#00b050">hash</font> in the main blockchain while other data stored in off-chain solutions
		- sharding: proposed to handle transaction capacity
			- essence: splitting the network into smaller blockchains
			- blockchain nodes are <font color="#548dd4">divided</font> into multiple groups (shards) and each shard handle a certain amount of transactions in <font color="#548dd4">parallel</font>
			- but need to consider how different groups of nodes <font color="#00b050">communicate</font> with each other
- Interoperability (互通性)
	- implement and operate multiple distributed ledgers
	- ledgers can be developed by different organizations and thus designed for specific purposes
	- interoperability then required among ledgers to share information
	- this feature is promising to share and exchange cryptocurrencies of different ledgers
	- factors of interoperability
		- Smart Contract
		- Exchange
		- Consensus Protocols
		- Generation of blockchain systems
		- Transaction Speed
		- Semantic
		- Transaction Fees
		- Tokens
	- how to achieve interoperability
		- side chain
		- notary scheme
		- oracles
		- blockchain router
		- hash timelocks

## Lecture 15-16 Blockchain Consensus

- definition of consensus
	- reach a common agreement
	- decision of consensus reached, it will be <font color="#00b050">communicated</font> to other parties and the system state must be <font color="#00b050">updated</font>
	- there are different settings of consensus
- two types of nodes in consensus
	- legitimate nodes
	- malicious nodes
- system must operate properly even failures occur
	- types of failure
		- crash failure: legitimate node causes
		- byzantine failure: malicious node causes
- main responsibility of consensus protocol
	- <font color="#00b050">maintain</font> data in blockchain
		- originality, ordering and tamper-resistance
	- <font color="#00b050">reach agreement</font> among nodes

### Proof of Work
- PoW: consensus algorithms used in blockchain networks
- building block of Bitcoin blockchain, designed for public blockchain
- consensus finality in PoW is not guaranteed
- miner acts both leader and validator node
- main idea of PoW
	- <font color="#00b050">higher the hash rate</font>, <font color="#00b050">higher the chances</font> to solve the PoW cryptographic puzzle
	- node that solves PoW puzzle is winner, who will be able to <font color="#00b050">add</font> block to the blockchain and win the <font color="#00b050">reward</font>
- PoW nodes
	- leader node: win the mining process
	- wining probability: $$ P_{w_i}=\frac{\varphi_i}{\sum_{j=1}^N\varphi_j}$$, where $i$ is the participating node, $N$ is the total number of nodes, and $\varphi$ is the computational power
- issues of PoW
	- double spending problem
		- Double-spending occurs when someone alters a blockchain network and inserts a special one that allows them to reacquire a cryptocurrency.
	- probabilistic in nature since two or more nodes may solve the puzzle simultaneously, resulting in the creation of fork
	- long latency
	- computationally expensive
- fault-tolerant of PoW
	- susceptible to 51% attack
		- control more than 50% of the network's mining hash rate (computational power)
	- fault-tolerant to Byzantine Failure
	- attack-resistant against Sybil attacks
		- Sybil attack: malicious blockchain node create multiple pseudo identities to launch this attack

### PoS
- main idea of PoS
	- selection of miners depends on the amount of stakes each node carries instead of computational power
		- higher stake a node has, higher chances to select that node as a winning miner node
- <span style="background:#d3f8b6">advantage</span>
	- less consumption of energy
	- lower requirement in terms of computation power
	- faster transaction confirmation speed
- form of stake
	- amount of cryptocurrency
	- digital token
	- energy
	- computational power
- issues of PoS
	- subject to dominance by the most significant token holders
	- positive feedback loop (more token -> higher winning probability -> more reward -> more token)
	- message transmission loss and delay (synchronous problem)
		- without timely sharing message among committee members, performance of PoS consensus algorithm can be serious degraded
	- reward incentivization
		- reward should be awarded in the manner that all nodes get equal probability to participate the mining process

comparison between PoW and PoS

| aspect of comparison      | PoW                                                  | PoS                                                                 |
| ------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------- |
| mining/validating a block | amount of computational work                         | amount of stake                                                     |
| distribution of reward    | mines the block first wins                           | validator doesn't receive a block award since paid by network fee   |
| competition               | use computer processing power to solve puzzles       | algorithm determines winner based on the size of stake              |
| centralization            | centralized in nature                                | algorithm determines winner based on the size of stake              |
| specialized equipment     | GPU                                                  | standard server-grade service is sufficient for PoS system          |
| efficiency                | less energy efficient, less expensive, more reliable | cost and energy efficient, less reliable                            |
| adding a malicious block  | need more than 50% of computing power                | hackers should have more than 51% of all cryptocurrency              |
| security                  | greater the hash, more secure the work               | stake helps lock crypto assets to secure the network for the reward |
| forking                   | naturally prevent constant forkng                    | forking is not automatically discouraged by PoS                                                                    |

### Metrics of Consensus
- performance
	- transaction throughput
		- defined as: number of transactions per second a blockchain network can process
		- $$ Transaction\:Throughput=\frac{Block\:Size\:(Bytes)}{Transaction\:Size\:(Bytes)\times Block\:Time\:(seconds)},$$, where $Block\:Size$ varies from different block chain system, $Block\:Time$ is the time required to add a block to the blockchain
		- impact of transaction throughput and block size
			- larger block size, higher throughput (nearly linear)
		- impact of block confirmation time and throughput
			- near $Throughput=\cfrac{1}{Block\:Confirmation\:Time}$
		- impact of transaction size and transaction throughput
			- near $Throughput=\cfrac{1}{Transaction\:Size}$
		- a estimation formula: $$Transaction\:Throughput = \dfrac{Block\:Size}{Transaction\:Size \times Block\:Confirmation \: Time}$$
	- block confirmation time
		- defined as: time to confirm the block and it tells us how quickly a block can be confirmed in a blockchain system
		- depend on the number of blocks
		- a new block must wait before it's confirmed
		- can be measured in seconds
- scalability
	- ability to support increasing load of transactions & the number of nodes in the network
	- off-chain solutions
		- built on the top of the main chain blockchain and handle most of the transaction off-chain

### PAXOS

[reference textbook](https://link.springer.com/chapter/10.1007/978-1-4842-8179-6_7#Sec4)

#### main idea of PAXO
- allows consensus over a value under unreliable communications
- <font color="#00b050">majority</font> represents the whole — if more than half of processes choose a value, that value is the consensus
- scenarios
	- messages can pass through network without corrupted
	- fail-stop model: process can fail but not present Byzantine fault (not operate in malicious way)

#### nodes in PAXOS
three roles:
1. *proposer*: an <font color="#00b050">elected</font> proposer acts as a single <font color="#00b050">leader</font> to <font color="#00b050">propose</font> a new value. Proposers handle client <font color="#00b050">requests</font>.
2. *acceptor*: <font color="#00b050">evaluate</font> and <font color="#00b050">accept</font> or <font color="#00b050">reject</font> proposals proposed by the proposers according to rules and conditions
3. *learner*: <font color="#00b050">learn</font> the decision or the agreed-upon value

#### phases in PAXOS
- two phases: prepare & accept
- end of prepare phase: majority of acceptors have <font color="#00b050">promised</font> a specific proposal number
- end of the accept phase: majority of acceptors have <font color="#00b050">accepted</font> a proposed value, and consensus is reached

##### prepare phase
procedure
- proposer <font color="#00b050">receives a request</font> to reach consensus on a value by a client
- <font color="#00b050">sends a message</font> prepare (n) to a majority or all acceptors
- acceptor <font color="#00b050">receives</font> this prepare (n) message, it makes a “<font color="#00b050">promise</font>”

at this phase: <font color="#00b050">no value</font> is proposed for a decision yet. Here $n$ represents the proposal number, which must be globally <font color="#00b050">unique</font> and <font color="#00b050">greater</font> than any proposal number this proposer used before. Acceptors in the majority will respond.
- If <font color="#00b050">no previous promise</font> has been made by responding to this prepare ($n$) message, then the acceptor now promises to <font color="#00b050">ignore any request less than the proposal number n</font>. It <font color="#00b050">records n</font> and <font color="#00b050">replies</font> with message <font color="#00b050">promise(n)</font>.
- If the acceptor has <font color="#00b050">previously promised</font>, that is, already responded to another prepare message with some proposal number lower than n, acceptors will
	- if acceptor has <font color="#00b050">not received</font> any accept messages from proposer in accept phase: <font color="#00b050">store</font> the <font color="#00b050">higher</font> proposal number and <font color="#00b050">sends</font> a promise message to the proposer
	- if acceptor has received an accept message earlier with other lower proposal number, it must have <font color="#00b050">already accepted a proposed value</font> from some proposer. Previous full proposal is now <font color="#00b050">sent along with the promise message</font> to the proposer, <font color="#00b050">indicating</font> that the acceptor has already accepted a value.

##### accept phase
procedure
1. proposer waits until it gets response from majority of the acceptors for this proposal $n$
2. when responses are received, the proposer <font color="#00b050">evaluates</font> what value v should be sent in the accept message
3. proposer now <font color="#00b050">sends an accept message</font> – a <font color="#00b050">full proposal</font> of the form accept <font color="#00b050">(n, v)</font> – to the acceptors, where n is the promised proposal number and v is the actual proposed value
4. when an acceptor receives this accept(n, v) message, it <font color="#00b050">replies with accepted(n, v)</font> and sends accepted(n, v) to all <font color="#00b050">learners</font> or ignores the proposal
5. if a majority of acceptors accept the value v in the proposal, then <font color="#00b050">v becomes the decided value</font> of the protocol i.e., consensus is reached

number of acceptors
- in order to tolerate $f$ faulty acceptors, at least a set consisting of $2f + 1$ acceptors is required

how does proposer evaluate what value $v$ should be sent in the accept message:
- if proposer <font color="#00b050">received</font> one or more promise messages with <font color="#00b050">full proposals</font>, it chooses value $v$ in the proposal with <font color="#00b050">highest proposal number</font>
- if <font color="#00b050">no</font> promise messages received by proposer include a full proposal, proposer can choose <font color="#00b050">any</font> value

what do acceptors do when receive accept(n,v) message
- if the acceptor has <font color="#00b050">promised not to</font> accept this proposal number previously, it will <font color="#00b050">ignore</font> the message
- if it <font color="#00b050">has responded</font> to the corresponding prepare request with the same n, that is, prepare(n), only then it replies with accepted(n, v) <font color="#00b050">indicating acceptance</font> of the proposal
- finally, acceptors send accepted(n,v) to all learners

![[IS notes-20231218-1.png|600]]


### RAFT

#### main idea
- RAFT: Replicated And Fault Tolerant
- key idea: enable state machine replication with a persistent log
- allows cluster reconfiguration which enables <font color="#00b050">cluster membership</font> changes without service interruption
- RAFT allows <font color="#00b050">log compaction</font> to alleviate the issue of consuming too much storage and slow rebuild after node crashes
- scenarios: no byzantine failures, unreliable network communiacation, asynchronous communication and processors

#### nodes in RAFT
three roles:
1. leader: receives client <font color="#00b050">requests</font>, manages replication <font color="#00b050">logs</font>, and manages <font color="#00b050">communication</font> with the followers
2. follower: nodes are <font color="#00b050">passive</font> in nature and only <font color="#00b050">respond</font> to Remote Procedure Call (RPCs), <font color="#00b050">never initiate</font> any communication
3. candidate: used by a node that is trying to become a leader by <font color="#00b050">requesting votes</font>

![[IS notes-20231218-2.png|500]]

#### phases in RAFT
2 phases:
- leader election
- log replication

##### leader election
process
1. all nodes start up as followers
2. followers will run as followers as long as they keep receiving valid RPCs from a leader or candidate
3. if a follower does <font color="#00b050">not receive heartbeats</font> from the leader for some time, then an “<font color="#00b050">election timeout</font>” occurs, which indicates that the leader has failed. Now the follower node undertakes the candidate role and attempts to become the leader by starting the election process
4. if a node receives votes from the <font color="#00b050">majority</font> of the nodes, then it becomes the leader, other nodes are followers. If no one wins the elections and election timeout occurs, the election process <font color="#00b050">starts again</font> with a new term

leader election

![[IS notes-20231218-3.png|500]]

##### log replication
process
1. client <font color="#00b050">sends command</font>s/requests to the leader to be executed by the replicated state machines
2. leader assigns a <font color="#00b050">term</font> and <font color="#00b050">index</font> to the command so that the command can be <font color="#00b050">uniquely identified</font> in the logs held by nodes. Leader appends this command to its log
3. when the leader has a <font color="#00b050">new entry</font> in its log, at the same time it sends out the <font color="#00b050">requests</font> to replicate this command via the <font color="#00b050">AppendEntries RPC</font> to the follower nodes
4. when the leader is <font color="#00b050">able to replicate</font> the command to the majority of the follower nodes, that is, <font color="#00b050">acknowledged</font>, the entry is considered committed on the cluster.
5. leader <font color="#00b050">executes</font> the command in its state machine and returns the <font color="#00b050">result</font> to the client. It also notifies the followers that the entry is committed via the AppendEntries RPC, and the followers execute committed commands in their state machines

logs:

![[IS notes-20231218-4.png|400]]

log replication:

![[IS notes-20231218-5.png|500]]

[visualization of RAFT](http://thesecretlivesofdata.com/raft/)

### PBFT

#### main idea
- Practical Byzantine fault tolerance (PBFT), is a protocol designed to provide consensus in the presence of Byzantine faults
- PBFT constitutes three subprotocols called *normal operation*, *view change*, and *checkpointing*

subprotocols
- normal operation: a mechanism executed when everything is running normally, and the system is <font color="#00b050">error-free</font>
- view change: runs when a <font color="#00b050">faulty leader node</font> is detected in the system
- checkingpoint: discard the old data from the system

#### nodes in PBFT
3 roles (modules):
1. replicas: participants
2. leader: or primary node, handles the <font color="#00b050">communication</font> with the client
3. backup: rest of the nodes except the leader

minimum number required: $n=3f+1$, where $n$ is the number of nodes and $f$ is the number of <font color="#00b050">faculty nodes</font>

#### phases in PBFT
3 phases
- pre-prepare
- prepare
- commit

##### pre-prepare
process (if not specified, subject is <font color="#00b050">leader node</font>)
1. accepts <font color="#00b050">request</font> from client
2. <font color="#00b050">assign</font> it to next <font color="#00b050">sequence number</font>. This sequence number is the order in which the request is going to be executed
3. <font color="#00b050">broadcast</font> this information as the pre-prepare message to all backup replicas

##### prepare
1. accepts the pre-prepare message only if the replica has not accepted any pre-prepare messages for the same view or sequence number before
2. sends the prepare message to all replicas

##### commit
1. replica waits for $2f + 1$ prepare messages with the same view, sequence, and request
2. sends a <font color="#00b050">commit message</font> to all replicas
3. waits until a $2f + 1$ valid commit message <font color="#00b050">arrives</font> and is <font color="#00b050">accepted</font>
4. <font color="#00b050">executes</font> the received request
5. sends a reply containing the execution <font color="#00b050">result</font> to the client

![[IS notes-20231218-6.png|650]]


## Lecture 17-18 Application of Blockchain

### cognitive radio (CR) network

#### background
- communication system: can be wireless and wire-based with different data rates
- wireless communication: required radio spectrum, which can be classified as 1) licensed spectrum 2) unlicensed spectrum
	- licensed spectrum: managed by governments and telecom operators needs to buy it then provide to customers
	- unlicensed spectrum: used free of charge by anyone at any time, also called: Industrial, Scientific, and Medical (ISM) band
- why CR: wireless radio spectrum is <font color="#00b050">underutilized</font>, and lot of licensed radio spectrum is not being utilized. The primary reason for CR is the <font color="#00b050">static allocation</font> of the spectrum by the regulatory bodies. To efficiently utilize wireless radio spectrum, we can use wireless radio spectrum dynamically, new paradigm introduced: Dynamic Spectrum Access (DSA), which is used by CR.

#### basic of CR

nodes in CR: 2 types co-exist
- primary radio (PR) nodes: <font color="#00b050">licensed</font> users and can only use the licensed spectrum
- secondary users (SU): can only use the licensed spectrum when it is not being utilized by the primary users and do not cause harmful interference to the PR nodes, required to leave the frequency band when a primary radio node arrives over it

CR network vs. primary network

![[IS notes-20231218-7.png|600]]

ad hoc CRN is formed in the presence of primary radio network in which CR nodes communicate with each other using different channels owned by the primary network when these channels are unoccupied by the primary radio nodes![[IS notes-20231218-8.png|550]]

*collision-free communication* (CFC)
- desirable in networks
- role of medium access <font color="#00b050">protocols</font> is to allow devices to access the medium (resource) without making a collision with other devices

different medium access protocols

![[IS notes-20231218-9.png|575]]

why need collision-free communication
- if not: packets will be lost, re-transmission will be required and thus result in energy and time consumption

Dynamic Spectrum Sharing (DSS) in CR
- enable use of LTE and 5G <font color="#00b050">simultaneously</font> in the same frequency band (different radios coexistence in the same carrier using spectrum sharing)
- helps in determining the <font color="#00b050">demand</font> for different radios in real-time
- how: available bandwidth of the network is divided into independent parts and dynamically assigns respective mobile communications standard it can be ideally used for available frequencies

Issues of DSS in CR
- *self-aware*: should be able to know what's going on inside, then according to it to determine actions to achieve goals
- *self-configuration*: should be able to <font color="#00b050">adapt</font> immediately with least human intervention to configure
- *self-healing*: network state can be <font color="#00b050">evaluated</font> and <font color="#00b050">corrective actions</font> should be initialized without interrupting system operation. (resilient to impact of failing components)
- *self-optimizing*: ability of the network environment to efficiently <font color="#00b050">maximize resource allocation</font> and <font color="#00b050">utilization</font> to achieve goals with least human intervention
- *self-protecting*: ability of <font color="#00b050">detecting</font> hostile or intrusive behavior and taking autonomous actions to make itself less vulnerable

### blockchain enabled CR

how blockchain help
- blockchain provides <font color="#00b050">verification</font> and <font color="#00b050">validation</font> schemes to ensure the security
- <font color="#00b050">decentralized</font> validation algorithm of blockchain enables a medium access protocol of CR to be <font color="#00b050">more accessible</font>, and the implementation will be easier since there is no need for a central-authority node
- <font color="#00b050">lacking a centralized node</font> for validating and monitoring spectrum access makes overall system more <font color="#00b050">robust</font> against <font color="#00b050">single-point failure</font>

steps carried out for collision-free communication:
1. each group reaches local consensus to allocate resources
2. broadcast information to all CR nodes
3. CR nodes will not use these resources
4. results in collision avoidance in channel hopping sequence-based CR network

benefits of using blockchain in CR network
1. lack of central entity
	- <font color="#00b050">remove reliance</font> of buying and selling spectrum without going to the central entity or spectrum regulator
	- <font color="#00b050">enhance spectrum assigning process</font> by making the buying and selling more faster than getting permission from a centralized regulator
2. immutability 
	- keep spectrum management-related records safe and secure
	- records cannot be tampered
3. availability
	- make dynamic spectrum management distributed ledger more available, and attackers are difficult to modify
	- no need to contact regional/national spectrum regulator every time when evaluating white spaces and determining spectrum opportunities
4. DoS resilient
	- denial of service attack resilient, compromise to a single node or few nodes will not hinder the activities of system
5. non-repudiation
	- more transparent and auditable
6. smart contract integration
	- bring new business models, rule-based spectrum management and assigning policies

Issues of Blockchain-enabled CR
- high computational overhead
- ownership of ledger
- capacity
- storage requirement of nodes