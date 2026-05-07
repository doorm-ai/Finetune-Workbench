# Finetune-Workbench

> **L2 training workbench — model-agnostic LoRA pipeline with three hard quality gates.**

[![Paper DOI](https://img.shields.io/badge/Paper%20DOI-10.5281%2Fzenodo.20053545-1682d4)](https://doi.org/10.5281/zenodo.20053545)
[![Status](https://img.shields.io/badge/status-pending%20%C2%A711%20gates-orange)](https://github.com/doorm-ai/WorldModel-OS-governance#three-release-gates-per-11-of-the-paper)
[![Last Commit](https://img.shields.io/github/last-commit/doorm-ai/Finetune-Workbench)](https://github.com/doorm-ai/Finetune-Workbench/commits/main)
[![Stars](https://img.shields.io/github/stars/doorm-ai/Finetune-Workbench?style=social)](https://github.com/doorm-ai/Finetune-Workbench/stargazers)
[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0--or--later-blue.svg)](https://www.gnu.org/licenses/agpl-3.0.html)

**Coming soon. Not released yet — by design.**

This is **Finetune Workbench**, the L2 training workbench in the **DOORM WorldModel-OS** architecture: a fully model-agnostic LoRA fine-tuning pipeline that treats data quality as a contract, not a benchmark target.

---

## 🎯 What Finetune-Workbench solves

Most fine-tuning code released today optimizes for a single base model and a single eval. We treat that as architectural debt:

- **Base-model agnostic** — any decoder-class LLM that respects the data-format and `adapter_version` handshake works as the base
- **Five-class data pipeline** — distinct quality lanes (gold / silver / bronze / synthetic / probe) with explicit blend rules
- **Three hard quality gates** — every adapter must pass *before* it gets a version number
- **Bucketed evaluator** — domain-stratified metrics with rollback thresholds, not a single average score

v0 reference base: `Llama-3.2-3B-Instruct` (substitutable, not binding).

---

## 🚀 What's coming (in this repo)

When released, this repository will contain:

| Module | Purpose |
|---|---|
| `data/` | 5-class data pipeline (gold / silver / bronze / synthetic / probe) |
| `train/` | LoRA training entry, config schemas, version pinning |
| `eval/` | Bucketed evaluator with per-bucket rollback thresholds |
| `adapter/` | Output adapter packaging + `adapter_version` handshake |
| `quality_gates/` | The three hard gates: schema · contamination · bucket-spread |

**Hardware target:** single consumer GPU (RTX 3090 / 4090, 24 GB VRAM) — the reproducibility gate is defined against this profile.

---

## 🚦 Release status

| Gate (§11 of paper) | Status |
|---|---|
| Reproducibility (single-GPU 24h reference run) | ⏳ Pending |
| Benchmark (TCM syndrome differentiation + rehabilitation) | ⏳ Pending |
| Real-adoption (MOU or paid deployment) | ⏳ Pending |

All three must pass before this repository goes public. **No code release for demo's sake.**

> See [§11 of the companion paper](https://github.com/doorm-ai/WorldModel-OS-governance#three-release-gates-per-11-of-the-paper) for full gate definitions and falsification criteria.

---

## 🔭 Architecture context

| Tier | Status | Scope | This repo? |
|---|---|---|---|
| **L3** Production artifacts | 🔒 Closed | Production weights, clinical adapters, partner data, device auth keys | No |
| **L2** Finetune Workbench | ⏳ Pending | Training pipeline + three hard quality gates | **← You are here** |
| **L1** Platform skeleton | ⏳ Pending | Gateway · State space · Audit · Redactor · Runtime | Sibling repo |

L2 produces adapters. L1 consumes them. They communicate via a stable `adapter_version` handshake — neither is locked to the other's release schedule.

---

## 📡 Stay updated

- **⭐ Star** this repo to track release
- **👁 Watch → Custom → Releases** for the first public drop notification
- **💬 [Discussions](https://github.com/doorm-ai/Finetune-Workbench/discussions)** for early design feedback
- **📬 [Issues](https://github.com/doorm-ai/Finetune-Workbench/issues)** for post-release bug reports

---

## 📚 Companion artifacts

- 📄 **[Paper + governance docs](https://github.com/doorm-ai/WorldModel-OS-governance)** — DOI [10.5281/zenodo.20053545](https://doi.org/10.5281/zenodo.20053545)
- 🛠 **[WorldModel-OS](https://github.com/doorm-ai/WorldModel-OS)** — L1 platform skeleton (sibling repo)

---

## 💼 Commercial / non-AGPL licensing

For commercial deployment outside AGPL-3.0-or-later terms, partner integrations, or clinical L3 access:

📧 **service@doorm.ai**

DOORM AI PTE. LTD. (UEN 202441729W) · Singapore
