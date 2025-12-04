# 🎮 Chance - Quick Start Guide

## ✅ Your Project is Now Running!

### 🌐 Access the Application
**Frontend**: http://localhost:3000
**Blockchain**: http://127.0.0.1:8545

### 📝 Contract Deployed
**Mines Contract Address**: `0x5FbDB2315678afecb367f032d93F642f64180aa3`

---

## 🚀 Quick Commands Reference

### Start Everything (3 Terminals Required)

**Terminal 1 - Blockchain**
```bash
cd d:\Chance\Chance\new_hardhat-main
npx hardhat node
```

**Terminal 2 - Deploy Contracts**
```bash
cd d:\Chance\Chance\new_hardhat-main
npx hardhat run scripts/deploy.js --network localhost
```

**Terminal 3 - Frontend**
```bash
cd d:\Chance\Chance\new_hardhat-main
npm run dev
```

---

## 🦊 MetaMask Setup for Local Testing

### Add Hardhat Network to MetaMask

1. Open MetaMask
2. Click network dropdown → "Add Network" → "Add a network manually"
3. Enter:
   - **Network Name**: Hardhat Local
   - **RPC URL**: `http://127.0.0.1:8545`
   - **Chain ID**: `1337`
   - **Currency Symbol**: `ETH`
4. Click "Save"

### Import Test Account

1. From the Hardhat node terminal, copy any private key
2. MetaMask → Account icon → "Import Account"
3. Paste the private key
4. You now have 10,000 ETH for testing! 🎉

---

## 🎯 How to Use

1. **Open**: http://localhost:3000
2. **Connect**: Click "Connect with MetaMask"
3. **Play**: Click "Play" → Select a game
4. **Bet**: Enter amount and start playing
5. **Win**: Cash out your winnings!

---

## 🎮 Available Games

- **Mines** - Minesweeper gambling (25 tiles, 10 bombs)
- **Blackjack** - Classic card game
- **Spin Wheel** - Wheel of fortune with risk levels
- **High-Low** - Card prediction game

---

## 🛑 Stop Everything

Press `Ctrl + C` in each terminal to stop:
1. Hardhat node
2. Frontend server

---

## 🔄 Restart After Stopping

Just run the 3 commands again:
1. `npx hardhat node`
2. `npx hardhat run scripts/deploy.js --network localhost`
3. `npm run dev`

---

## 📞 Need Help?

- **Email**: singhravish2900@gmail.com
- **Instagram**: @ravish_singh486
- **Full Guide**: See `SETUP_GUIDE.md`

---

**Happy Gaming! 🎰**
