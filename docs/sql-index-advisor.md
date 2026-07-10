# SQL Index Advisor

> Finds missing indexes and SQL anti-patterns across your codebase to keep database queries fast.

## Overview

SQL Index Advisor scans the SQL embedded in your project — string literals, JPA/Spring Data annotations, MyBatis mappers, and `.sql` files — and flags anti-patterns that hurt database performance. Each finding comes with an explanation and, where relevant, a ready-to-use `CREATE INDEX` suggestion. It is aimed at backend and full-stack developers who write SQL by hand or through an ORM and want to catch index-defeating queries before they reach production.

Beyond static rules, the plugin can connect to a live PostgreSQL, MySQL, or SQLite database to run `EXPLAIN` and surface sequential scans in real query plans.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"SQL Index Advisor"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+, JDK 17+. `EXPLAIN` analysis additionally requires access to a PostgreSQL, MySQL, or SQLite database.

## Features

### Free Tier
- 3 core anti-pattern rules: `SELECT *` (SIA001), missing `WHERE` in `UPDATE`/`DELETE` (SIA002), leading wildcard in `LIKE` (SIA003)
- Multi-source SQL extraction from Kotlin/Java literals, JPA annotations, MyBatis XML, and `.sql` files
- Tool window dashboard with findings grouped by file, rule, and severity
- Real-time editor inspections with quick fixes
- Basic `CREATE INDEX` suggestions with one-click copy

### Professional Tier
Everything in Free, plus:
- All 10 anti-pattern rules (see table below)
- `EXPLAIN` plan analysis against PostgreSQL, MySQL, and SQLite, with sequential-scan detection
- Advanced index suggestions, including Flyway migration file generation
- Findings export to JSON and self-contained HTML

## SQL Anti-Pattern Rules

| Rule | Description | Tier |
|------|-------------|------|
| SIA001 | `SELECT *` — blocks index-only scans | Free |
| SIA002 | Missing `WHERE` in `UPDATE`/`DELETE` | Free |
| SIA003 | Leading wildcard in `LIKE` (`'%...'`) | Free |
| SIA004 | Function call on an indexed column in `WHERE` | Pro |
| SIA005 | Implicit type conversion | Pro |
| SIA006 | Missing `LIMIT` with `ORDER BY` | Pro |
| SIA007 | `OR` across different columns | Pro |
| SIA008 | Potential Cartesian product in a join | Pro |
| SIA009 | `NOT IN` with a subquery (slow with NULLs) | Pro |
| SIA010 | `DISTINCT` combined with `ORDER BY` | Pro |

## Configuration

**Settings → Tools → SQL Index Advisor**

| Setting | Default | Description |
|---------|---------|-------------|
| JDBC Connections | — | Database connections used for `EXPLAIN`; passwords are stored via IntelliJ PasswordSafe |
| Sequential Scan Warning Threshold | 10,000 rows | Rows scanned in a plan before a warning is raised |
| Sequential Scan Error Threshold | 100,000 rows | Rows scanned in a plan before an error is raised |
| EXPLAIN Timeout | 5 seconds | Time budget per `EXPLAIN` query (1–60 s) |
| Include Patterns | `**/*.kt`, `**/*.java`, `**/*.sql`, `**/*.xml` | Globs for files to scan |
| Exclude Patterns | `**/target/**`, `**/build/**`, `**/.gradle/**` | Globs for files to skip |

## Tool Windows

### SQL Index Advisor
- **Location:** right panel
- **Content:** a findings tree grouped by file → rule → severity, severity/rule filter chips, and a multi-tab detail view (SQL, Rule, Fix Suggestion, EXPLAIN). Double-click a finding to jump to its source location.

## Inspections

Registered for both Kotlin and Java editors under the **SQL Index Advisor** inspection group.

| Inspection | Level | Description |
|-----------|-------|-------------|
| SQL: Missing WHERE clause | Warning | `UPDATE`/`DELETE` without a `WHERE` clause (SIA002) |
| SQL: Leading wildcard in LIKE | Warning | `LIKE '%...'` patterns that defeat index usage (SIA003) |
| SQL: Function on indexed column in WHERE | Warning | A function wrapping a column in `WHERE`, preventing index use (SIA004) |
| SQL: Potential Cartesian product | Error | A join that may expand into a Cartesian product (SIA008) |

## Actions

All actions are available from the SQL Index Advisor tool window toolbar.

| Action | Location | Description |
|--------|----------|-------------|
| Scan Project | Tool window | Scan the entire project for SQL issues |
| Scan Current File | Tool window | Scan the currently open file |
| Run EXPLAIN | Tool window | Run `EXPLAIN` on the selected SQL |
| Export JSON | Tool window | Export findings as JSON |
| Export HTML | Tool window | Export findings as an HTML report |

## Supported Languages / File Types

- **Kotlin** string literals, including triple-quoted strings
- **Java** string literals
- `@Query`, `@NamedQuery`, and `@NamedNativeQuery` annotations (Spring Data JPA / JPA)
- **MyBatis** XML mapper statements (`<select>`, `<update>`, `<insert>`, `<delete>`)
- Plain **`.sql`** files
- `EXPLAIN` engine dialects: PostgreSQL, MySQL, SQLite

## FAQ

**Do I need a database connection to use the plugin?**
No. Rule detection and editor inspections run entirely on static parsing. A JDBC connection is only needed for `EXPLAIN` plan analysis.

**Which rules are free?**
SIA001 (`SELECT *`), SIA002 (missing `WHERE`), and SIA003 (leading wildcard `LIKE`). The remaining seven rules, the `EXPLAIN` engine, and report export require the Professional tier.

**Where are my database passwords stored?**
In IntelliJ's built-in PasswordSafe — never in plugin settings or project files.

**Can I use findings in CI?**
Yes. Export findings to JSON (stable schema) or HTML for sharing and pipeline integration.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
