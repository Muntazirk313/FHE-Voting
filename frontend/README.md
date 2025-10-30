# 🎨 FHE Voting DApp - Frontend Application

> A modern React-based user interface for decentralized voting with Full Homomorphic Encryption

[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat&logo=react)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.x-38B2AC?style=flat&logo=tailwind-css)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-BSD--3--Clause-orange?style=flat)](LICENSE)

---

## 📖 Overview

This is the frontend application for the FHE Voting DApp, featuring complete integration with the FHEVoting smart contract. Built with React and TypeScript, it provides a seamless, privacy-focused voting experience powered by Full Homomorphic Encryption.

---

## ⚡ Quick Start

### Installation

```bash
# Install all dependencies
npm install
```

### Configuration

Update your deployed contract address in `src/config/contracts.ts`:

```typescript
export const CONTRACTS = {
  FHE_VOTING: "0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d"
};
```

### Development Server

```bash
# Start the application
npm start
```

Application will be available at **http://localhost:3000** 🚀

---

## 🏗️ Application Architecture

### Core Services

#### Contract Service (`src/services/contractService.ts`)
Manages all blockchain interactions with the FHEVoting smart contract.

**Key Methods:**
- `getAllProposals()` → Fetch all voting proposals
- `createProposal()` → Create new proposal on-chain
- `castVote()` → Submit encrypted vote
- `hasVoted()` → Check if user has voted on a proposal
- `getProposalResults()` → Retrieve voting results

#### Wallet Context (`src/contexts/WalletContext.tsx`)
Handles wallet connectivity and network management.

**Features:**
- Automatic Sepolia network switching
- Contract service initialization
- Network state monitoring
- Account change detection
- Connection status management

#### FHE Context (`src/contexts/FHEContext.tsx`)
Manages Full Homomorphic Encryption operations.

**Capabilities:**
- Vote encryption before submission
- Cryptographic proof generation
- Mock FHE for development environment
- Secure key management

---

## 📄 Page Components

### 🏠 Home Page
- Welcome interface and DApp introduction
- Quick access to core features
- Wallet connection prompt
- Feature highlights and benefits

### 📋 Proposals List
- Real-time proposal loading from blockchain
- Live status indicators (Active/Ended)
- User voting status display
- Manual refresh functionality
- Proposal filtering and search

### ➕ Create Proposal
- Form validation and input sanitization
- Date/time pickers for voting window
- Blockchain transaction submission
- Transaction status tracking
- Success/error notifications

### 🗳️ Vote Page
- Detailed proposal information display
- Encrypted vote submission (Yes/No)
- FHE encryption status indicator
- Voting confirmation modal
- Double-vote prevention

### 📊 Voting History
- Personal voting record display
- Proposal status filtering
- Privacy protection indicators
- Vote timestamp tracking
- Historical data pagination

---

## 🛠️ Development Features

### Mock FHE Implementation

For local development and testing, FHE operations use simulated implementations:

```typescript
// Mock encryption during development
const mockEncrypt = (value: boolean) => {
  return {
    encrypted: btoa(value.toString()),
    proof: "mock_proof_" + Date.now()
  };
};
```

**Benefits:**
- Fast local testing without real FHE setup
- Simplified debugging process
- Instant feedback during development

### Error Handling System

Comprehensive error management across the application:

| Error Type | Handling Strategy |
|------------|------------------|
| Network Errors | Auto-retry with user notification |
| Contract Call Failures | Detailed error messages with recovery steps |
| User Transaction Rejection | Graceful cancellation with guidance |
| Insufficient Balance | Balance check with faucet link |

---

## 🚀 Production Deployment

### Build for Production

```bash
# Create optimized production build
npm run build
```

Output will be in the `build/` directory.

### Deployment Options

