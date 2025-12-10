# 📜 Smart Tender Management System

![License](https://img.shields.io/badge/License-MIT-green.svg)
![Solidity](https://img.shields.io/badge/Solidity-%5E0.8.19-363636)
![Framework](https://img.shields.io/badge/Framework-Foundry-bf4b04)

## 📖 Overview

The **Smart Tender Management System** is a decentralized application (DApp) designed to bring transparency, security, and efficiency to the procurement and tendering process.

Traditional tendering systems often suffer from centralized manipulation, lack of transparency, and data tampering. This project leverages **Blockchain technology** to ensure that the bidding process is immutable and auditable. Government bodies or organizations can float tenders, and contractors can bid securely, with the contract logic ensuring the fairest outcome.

## ✨ Key Features

* **Immutable Tender Creation:** Only authorized entities (e.g., Government/Admin) can create new tenders.
* **Transparent Bidding:** Contractors can submit bids that are permanently recorded on the blockchain.
* **Tamper-Proof Logic:** Once a bid is placed, it cannot be altered or deleted.
* **Automated Selection:** Smart contracts automatically evaluate bids based on pre-defined criteria (e.g., lowest bid, reputation score) to declare a winner.
* **Time-Locked mechanism:** Bidding is only allowed within a specific timeframe (Start Time to End Time).
* **Security:** Prevents re-entrancy attacks and ensures only valid bids are accepted.

## 🛠️ Technology Stack

* **Smart Contracts:** Solidity
* **Development Framework:** Foundry (Forge, Cast, Anvil)
* **Frontend (Optional):** [React.js / Next.js / HTML & JS]
* **Blockchain Interaction:** [Ethers.js / Viem / Wagmi]
* **Testnet:** [Sepolia / Polygon Mumbai / Localhost]

## 🚀 Getting Started

Follow these steps to set up the project locally.

### Prerequisites

* [Git](https://git-scm.com/)
* [Foundry](https://getfoundry.sh/) (Ensure `forge` is installed)
* [Node.js](https://nodejs.org/) (If using a frontend)

### Installation

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/](https://github.com/)[YOUR-USERNAME]/smart-tender-system.git
    cd smart-tender-system
    ```

2.  **Install Dependencies**
    ```bash
    forge install
    ```

3.  **Compile Contracts**
    ```bash
    forge build
    ```

4.  **Run Tests**
    To ensure the smart contract logic works as expected:
    ```bash
    forge test
    ```
    
    *To view gas reports:*
    ```bash
    forge test --gas-report
    ```

## 📜 Usage Logic

1.  **Deploy:** The admin deploys the `TenderManager.sol` contract.
2.  **Create Tender:** Admin calls `createTender(string memory description, uint256 deadline)` .
3.  **Bid:** Contractors call `placeBid(uint256 tenderId)` along with the required ETH/Wei.
4.  **Close Tender:** After the deadline passes, `closeTender(uint256 tenderId)` is called to select the winner.

## 📂 Project Structure

```text
├── src/
│   ├── TenderManager.sol    # Main contract logic
│   └── Tender.sol           # Individual tender logic (if applicable)
├── test/
│   ├── Tender.t.sol         # Unit tests using Foundry
├── script/
│   └── Deploy.s.sol         # Deployment scripts
├── lib/                     # Dependencies (OpenZeppelin, etc.)
└── foundry.toml             # Configuration file
