# VulnSpeed — Fast Regex SAST

> Fast, low-noise pattern-based security scanning in the editor and in CI.

**Free & open source** — source: https://github.com/JirakJ/vulnspeed-plugin (Apache-2.0); contributions welcome.
Current version: **2026.10.0**.

## Overview

VulnSpeed is a lightweight static application security testing (SAST) plugin. It runs a curated set of line-level
regex rules, each scoped to the languages and file types where it is meaningful, highlights findings as you type,
and attaches a fix suggestion with CWE / OWASP references to every finding. It is a pattern scanner: it does not
do data-flow or taint analysis, so it reports what a single line (plus a little file context) proves.

Results can be exported as SARIF, a CycloneDX SBOM, findings JSON or a shareable HTML report, snapshotted into a
baseline to track regressions, and checked in CI with the standalone `vulnspeed-cli-<version>.jar`.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"VulnSpeed"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+. Real-time highlighting in Kotlin requires the Kotlin plugin.

## Features

### Detection
- **84 precise rules + 12 secret rules** — SQL / NoSQL / OS command / code / template / LDAP / XPath injection, XSS,
  SSRF, open redirect, path traversal and zip / tar slip, unsafe deserialization, XXE, weak hashes / ciphers / TLS,
  JWT signature verification, insecure randomness for tokens, CSRF / CORS / cookie misconfiguration, container,
  Kubernetes, Compose and IAM misconfiguration, unbounded C string functions and format strings
- Every rule carries a CWE id and an OWASP Top 10 (2021) category
- Secrets: 12 vendor-specific rules — AWS, GitHub, GitLab, Slack, Stripe, Google, SendGrid, Twilio, npm tokens,
  private-key blocks, JWTs and credentials in URLs (CWE-798)

### Precision (2026.10.0)
- Rules run only on their languages / file types (Docker rules on Dockerfiles, Spring rules on Java / Kotlin and
  Spring config, …) and match a concrete API or syntax, never a bare keyword
- Comment lines, block comments, KDoc / Javadoc, Python docstrings and lines over 1,000 characters (minified code)
  are skipped — except by the secret rules
- Some rules need file context (e.g. LDAP injection only in files that use LDAP) or are skipped when the file shows
  the hardening (e.g. XXE once DOCTYPEs are disabled)
- Credential, TLS-verification, randomness, CSRF, cookie, debug-mode, plaintext-transport and DOM-XSS rules skip test
  sources (`src/test/`, `tests/`, `*Test.kt`, `test_*.py`, `*_test.go`, `*.spec.ts`, …)
- One finding per rule per line; same-CWE findings on one line keep only the most severe
- Every rule has positive and negative test samples

Findings before → after the 2026.10.0 overhaul (CLI defaults):

| Project | 2026.9.2 | 2026.10.0 |
|---|---:|---:|
| VulnSpeed's own production code | 850 | 0 |
| spring-projects/spring-petclinic | 205 | 4 |
| expressjs/express | 1,104 | 2 |
| pallets/flask | 1,507 | 1 |
| we45/Vulnerable-Flask-App (intentionally vulnerable) | 385 | 9 |
| OWASP/NodeGoat (intentionally vulnerable) | 377 | 9 |

On the two intentionally vulnerable apps all ten planted issues checked are reported (2026.9.2: three).

### Remediation & workflow
- Fix suggestion with example code and OWASP / CWE references on every finding (applied by you — there is no auto-fix)
- Inline suppression: `// vulnspeed-ignore` (same line or the comment line directly above),
  `// vulnspeed-ignore: RULE_ID, RULE_ID`, or `vulnspeed-ignore-file` within the first five lines
- On-demand file scan, project scan and optional scan on save
- VulnSpeed tool window with the findings list and statistics
- Report export: SARIF 2.1.0, CycloneDX 1.5 SBOM, findings JSON and self-contained HTML

### CI/CD
- `vulnspeed-cli-<version>.jar` (attached to every GitHub release, Java 17+): `scan` to findings JSON / SARIF,
  `baseline --create|--compare` and `enrich`, with exit code `2` when a `--fail-on` policy trips
- Security baseline: snapshot accepted findings into `.vulnspeed-baseline.json` and fail only on new regressions
- CVE enrichment from OSV.dev and NVD for findings that reference CVE ids. Built-in rules detect code patterns, not
  vulnerable dependency versions, so they carry CWE ids only and pass through enrichment unchanged

## Command-Line Scanner

