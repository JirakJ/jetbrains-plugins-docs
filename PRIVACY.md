# Privacy Policy — Free & Open-Source JetBrains Plugins by Jakub Jirák

**Last updated:** 2026-11-13

This policy covers the 28 free, open-source (Apache-2.0) JetBrains plugins listed
[below](#per-plugin-details). Every statement here was checked against the source code on
the `main` branch of each plugin's public GitHub repository, which you can read yourself.

## Summary

- **Open source.** Each plugin's full source code is public on GitHub (links below), so you
  can check everything this page says.
- **No telemetry, no analytics, no crash reporting.** No plugin collects usage statistics or
  sends diagnostic data anywhere.
- **No accounts, no licence checks.** The plugins are free and need no sign-up or
  activation.
- **Your data stays on your machine** unless a section below says otherwise. Most plugins
  make **no network connections at all**.
- **The vendor receives nothing.** No plugin sends data to the author or to any server the
  author runs. A few plugins contact third-party services, but only when you use the
  feature that needs them (see the per-plugin sections). Those services' own privacy
  policies apply to those requests.
- **JetBrains Marketplace.** Installing and updating plugins goes through the IDE and the
  JetBrains Marketplace, which have their own privacy policy:
  <https://www.jetbrains.com/legal/docs/privacy/privacy/>. The author does not get personal
  data about you from those downloads.

## Behaviour shared by all plugins

- **Settings** are stored by the IDE as XML files in the IDE configuration directory
  (application-level) or in the project's `.idea/` directory or workspace file
  (project-level). They never leave your machine except through the IDE's own Settings
  Sync, if you have it turned on.
- **Feedback reminder.** About 7 days after first use, each plugin shows one notification
  asking for feedback. It stores only the date of first use and whether the notification
  was shown or dismissed. Nothing is sent. If you click *Send Feedback*, your mail client
  opens with a draft to `feedback@jakubjirak.com`. If you click *Rate on Marketplace*, your
  browser opens the plugin's Marketplace review page. Nothing happens unless you click.
- **External processes** that some plugins start (for example `git`, `kubectl`, `nvcc`)
  run locally on your machine with your user permissions. They are listed per plugin.
- **Files written into your project** (reports, baselines, config files) are listed per
  plugin. They are ordinary files that you control, and you choose whether to commit them.

## Removing data

Uninstall the plugin. Then, if you want, delete its XML file from the IDE configuration
directory and any project files listed in its section below.

## Contact

Please report questions or concerns about privacy as an issue in the GitHub repository of
the plugin concerned (`https://github.com/JirakJ/<repository>/issues`). Each section below
links to the right one.

## Changes

This document is versioned in
[JirakJ/jetbrains-plugins-docs](https://github.com/JirakJ/jetbrains-plugins-docs). Its Git
history shows every change.

---

## Per-plugin details

Plugins are listed by repository name. The anchor of each section is the repository name,
e.g. `PRIVACY.md#vulnspeed-plugin`.

### Plugins that make network connections

| Plugin | Endpoint | What is sent | When |
|---|---|---|---|
| [VulnSpeed](#vulnspeed-plugin) | `api.osv.dev`, `services.nvd.nist.gov` | CVE identifiers from findings | Only when you run *Enrich Vulnerabilities with CVE Metadata* |
| [Zero-Trust Enterprise Secret Guardian](#zero-trust-secret-guardian) | Doppler (`api.doppler.com`) or Infisical (`app.infisical.com`), or a custom URL you set | Your vault access token, project/workspace ID and environment name | Before a run and during the pre-commit check, only once you have entered a token |
| [SeleniumIQ](#selenium-iq-plugin) | The page URL you enter | One HTTP GET request | Only when you enter a URL in *Generate Page Object* |
| [API First & Mocking Studio](#api-first-mocking-studio) | URLs you enter; mock server on `127.0.0.1` | The requests you build | Only when you send a request, open a WebSocket, import a spec from a URL or start the mock server |

All other plugins make no network connections.

---

<a id="api-contract-guard"></a>
### Kei - API Contract Testing (`api-contract-guard`)

- **Network:** None. OpenAPI/Swagger contracts are parsed from project files with external
  `$ref` resolution turned off.
- **External processes:** None.
- **Local data:** project settings in `.idea/kei.xml`.
- **Issues:** <https://github.com/JirakJ/api-contract-guard/issues>

<a id="api-first-mocking-studio"></a>
### API First & Mocking Studio (`api-first-mocking-studio`)

- **Network:** Yes. Every connection is one you start yourself:
  - *HTTP client:* sends the request you build (URL, method, headers, body, cookies) to the
    URL you enter, and only when you click Send.
  - *WebSocket client:* connects to the `ws://`/`wss://` URL you enter when you click
    Connect.
  - *Import OpenAPI from a URL or file:* the spec is read from where you point it. Remote
    `$ref`s inside the spec are fetched from their URLs.
  - *Mock server:* when you start it, it listens on `127.0.0.1` (loopback only) on the
    port set in Settings. Other machines cannot reach it.
  - Nothing is sent anywhere else.
- **External processes:** None.
- **Local data:** request history, collections, environments and variables (including any
  tokens you put into them) are stored in project settings (`api-first-studio.xml`,
  `api-first-plugin-settings.xml`). Responses you save go to files you choose.
- **Issues:** <https://github.com/JirakJ/api-first-mocking-studio/issues>

<a id="architecture-breadcrumbs"></a>
### Architecture Breadcrumbs (`architecture-breadcrumbs`)

- **Network:** None.
- **External processes:** None.
- **Local data:** breadcrumbs in `.arch-breadcrumbs.json` in the project root. Settings
  are in `archBreadcrumbsSettings.xml`.
- **Issues:** <https://github.com/JirakJ/architecture-breadcrumbs/issues>

<a id="branch-health-dashboard"></a>
### Branch Health Dashboard (`branch-health-dashboard`)

- **Network:** None. The plugin never fetches or pushes. It reads only local refs,
  including remote-tracking branches that are already fetched.
- **External processes:** `git` (`branch`, `rev-list`, `diff`) through the IDE's Git
  integration. `git branch -d` runs only when you confirm a cleanup.
- **Local data:** settings in `branchHealthSettings.xml`.
- **Issues:** <https://github.com/JirakJ/branch-health-dashboard/issues>

<a id="dead-code-drift-radar"></a>
### Dead Code & Drift Radar (`dead-code-drift-radar`)

- **Network:** None.
- **External processes:** `git log` per scanned file, to read commit dates and the number
  of distinct author e-mails. Results are only used locally to calculate the score.
- **Local data:** settings in `deadCodeRadarSettings.xml`.
- **Issues:** <https://github.com/JirakJ/dead-code-drift-radar/issues>

<a id="dependency-license-lens"></a>
### Dependency License Lens (`dependency-license-lens`)

- **Network:** None. Licences come from a database built into the plugin and from your
  build files. No package registry is queried.
- **External processes:** None.
- **Local data:** settings and licence policy in `licenseLensSettings.xml`.
- **Issues:** <https://github.com/JirakJ/dependency-license-lens/issues>

<a id="docstring-freshness-monitor"></a>
### Docstring Freshness Monitor (`docstring-freshness-monitor`)

- **Network:** None.
- **External processes:** `git log` through the IDE's Git integration.
- **Local data:** settings in `docFreshnessSettings.xml`.
- **Issues:** <https://github.com/JirakJ/docstring-freshness-monitor/issues>

<a id="flaky-test-detector"></a>
### Flaky Test Detector (`flaky-test-detector`)

- **Network:** None.
- **External processes:** None. The plugin only watches test runs you start in the IDE.
- **Local data:** test-run history (test names and pass/fail outcomes) in the project
  workspace file. Settings are in `flakyTestDetectorSettings.xml`.
- **Issues:** <https://github.com/JirakJ/flaky-test-detector/issues>

<a id="git-aware-dev-journal"></a>
### Git-Aware Dev Journal (`git-aware-dev-journal`)

- **Network:** None.
- **External processes:** None. It reads the current branch from the IDE's Git
  integration.
- **Local data:** journal entries in `.dev-journal/entries.json` in the project (the path
  can be changed in Settings). Settings are in `devJournalSettings.xml`.
- **Issues:** <https://github.com/JirakJ/git-aware-dev-journal/issues>

<a id="git-workflow-enforcer"></a>
### Git Workflow Enforcer (`git-workflow-enforcer`)

- **Network:** None.
- **External processes:** None. It reads repository state from the IDE's Git integration.
- **Local data:** reads the team rules file `.git-workflow.yaml` from the project. Settings
  are in `gitWorkflowSettings.xml`.
- **Issues:** <https://github.com/JirakJ/git-workflow-enforcer/issues>

<a id="gpu-dev-accelerator-ultimate"></a>
### GPU Dev Accelerator Ultimate (`gpu-dev-accelerator-ultimate`)

- **Network:** None.
- **External processes:** only when you trigger the matching action: `nvcc` (compile, PTX),
  `nvidia-smi` and `system_profiler SPDisplaysDataType` (GPU info), `ncu`/`nvprof`
  (profile) and `compute-sanitizer`/`cuda-memcheck` (memory check).
- **Local data:** settings (tool paths) in `com-jakubjirak-gpudev-ultimate.xml`. Compiler
  output goes next to your source files.
- **Issues:** <https://github.com/JirakJ/gpu-dev-accelerator-ultimate/issues>

<a id="intel-dpcpp-plugin"></a>
### Intel DPC++ Support (`intel-dpcpp-plugin`)

- **Network:** None. The *Open Documentation* and *Show Examples* actions open Intel's
  documentation and the oneAPI samples on GitHub in your browser, and only when you choose
  them.
- **External processes:** None.
- **Local data:** only the feedback-reminder state.
- **Issues:** <https://github.com/JirakJ/intel-dpcpp-plugin/issues>

<a id="kubernetes-context-guard"></a>
### KubeContext Safety (`kubernetes-context-guard`)

- **Network:** None. The plugin never contacts a Kubernetes API server.
- **External processes:** `kubectl config use-context <name>`, only when you switch
  context from the plugin. This changes only your local kubeconfig.
- **Local data:** reads your kubeconfig (`KUBECONFIG`, `~/.kube/config` or the path you
  set) to get context, cluster and namespace names, and an optional `.k8s-guard.yaml` from
  the project. It does not copy or send any credentials in the kubeconfig. Settings are in
  `k8sGuardSettings.xml`.
- **Issues:** <https://github.com/JirakJ/kubernetes-context-guard/issues>

<a id="local-secrets-tripwire"></a>
### Local Secrets Tripwire (`local-secrets-tripwire`)

- **Network:** None. All secret detection runs locally, and matches are never sent
  anywhere.
- **External processes:** None. The optional pre-commit check uses the IDE's commit
  dialog.
- **Local data:** reads an optional `.secrets-allowlist` from the project. Settings are in
  `secretsTripwireSettings.xml`.
- **Issues:** <https://github.com/JirakJ/local-secrets-tripwire/issues>

<a id="logparser-premium-plugin"></a>
### LogParser Pro (`logparser-premium-plugin`)

- **Network:** None.
- **External processes:** None.
- **Local data:** settings in `com-jakubjirak-logparser-pro.xml`. Exported and redacted
  logs go to files you choose.
- **Issues:** <https://github.com/JirakJ/logparser-premium-plugin/issues>

<a id="metal-gpu-monitor-plugin"></a>
### Metal GPU Monitor (`metal-gpu-monitor-plugin`)

- **Network:** None.
- **External processes:** `sysctl -n hw.memsize` (total RAM). GPU metrics are read locally
  from macOS IOKit.
- **Local data:** metric history is kept in memory only (5 minutes by default). Exports go
  to files you choose. Settings are in `gpu-monitor-settings.xml`.
- **Issues:** <https://github.com/JirakJ/metal-gpu-monitor-plugin/issues>

<a id="metal-shader-support-plugin"></a>
### Metal Shader Support (`metal-shader-support-plugin`)

- **Network:** None.
- **External processes:** None.
- **Local data:** the transpiler writes its output file next to the source shader.
- **Issues:** <https://github.com/JirakJ/metal-shader-support-plugin/issues>

<a id="obfuscate-guard"></a>
### ObfuscateGuard (`obfuscate-guard`)

- **Network:** None from the plugin.
- **External processes:** the obfuscation run configuration starts your project's own
  build (e.g. `./gradlew` with ProGuard/R8), only when you run it. Your build tool may
  download dependencies as usual.
- **Local data:** writes `obfuscateguard-policy.json`, keep-rule files and CI templates into
  the project when you ask it to. Settings are in `ObfuscateGuardSettings.xml`.
- **Issues:** <https://github.com/JirakJ/obfuscate-guard/issues>

<a id="obsidian-bridge"></a>
### Obsidian IDE Bridge (`obsidian-bridge`)

- **Network:** None. The plugin works directly on the vault folder on disk and does not
  use the Obsidian app or any REST API.
- **External processes:** None.
- **Local data:** indexes the vault folder you configure, and creates notes there when you
  ask. Settings (vault path) are in `obsidian-bridge.xml`.
- **Issues:** <https://github.com/JirakJ/obsidian-bridge/issues>

<a id="robot-framework-plugin"></a>
### Robot Framework (`robot-framework-plugin`)

- **Network:** None from the plugin.
- **External processes:** `<python> -m robot …` when you run a Robot Framework run
  configuration. Your tests do whatever they are written to do.
- **Local data:** settings in `robot-framework-settings.xml`.
- **Issues:** <https://github.com/JirakJ/robot-framework-plugin/issues>

<a id="run-config-drift-detector"></a>
### Run Config Drift Detector (`run-config-drift-detector`)

- **Network:** None.
- **External processes:** None.
- **Local data:** reads `.run-requirements.yaml` from the project. Settings are in
  `DriftDetectorSettings.xml`.
- **Issues:** <https://github.com/JirakJ/run-config-drift-detector/issues>

<a id="selenium-iq-plugin"></a>
### SeleniumIQ - Selenium Test Automation Toolkit (`selenium-iq-plugin`)

- **Network:** Only in *Generate Page Object*, and only if you enter a page URL. The plugin
  then sends one HTTP GET request to that URL (User-Agent
  `SeleniumIQ-PageObjectGenerator/1.0`) to read form fields and links. If you leave the
  URL empty, nothing is fetched. The cloud-grid (BrowserStack, Sauce Labs, LambdaTest) and
  Jira/TestRail generators only produce source code. The plugin never connects to those
  services, and credentials you type into a generator are written only into the generated
  code.
- **External processes:** None.
- **Local data:** generated classes are written into your project.
- **Issues:** <https://github.com/JirakJ/selenium-iq-plugin/issues>

<a id="slow-build-hotspots"></a>
### Slow Build Hotspots (`slow-build-hotspots`)

- **Network:** None.
- **External processes:** None. The plugin reads the HTML profile reports that Gradle
  writes when you build with `--profile`.
- **Local data:** build-timing history in `buildHotspotsHistory.xml` (stored only on this
  machine, never roamed). Settings are in `buildHotspotsSettings.xml`.
- **Issues:** <https://github.com/JirakJ/slow-build-hotspots/issues>

<a id="structurizr-dsl-plugin"></a>
### Structurizr DSL (`structurizr-dsl-plugin`)

- **Network:** None. The live preview is rendered from local HTML in the IDE's embedded
  browser (JCEF) without loading remote resources, and remote `!include` URLs are not
  fetched.
- **External processes:** the Structurizr CLI (`structurizr-cli export …`), only if you
  have installed it and use an export that needs it.
- **Local data:** settings in `structurizr.xml` and the project workspace file. Exported
  diagrams go to paths you choose.
- **Issues:** <https://github.com/JirakJ/structurizr-dsl-plugin/issues>

<a id="technical-debt-accountant"></a>
### Technical Debt Accountant (`technical-debt-accountant`)

- **Network:** None.
- **External processes:** None.
- **Local data:** debt inventory in `.tech-debt/inventory.json` and an optional SLA policy
  in `.debt-sla.json` in the project. Reports (digest, forecast, sprint plan, SLA report,
  export) go to files you choose. Settings are in `debtAccountantSettings.xml`.
- **Issues:** <https://github.com/JirakJ/technical-debt-accountant/issues>

<a id="terminal-safety-rails"></a>
### Terminal Safety Rails (`terminal-safety-rails`)

- **Network:** None. The "rule analytics" feature is a local counter of rule matches. It
  is not telemetry and is never sent anywhere.
- **External processes:** None. The plugin inspects commands typed into the IDE terminal
  but does not run them.
- **Local data:**
  - Audit log under `.idea/terminal-safety/`. Each entry holds the command (obvious
    secrets masked), the matched rule, your OS user name and host name.
  - Rule statistics in `terminalSafetyRuleAnalytics.xml`.
  - *Audit Shell History* reads your shell history file (`~/.zsh_history`,
    `~/.bash_history`), only when you run it.
  - Settings are in `terminalSafetySettings.xml`.
- **Issues:** <https://github.com/JirakJ/terminal-safety-rails/issues>

<a id="vulnspeed-plugin"></a>
### VulnSpeed - Fast Regex SAST (`vulnspeed-plugin`)

- **Network:** Only in *Enrich Vulnerabilities with CVE Metadata* (Tools → VulnSpeed) and
  in the optional enrichment command-line tool. For each finding that carries a CVE ID,
  the plugin sends an HTTPS GET request with that ID to:
  - `https://api.osv.dev/v1/vulns/<id>` (OSV.dev, Google), and/or
  - `https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=<id>` (NVD, NIST).

  The User-Agent is `VulnSpeed/<version>`. If the `NVD_API_KEY` environment variable is
  set, it is sent to NVD as the `apiKey` header. No source code, file paths or project
  names are sent. Scanning itself (editor, project scan, CLI) is fully offline.
- **External processes:** None.
- **Local data:** CVE metadata cache in `<IDE config>/vulnspeed/cve-cache/`. Without an IDE,
  the CLI uses `~/.vulnspeed/cve-cache/`. An optional baseline `.vulnspeed-baseline.json`
  is saved in the project. Reports (HTML, SARIF, CycloneDX SBOM, JSON) go to files you
  choose. Settings are in `vulnspeed.xml`.
- **Issues:** <https://github.com/JirakJ/vulnspeed-plugin/issues>

<a id="zero-trust-secret-guardian"></a>
### Zero-Trust Enterprise Secret Guardian (`zero-trust-secret-guardian`)

- **Network:** Yes, to the secret vault **you** configure, and only after you have entered
  an access token:
  - **Infisical:** `GET <base>/api/v3/secrets/raw?workspaceId=…&environment=…`. The default
    base is `https://app.infisical.com`.
  - **Doppler:** `GET <base>/v3/configs/config/secrets/download?project=…&config=…`. The
    default base is `https://api.doppler.com`.
  - A custom base URL (e.g. self-hosted Infisical) can be set in Settings.
  - **Sent:** your access token (as `Authorization: Bearer`), the project/workspace ID and
    the environment name.
  - **Received:** the secrets for that environment.
  - **When:** before a run configuration starts (to inject the secrets as environment
    variables), and during the pre-commit check if no secrets are cached from an earlier
    run.
- **External processes:** None of its own. Secrets are passed as environment variables to
  the run you start.
- **Credentials:** the access token is stored in the IDE's secure credential store
  (PasswordSafe: OS keychain or KeePass), not in plain-text settings.
- **Local data:**
  - Fetched secrets are kept **in memory only**, used to mask console output and to warn
    before a commit that contains a vault value. They are never written to disk.
  - Settings (provider, project ID, environment, URL) are in `zeroTrustVault.xml`.
- **Issues:** <https://github.com/JirakJ/zero-trust-secret-guardian/issues>
