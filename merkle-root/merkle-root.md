# Merkle Tree Root

Spec v1 (2021-12-17)

The task is to compute the merkle tree root corresponding to a set of transactions as fast and efficiently as possible.

## Requirements

- The program must output the merkle root.
- Sha-256 must be used to perform the hashing at each step, you may use a library for this.
- The code must be tested and documented.

## Input

The supplied transactions are in their hashed form and are ordered. The input file has one hex-encoded transaction per line.
