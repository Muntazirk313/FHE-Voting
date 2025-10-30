<div align="center">

# 🗳️ FHE Voting

### *Decentralized Confidential Voting with Full Homomorphic Encryption*

[![Live Demo](https://img.shields.io/badge/Demo-Live-success?style=for-the-badge)](https://fhe-voting.vercel.app/)
[![Contract](https://img.shields.io/badge/Contract-Deployed-blue?style=for-the-badge)](https://sepolia.etherscan.io/address/0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

**Experience true privacy in blockchain voting using cutting-edge FHE technology**

[View Demo](https://fhe-voting.vercel.app/) •  [Report Bug](https://github.com/Muntazirk313/FHE-Voting/issues)

</div>

---

## 💡 What is FHE Voting?

This DApp leverages Solidity smart contracts and Full Homomorphic Encryption (FHE) through the FHEVM framework to enable secure, privacy-preserving voting. The React-based frontend provides a seamless and transparent user experience without compromising data security.

**Contract Address**: `0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d`

---

## ✨ Core Features

| Feature | Description |
|---------|-------------|
| 🔒 **End-to-End Encryption** | Votes remain encrypted using FHE technology from submission to tallying |
| ⚡ **Real-time Updates** | Live tracking of active proposals and voting status |
| 🎯 **Proposal Management** | Create, track, and manage voting proposals with customizable parameters |
| ⏱️ **Time-Bound Voting** | Automated voting windows with precise start and end times |
| 👁️ **Transparent Results** | Verifiable outcomes while preserving individual vote privacy |
| 🦊 **MetaMask Integration** | Seamless wallet connectivity for Ethereum interactions |
| 🌍 **Multi-Network Support** | Compatible with Sepolia testnet and local development networks |

---

## 🏛️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend Layer (React)                   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │   Wallet     │  │  FHE Client  │  │   UI/UX      │     │
│  │ Integration  │  │  Management  │  │  Components  │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
└─────────────────────────────────────────────────────────────┘
                            ↕️
┌─────────────────────────────────────────────────────────────┐
│              Ethereum Blockchain (Sepolia)                   │
│  ┌────────────────────────────────────────────────────┐    │
│  │         FHEVoting Smart Contract                    │    │
│  │  ┌──────────┐  ┌──────────┐  ┌────────────────┐  │    │
│  │  │ Proposal │  │ Encrypted │  │ Result         │  │    │
│  │  │ Manager  │  │ Voting    │  │ Publication    │  │    │
│  │  └──────────┘  └──────────┘  └────────────────┘  │    │
│  └────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────┘
                            ↕️
┌─────────────────────────────────────────────────────────────┐
│                  FHEVM Layer (Zama)                          │
│         Full Homomorphic Encryption Operations               │
└─────────────────────────────────────────────────────────────┘
```

---

## 📂 Repository Structure

```plaintext
FHE-Voting/
│
├── 📜 contracts/                    # Solidity smart contracts
│   └── FHEVoting.sol               # Core voting contract with FHE
│
├── 🚀 deploy/                       # Deployment configurations
│   └── FHEVoting.ts                # Contract deployment script
│
├── 🔐 fhevmTemp/                    # FHE temporary files & configs
│
├── 🎨 frontend/                     # React application
│   ├── public/                     # Static assets & HTML template
│   ├── src/
│   │   ├── components/             # Reusable React components
│   │   ├── config/                 # App configuration files
│   │   ├── contexts/               # React Context providers
│   │   ├── pages/                  # Page-level components
│   │   ├── utils/                  # Helper functions
│   │   └── App.tsx                 # Main application component
│   └── package.json                # Frontend dependencies
│
├── 📚 references/                   # Documentation & references
├── ⚙️ tasks/                        # Custom Hardhat tasks
├── 📝 types/                        # TypeScript type definitions
│
├── .env.example                # Environment variables template
├── hardhat.config.ts           # Hardhat configuration
├── tsconfig.json               # TypeScript configuration
├── package.json                # Root dependencies
|
├── LICENSE                     # MIT License
├── README.md                   # You are here!
```

---

## 🛠️ Technology Stack

<table>
<tr>
<td width="50%">

### Backend & Blockchain
- **Solidity** - Smart contract language
- **Hardhat** - Development framework
- **FHEVM** - Zama's FHE implementation
- **Ethers.js** - Ethereum interaction library
- **TypeScript** - Type-safe development

</td>
<td width="50%">

### Frontend & UI
- **React 18** - UI framework
- **TypeScript** - Static typing
- **Tailwind CSS** - Styling framework
- **React Router** - Navigation
- **Lucide React** - Icon library

</td>
</tr>
</table>

---

## 🚀 Getting Started

### 📋 System Requirements

Before you begin, ensure you have the following installed:

- Node.js v16 or higher
- npm v7+ or yarn v1.22+
- Git
- MetaMask browser extension
- Sepolia testnet ETH (get from faucet)

---

### 🔧 Installation Process

**Step 1: Clone Repository**
```bash
git clone https://github.com/Muntazirk313/FHE-Voting.git
cd FHE-Voting
```

**Step 2: Install Dependencies**
```bash
# Install backend dependencies
npm install

# Install frontend dependencies
cd frontend && npm install && cd ..
```

**Step 3: Configure Environment**

Set your variables in `.env.example` file:

```env
PRIVATE_KEY=your_wallet_private_key_here
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/<YOUR_INFURA_API_KEY>
ETHERSCAN_API_KEY=your_etherscan_api_key_here
```

**Step 4: Deploy Smart Contract**
```bash
# Deploy to Sepolia testnet
npx hardhat run deploy/FHEVoting.ts --network sepolia

# OR deploy locally for testing
npx hardhat node  # Terminal 1
npx hardhat run deploy/FHEVoting.ts --network localhost  # Terminal 2
```

**Step 5: Update Contract Address**

Edit `frontend/src/config/contracts.ts` with your deployed contract address:

```typescript
export const CONTRACTS = {
  FHE_VOTING: "0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d"
};
```

**Step 6: Launch Application**
```bash
cd frontend
npm start
```

Visit `http://localhost:3000` 🎉

---

## 📖 How to Use

### 🔗 Connecting Your Wallet
1. Open the application in your browser
2. Click "Connect Wallet" in the navigation bar
3. Approve MetaMask connection request
4. Ensure you're on Sepolia testnet

### ➕ Creating a Proposal
1. Navigate to "Create Proposal" page
2. Enter proposal title and detailed description
3. Set voting start time and end time
4. Submit transaction and wait for confirmation

### 🗳️ Casting Your Vote
1. Browse available proposals on home page
2. Click on a proposal to view details
3. Select "Yes" or "No" for your vote
4. Confirm the encrypted vote transaction
5. Your vote is now recorded on-chain (encrypted)

### 📊 Viewing Results
1. Wait for voting period to end
2. Results are automatically tallied using FHE
3. Final counts are revealed while preserving vote privacy
4. Check your voting history in your profile

---

## 🔐 Security & Privacy

### Encryption Technology
- **FHE Operations**: All votes encrypted using Full Homomorphic Encryption
- **On-Chain Privacy**: Encrypted data stored directly on blockchain
- **Zero-Knowledge**: Vote validity proven without revealing choice
- **Secure Computation**: Results computed on encrypted data

### Smart Contract Security
- ✓ Access control mechanisms
- ✓ Time-locked result publication
- ✓ Reentrancy protection
- ✓ Input validation and sanitization
- ✓ Emergency pause functionality

### Privacy Guarantees
- Individual votes remain permanently private
- Only aggregated results are published
- No correlation between voters and their choices
- Complete audit trail for transparency

---

## 🧪 Testing

### Run Smart Contract Tests
```bash
npx hardhat test
```

### Run Frontend Tests
```bash
cd frontend
npm test
```

### Integration Testing
```bash
npx hardhat run scripts/test-voting-flow.js --network localhost
```

### Coverage Report
```bash
npx hardhat coverage
```

---

## 🌐 Deployment

### Deploy to Sepolia Testnet
```bash
npx hardhat run deploy/FHEVoting.ts --network sepolia
```

### Deploy to Ethereum Mainnet
```bash
npx hardhat run deploy/FHEVoting.ts --network mainnet
```

### Verify Contract on Etherscan
```bash
npx hardhat verify --network sepolia 0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d
```

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

1. 🍴 Fork the repository
2. 🌿 Create a feature branch (`git checkout -b feature/amazing-feature`)
3. 💾 Commit your changes (`git commit -m 'Add amazing feature'`)
4. 📤 Push to the branch (`git push origin feature/amazing-feature`)
5. 🎯 Open a Pull Request

Please ensure your code follows our coding standards and includes appropriate tests.

---

## 👨‍💻 Author

**Muntazir Khan**

- 🐙 GitHub: [@Muntazirk313](https://github.com/Muntazirk313)
- 🐦 Twitter/X: [@bosonatom1](https://x.com/bosonatom1)
- 📁 Repository: [FHE-Voting](https://github.com/Muntazirk313/FHE-Voting)

---

## 🙌 Acknowledgments

Special thanks to the following projects and communities:

- **[Zama](https://www.zama.ai/)** - For pioneering FHEVM technology
- **[Hardhat](https://hardhat.org/)** - For robust development tools
- **[React](https://react.dev/)** - For the powerful UI framework
- **[Ethereum Foundation](https://ethereum.org/)** - For the blockchain platform

---

## 📚 Resources & Documentation

### Official Documentation
- 📖 [Zama FHEVM Docs](https://docs.zama.ai/) - Complete FHEVM documentation
- 🔨 [Hardhat Documentation](https://hardhat.org/docs) - Development environment guide
- ⚡ [Solidity Docs](https://docs.soliditylang.org/) - Smart contract language reference
- 🌐 [Ethers.js Documentation](https://docs.ethers.org/) - Ethereum library guide

### Community & Support
- 💬 [Zama Discord](https://discord.com/invite/fhe-org) - FHE community discussions
- 🐦 [Zama on X](https://x.com/zama_fhe) - Latest FHE updates and announcements
- 🐛 [Report Issues](https://github.com/Muntazirk313/FHE-Voting/issues) - Bug reports and feature requests

### Code Repositories
- 🗂️ [FHEVM GitHub](https://github.com/zama-ai/fhevm) - Source code and examples
- 📦 [FHEVM Solidity](https://github.com/zama-ai/fhevm-solidity) - Solidity library for FHE

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for complete details.

---

## 💬 Support & Contact

Need help or have questions?

- 📧 Open an [issue](https://github.com/Muntazirk313/FHE-Voting/issues) on GitHub
- 💭 Join the [Zama Discord](https://discord.com/invite/fhe-org) community
- 📖 Check the [documentation](#-resources--documentation) section above
- 🐦 Reach out on [Twitter/X](https://x.com/bosonatom1)

---

<div align="center">

### ⭐ Star this repository if you find it helpful!

**Built with privacy in mind using Full Homomorphic Encryption**

*Making blockchain voting truly confidential* 🔐

</div>
