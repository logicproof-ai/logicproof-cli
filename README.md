<div align="center">

# LogicProof CLI (`logicproof`)

### **Standalone Native Binaries for Mathematical Security & Business Logic Verification**
*Zero Dependencies. Zero Code Retention. Sub-Second Local Pre-Push Verification.*

[![Release](https://img.shields.io/github/v/release/logicproof-ai/logicproof-cli?style=flat-square&color=2088FF)](https://github.com/logicproof-ai/logicproof-cli/releases)
[![Platforms](https://img.shields.io/badge/Platforms-Linux_x64_%7C_macOS_arm64%2FIntel_%7C_Windows_x64-brightgreen?style=flat-square)](#-binary-downloads)
[![Engine](https://img.shields.io/badge/Engine-Microsoft_Z3_SMT-007acc?style=flat-square)](https://github.com/Z3Prover/z3)
[![License](https://img.shields.io/badge/License-Proprietary_EULA-lightgrey?style=flat-square)](#-licensing)

<p align="center">
  <a href="#-quick-installation">Installation</a> •
  <a href="#-binary-downloads">Releases</a> •
  <a href="#-usage-guide">CLI Usage</a> •
  <a href="#-pre-push-git-hook">Git Hook</a> •
  <a href="#-integrity-verification">Checksums</a>
</p>

---

</div>

## 📥 Quick Installation

LogicProof is distributed as a single standalone native executable with the **Z3 SMT solver statically embedded**. You do **not** need Python, Node, Docker, or external compilers installed.

### Linux (x86_64)
```bash
curl -fsSL -o logicproof https://github.com/logicproof-ai/logicproof-cli/releases/latest/download/logicproof-linux-x64
chmod +x logicproof
sudo mv logicproof /usr/local/bin/
logicproof --version
```

### macOS (Apple Silicon arm64 / Intel x64)
```bash
curl -fsSL -o logicproof https://github.com/logicproof-ai/logicproof-cli/releases/latest/download/logicproof-macos
chmod +x logicproof
sudo mv logicproof /usr/local/bin/
logicproof --version
```

### Windows (x86_64 PowerShell)
```powershell
Invoke-WebRequest -Uri "https://github.com/logicproof-ai/logicproof-cli/releases/latest/download/logicproof-windows-x64.exe" -OutFile "logicproof.exe"
.\logicproof.exe --version
```

---

## 🔑 Activating Your License

Before running your first analysis, activate your client license key from the [LogicProof Portal](https://logicproofai.com/panel):

```bash
logicproof --activar YOUR_API_KEY
```

For continuous integration servers or transient container environments, export the environment variable:

```bash
export LOGICPROOF_API_KEY=your_api_key
```

> **🔒 Privacy Guarantee:** The CLI performs verification completely offline and locally. The only network call made by the binary is an encrypted license token verification. **No source code, file contents, or AST structures ever leave your machine.**

---

## 💻 CLI Usage Guide

### 1. Analyze an Entire Repository
```bash
logicproof .
```

### 2. Analyze a Specific File or Directory
```bash
logicproof src/api/payments.ts
logicproof app/services/
```

### 3. Fast Mode (Rapid Development)
Focuses on immediate path exploration for instant feedback during active development:
```bash
logicproof . --fast
```

### 4. Critical Breaches Only (Zero Noise)
Hides informational review notes and only outputs mathematically proven high-severity vulnerabilities:
```bash
logicproof . --solo-criticas
```

### 5. Generate SARIF 2.1.0 for IDEs and CI/CD
```bash
logicproof . --sarif audit.sarif
```

### 6. Machine-Readable JSON Output
```bash
logicproof . --json > findings.json
```

---

## 🪝 Pre-Push Git Hook: Catch Flaws Before Committing

Never push a vulnerability to remote branches again. Install the automated pre-push hook with a single command:

```bash
logicproof --instalar-hook
```

This installs `.git/hooks/pre-push`. Every time you run `git push`:
- LogicProof verifies changed files in sub-seconds.
- If a critical breach or invariant violation is proven, the push is safely blocked.
- You receive the exact counterexample and certified code patch in your terminal.

To uninstall:
```bash
logicproof --desinstalar-hook
```

---

## 🛡️ Supported Vulnerability & Logic Coverage

- **OWASP / Taint Sinks:** SQL Injection, SSRF, Command Injection (RCE), Path Traversal, Insecure Direct Object References (IDOR/BOLA), Reflected/Stored XSS, Mass Assignment, Insecure Deserialization, Dynamic Code Evaluation.
- **Business Logic Invariants:** Custom declarative constraints via `logicproof.yaml` (`@balance >= 0`, `@shipped implies @paid`).
- **Auto-PoC Engine:** Generates responsible `curl` commands and reproduction scripts for critical findings.

---

## 🔐 Integrity Verification

Every release includes a cryptographically signed `SHA256SUMS.txt`. Always verify binary integrity after downloading:

```bash
# Verify Linux checksum
sha256sum -c SHA256SUMS.txt --ignore-missing

# Or manual verification
sha256sum logicproof
```

---

## 📄 Licensing & Commercial Support

The `logicproof` binary is proprietary commercial software. Use of the binary requires a valid subscription license key.

- **Web:** [logicproofai.com](https://logicproofai.com)
- **Support:** [soporte@logicproof.ai](mailto:soporte@logicproof.ai)
- **Security Inquiries:** [security@logicproof.ai](mailto:security@logicproof.ai)
