# 🛡️ Secure Smart Tender Management System

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Django](https://img.shields.io/badge/Framework-Django-092E20)
![Blockchain](https://img.shields.io/badge/Blockchain-Ethereum-3C3C3D)
![Security](https://img.shields.io/badge/Security-AES%20Encryption-red)

## 📖 Overview

The **Secure Smart Tender Management System** is a Hybrid Decentralized Application (DApp) that automates the government tendering process. Unlike standard DApps, this project prioritizes **Data Privacy** by implementing off-chain AES encryption before data is stored on-chain.

It solves the "open ledger" problem where sensitive bid data is visible to competitors. In this system, bid details remain confidential and tamper-proof until the tender is closed and the winner is declared.

## 🏗️ Architecture

The system uses a **Hybrid Architecture**:
1.  **Frontend/Backend:** Django (Python) handles user authentication, views, and data processing.
2.  **Security Layer:** Custom Python implementation (`pyaes`) encrypts sensitive data.
3.  **Blockchain Layer:** Solidity Smart Contracts store the *encrypted* data, ensuring immutability without sacrificing privacy.
4.  **Connector:** `Web3.py` acts as the bridge between Django and the Ethereum network.

## ✨ Key Features

* **AES-256 Data Encryption:** All tender and bid data is encrypted using `pyaes` (CTR Mode) before reaching the blockchain.
* **Tamper-Proof Bidding:** Once a bid is placed, it is cryptographically signed and stored on Ethereum; it cannot be altered by admins or hackers.
* **Role-Based Access:**
    * **Admin/Government:** Create tenders, decrypt bids after deadline, declare winners.
    * **Bidder:** View active tenders, place encrypted bids.
* **Automated Evaluation:** Python logic parses decrypted blockchain data to automatically calculate the lowest qualifying bid.
* **Transparency:** Every transaction hash is visible, ensuring the process is auditable.

## 🛠️ Technology Stack

* **Backend Framework:** Django (Python)
* **Blockchain Interface:** Web3.py
* **Smart Contract:** Solidity (Deployed on local Ganache/Anvil node)
* **Encryption:** `pyaes` (AES-CTR mode), `pbkdf2` (Key derivation)
* **Database:** SQLite (for user session management) + Ethereum Blockchain (for record storage)

## 🚀 Getting Started

### Prerequisites
* Python 3.x
* [Ganache](https://trufflesuite.com/ganache/) (or Foundry Anvil) running on `http://127.0.0.1:7545`
* A deployed instance of `TenderContract.json`

### Installation

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/](https://github.com/)[YOUR-USERNAME]/smart-tender-system.git
    cd smart-tender-system
    ```

2.  **Install Python Dependencies**
    ```bash
    pip install django web3 pyaes pbkdf2 numpy
    ```

3.  **Configure Blockchain Connection**
    * Open `views.py`.
    * Update `deployed_contract_address` with your actual contract address from Ganache/Anvil.
    * Ensure the `blockchain_address` matches your local node (default: `http://127.0.0.1:7545`).

4.  **Run the Server**
    ```bash
    python manage.py runserver
    ```

5.  **Access the DApp**
    Open your browser and navigate to `http://127.0.0.1:8000`.

## 🧩 Code Structure

* `views.py`: Core logic. Handles encryption (`encrypt/decrypt`), connects to Web3, and manages Django views.
* `TenderContract.json`: The ABI of the compiled Solidity contract.
* `templates/`: HTML frontend files (`CreateTender.html`, `BidderScreen.html`).

## 🔐 Security Deep Dive

To ensure bid confidentiality, the system uses the following flow:
1.  **Input:** User enters bid amount.
2.  **Key Generation:** A session-based key is generated using `PBKDF2`.
3.  **Encryption:** `pyaes.AESModeOfOperationCTR` encrypts the data string.
4.  **Encoding:** The ciphertext is Base64 encoded.
5.  **Storage:** The Base64 string is sent to the Smart Contract via `contract.functions.createTender()`.

## 🤝 Contributing

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/NewFeature`)
3.  Commit your Changes (`git commit -m 'Add NewFeature'`)
4.  Push to the Branch (`git push origin feature/NewFeature`)
5.  Open a Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 👤 Author

**Mirwaise Khan**
* **Role:** Blockchain Developer & Security Researcher
* **Institute:** Rajiv Gandhi Institute of Technology, Bangalore
* **Interests:** Web3, Smart Contracts, Cryptography

---
*Built with ❤️ using Python & Ethereum.*
