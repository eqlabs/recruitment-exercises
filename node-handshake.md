# P2P node handshake

_Spec v3 (2023-03-30)_

Pick a publicly available P2P node (e.g. a blockchain one) implementation - which itself doesn't need to be written in Rust - and write a [network handshake](https://en.wikipedia.org/wiki/Handshaking) for it in Rust, and instructions on how to test it.

## Requirements

- Both the target node and the handshake code should compile at least on Linux.
- The solution has to perform a full **protocol-level** (post-TCP/etc.) handshake with the target node.
- The provided **instructions** should include information on how to verify that the handshake has concluded.
- The solution can not depend on the code of the target node (but it can share some of its dependencies).
- The submitted code can not reuse entire preexisting handshake implementations like `libp2p_noise/XX`.

### Non-requirements

- A lot of parameters can potentially be exchanged during the handshake, but only the mandatory ones need to be included.
- The solution can ignore any post-handshake traffic from the target node, and it doesn't have to keep the connection alive.

## Evaluation

- **Quality**: the solution should be idiomatic and adhere to Rust coding conventions.
- **Performance**: the solution should be as fast as the handshake protocol allows, and it shouldn't block resources.
- **Security**: the network is an inherently untrusted environment, and it should be taken into account.
- **Minimalism**: any number of dependencies can be used, but they should be tailored to the task.
- **Versatility**: the more broadly applicable the solution is (bi-directional, unfixed values, etc.), the better.
- **Uniqueness**: bonus points for non-Bitcoin implementations.