Each [GitHub release](https://github.com/JirakJ/vulnspeed-plugin/releases) includes a self-contained
`vulnspeed-cli-<version>.jar` next to the plugin zip. It needs only a Java 17+ runtime — no IDE and no
build-tool plugin — and runs the same rules as the plugin with the same skip rules: the 1000 KB max file
size, `vulnspeed-ignore` comments, and the same skipped directories and minified bundles (see Configuration).

```bash
java -jar vulnspeed-cli.jar scan --project=. \
  --out-json=build/vulnspeed/findings.json \
  --out-sarif=build/vulnspeed/vulnspeed.sarif \
  --fail-on=severity:HIGH
```

| Command | Purpose |
|---------|---------|
| `scan --project=<dir>` | Scan a directory; `--out-json` / `--out-sarif` write findings JSON and SARIF 2.1.0; `--fail-on=severity:<LEVEL>` gates the build; `--max-file-size-kb` and `--max-files` (default 1000) tune limits |
| `baseline --create` / `--compare` | Create `.vulnspeed-baseline.json` from findings JSON, or compare against it (`--fail-on=regression` or `severity:<LEVEL>`, Markdown or JSON diff) |
| `enrich --findings=<file>` | Add OSV.dev / NVD metadata (`--offline`, `--cache-dir`, `--fail-on-severity`) |
| `version` | Print the CLI version |

Exit codes: `0` success, `1` bad arguments or I/O error, `2` the fail-on policy was triggered. Typical CI
use: download the jar from the release, run `scan`, upload the SARIF file to GitHub Code Scanning and run
`baseline --compare` against the committed baseline. The project README has complete GitHub Actions
workflows.

## Configuration

VulnSpeed has an application-level and a project-level settings page, both under **Settings → Tools → VulnSpeed**.

| Setting | Scope | Default | Description |
|---------|-------|---------|-------------|
| Enable real-time scanning | IDE | On | As-you-type editor highlighting; manual scans keep working when off |
| Max file size (KB) | IDE | 1000 | Larger files are skipped by highlighting, Scan File, Scan Project and scan on save |
| Scan changed file on save | Project | Off | Scan a supported file whenever it is saved |

Project scans and the CLI skip hidden (dot) directories, `node_modules`, `bower_components`, `vendor`, `build`,
`dist`, `target`, `out`, `__pycache__`, `venv`, `site-packages` and minified bundles (`*.min.js`, `*.bundle.js`).
VulnSpeed collects no telemetry; the only network access is the opt-in CVE enrichment.

## Tool Windows

### VulnSpeed
- **Location:** Bottom panel
- **Content:** Vulnerability list and scan statistics

## Actions

Every action is available from the **Tools → VulnSpeed** menu; the two scan actions also appear in context menus.

| Action | Location | Description |
|--------|----------|-------------|
| Scan File with VulnSpeed | Editor right-click; Tools → VulnSpeed | Scan the current file |
| Scan Project with VulnSpeed | Project view right-click; Tools → VulnSpeed | Scan the entire project |
| Export SARIF Report | Tools → VulnSpeed | Export the latest results as SARIF 2.1.0 (GitHub Code Scanning / GitLab SAST) |
| Export HTML Report | Tools → VulnSpeed | Export the latest results as a self-contained HTML report |
| Export Findings JSON | Tools → VulnSpeed | Export the latest results in the format the CLI `baseline` / `enrich` commands read |
| Export CycloneDX SBOM | Tools → VulnSpeed | Export a CycloneDX 1.5 SBOM for Dependency-Track / Sonatype / FOSSA |
| Create Security Baseline | Tools → VulnSpeed | Snapshot current findings as accepted into `.vulnspeed-baseline.json` |
| Compare Against Security Baseline | Tools → VulnSpeed | Differential scan against the baseline to surface regressions |
| Enrich Vulnerabilities (OSV / NVD) | Tools → VulnSpeed | Add CVSS, CWE and fixed-version metadata for CVE-referencing findings |

## Supported Languages and Files

| Language / file type | Real-time (as-you-type) | Scan File / Project / CLI |
|----------------------|:-----------------------:|:-------------------------:|
| Java | Yes | Yes |
| Kotlin | Yes (Kotlin plugin) | Yes |
| Python | Yes | Yes |
| JavaScript (`.js .mjs .cjs .jsx`) | Yes | Yes |
| TypeScript (`.ts .mts .cts .tsx`) | Yes | Yes |
| Go | — | Yes |
| C/C++ | — | Yes |
| Swift | — | Yes |
| Rust | — | Secret and generic credential rules only |
| Dockerfile | — | Yes |
| YAML (Kubernetes, Compose, CloudFormation, Spring) | — | Yes |
| `.properties` (Spring) | — | Yes |

The full rule catalogue (id, severity, CWE, file types) is in the
[plugin README](https://github.com/JirakJ/vulnspeed-plugin#rules--precision).

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
