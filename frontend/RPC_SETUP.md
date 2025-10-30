# 🌐 RPC Configuration Guide for FHE Voting DApp

> Essential guide to connecting your frontend with the Ethereum Sepolia network

---

## 🔍 Understanding RPC

**Remote Procedure Call (RPC)** serves as the communication gateway between your frontend application and the Ethereum blockchain network.

### Why Do We Need RPC?

Your browser-based application cannot directly communicate with blockchain nodes. RPC providers act as intermediaries that enable:

- 📖 Reading blockchain state and data
- 💸 Broadcasting transactions to the network
- 🤝 Interacting with deployed smart contracts
- 📊 Querying historical blockchain information

---

## 🛠️ Getting Your Infura RPC URL

**Why Infura?**
- Industry-standard reliability
- Generous free tier (100K requests/day)
- Simple setup process
- Excellent documentation

### Setup Instructions

**Step 1:** Navigate to [infura.io](https://infura.io/)

**Step 2:** Sign up for a free account

**Step 3:** Create a new project
- Click "Create New Project"
- Name it "FHE Voting" (or any name you prefer)
- Select "Web3 API" from the product options

**Step 4:** Copy your API key
- Open your project dashboard
- Find your API key in the project settings
- Copy the API key to your clipboard

**Your RPC URL Format:**
```
https://sepolia.infura.io/v3/<YOUR_API_KEY>
```

---

## ⚙️ Configuration Steps

### 🎯 Direct Configuration Method

**Step 1:** Navigate to configuration file
```bash
frontend/src/config/contracts.ts
```

**Step 2:** Locate the Sepolia network configuration

**Step 3:** Replace `YOUR_INFURA_API_KEY` with your actual API key

```typescript
export const NETWORKS = {
  SEPOLIA: {
    chainId: 11155111,
    name: "Sepolia Testnet",
    rpcUrls: [
      "https://sepolia.infura.io/v3/<PASTE_YOUR_API_KEY_HERE>",
      "https://rpc.sepolia.org",  // Fallback option
    ],
    defaultRpcUrl: "https://sepolia.infura.io/v3/<PASTE_YOUR_API_KEY_HERE>",
    blockExplorer: "https://sepolia.etherscan.io",
    nativeCurrency: {
      name: "Sepolia ETH",
      symbol: "SepoliaETH",
      decimals: 18
    }
  }
};

export const CONTRACTS = {
  FHE_VOTING: "0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d"
};
```

**Step 4:** Save the file

**Step 5:** Restart your development server
```bash
npm start
```

---

## ✅ Verification Steps

### Pre-flight Checklist

Before testing, ensure:

- [ ] API key is correctly copied (no extra spaces)
- [ ] File is saved after making changes
- [ ] Development server is restarted
- [ ] MetaMask is installed and connected to Sepolia
- [ ] You have Sepolia ETH in your wallet ([Get from faucet](https://sepoliafaucet.com/))

### Testing Your RPC Connection

**Test 1: Proposal Loading**
1. Navigate to Proposals page
2. Watch for loading spinner
3. Proposals should appear within 3-5 seconds
4. If proposals load successfully, your RPC is working! ✅

**Test 2: Create a Proposal**
1. Try creating a test proposal
2. Approve MetaMask transaction
3. Wait for confirmation
4. Verify on [Sepolia Etherscan](https://sepolia.etherscan.io)

---

## 🔒 Security Best Practices

### Important Reminders

| ✅ DO | ❌ DON'T |
|-------|----------|
| Keep your API key private | Share your API key publicly |
| Use separate keys for different projects | Commit API keys to GitHub |
| Monitor your usage on Infura dashboard | Exceed your rate limits |
| Rotate keys periodically | Use the same key everywhere |

---

## 🚨 Troubleshooting

### Issue: "Failed to fetch" or "Network Error"

**Possible Causes:**
- Invalid or incorrectly copied API key
- Rate limit exceeded (100K requests/day on free tier)
- Network connectivity issues

**Solutions:**
1. Double-check your API key is correct (no extra spaces or characters)
2. Verify on Infura dashboard that your project is active
3. Check you haven't exceeded the daily request limit
4. Try the fallback RPC: `https://rpc.sepolia.org`

---

### Issue: Proposals Not Loading

**Possible Causes:**
- Wrong network selected in MetaMask
- Contract address mismatch
- RPC connection timeout

**Solutions:**
1. Confirm MetaMask is on Sepolia (Chain ID: 11155111)
2. Verify contract address is: `0x4a5caBC0d048F7af974B1C99DBaF3A20283ECA0d`
3. Clear browser cache and reload
4. Check browser console (F12) for detailed errors

---

### Issue: Transactions Failing

**Possible Causes:**
- Insufficient Sepolia ETH for gas
- MetaMask not connected properly
- RPC provider temporarily unavailable

**Solutions:**
1. Get Sepolia ETH from [faucet](https://sepoliafaucet.com/)
2. Disconnect and reconnect MetaMask
3. Wait a moment and try again
4. Check Infura status page for any outages

---

## 📊 Infura Rate Limits

**Free Tier:**
- **Daily Requests:** 100,000 requests per day
- **Requests Per Second:** 10 req/sec
- **Cost:** Free forever

**When You Need More:**
- Upgrade to Developer plan for 25M requests/month
- Check [Infura Pricing](https://www.infura.io/pricing) for details

---

## 🎓 FAQ

<details>
<summary><strong>Q: Can I use mainnet RPC for testing?</strong></summary>

**A:** No! This is a test application. Always use Sepolia testnet to avoid spending real ETH on gas fees and to prevent deploying test contracts to mainnet.
</details>

<details>
<summary><strong>Q: Why do I need Infura?</strong></summary>

**A:** Your browser cannot directly connect to blockchain nodes. Infura provides infrastructure that allows your dApp to communicate with Ethereum securely and reliably.
</details>

<details>
<summary><strong>Q: Is Infura free tier enough?</strong></summary>

**A:** Yes! For development and testing, the free tier (100K requests/day) is more than sufficient. You'll only need to upgrade if you're running a production dApp with heavy traffic.
</details>

<details>
<summary><strong>Q: How do I know if my RPC is working?</strong></summary>

**A:** Check these indicators:
- ✅ Proposals load successfully on the frontend
- ✅ MetaMask shows correct network and balance
- ✅ Transactions are confirmed within 30 seconds
- ✅ No network errors in browser console
</details>

<details>
<summary><strong>Q: What if I hit the rate limit?</strong></summary>

**A:** Rate limits reset daily. If you hit the limit:
- Wait for the daily reset
- Optimize your requests (cache data when possible)
- Consider upgrading to a paid plan
- Use the fallback public RPC temporarily
</details>

---

## 📞 Support Resources

**Need More Help?**

- 📚 [Infura Documentation](https://docs.infura.io/)
- 💬 [Ethereum Stack Exchange](https://ethereum.stackexchange.com/)
- 🐛 [Project Issues](https://github.com/Muntazirk313/FHE-Voting/issues)
- 📧 [Infura Support](https://support.infura.io/)

---

<div align="center">

### 🎉 Configuration Complete!

You're now ready to start using the FHE Voting DApp with Infura RPC connectivity.

**Next Steps:** [Run the Application](../README.md#-getting-started) | [Deploy Contract](../contracts/README.md)

---

**Built with 🔐 FHE technology for private voting**

</div>
