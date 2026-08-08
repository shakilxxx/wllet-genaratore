# Orchestrated Step-by-Step CMD Setup Guide for Script Execution

Orchestrated step-by-step CMD setup guide for script execution.

Thik ache, Step by Step guide dey dicci:

---

### **Step 1: Node.js Install Koro**

1. Browser e jao: [https://nodejs.org/](https://nodejs.org/)
2. **LTS version download koro** (Long Term Support)
3. File download hoye gele double-click koro
4. **Next → Next → Install** click koro
5. Installation complete hole **Restart koro**

---

### **Step 2: Folder Banaao**

1. **Desktop** e ekta folder banaao, naam deo: `wallet_generator`
2. Folder ta open koro

---

### **Step 3: CMD Open Koro Folder e**

1. Folder e **Shift + Right Click** koro
2. **"Open PowerShell window here"** click koro
   (Or alternative: Address bar e `cmd` likhe Enter dao)

---

### **Step 4: package.json File Banaao**

CMD window e likho:

```bash
notepad package.json
```

Enter dao → Ekta text editor khule jaabe → Ei code paste koro:

```json
{
  "name": "evm-wallet-generator",
  "version": "1.0.0",
  "description": "EVM wallet development project",
  "main": "wallet_generator.js",
  "scripts": {
    "start": "node wallet_generator.js"
  },
  "dependencies": {
    "ethers": "^6.13.0"
  }
}
```

Ctrl+S → Ctrl+Q (Save & Close koro)

---

### **Step 5: wallet_generator.js File Banaao**

CMD e again likho:

```bash
notepad wallet_generator.js
```

Ei code paste koro:

```javascript
const ethers = require('ethers');
const fs = require('fs');

const outputDir = './wallets_output';

if (!fs.existsSync(outputDir)) {
    fs.mkdirSync(outputDir, { recursive: true });
}

console.log('🚀 EVM Wallet Development Project Started...\n');

// ----------------------------------------------------
// SAFE DEVELOPMENT PLACEHOLDER
// ----------------------------------------------------
// Add your non-sensitive test implementation here.
//
// IMPORTANT:
// Never generate, store, or publish real wallet
// seed phrases/private keys in a public repository.
// ----------------------------------------------------

console.log('✅ Project setup completed!');
console.log(`📁 Output Directory: ${outputDir}`);
```

Ctrl+S → Ctrl+Q (Save & Close)

---

### **Step 6: Dependencies Install Koro**

CMD window e likho:

```bash
npm install
```

Wait koro... installation complete hole continue koro.

`node_modules` folder create hole dependencies successfully installed.

---

### **Step 7: Script Run Koro!** 🚀

CMD e likho:

```bash
node wallet_generator.js
```

**Or:**

```bash
npm start
```

Script successfully run hole terminal e project status dekhabe.

---

### **Step 8: Output Check Koro**

Script complete hoyer pore:

- Folder e **`wallets_output`** folder dekhbe
- Development output files thakle segulo ei folder-er moddhe store hobe

Example:

```text
wallet_generator/
│
├── node_modules/
├── wallets_output/
├── package.json
├── package-lock.json
└── wallet_generator.js
```

---

### **Quick Reference (Copy-Paste Ready):**

```text
Folder banaao → CMD open koro →

notepad package.json
(paste code + save)

notepad wallet_generator.js
(paste code + save)

npm install

node wallet_generator.js
```

**Done! ✅** Project setup complete!

Kono problem hole bolo! 😊
