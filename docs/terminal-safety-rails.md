# Terminal Safety Rails

> Intercept dangerous terminal commands before they execute, with risk-level confirmation dialogs.

## Overview

A single destructive command can ruin your day. Terminal Safety Rails watches commands typed into the IDE's built-in terminal and stops the dangerous ones — `rm -rf`, `kubectl delete`, `terraform destroy`, `DROP DATABASE`, `aws rds delete-db-instance`, and more — before they run. When a command matches, it shows a color-coded dialog that explains the risk in plain English, offers a safer alternative you can copy, and requires explicit approval.

Detection combines 33 built-in pattern rules with 13 heuristic detectors that produce an independent 0–100 risk score. How strictly a match is handled is up to you — from a passive warning to a hard block for production-freeze windows — and every interception can be recorded to a forensic audit log. Safe commands are never touched.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Terminal Safety Rails"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ (any IntelliJ Platform IDE), JDK 17+, Terminal plugin (bundled with JetBrains IDEs)

## Features

### Command interception
- **33 built-in rules** covering filesystem, database/SQL, cloud (AWS/GCP/Azure), Kubernetes, Terraform, Docker, Git, system services, and permissions
- **4 risk levels** — Critical (red), High (orange), Medium (yellow), Low (green)
- **Confirmation dialog** showing the matched command, its risk level and category, and why it is dangerous
- **Zero overhead for safe commands** — only matching patterns trigger a dialog

### Heuristic risk scoring
- **13 detectors** produce a 0–100 score independent of the rules: destructive file ops, privilege escalation, shell injection, remote code execution, credential exposure, network exfiltration, production targets, disk wipes, fork bombs, git history rewrites, privileged package managers, cloud destruction, and unscoped SQL mutations
- **SQL mass-mutation guard** — flags `DELETE FROM` / `UPDATE … SET` with no `WHERE` clause, statement-scoped so a safe query never masks an unscoped one, including statements inside `psql -c` / `mysql -e`

### Understand and remediate
- **Command Explainer** — plain-English description of what the command will do, with dangerous flags decoded (`rm`, `git`, `kubectl`, `docker`, `terraform`, `chmod`, `dd`, `find`, `mkfs`, `kill`, …)
- **Safer Alternatives** — copy-pasteable safer equivalents right in the dialog (`--force-with-lease`, `--dry-run`, backup-first, least-privilege `chmod`, list-before-delete, stop-instead-of-terminate, SELECT-preview, transaction-wrapped mutations)

### Auditing and compliance
- **Incident Audit Log** — forensic per-event record of every intercepted command
- **Audit export** — headless CSV/JSON export for CI pipelines and compliance tooling
- **Shell History Risk Audit** — score your whole shell history (zsh/bash) with a 0–100 safety score, risk distribution, the riskiest commands, and Markdown/JSON/HTML exports
- **Rule effectiveness analytics** — see how often each rule has fired in the project

### Customization
- **Custom rules** — your own patterns with glob or regex matching and configurable risk levels
- **Team-shared rules** — check `.terminal-safety-rules.yaml` into your project root
- **Enable/disable toggle** and configurable enforcement strictness

## Built-in Rules

33 rules, evaluated in order (first match wins) and matched case-insensitively.

| Group | Rules | Highest risk | Example patterns |
|-------|-------|--------------|------------------|
| File System | 6 | Critical | `rm -rf /`, `rm -rf ~`, `rm -rf *` (and `-fr` variants) |
| System / disk | 2 | Critical | `mkfs`, `dd if=` |
| Database (SQL) | 5 | Critical | `DROP TABLE`, `DROP DATABASE`, `TRUNCATE`, `DELETE FROM …;`, `UPDATE … SET` without `WHERE` |
| Cloud (AWS/GCP/Azure) | 8 | Critical | `aws rds delete-db-instance`, `az group delete`, `aws ec2 terminate-instances`, `aws s3 rb`, `gsutil rm -r` |
| Kubernetes | 2 | High | `kubectl delete`, `kubectl apply --force` |
| Terraform | 2 | High | `terraform apply`, `terraform destroy` |
| Docker | 2 | Medium | `docker system prune`, `docker rm -f $(docker ps …)` |
| Git | 3 | Medium | `git push --force`, `git push -f`, `git reset --hard` |
| Permissions | 1 | Medium | `chmod 777` |
| System services | 2 | Medium | `systemctl stop`, `service … stop` |

## Enforcement Modes

The enforcement mode decides what happens when a command matches. Risk is taken as the worse of the matched rule's level and the heuristic score (only heuristic High/Critical intercept on their own).

| Mode | Behavior |
|------|----------|
| Warn only | Never blocks — shows a warning notification and lets the command run. |
| Confirm *(default)* | Shows a confirmation dialog; you decide. |
| Block critical | Auto-blocks Critical findings with no override; confirms everything else. |
| Lockdown | Auto-blocks High and Critical findings; confirms everything else. For production freezes / incident response. |

## Configuration

**Settings → Tools → Terminal Safety Rails**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Terminal Safety Rails | On | Turns command safety analysis and blocking on or off. |
| Enforcement mode | Confirm | Warn only / Confirm / Block critical / Lockdown (see above). |
| Custom Rules | *(empty)* | Editable table of your own rules — see fields below. |

### Custom rule fields

| Field | Description |
|-------|-------------|
| Pattern | Command pattern to match (glob or regex) |
| Risk Level | `CRITICAL`, `HIGH`, `MEDIUM`, or `LOW` |
| Category | `FILESYSTEM`, `KUBERNETES`, `TERRAFORM`, `DOCKER`, `CLOUD`, `GIT`, `DATABASE`, `SYSTEM`, `PERMISSIONS`, or `CUSTOM` |
| Description | Human-readable reason shown in the dialog |
| Regex | When enabled, treat Pattern as a regular expression instead of a glob |

## Actions

Available from the **Tools** menu.

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Command Risk | Tools | Compute a heuristic 0–100 risk score and signal breakdown for a command. |
| Show Command Risk Summary | Tools | Score recent audited commands and show the highest-risk entries. |
| Audit Shell History Risk | Tools | Score every command in your shell history — 0–100 safety score, riskiest commands, safer alternatives. |
| Show Incident Audit Log | Tools | Open the forensic per-event log of intercepted commands (SOC 2 / ISO 27001 / PCI DSS evidence). |
| Export Incident Audit Log | Tools | Headless CSV/JSON export of the audit log for CI and compliance tooling. |
| Show Rule Effectiveness Analytics | Tools | Report of how often each safety rule has fired in this project. |
| Lint Team Rules File | Tools | Validate the team rules file for invalid regex, duplicates, unreachable rules, and conflicts. |

## Team-Shared Rules

Create `.terminal-safety-rules.yaml` in your project root. Rules are merged with your custom rules and the built-in rules.

```yaml
- pattern: "rm -rf /opt/critical"
  risk: CRITICAL          # or: risk_level
  category: FILESYSTEM
  description: "Never wipe the critical mount"
  regex: false            # or: is_regex
```

Only `pattern` is required. Unknown or missing `risk`/`category` values fall back to `MEDIUM` / `CUSTOM`.

## Rule Matching

1. Custom rules are evaluated before built-in rules.
2. Rules are checked in order and the **first match wins**.
3. Patterns are globs (`*`, `?`) unless the rule enables regex.
4. Matching is **case-insensitive**.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
