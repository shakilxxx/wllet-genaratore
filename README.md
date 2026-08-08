Thik ache, Step by Step guide dey dicci:

Step 1: Node.js Install Koro
Browser e jao: https://nodejs.org/
LTS version download koro (Long Term Support)
File download hoye gele double-click koro
Next → Next → Install click koro
Installation complete hole Restart koro
Step 2: Folder Banaao
Desktop e ekta folder banaao, naam deo: wallet_generator
Folder ta open koro
Step 3: CMD Open Koro Folder e
Folder e Shift + Right Click koro
"Open PowerShell window here" click koro
(Or alternative: Address bar e cmd likhe Enter dao)
Step 4: package.json File Banaao

CMD window e likho:

bash
notepad package.json

Enter dao → Ekta text editor khule jaabe → Ei code paste koro:

json
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

Ctrl+S → Ctrl+Q (Save & Close koro)

Step 5: wallet_generator.js File Banaao

CMD e again likho:

bash
notepad wallet_generator.js

Ei code paste koro:

javascript
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

console.log('🚀 1000 EVM Wallet Generate Korchi...\n');

let phraseAddressContent = '';
let addressOnlyContent = '';

// Generate 1000 wallets
for (let i = 1; i <= 1000; i++) {
    // Random mnemonic generate koro
    const entropy = crypto.randomBytes(16);
    const mnemonic = ethers.Mnemonic.entropyToPhrase(entropy);
    
    // Wallet create koro from mnemonic
    const wallet = ethers.Wallet.fromPhrase(mnemonic);
    const address = wallet.address;
    
    // First 5 characters of address (0x ke remove korle porer 5 digit)
    const first5Digits = address.substring(0, 7); // 0x + 5 digits
    
    // Phrase file name
    const phraseFileName = path.join(outputDir, `wallet_${i}_phrase.txt`);
    
    // Save mnemonic to separate file
    fs.writeFileSync(phraseFileName, mnemonic);
    
    // Format: mnemonic phrase - 0x12345
    const lineForMaster = `${mnemonic} - ${first5Digits}`;
    phraseAddressContent += lineForMaster + '\n';
    
    // Just address for other file
    addressOnlyContent += address + '\n';
    
    // Progress show koro
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

Ctrl+S → Ctrl+Q (Save & Close)

Step 6: Dependencies Install Koro

CMD window e likho:

bash
npm install

Wait koro... "added 9 packages" dike dektar pore continue koro

Step 7: Script Run Koro! 🚀

CMD e likho:

bash
node wallet_generator.js

Or:

bash
npm start
Step 8: Output Check Koro

Script complete hoyer pore:

Folder e wallets_output folder dekhbe
Ek ghure dekho:
✅ wallet_phrases_and_addresses.txt (phrases + short address)
✅ addresses_only.txt (full addresses)
✅ wallet_1_phrase.txt to wallet_1000_phrase.txt (individual files)
