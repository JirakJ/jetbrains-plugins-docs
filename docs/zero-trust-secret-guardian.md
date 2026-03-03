# Zero-Trust Enterprise Secret Guardian

> Secure vault-to-IDE secret injection with zero disk footprint.

## Overview

Zero-Trust Enterprise Secret Guardian eliminates security risks from leaked sensitive data by creating a **secure bridge between cloud secret vaults and your JetBrains IDE**. Secrets exist solely in RAM during IDE sessions — no disk storage, no cache, no `.env` files. It integrates with **Infisical** and **Doppler** vaults and automatically injects secrets into run configurations.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Zero-Trust Secret Guardian"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Infisical or Doppler account

## Features

### Free Tier
- Vault authentication (Infisical, Doppler)
- Environment picker (dev, staging, prod)
- Dynamic run configuration interception
- Secret injection into process memory (JVM, Node.js, Python)
- Log masking (auto-censors secrets in terminal output with `********`)
- Connection testing with visual status indicators
- Automatic retry (up to 3 retries for transient failures)
- Cache lifecycle management (secrets flushed on process termination)

### Enterprise Tier
- Pre-commit scanner (guardrail) — blocks commits containing vault secrets
- Team-wide vault policies
- Audit logging

## How It Works

1. **Configure** vault connection in the Zero-Trust Vault tool window
2. **Run** any application from the IDE
3. **Plugin intercepts** the run configuration before execution
4. **Downloads secrets** asynchronously from your vault (with progress dialog)
5. **Injects secrets** directly into process environment variables (in RAM only)
6. **Application runs** with secrets available as env vars
7. **On termination**, secrets are flushed from memory

## Configuration

### Tool Window (Zero-Trust Vault, Right Panel)

| Setting | Description |
|---------|-------------|
| Vault Provider | Infisical or Doppler |
| Custom Base URL | On-premise vault URL (optional) |
| Access Token | Securely stored via JetBrains Credential Store |
| Project ID/Config | Project identifier in vault |
| Environment | dev, staging, or prod |

**Security:** Access tokens are stored via JetBrains `PasswordSafe` API — never as plaintext on disk.

## Tool Windows

### Zero-Trust Vault
- **Location:** Right panel
- **Content:** Vault configuration form, connection status indicator, Save & Test button
- **Status Colors:**
  - 🟢 Green — Connected, secrets loaded (shows count)
  - 🟠 Orange — Connected but no secrets found
  - 🔴 Red — Connection error

## Supported Vaults

| Vault | API Endpoint | Auth Method |
|-------|-------------|-------------|
| **Infisical** | `https://app.infisical.com/api/v3/secrets/raw` | Bearer token |
| **Doppler** | `https://api.doppler.com/v3/configs/config/secrets/download` | Bearer token |
| **Custom** | Configurable base URL | Bearer token |

## Log Masking

All console output is filtered automatically:
- Secrets ≥5 characters are replaced with `********`
- Common values excluded from masking (`true`, `false`, `dev`, `staging`, `prod`)
- Works on both IDE terminal and application output

## Pre-Commit Scanner (Enterprise)

When enabled:
1. Scans all modified files before commit
2. Checks file contents against known vault secrets
3. Shows warning dialog if secrets detected
4. Options: "Review Commit" (cancel) or "Commit Anyway (Unsafe)"
5. Excludes `.jar`, `.class` files and directories

## Supported Runtimes

Secrets are injected as environment variables, compatible with:
- Java (JVM)
- JavaScript / Node.js
- Python
- Any runtime that reads environment variables

## FAQ

**Q: Are secrets ever written to disk?**
A: No. Secrets exist only in RAM and are flushed when the process terminates.

**Q: What happens if the vault is unreachable?**
A: The plugin shows a retry dialog. After 3 failed attempts, execution proceeds without secrets (with a warning).

**Q: Can I use both Infisical and Doppler?**
A: Currently one vault per project. Switch in the tool window settings.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
