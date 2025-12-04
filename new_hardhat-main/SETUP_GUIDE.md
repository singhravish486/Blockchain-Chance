# 🎮 Chance - Blockchain Gaming Platform Setup Guide

## 📋 Prerequisites

Before starting, ensure you have:

- ✅ **Node.js v18+** installed ([Download](https://nodejs.org/))
- ✅ **MetaMask** browser extension installed
- ✅ **Git** installed
- ✅ **Sepolia ETH** (optional, for testnet deployment - get from [Sepolia Faucet](https://sepoliafaucet.com/))

---

## 🚀 Quick Start (Local Development)

### 1️⃣ Install Dependencies

```bash
cd d:\Chance\Chance\new_hardhat-main
npm install
```

### 2️⃣ Compile Smart Contracts

```bash
npx hardhat compile
```

### 3️⃣ Start Local Blockchain (Terminal 1)

```bash
npx hardhat node
```

**Keep this terminal running!** It will display 20 test accounts with private keys.

### 4️⃣ Deploy Contracts to Local Network (Terminal 2)

Open a **new terminal** and run:

```bash
npx hardhat run scripts/deploy.js --network localhost
```

This will:
- Deploy the `Mines.sol` contract
- Save the contract address to `src/contract_data/Mines-address.json`
- Save the ABI to `src/contract_data/Mines.json`

### 5️⃣ Configure MetaMask for Local Network

1. Open MetaMask
2. Click on the network dropdown (top)
3. Click "Add Network" → "Add a network manually"
4. Enter the following details:
   - **Network Name**: Hardhat Local
   - **RPC URL**: `http://127.0.0.1:8545`
   - **Chain ID**: `1337`
   - **Currency Symbol**: `ETH`
5. Click "Save"

### 6️⃣ Import Test Account to MetaMask

1. Copy one of the private keys from the Hardhat node terminal
2. In MetaMask: Click account icon → "Import Account"
3. Paste the private key
4. You should now have 10000 ETH for testing!

### 7️⃣ Start the Frontend

```bash
npm run dev
```

### 8️⃣ Open the Application

Navigate to: **http://localhost:3000**

---

## 🌐 Deploying to Sepolia Testnet

### 1️⃣ Get Sepolia ETH

Get free Sepolia ETH from:
- [Alchemy Sepolia Faucet](https://sepoliafaucet.com/)
- [Infura Sepolia Faucet](https://www.infura.io/faucet/sepolia)

### 2️⃣ Export Your MetaMask Private Key

⚠️ **NEVER share your private key or commit it to GitHub!**

1. Open MetaMask
2. Click the 3 dots → Account Details → Export Private Key
3. Enter your password
4. Copy the private key

### 3️⃣ Create `.env` File

Create a `.env` file in the project root:

```bash
PRIVATE_KEY=your_metamask_private_key_here
```

### 4️⃣ Deploy to Sepolia

```bash
npx hardhat run scripts/deploy.js --network sepolia
```

### 5️⃣ Update Frontend

The deployment script automatically updates the contract address in `src/contract_data/`.

### 6️⃣ Switch MetaMask to Sepolia

1. Open MetaMask
2. Switch network to "Sepolia Test Network"

### 7️⃣ Run Frontend

```bash
npm run dev
```

---

## 📂 Project Structure

```
new_hardhat-main/
├── contracts/              # Solidity Smart Contracts
│   ├── GetSet.sol         # Basic value storage & ETH deposit contract
│   └── Mines.sol          # Main betting contract for games
│
├── scripts/
│   └── deploy.js          # Contract deployment script
│
├── src/
│   ├── app/               # Next.js App Router
│   │   ├── layout.jsx     # Root layout
│   │   └── page.jsx       # Main entry point
│   │
│   ├── Pages/
│   │   ├── launcher.jsx   # Landing page with MetaMask connection
│   │   ├── navbar.jsx     # Navigation component
│   │   ├── ContactUs.jsx  # Contact page
│   │   └── Games/         # Game implementations
│   │       ├── games.jsx      # Game selection lobby
│   │       ├── Mines.jsx      # Minesweeper gambling game
│   │       ├── BlackJack.jsx  # Blackjack card game
│   │       ├── SpinWheel.jsx  # Wheel of fortune game
│   │       └── highlow.jsx    # High-Low card game
│   │
│   └── contract_data/     # Deployed contract ABIs & addresses
│
├── hardhat.config.js      # Hardhat configuration
├── package.json
└── tailwind.config.js
```

---

## 🎮 Available Games

1. **Mines** - Minesweeper-style gambling game with multipliers
2. **Blackjack** - Classic card game with dealer AI
3. **Spin Wheel** - Wheel of fortune with risk levels
4. **High-Low** - Card prediction game

---

## 🛠️ Available Commands

### Smart Contract Commands

```bash
# Compile contracts
npx hardhat compile

# Run tests
npx hardhat test

# Start local blockchain
npx hardhat node

# Deploy to localhost
npx hardhat run scripts/deploy.js --network localhost

# Deploy to Sepolia
npx hardhat run scripts/deploy.js --network sepolia

# Check gas usage
REPORT_GAS=true npx hardhat test
```

### Frontend Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm run start
```

---

## 🔍 How to Use the Application

### 1. Connect Wallet

1. Click "Connect with MetaMask" on the landing page
2. Approve the connection in MetaMask
3. Your account address will be displayed

### 2. Play Games

1. Click "Play" button
2. Select a game from the lobby
3. Enter your bet amount
4. Play the game!

### 3. Cash Out

- Click "Cash Out" to withdraw your winnings
- The smart contract will transfer ETH to your wallet
- Transaction will be confirmed on the blockchain

---

## ⚠️ Known Challenges

- 🧾 **High Gas Fees**: May impact real-time gameplay
- ⚖️ **Regulatory Barriers**: Legal issues in some regions
- 🔄 **UX for New Users**: Web3 onboarding can be complex
- 🧱 **Immutable Contracts**: Once deployed, cannot be altered
- 🛠️ **Error Handling**: Smart contracts require precise handling of logic

---

## 💡 Future Improvements

- 🎲 Add multiple betting games and user stats
- 🔐 NFT-based game access or identity
- 🌐 IPFS-based bet history and logs
- 📊 Admin dashboard with analytics
- 🔁 Cross-chain support (Polygon, BNB Chain)
- 🎰 Chainlink VRF for provably fair randomness
- 🔒 Access control for contract functions
- 📈 User leaderboards and achievements

---

## 🐛 Troubleshooting

### Issue: "MetaMask not detected"
**Solution**: Install MetaMask browser extension and refresh the page

### Issue: "Transaction failed"
**Solution**: 
- Ensure you have enough ETH for gas fees
- Check if you're on the correct network (localhost or Sepolia)
- Try increasing gas limit

### Issue: "Contract not deployed"
**Solution**: 
- Run the deployment script: `npx hardhat run scripts/deploy.js --network localhost`
- Check that `src/contract_data/Mines-address.json` exists

### Issue: "npm install" fails
**Solution**: 
- Delete `node_modules` and `package-lock.json`
- Run `npm install` again
- Ensure Node.js v18+ is installed

### Issue: Port 3000 already in use
**Solution**: 
- Kill the process using port 3000
- Or run on a different port: `npm run dev -- -p 3001`

---

## 📞 Contact & Support

- **Email**: singhravish2900@gmail.com
- **Instagram**: [@ravish_singh486](https://instagram.com/ravish_singh486)
- **GitHub**: [singhravish486](https://github.com/singhravish486)

---

## 📄 License

This project is for educational purposes. Use at your own risk.

---

## 🙏 Acknowledgments

Built with:
- Next.js 15
- React 19
- Hardhat
- ethers.js
- TailwindCSS
- Framer Motion

---

**Happy Gaming! 🎰🎲🃏**
