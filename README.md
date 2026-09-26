# Sentinel &bull; Endpoint Threat &amp; Hash Scanner

[![Live Web Demo](https://img.shields.io/badge/Live_Demo-Vercel-black?style=for-the-badge&logo=vercel)](https://python-endpoint-scanner.vercel.app)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Security](https://img.shields.io/badge/Threat_Intel-MD5%20%7C%20SHA256-F43F5E?style=for-the-badge)](https://github.com/nagpalansh27/Malware-Signature-Database)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

An institutional-grade endpoint security and malware detection suite combining a **native Python desktop filesystem scanner** with an **in-browser, zero-upload cryptographic hash and Shannon entropy inspection tool**.

🌐 **Instant Live Web Demo**: **[python-endpoint-scanner.vercel.app](https://python-endpoint-scanner.vercel.app)**

---

## 🏛️ System Architecture & Detection Mechanisms

Sentinel operates via a three-tier defensive detection pipeline:

```
[ Target File / Executable ]
             │
             ├──► [ Tier 1: Hardware-Accelerated Hashing ]
             │    Computes MD5, SHA-1, and SHA-256 digests in chunks.
             │
             ├──► [ Tier 2: Signature Database Lookup ]
             │    Matches hashes against 15,000+ known malware signatures (MD5/SHA256).
             │
             └──► [ Tier 3: Shannon Byte Entropy Analysis ]
                  Calculates informational randomness:
                  H(X) = - Σ P(x) * log₂(P(x))
                  Entropy > 7.20 ⟹ High probability of packing, UPX, or ransomware encryption.
```

---

## 📂 Project Structure & Key Files

```
Python-Endpoint-Scanner/
├── Antivirus.py         # P0: Python desktop GUI/CLI filesystem scanner & quarantine engine
├── index.html           # P0: Client-side zero-install web scanner (Web Crypto API & Entropy)
├── hard_signatures/     # P0: Precompiled binary threat signatures
├── settings/            # P1: Quarantine paths, whitelist configurations, and scan rules
├── res/                 # P2: GUI icons and auditory alert assets
└── README.md            # P1: Engineering documentation & AI tweaking guide
```

---

## 🚀 How to Run & Test

### 1. Web Application (Zero Install / Instant)
- **Live Vercel Production**: [python-endpoint-scanner.vercel.app](https://python-endpoint-scanner.vercel.app)
- **Local Testing**: Double-click `index.html` in any modern web browser.

### 2. Desktop Python Antivirus Engine
```bash
# Clone the repository
git clone https://github.com/nagpalansh27/Python-Endpoint-Scanner.git
cd Python-Endpoint-Scanner

# Launch the desktop antivirus engine
python Antivirus.py
```

---

## 🤖 AI & Developer Tweaking Cheatsheet

If an AI agent or developer is modifying this tool, follow these exact guidelines:

| File | Component | What to Tweak | How to Modify |
| :--- | :--- | :--- | :--- |
| `index.html` | Entropy Threshold | Adjust sensitivity for detecting packed malware | Modify `if (entropy > 7.3)` (7.2 = sensitive, 7.6 = strict). |
| `index.html` | Hash Signatures | Add new IOC (Indicators of Compromise) | Append hex strings to `const KNOWN_THREAT_HASHES = [...]`. |
| `Antivirus.py` | Signature Path | Change path to malware signature files | Modify `SIGNATURE_PATH` in `Antivirus.py` or `settings/`. |
| `Antivirus.py` | Quarantine Action | Modify file isolation policy | Tweak `quarantine_file(filepath)` function to move rather than delete. |
