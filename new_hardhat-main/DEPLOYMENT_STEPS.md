# 🎯 Step-by-Step Deployment Instructions

## ✅ PHASE 1: Get Sepolia ETH (Testnet Currency)

### Step 1.1: Add Sepolia Network to MetaMask

1. Open MetaMask
2. Click network dropdown (top center)
3. Click "Show test networks" toggle (if not visible)
4. Select "Sepolia test network"

### Step 1.2: Get Free Sepolia ETH

Visit these faucets (you need ~0.5 Sepolia ETH):

**Option 1: Alchemy Faucet** (Recommended)
1. Go to: https://sepoliafaucet.com/
2. Sign in with Alchemy account (free)
3. Enter your MetaMask wallet address
4. Click "Send Me ETH"
5. Wait 1-2 minutes
6. Check MetaMask - you should have 0.5 Sepolia ETH

**Option 2: Infura Faucet**
1. Go to: https://www.infura.io/faucet/sepolia
2. Sign in with Infura account (free)
3. Enter wallet address
4. Receive 0.5 Sepolia ETH

**Option 3: QuickNode Faucet**
1. Go to: https://faucet.quicknode.com/ethereum/sepolia
2. Enter wallet address
3. Complete CAPTCHA
4. Receive Sepolia ETH

---

## ✅ PHASE 2: Configure Environment

### Step 2.1: Export Your MetaMask Private Key

⚠️ **WARNING**: Keep this EXTREMELY secret! Never share or commit to GitHub!

1. Open MetaMask
2. Click the 3 dots (⋮) on your account
3. Click "Account details"
4. Click "Show private key"
5. Enter your MetaMask password
6. **Copy the private key** (starts with 0x...)

### Step 2.2: Create .env File

Create a file called `.env` in `new_hardhat-main` directory:

```bash
# In new_hardhat-main directory
# Create .env file (NOT .env.example)
```

Add this content (replace with YOUR private key):

```env
PRIVATE_KEY=your_actual_private_key_here_without_0x_prefix
```

**Example:**
```env
# If your private key is: 0xabcdef123456...
# Put it like this (without 0x):
PRIVATE_KEY=abcdef123456789abcdef123456789abcdef123456789abcdef123456789abc
```

### Step 2.3: Verify .env is in .gitignore

Check that `.env` is listed in `.gitignore` (it should be already):

```bash
# Check .gitignore contains:
.env
```

---

## ✅ PHASE 3: Deploy Smart Contracts to Sepolia

### Step 3.1: Verify Hardhat Configuration

Check `hardhat.config.js` has Sepolia network configured:

```javascript
networks: {
  sepolia: {
    url: "https://eth-sepolia.g.alchemy.com/v2/8M-A8S59VNodqtUAIom94hhtunRlqYHF",
    accounts: process.env.PRIVATE_KEY ? [process.env.PRIVATE_KEY] : []
  }
}
```

### Step 3.2: Deploy Contracts

Run this command:

```bash
npx hardhat run scripts/deploy.js --network sepolia
```

**Expected Output:**
```
Contract deployed to: 0x1234567890abcdef1234567890abcdef12345678
```

**Copy this contract address!** You'll need it.

### Step 3.3: Verify Deployment

The script automatically updates these files:
- `src/contract_data/Mines-address.json`
- `src/contract_data/Mines.json`

Check the files were updated:

```bash
# View the deployed address
type src\contract_data\Mines-address.json
```

Should show:
```json
{
  "address": "0xYourDeployedContractAddress"
}
```

---

## ✅ PHASE 4: Test Locally with Sepolia

### Step 4.1: Update MetaMask to Sepolia

1. Open MetaMask
2. Switch network to "Sepolia test network"
3. Verify you have Sepolia ETH

### Step 4.2: Test Your App Locally

```bash
# Make sure dev server is running
npm run dev
```

1. Open http://localhost:3000
2. Click "Connect with MetaMask"
3. Approve connection
4. Try placing a small bet (0.01 ETH)
5. Confirm transaction in MetaMask
6. Wait for transaction confirmation
7. Verify it works!

**If it works locally with Sepolia, it will work on Vercel!**

---

## ✅ PHASE 5: Prepare Code for Vercel

### Step 5.1: Test Production Build

```bash
# Build the project
npm run build
```

**Fix any errors that appear!**

Common errors:
- Missing dependencies
- TypeScript errors
- Import errors

### Step 5.2: Test Production Build Locally

```bash
# Start production server
npm start
```

Open http://localhost:3000 and test everything works.

### Step 5.3: Commit Changes

