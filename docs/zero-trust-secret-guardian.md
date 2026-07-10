# Zero-Trust Enterprise Secret Guardian

> Bridge cloud secret vaults to your JetBrains IDE and inject secrets into runs from RAM only — never to disk.

## Overview

Zero-Trust Enterprise Secret Guardian eliminates the risk of leaked sensitive data (API keys, database credentials, cloud certificates) during local development. Instead of keeping `.env` files on disk, it connects your IDE directly to a cloud secret vault (**Infisical** or **Doppler**) and injects secrets into your run configurations as environment variables at launch time.

Retrieved secrets live only in RAM for the duration of the run. The plugin does not write them to any cache, registry, or file; the access token itself is kept in the JetBrains Credential Store (PasswordSafe), not in plaintext.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Zero-Trust Secret Guardian"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.2+ with the Java module (e.g. IntelliJ IDEA), and an Infisical or Doppler account with an access token.

## Features

- **Vault authentication** — connect to Infisical or Doppler using an access token stored via the JetBrains Credential Store.
- **Environment picker** — switch between `dev`, `staging`, and `prod`.
- **Dynamic run-configuration interception** — secrets are fetched and injected into the launched process's environment variables in memory, never read from disk.
- **Pre-commit scanner** — blocks a commit when a modified file contains a value matching a known vault secret.
- **Log masking** — known secret values are censored in console output.

## How It Works

1. **Configure** the vault connection in the **Zero-Trust Vault** tool window (provider, project, environment, and access token).
2. **Run** a JVM-based run configuration as usual.
3. The plugin **intercepts** execution and opens a cancelable *"Fetching Zero-Trust Secrets"* progress dialog.
4. It **downloads secrets** from your vault (the HTTP client retries up to 3 times on a failed response). On persistent failure it shows a dialog offering **Retry**, **Continue Without Secrets**, or **Cancel Execution**.
5. Secrets are **injected** as environment variables into the process and held in an in-memory cache (used for log masking).
6. When the last run process **terminates**, the in-memory cache is cleared.

## Configuration

**Settings → Tools → Zero-Trust Secret Guardian**

| Setting | Default | Description |
|---------|---------|-------------|
| Vault provider | `Infisical` | Vault service — `Infisical` or `Doppler`. |
| Vault URL | *(empty)* | Optional custom/on-premise base URL; leave blank to use the provider's public API. |
| Vault project | *(empty)* | Project/workspace identifier (Infisical `workspaceId`, Doppler project). |
| Environment | `dev` | Target environment — `dev`, `staging`, or `prod`. |

The **access token** is entered and stored in the tool window (see below), not on this settings page.

## Tool Windows

### Zero-Trust Vault

- **Location:** right panel
- **Content:** a connection form — Vault Provider (Infisical/Doppler), Custom Base URL (optional), Access Token, Project ID/Config, and Environment (dev/staging/prod) — plus a **Save & Test Connection** button and a live status indicator.
- **Status colors:**

| Color | Meaning |
|-------|---------|
| 🟢 Green | Connected — shows the number of secrets found. |
| 🟠 Orange | Connected, but no secrets found. |
| 🔴 Red | Connection error (message shown). |

The access token is saved to the JetBrains Credential Store (PasswordSafe) under the service name `ZeroTrustSecretGuardian/vault-token`.

## Log Masking

Console output of run configurations is filtered automatically while secrets are cached:

- Only cached secret values of **5 characters or longer** are masked.
- Common values are never masked: `true`, `false`, `null`, `undefined`, `dev`, `prod`, `staging`, `test`, `local`, and single digits `0`–`9`.
- Matches are replaced with `********`.

Masking is active only while secrets are cached, i.e. after a run injects them and until the last process terminates.

## Pre-Commit Scanner

Integrated into the commit flow, this guardrail runs before every commit:

1. Collects known secret values (from the in-memory cache, or fetched from the vault if a token is configured); only values longer than 3 characters are checked.
2. Scans the modified files in the commit, skipping directories and `.jar`/`.class` files.
3. If a file's contents contain a known secret, shows a warning dialog with two options:
   - **Review Commit** — cancels the commit so you can remove the secret.
   - **Commit Anyway (Unsafe)** — proceeds with the commit.

If no secrets are known or none are found, the commit proceeds normally.

## Supported Vaults

| Vault | Endpoint | Auth |
|-------|----------|------|
| **Infisical** | `https://app.infisical.com/api/v3/secrets/raw` | Bearer token |
| **Doppler** | `https://api.doppler.com/v3/configs/config/secrets/download` | Bearer token |
| **Custom** | Your own base URL (override via *Vault URL*) | Bearer token |

## FAQ

**Q: Are secrets ever written to disk?**
A: No. Fetched secrets are held only in an in-memory cache and are cleared when the last run process terminates. The access token is stored in the JetBrains Credential Store, never as plaintext.

**Q: What happens if the vault is unreachable?**
A: The HTTP client retries up to 3 times. If it still fails, a dialog lets you Retry, Continue Without Secrets, or Cancel Execution.

**Q: Can I use both Infisical and Doppler at once?**
A: One provider per project. Switch it in the tool window or in Settings → Tools → Zero-Trust Secret Guardian.

**Q: Which run configurations get secrets injected?**
A: JVM-based run configurations — secrets are added to the launched process's environment variables, so any code that reads env vars can consume them.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