**Recommended Platforms:**
- [Vercel](https://vercel.com) - Zero configuration deployment
- [Netlify](https://netlify.com) - Continuous deployment from Git
- [AWS S3](https://aws.amazon.com/s3/) + CloudFront - Scalable hosting
- [GitHub Pages](https://pages.github.com) - Free static hosting

### Environment Configuration

Create `.env.production` file:

```env
REACT_APP_CONTRACT_ADDRESS=0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d
REACT_APP_NETWORK_ID=11155111
REACT_APP_ENABLE_MOCK_FHE=false
```

---

## 🔒 Security Considerations

### Development Environment
- ✅ Use test wallets only
- ✅ Never use real funds on testnet
- ✅ FHE operations are mocked
- ✅ Enable verbose logging for debugging

### Production Environment
- ✅ Integrate real FHEVM library
- ✅ Complete security audit
- ✅ Implement rate limiting
- ✅ Enable HTTPS only
- ✅ Wallet security best practices
- ✅ Input sanitization and validation

---

## 🐛 Troubleshooting Guide

### Common Issues

<details>
<summary><b>Contract Service Not Initialized</b></summary>

**Symptoms:** Error message "Contract service not initialized"

**Solutions:**
1. Verify wallet is connected
2. Check network is set to Sepolia
3. Refresh the page and reconnect wallet
4. Clear browser cache
</details>

<details>
<summary><b>Proposals Not Loading</b></summary>

**Symptoms:** Empty proposal list or loading spinner stuck

**Solutions:**
1. Verify contract address in `contracts.ts`
2. Check network connectivity
3. Inspect browser console for errors
4. Ensure contract is deployed on Sepolia
</details>

<details>
<summary><b>Transaction Failures</b></summary>

**Symptoms:** "Transaction failed" error

**Solutions:**
1. Check Sepolia ETH balance (get from faucet)
2. Confirm correct network selection
3. Review error message details
4. Try increasing gas limit
</details>

### Debug Mode

Enable detailed logging in browser console:

```javascript
// In browser console
localStorage.setItem('debug', 'true');
```

**Available Logs:**
- Contract service initialization status
- Transaction details and receipts
- FHE encryption operations
- Network state changes

---

## 📦 Technology Stack

| Category | Technology | Purpose |
|----------|-----------|---------|
| **Framework** | React 18 | UI component library |
| **Language** | TypeScript | Type-safe development |
| **Styling** | Tailwind CSS | Utility-first CSS framework |
| **Blockchain** | Ethers.js v6 | Ethereum interaction |
| **Encryption** | FHEVM | Homomorphic encryption |
| **Routing** | React Router v6 | Client-side navigation |
| **Icons** | Lucide React | Modern icon library |

---

## 📁 Project Structure

```plaintext
frontend/
├── public/                    # Static assets
│   ├── index.html            # HTML template
│   └── favicon.ico           # App icon
│
├── src/
│   ├── components/           # Reusable components
│   │   ├── Header.tsx       # Navigation header
│   │   ├── ProposalCard.tsx # Proposal display
│   │   └── WalletButton.tsx # Wallet connection
│   │
│   ├── contexts/             # React contexts
│   │   ├── WalletContext.tsx # Wallet management
│   │   └── FHEContext.tsx    # FHE operations
│   │
│   ├── pages/                # Page components
│   │   ├── Home.tsx         # Landing page
│   │   ├── Proposals.tsx    # Proposal list
│   │   ├── CreateProposal.tsx
│   │   ├── Vote.tsx         # Voting interface
│   │   └── VotingHistory.tsx
│   │
│   ├── services/             # Business logic
│   │   └── contractService.ts # Contract interactions
│   │
│   ├── config/               # Configuration
│   │   └── contracts.ts      # Contract addresses
│   │
│   ├── utils/                # Helper functions
│   │   ├── encryption.ts     # FHE utilities
│   │   └── validators.ts     # Input validation
│   │
│   ├── App.tsx               # Main component
│   └── index.tsx             # Entry point
│
├── package.json              # Dependencies
├── tsconfig.json             # TypeScript config
└── tailwind.config.js        # Tailwind config
```

---

## 🤝 Contributing

We welcome contributions! Here's how to get started:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** your changes: `git commit -m 'Add amazing feature'`
4. **Push** to branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

**Contribution Guidelines:**
- Follow existing code style and conventions
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting

---

## 📜 Scripts Reference

| Command | Description |
|---------|-------------|
| `npm start` | Start development server |
| `npm run build` | Build for production |
| `npm test` | Run test suite |
| `npm run lint` | Check code style |
| `npm run format` | Format code with Prettier |

---

## 📄 License

This project is licensed under the **BSD-3-Clause-Clear License**.

See [LICENSE](../LICENSE) file for details.

---

## 🔗 Related Resources

- [Main Repository](https://github.com/Muntazirk313/FHE-Voting)
- [Smart Contract Documentation](../contracts/README.md)
- [Zama FHEVM Docs](https://docs.zama.ai/)
- [React Documentation](https://react.dev/)

---

<div align="center">

**Built with ⚛️ React and 🔐 FHE technology**

*Empowering private, secure voting on the blockchain*

</div>

**注意**: 这是一个演示项目。生产使用前请进行安全审计。
