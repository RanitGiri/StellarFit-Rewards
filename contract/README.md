# Soroban Project
# StellarFit Rewards 🏃‍♂️🔗

A Web3 fitness incentive platform built on the Stellar network using Soroban smart contracts. 

## 📖 Project Description

Staying consistent with fitness goals is difficult. StellarFit Rewards bridges the gap between physical health and decentralized finance by gamifying daily movement. By logging physical activity (like daily steps) on-chain, users build up an immutable record of their fitness journey and unlock tangible, blockchain-based rewards for hitting their milestones. 

This project serves as the smart contract backbone for a fitness dApp, ensuring that user activity data is securely managed and rewards are distributed in a trustless environment.

## 🚀 What it does

StellarFit Rewards acts as a decentralized point ledger for physical activity. 

1. **Log:** Users (or a trusted oracle connected to a pedometer/fitness API) submit their daily step counts to the Soroban smart contract.
2. **Accumulate:** The contract securely updates and stores the user's total step balance in persistent on-chain storage. 
3. **Earn:** Once a user accumulates a target milestone (e.g., 10,000 steps), they can trigger the `claim_reward` function. The contract automatically deducts the required steps and authorizes the release of a reward (which can be wired to mint an actual Stellar token or NFT).

## ✨ Features

- **On-Chain Step Tracking:** Securely stores step balances mapped directly to user wallet addresses.
- **Cryptographic Authorization:** Utilizes Soroban's native `require_auth()` to ensure that only the wallet owner can log steps or trigger a reward claim, preventing malicious manipulation of accounts.
- **Automated Milestone Verification:** Smart contract logic handles the verification of milestones (10k steps) and subsequent balance deductions without the need for a centralized server.
- **Extensible Reward System:** Designed to be easily integrated with the Soroban Token Interface (`token::Client`) to mint standard Stellar assets as a reward in future iterations.

## 🛠️ Getting Started (Development)

To build and test this contract locally, ensure you have the Rust toolchain and Soroban CLI installed.

```bash
# Build the contract
soroban contract build

# Run tests (if configured)
cargo test
## Project Structure

This repository uses the recommended structure for a Soroban project:

```text
.
├── contracts
│   └── hello_world
│       ├── src
│       │   ├── lib.rs
│       │   └── test.rs
│       └── Cargo.toml
├── Cargo.toml
└── README.md
```

- New Soroban contracts can be put in `contracts`, each in their own directory. There is already a `hello_world` contract in there to get you started.
- If you initialized this project with any other example contracts via `--with-example`, those contracts will be in the `contracts` directory as well.
- Contracts should have their own `Cargo.toml` files that rely on the top-level `Cargo.toml` workspace for their dependencies.
- Frontend libraries can be added to the top-level directory as well. If you initialized this project with a frontend template via `--frontend-template` you will have those files already included.
