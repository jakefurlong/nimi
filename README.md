# Nimi

> Hands-on Kubernetes practice platform. Live cluster scenarios, cert prep for the full Golden Kubestronaut path, and zero AI API dependency. Self-hosted on your laptop or homelab.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](LICENSE)
[![Status](https://img.shields.io/badge/status-under%20development-orange)](#status)

---

## What is Nimi?

Nimi is a self-hosted Kubernetes learning platform that runs inside your own cluster. Two modes, one install:

**Live cluster** — Nimi deploys scenarios directly into your cluster. It breaks things on purpose, asks you to build things from spec, and verifies your work automatically with `kubectl`. No simulated environments — real resources, real commands, real feedback.

**Cert study** — Structured knowledge prep for every certification on the [Golden Kubestronaut path](https://training.linuxfoundation.org/resources/kubestronaut-program/), with spaced repetition, per-domain readiness scoring, and content grounded in official documentation.

Both modes work fully offline after install. Content syncs automatically from this repo in the background when internet is available.

---

## Status

🚧 **Under active development — not yet ready for use.**

Watch this repo or check [Releases](https://github.com/jakefurlong/nimi/releases) for the first version.

---

## Certifications

Nimi covers all 16 certifications on the Golden Kubestronaut path:

| Tier | Certifications |
|------|---------------|
| Kubestronaut | KCNA · KCSA · CKA · CKAD · CKS |
| Golden path | LFCS · PCA · ICA · CCA · CAPA · CGOA · CBA · OTCA · KCA · CNPA · CNPE |

---

## Quick start *(coming in v1)*

Download the `nimi` CLI from [Releases](https://github.com/jakefurlong/nimi/releases) for your platform, then:

```bash
nimi install
```

That's it. The CLI runs preflight checks, installs Nimi into your current `kubectl` context, and prints the URL with a QR code you can scan from your phone.

**Requirements:** `kubectl` pointing at a local test cluster (minikube, kind, or k3s) and `helm` v3+.

> ⚠️ **Destructive by design.** Nimi creates, modifies, and deletes real Kubernetes resources. Only use it against a local test cluster. Never point it at a work or production cluster.

### CLI commands

```
nimi install      # preflight + install
nimi check        # preflight checks only, no install
nimi upgrade      # rolling upgrade, no downtime
nimi status       # cluster connection, version, content sync state
nimi uninstall    # remove Nimi and clean up
```

---

## Features

- **Live cluster scenarios** — break-and-fix, build-it, and answer-it tasks verified against your real cluster
- **Cert study** — spaced repetition (SM-2), per-domain readiness scores with decay, 16 cert tracks
- **Profile and badges** — earn badges for domain proficiency and cert readiness, exportable for LinkedIn and other platforms as Open Badges 3.0 credentials
- **Phone study** — scan a QR code from the app to study cert questions on your phone, no separate setup
- **Offline-first** — works with no internet; content syncs automatically in the background when available
- **Zero AI dependency** — no API key required to run; content is pre-generated and ships with the app
- **Auto content updates** — new questions and scenarios sync from this repo automatically, no action needed

---

## How it works

Nimi runs as a Kubernetes Deployment in your cluster. A single `nimi install` command handles everything:

1. Preflight checks (kubectl, helm, cluster reachability, permissions, DNS)
2. Helm install into the `nimi` namespace
3. Waits for the deployment to be ready
4. Prints the access URL and a terminal QR code

The frontend is accessible from any browser on the same network. Live cluster scenarios use a real embedded terminal — your actual `kubectl` commands, your actual cluster state.

---

## Contributing

Not yet open for contributions — the initial architecture is still being established.

Once v1 ships, contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for how to add scenarios, submit question corrections, and run tests locally.

---

## License

Apache 2.0 — see [LICENSE](LICENSE).
