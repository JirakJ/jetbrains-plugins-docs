# Migration Safety Net

> Validate database migration files for dangerous operations before they reach production.

## Overview

Migration Safety Net scans your project's database migration files and flags operations that can cause irreversible data loss — `DROP TABLE`, `TRUNCATE`, unbounded `DELETE`/`UPDATE`, destructive schema changes, and more. It targets Flyway-style SQL migrations and also validates their ordering and file naming.

Run a validation on demand and review the results in a dedicated, color-coded dashboard where every finding is ranked by severity and links back to the exact line in the migration file. It is aimed at teams who want a fast, automated safety check before shipping schema changes.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Migration Safety Net"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2+

## Features

Migration Safety Net is freemium: core checks are free, and a Professional subscription unlocks the full rule set.

### Free Tier
- Core destructive-operation detection: `DROP TABLE`, `DROP COLUMN`, `TRUNCATE TABLE`
- Missing-`WHERE` detection on `DELETE` and `UPDATE` statements

### Professional Tier ($5.90/month)
- Full rule set, including `DROP CONSTRAINT`, `RENAME TABLE`, `ALTER COLUMN` type changes, `NOT NULL` without a default, and large data-modification checks
- Flyway migration ordering and naming validation
- Custom safety rules — extra migration paths and custom dangerous-pattern (regex) matching
- Advanced, color-coded violation reporting

## Configuration

**Settings → Tools → Migration Safety Net**

| Setting | Default | Description |
|---------|---------|-------------|
| Destructive-operation checks | Enabled | Individual toggles for `DROP TABLE`, `DROP COLUMN`, `TRUNCATE TABLE`, `DROP CONSTRAINT`, `RENAME TABLE`, `ALTER COLUMN` type change, and `NOT NULL` without default |
| Missing-`WHERE` checks | Enabled | Toggles for `DELETE` without `WHERE` and `UPDATE` without `WHERE` |
| Large data modification detection | Enabled | Flags migrations that modify large volumes of data |
| Migration ordering validation | Enabled | Detects version-ordering problems across migrations |
| Naming convention validation | Enabled | Enforces Flyway migration file-naming conventions |
| Custom Migration Paths | (empty) | Comma-separated extra directories to scan for migration files |
| Custom Dangerous Patterns | (empty) | Comma-separated regular expressions treated as additional violations |

Each safety check is a separate checkbox and is enabled by default.

## Tool Windows

### Migration Safety
- **Location:** bottom panel
- **Content:** A summary bar reporting overall **PASSED**/**FAILED** status and the number of migrations plus critical, warning, and info counts, above a table of violations. Columns are **Severity**, **Check**, **Message**, **Line**, and **Suggestion**. Rows are color-coded by severity; double-click a row to jump to the offending migration file.

Severity levels:

| Severity | Meaning |
|----------|---------|
| 🔴 Critical | Data loss or destructive operation |
| 🟡 Warning | Potentially risky operation |
| 🔵 Info | Informational notice |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Validate Migrations | **Tools** menu | Scans all discovered migration files with the enabled checks and populates the Migration Safety tool window |

## FAQ

**Which files are checked?**
Flyway-style SQL migration files found in your project, plus any directories you add under **Custom Migration Paths**.

**When does validation run?**
On demand. Trigger it from **Tools → Validate Migrations** and read the results in the Migration Safety tool window.

**How do I silence a check I don't want?**
Open **Settings → Tools → Migration Safety Net** and turn off the individual check. You can also add project-specific regexes under **Custom Dangerous Patterns**.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
