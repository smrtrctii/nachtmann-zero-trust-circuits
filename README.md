# N-1 Protocol // Zero-Trust Cryptographic Verification

This repository publishes the mathematical specifications and Zero-Knowledge Succinct Non-Interactive Arguments of Knowledge (zk-SNARK) circuits utilized by the N-1 Protocol Engine to enforce data sovereignty and payload integrity.

## Cryptographic Commitments

1. **Zero-Knowledge Payload Proofs (`payload_integrity.circom`)**
   - Proves byte weight and structural boundaries client-side via Groth16.
   - Prevents finite-field wrapping exploits by constraining payload sizes to strictly positive 32-bit integers ($< 4.29\text{ GB}$).
   - Generates Pedersen-style Poseidon commitments binding hardware entropy and compliance metrics without exposing raw data across the network boundary.

2. **Stateless Processing Guarantee**
   - Workloads operate strictly in ephemeral memory buffers.
   - Raw source text is dereferenced upon manifest generation.
   - Public notarization is anchored to the Polygon network for immutable event verification.

## Verification

The circuit parameters in this repository correspond directly to the client-side WebAssembly verifier deployed in the N-1 Engine runtime. Counterparties can verify transaction proofs using SnarkJS against the published verification key.
