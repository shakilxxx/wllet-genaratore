# 🔐 EVM Wallet Generator

Generate **1000 EVM wallets** with mnemonic phrases automatically using Node.js and ethers.js.

---

## 📋 Requirements

- [Node.js](https://nodejs.org/) (LTS version recommended)
- npm (comes with Node.js)

---

## 🚀 Setup Guide (Step by Step)

### Step 1 — Node.js Install করো

1. Browser এ যাও: [https://nodejs.org/](https://nodejs.org/)
2. **LTS version** download করো
3. File download হলে double-click করো
4. `Next → Next → Install` click করো
5. Installation complete হলে **Restart** করো

---

### Step 2 — Folder বানাও

Desktop এ একটা folder বানাও, নাম দাও:

```
wallet_generator
```

---

### Step 3 — CMD Open করো Folder এ

Folder এ **Shift + Right Click** করো → `"Open PowerShell window here"` click করো

> **Alternative:** Address bar এ `cmd` লিখে Enter দাও

---

### Step 4 — `package.json` File বানাও

CMD window এ লিখো:

```bash
notepad package.json
```

Enter দাও → Text editor খুলবে → নিচের code paste করো:

```json
{
  "name": "evm-wallet-generator",
  "version": "1.0.0",
  "description": "Generate 1000 EVM wallets with mnemonics",
  "main": "wallet_generator.js",
  "scripts": {
    "start": "node wallet_generator.js"
  },
  "dependencies": {
    "ethers": "^6.13.0"
  }
}
```

`Ctrl+S` → `Ctrl+W` (Save & Close)

---

### Step 5 — `wallet_generator.js` File বানাও

CMD এ আবার লিখো:

```bash
notepad wallet_generator.js
```

নিচের code paste করো:

```javascript
const ethers = require('ethers');
const fs = require('fs');
const path = require('path');
const crypto = require('crypto');

// Create output directory
const outputDir = './wallets_output';
if (!fs.existsSync(outputDir)) {
    fs.mkdirSync(outputDir, { recursive: true });
}

// Files to store data
const phraseAddressFile = path.join(outputDir, 'wallet_phrases_and_addresses.txt');
const addressOnlyFile = path.join(outputDir, 'addresses_only.txt');

// Initialize these files
fs.writeFileSync(phraseAddressFile, '');
fs.writeFileSync(addressOnlyFile, '');

console.log('🚀 1000 EVM Wallet Generate করছি...\n');

let phraseAddressContent = '';
let addressOnlyContent = '';

// Generate 1000 wallets
for (let i = 1; i <= 1000; i++) {
    // Random mnemonic generate করো
    const entropy = crypto.randomBytes(16);
    const mnemonic = ethers.Mnemonic.entropyToPhrase(entropy);

    // Wallet create করো from mnemonic
    const wallet = ethers.Wallet.fromPhrase(mnemonic);
    const address = wallet.address;

    // First 5 characters of address (0x + 5 digits)
    const first5Digits = address.substring(0, 7);

    // Phrase file name
    const phraseFileName = path.join(outputDir, `wallet_${i}_phrase.txt`);

    // Save mnemonic to separate file
    fs.writeFileSync(phraseFileName, mnemonic);

    // Format: mnemonic phrase - 0x12345
    const lineForMaster = `${mnemonic} - ${first5Digits}`;
    phraseAddressContent += lineForMaster + '\n';

    // Just address for other file
    addressOnlyContent += address + '\n';

    // Progress show করো
    if (i % 100 === 0) {
        console.log(`✅ ${i} wallets generated...`);
    }
}

// Save master files
fs.writeFileSync(phraseAddressFile, phraseAddressContent);
fs.writeFileSync(addressOnlyFile, addressOnlyContent);

console.log('\n✨ Generation Complete!\n');
console.log(`📁 Output Directory: ${outputDir}`);
console.log(`📄 Individual phrase files: wallet_1_phrase.txt to wallet_1000_phrase.txt`);
console.log(`📋 Master file (phrases + addresses): wallet_phrases_and_addresses.txt`);
console.log(`📍 Address only file: addresses_only.txt`);
console.log(`\n✅ 1000 wallets successfully created!`);
```

`Ctrl+S` → `Ctrl+W` (Save & Close)

---

### Step 6 — Dependencies Install করো

```bash
npm install
```

> Wait করো... `added 9 packages` দেখলে continue করো

---

### Step 7 — Script Run করো 🚀

```bash
node wallet_generator.js
```

অথবা:

```bash
npm start
```

---

### Step 8 — Output Check করো

Script complete হওয়ার পরে `wallets_output` folder এ যাও:

| File | Description |
|------|-------------|
| `wallet_phrases_and_addresses.txt` | সব phrases + short address (একসাথে) |
| `addresses_only.txt` | শুধু full addresses |
| `wallet_1_phrase.txt` → `wallet_1000_phrase.txt` | Individual wallet phrase files |

---

## ⚡ Quick Reference (Copy-Paste Ready)

```bash
# Step 1: package.json বানাও
notepad package.json

# Step 2: wallet_generator.js বানাও
notepad wallet_generator.js

# Step 3: Dependencies install করো
npm install

# Step 4: Script run করো
node wallet_generator.js
```

---

## 📁 Project Structure

```
wallet_generator/
├── package.json
├── wallet_generator.js
└── wallets_output/
    ├── wallet_phrases_and_addresses.txt
    ├── addresses_only.txt
    ├── wallet_1_phrase.txt
    ├── wallet_2_phrase.txt
    └── ... (wallet_1000_phrase.txt পর্যন্ত)
```

---

## 🛠️ Tech Stack

- **Runtime:** Node.js
- **Library:** [ethers.js v6](https://docs.ethers.org/v6/)
- **Crypto:** Node.js built-in `crypto` module

---

## ⚠️ Disclaimer

> এই tool টি শুধুমাত্র **educational / testing purpose** এর জন্য।  
> Generated wallets গুলো নিরাপদ জায়গায় রাখো এবং কখনো publicly share করো না।

---

## 📄 License

MIT License



## 🎬 Demo Video

[▶️ Watch Demo Video](./demo.mp4)
