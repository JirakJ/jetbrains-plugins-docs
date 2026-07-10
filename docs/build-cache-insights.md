# Build Cache Insights

> Stop waiting for builds. Optimize your cache.

## Overview

Build Cache Insights analyzes Gradle and Maven build cache performance so you can understand where build time goes and reduce it. It parses a build log, classifies every task by how it was resolved (served from cache, up to date, executed, skipped, or failed), and surfaces a color-coded dashboard with cache hit rates, a per-task breakdown, prioritized optimization advice, and build-time trends across your recent builds.

It is aimed at developers and build engineers on Gradle or Maven projects who want to raise their cache hit rate and cut incremental build times without manually combing through build output.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Build Cache Insights"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ (any IDE based on the IntelliJ Platform)

## Features

- **Gradle and Maven log parsing** — Analyze a build log from either tool. The plugin auto-detects the build tool from the log content and falls back to your configured preference when it can't tell.
- **Cache hit/miss analysis** — Every task is classified by outcome: `FROM-CACHE` (cache hit), `UP-TO-DATE`, `EXECUTED`, `SKIPPED`, or `FAILED`.
- **Hit-rate dashboard** — Color-coded summary cards show your cache hit rate at a glance, alongside total tasks, cached count, executed count, and estimated time saved.
- **Task breakdown** — A per-task table lists each task with its outcome and duration.
- **Optimization advice** — Prioritized, actionable suggestions: add caching to never-cached tasks, prioritize slow uncached tasks, stabilize inputs for tasks that are frequently invalidated, and enable the build cache when the overall hit rate is low.
- **Build-time trends** — Once you have analyzed more than one build, the dashboard reports whether builds are trending faster or slower, with average, minimum, and maximum build times.
- **Build history** — Each analysis is stored so trends and repeat-offender tasks can be tracked across builds, up to a configurable retention limit.

## Configuration

Configure the plugin under **Settings → Tools → Build Cache Insights**.

| Setting | Default | Description |
|---------|---------|-------------|
| Max build history | 50 | Number of analyzed build records to retain (1–500). |
| Gradle log path | (empty) | Default path to your Gradle build log. |
| Maven log path | (empty) | Default path to your Maven build log. |
| Auto-analyze builds after completion | Off | Analyze builds automatically once they finish. |

## Tool Windows

### Build Cache

Docked to the bottom of the IDE, the **Build Cache** tool window hosts the analysis dashboard. After you analyze a build it shows:

- **Summary cards** — Cache hit rate (color-coded by how healthy it is), total tasks, cached tasks, executed tasks, and estimated time saved.
- **Task results** — A table of every task with its outcome and duration.
- **Optimization advice** — A table of suggestions with a priority, title, the task it applies to, and a category.
- **Build-time trend** — Trend direction plus average, minimum, and maximum build times (populated once at least two builds have been analyzed).

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Build Cache | **Tools** menu | Choose a Gradle or Maven build log file and analyze its cache performance. Parsing runs in the background; a notification appears when it finishes and results open in the Build Cache tool window. |

## FAQ

**Which build tools are supported?**
Gradle and Maven. The plugin detects the tool from the log — `> Task :` marks a Gradle log and `[INFO] --- ` marks a Maven log — and falls back to your preferred build tool when the format is ambiguous.

**What file do I select when analyzing a build?**
A plain-text (`.txt`) build log. Capture one by redirecting your build output, for example `./gradlew build > build.txt` or `mvn install > build.txt`, then pick that file in the **Analyze Build Cache** dialog.

**What do the task outcomes mean?**
`FROM-CACHE` = served from the build cache (a hit), `UP-TO-DATE` = no work was needed, `EXECUTED` = the task ran in full, `SKIPPED` = the task was skipped, `FAILED` = the task failed.

**Why is the build-time trend empty?**
The trend needs at least two analyzed builds. Analyze another build and the trend, along with average, minimum, and maximum times, will populate.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
