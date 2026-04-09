# Hardened Deterministic Seed Generator

A lightweight, single-file web tool to generate standard BIP-39 mnemonics from personal secrets. Designed for maximum security and brute-force resistance.

## 🛡️ Security Features

- **Extreme Key Stretching:** Uses **1,000,000 iterations** of PBKDF2. This makes hardware-accelerated brute-force attacks computationally expensive.
- **Client-Side Only:** No data ever leaves your browser. The tool is designed to be used **offline**.
- **Transparent:** Built with [ethers.js v6](https://github.com/ethers-io/ethers.js), a trusted and audited library.
- **Flexible Entropy:**
  - Generates **12 words** by default (128-bit entropy).
  - Can be easily toggled to generate **24 words** (256-bit entropy) by changing the byte length to 32.

## 🚀 How to Use

1. **Clone the repository:**
   ```bash
   git clone https://github.com/pitbred/brainwallet-gen.git
   cd brainwallet-gen
   ```
2. **Go Offline:** Disconnect your device from the internet (highly recommended for maximum security).
3. **Open the tool:** Launch index.html in any modern web browser.
4. Generate:
  * Enter your Salt (can be a number or a simple word).
  * Enter your Secret Phrase (use long, complex sentences for better security).
  * Click "Generate".
5. **Clean up:** After you have safely noted your 12 words, **close the browser tab and clear your browser cache** (or simply use Incognito mode) to ensure no traces remain in memory.  

## 🛠 Configuration (12 vs 24 words)

The mnemonic length depends on the entropy size in the code:
- **For 12 words:** Use `16` bytes.
- **For 24 words:** Use `32` bytes.

```javascript
// Current implementation for 24 words:
const entropy = ethers.pbkdf2(password, salt, 1000000, 32, 'sha256');
```

## ⚠️ Disclaimer
Use at your own risk. This is a tool for educational and personal use. Always verify your generated seed phrase before sending significant funds. I am not responsible for any lost funds due to forgotten secrets or misuse of this tool.