```bash
# Add all changes
git add .

# Commit
git commit -m "Prepare for Vercel deployment - contracts deployed to Sepolia"

# Push to GitHub
git push origin main
```

---

## ✅ PHASE 6: Deploy to Vercel

### Step 6.1: Sign Up for Vercel

1. Go to: https://vercel.com
2. Click "Sign Up"
3. Click "Continue with GitHub"
4. Authorize Vercel to access your GitHub account

### Step 6.2: Import Your Repository

1. On Vercel dashboard, click "Add New..." → "Project"
2. Find "Blockchain-Chance" in the list
3. Click "Import"

### Step 6.3: Configure Project Settings

**IMPORTANT SETTINGS:**

**Framework Preset:**
- Should auto-detect: "Next.js" ✅

**Root Directory:**
- Click "Edit" next to Root Directory
- Enter: `new_hardhat-main`
- Click "Continue"

**Build Settings:**
- Build Command: `npm run build` (default)
- Output Directory: `.next` (default)
- Install Command: `npm install` (default)

**Environment Variables:**
- Skip for now (no secrets needed for frontend)

### Step 6.4: Deploy!

1. Click "Deploy"
2. Wait 2-3 minutes
3. Watch the build logs
4. When done, you'll see: "🎉 Congratulations!"

### Step 6.5: Get Your Live URL

You'll see:
```
https://blockchain-chance.vercel.app
```

Or something like:
```
https://blockchain-chance-xyz123.vercel.app
```

**Copy this URL!**

---

## ✅ PHASE 7: Test Your Live App

### Step 7.1: Open Your Live URL

Visit your Vercel URL in a browser

### Step 7.2: Connect MetaMask

1. Make sure MetaMask is on **Sepolia network**
2. Click "Connect with MetaMask"
3. Approve the connection

### Step 7.3: Test a Transaction

1. Try placing a small bet (0.01 Sepolia ETH)
2. Confirm in MetaMask
3. Wait for transaction
4. Verify it works!

### Step 7.4: Verify on Etherscan

1. Go to: https://sepolia.etherscan.io/
2. Search for your contract address
3. You should see your transactions!

---

## ✅ PHASE 8: Set Up Custom Domain (Optional)

### Step 8.1: Add Domain in Vercel

1. In Vercel dashboard, go to your project
2. Click "Settings" → "Domains"
3. Enter your domain name
4. Follow DNS configuration instructions

### Step 8.2: Update DNS

Add these records to your domain:
```
Type: A
Name: @
Value: 76.76.21.21

Type: CNAME
Name: www
Value: cname.vercel-dns.com
```

---

## ✅ PHASE 9: Set Up Automatic Deployments

### Already Done! ✅

Every time you push to GitHub:

```bash
git add .
git commit -m "Update game UI"
git push origin main
```

Vercel will automatically:
1. Detect the push
2. Build your app
3. Deploy to production
4. Update your live site

**No manual deployment needed!**

---

## 🎊 DEPLOYMENT COMPLETE!

Your app is now live at:
- **Vercel URL**: https://blockchain-chance.vercel.app
- **Smart Contracts**: On Sepolia blockchain
- **Users can**: Play games, bet ETH, win/lose

---

## 📊 Quick Reference

| Component | Location | URL |
|-----------|----------|-----|
| **Frontend** | Vercel | https://blockchain-chance.vercel.app |
| **Smart Contracts** | Sepolia | https://sepolia.etherscan.io/address/YOUR_CONTRACT |
| **Source Code** | GitHub | https://github.com/singhravish486/Blockchain-Chance |

---

## 🐛 Troubleshooting

### Build Fails on Vercel

**Error**: "Module not found"
```bash
# Solution: Install missing dependency
npm install <missing-package>
git add package.json package-lock.json
git commit -m "Add missing dependency"
git push origin main
```

### Contract Not Found

**Error**: "Contract not deployed"
```bash
# Solution: Redeploy to Sepolia
npx hardhat run scripts/deploy.js --network sepolia
git add src/contract_data/
git commit -m "Update contract address"
git push origin main
```

### Wrong Network

**Error**: "Please switch to Sepolia"
```
Solution: In MetaMask, switch to Sepolia test network
```

### Transaction Fails

**Error**: "Insufficient funds"
```
Solution: Get more Sepolia ETH from faucet
```

---

## 📞 Support Resources

- **Vercel Docs**: https://vercel.com/docs
- **Hardhat Docs**: https://hardhat.org/docs
- **Sepolia Faucet**: https://sepoliafaucet.com/
- **Sepolia Explorer**: https://sepolia.etherscan.io/

---

**Good luck with your deployment!** 🚀
