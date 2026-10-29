🚀 **Andres Arias**
*Senior Cloud Engineer & Node.js Developer | AWS Solutions Architect | Distributed Systems | Infrastructure Automation*

I'm building a **software factory**: AI agents that turn an approved requirement into a released change, under the same standards, gates, and human-approved merges as any engineer. The standard it is held to is public, in the **[Engineering Excellence Playbook](https://github.com/Drecoder/Engineering_Excellence_Playbook)**.

The rule I hold myself to: **a standard counts only when it is enforced and running**, not when it is written down.

📊 **[The AI Software Factory: architecture overview](software-factory-overview.pdf)** (PDF, 10 slides)

## 🎯 The Goals

Not a bigger factory: **a smaller one that is complete and independently verifiable.** No new features until the first complete release path is proven.

**P0: Prove the trust boundaries**
- Rulesets and required checks on every factory repository, with no bypass.
- Compliance decisions bound to the exact commit, CI run, image digest, and policy version.
- Tampered, expired, mis-scoped, and replayed release tokens rejected; a token consumed exactly once, even under concurrent requests; deploys fail closed when the verifier is down.
- Deploys refused for any image without trusted attestations.
- *Exit:* negative tests show each unauthorized path is rejected, and the paths not yet tested are listed.

**P0: Complete one release lifecycle**
- One change from approved spec through the Builder, the Reviewer, the central gate, a human-approved merge, signed provenance and an SBOM, the compliance decision, and deployment admission.
- The first real workload is the factory's own infrastructure: the agents take Genesis, whose gate is red today, to green.
- *Exit:* a reproducible run with a verified artifact, an auditable decision, and a deploy, with no other way to release.

**P1: Demonstrate the economics**
- Factory-assisted delivery against a documented manual baseline, on comparable tasks with the same acceptance criteria: time from requirement to accepted release, human correction time, escaped defects, cost per accepted change, and recovery time.
- *Exit:* the measurements published with their method, sample size, and limits.

**P2: Earn broader autonomy**
- Larger work only after repeated evidence of reliable behavior, with escalation paths, recovery procedures, and explicit limits on high-risk operations.
- *Exit:* a defined workload handled with measured reliability, bounded authority, and safe recovery.

Progress is scored from evidence against the playbook: a baseline of 61, toward 90.

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
