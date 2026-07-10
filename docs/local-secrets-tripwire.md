# Local Secrets Tripwire

> Real-time, fully local detection of API keys, tokens, passwords, and private keys before they reach version control.

## Overview

Local Secrets Tripwire scans your files in real time for hardcoded secrets — API keys, tokens, passwords, and private keys — and flags them as you type. All scanning happens on your machine; nothing is uploaded anywhere.

It runs as a standard IntelliJ code inspection (in the **Security** group) and adds a pre-commit guard that checks staged files when you commit from the IDE, so leaked credentials are caught before they land in a commit.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Local Secrets Tripwire"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, JDK 17+. The bundled Git plugin (Git4Idea) is needed only for the pre-commit guard.

## Features

### Detection engine
- **42 built-in patterns**, including AWS (with temporary keys), GitHub (classic, fine-grained, OAuth, refresh), OpenAI, Anthropic, GitLab, npm, PyPI, Hugging Face, Slack (bot/user/app tokens, webhooks), Stripe (keys and webhook secrets), Twilio, Telegram, DigitalOcean, Shopify, Databricks, Atlassian, Doppler, HashiCorp Vault, Azure Storage, Mailchimp, Firebase, Google, SendGrid, JWTs, private keys (RSA/EC/DSA/OpenSSH/PGP), connection strings, credentials in URLs, and Bearer headers.
- **Shannon entropy analysis** for high-randomness strings — opt-in, with a configurable threshold.
- **Custom regex patterns** for organization-specific secrets (free: up to 10; a paid license lifts the cap).
- Overlapping matches are deduplicated to the single most severe finding.

### Editor integration
- Severity-aware inline highlighting of the exact secret range.
- Quick fixes: add the finding to the allowlist, or suppress it with an inline `tripwire:ignore` comment — straight from the inspection popup.
- Detected values are shown **masked**; the raw secret is never displayed.

### Git integration
- **Pre-commit guard** — when you commit from the IDE, staged files are scanned. If potential secrets are found, a dialog lists them (masked, as `file:line — pattern (masked value)`) and lets you **Commit Anyway** or **Cancel Commit**. It warns; it does not silently block.
- The guard respects the allowlist, your custom patterns, inline `tripwire:ignore` suppressions, and the plugin's enable toggle.

## Configuration

**Settings → Tools → Secrets Tripwire**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Secrets Tripwire | On | Turns real-time secret scanning on or off |
| Pre-commit guard | On | Scans staged files on commit and warns when potential secrets are found |
| Detect high-entropy strings | Off | Flags quoted strings with unusually high randomness even when no known pattern matches |
| Entropy threshold | `4.5` | Shannon entropy cutoff for high-entropy detection; lower values catch more but produce more false positives |
| Custom patterns | *(empty)* | Your own rules — each has a name, regex, severity, and enable toggle (free: up to 10; paid: unlimited) |

### Suppressing false positives
- **Allowlist file** — add substrings of known-safe values to a `.secrets-allowlist` file in the project; matching findings are ignored in the editor and by the pre-commit guard.
- **Inline** — put a `tripwire:ignore` comment on a line to silence findings for that line.

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Secret detection | Warning | Flags hardcoded API keys, tokens, passwords, and private keys in source; grouped under **Security** and enabled by default |

## Licensing

Local Secrets Tripwire is free to use. A paid license unlocks a single capability: **unlimited custom patterns** (the free tier is capped at 10). All built-in patterns, entropy detection, the pre-commit guard, quick fixes, and suppression work without a license.

## FAQ

**Does any of my code or the detected secrets leave my machine?**
No. All scanning is local, and detected values are only ever shown masked.

**Does the pre-commit guard block my commit?**
No — it warns. When it finds potential secrets it shows a dialog with **Commit Anyway** and **Cancel Commit**. It runs when you commit from the IDE and requires the Git plugin to be enabled.

**How do I silence a false positive?**
Add a substring of the value to a `.secrets-allowlist` file, or add a `tripwire:ignore` comment on the line. The inspection's quick fix can do either for you.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
