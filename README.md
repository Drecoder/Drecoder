🚀 **Andres Arias**
*Senior Cloud Engineer & Node.js Developer | AWS Solutions Architect | Distributed Systems | Infrastructure Automation*

I'm building a **software factory**: AI agents that turn an approved requirement into a released change, under the same standards, gates, and human-approved merges as any engineer. The standard it is held to is public, in the **[Engineering Excellence Playbook](https://github.com/Drecoder/Engineering_Excellence_Playbook)**.

The rule I hold myself to: **a standard counts only when it is enforced and running**, not when it is written down.

📊 **[The AI Software Factory: architecture overview](software-factory-overview.pdf)** (PDF, 10 slides)

---

## 📘 The Playbook

The [Engineering Excellence Playbook](https://github.com/Drecoder/Engineering_Excellence_Playbook) is the factory's rulebook. Its enforceable rules (`AGENTS.md`) are vendored into each service repository at a pinned commit, so engineers, coding assistants, and the factory's own agents read the same contract.

- **Standards by zone:** universal, frontend, backend, infrastructure, runbooks, and agents.
- **Contracts as versioned JSON Schemas** with test vectors.
- **Incident records** in post-mortem form for every failure and near miss, each pointing at its evidence.
- **Program increments** that grade the factory against the playbook from evidence, from a baseline of 61 toward a bar of 90.

## 🏭 The Factory

Each repository is a bench with one job. The playbook is public; the benches are private.

| Bench | Job | Status |
| :--- | :--- | :--- |
| Central CI | One reusable gate that every repository calls | Running |
| Builder | Builds a change from an approved spec and opens the pull request | Built, pull-request driven |
| Reviewer | Reviews through lenses (reuse, security, architecture); it advises, people approve | Built, pull-request driven |
| rig | Measures: architecture checks, features, the symbol index | Built |
| Compliance authority | Verifies evidence and issues single-use release tokens | Runs as a CLI; service in progress |
| Notepad | Working memory: a sealed, hash-chained record of every task | Library on local backends |
| Genesis | Governance guardrails and project vending, per cloud | Bootstrap in progress |

## ✅ Running Today

- **One central CI gate**, called by commit SHA from every repository: secret scanning, Trivy, Semgrep, and per-stack lint, type checks, tests, coverage floors, and license policy. One severity rule for every scanner: CRITICAL or CISA KEV blocks, and the gate fails closed.
- **The gate tests itself.** Fixture projects run the real gate on every change to it, and each check is shown to fail on the defect it guards against before it counts. A skipped job is not a pass.
- **Every service ships a container image:** the gate builds it, runs its tests inside it unprivileged with no network, and scans it, and fails a repository that neither builds one nor says why it has none. Vulnerabilities are fixed at their source, not excepted. Services are moving onto this gate version now.
- **Pinned inputs:** images by digest, actions by commit SHA, downloaded tools by checksum, dependencies through committed lockfiles.

## 🔜 In Progress

- **Continuous delivery:** every merge publishes an image by digest with an SBOM, a keyless signature, and SLSA provenance; promotion through human-approved merges; deploys admitted only through a deployment guard and Binary Authorization.
- **The event-driven loop:** every handoff between benches as an event, with an outbox, an inbox, and dead-letter queues.
- **Autonomy by evidence:** a person leaves a step only when the measurements show the step is stable and better without them.
