# SpeyTech

**Deterministic and verifiable systems for software and AI.**

For engineers building systems where correctness must be provable.

SpeyTech builds infrastructure for regulated industries where correctness is non-negotiable: deterministic computation (`certifiable-*`), verifiable AI execution and governance (Axioma), and safety-critical system design.

These open-source components underpin commercial systems deployed in regulated environments.

Built in the Scottish Highlands. Patent: UK GB2521625.0 (Murray Deterministic Computing Platform).

---

## Where to Start

- **Understand the system** — [axioma-spec](https://github.com/SpeyTech/axioma-spec)
  Framework specification, determinism contract, and system architecture.

- **See deterministic ML in practice** — [certifiable-inference](https://github.com/SpeyTech/certifiable-inference)
  Run a forward pass and verify bit-identical output.

- **Explore verification** — [axioma-verify](https://github.com/SpeyTech/axioma-verify) · [certifiable-verify](https://github.com/SpeyTech/certifiable-verify)

---

## Axioma

**A verifiable AI execution layer for regulated industries.**

Axioma wraps non-deterministic AI (LLMs, retrieval, agent workflows) inside a cryptographically auditable determinism envelope.

- Every decision is traceable
- Every computation is evidence-committed
- Non-deterministic components are contained behind formal oracle boundaries

Axioma builds upon the `certifiable-*` deterministic computation substrate, adding governance, policy enforcement, and audit capabilities for production AI systems.

**Eight layers · 270 SHALL requirements · 358 tests · Zero failures**
**Bit-identical across x86_64, ARM64, and RISC-V**

| Layer | Concern | Repo | Role |
|-------|---------|------|------|
| L0 | Epistemic containment | [axioma-l0](https://github.com/SpeyTech/axioma-l0) | Pre-admission proxy — ensures no regime-identifying information crosses the model boundary |
| L7 | Accountability | [axioma-governance](https://github.com/SpeyTech/axioma-governance) | Proof-carrying governance and compliance reporting |
| L6 | Truth | [axioma-audit](https://github.com/SpeyTech/axioma-audit) | Cryptographic audit ledger with total ordering |
| L5 | Behaviour | [axioma-agent](https://github.com/SpeyTech/axioma-agent) | Agent totality contracts and health FSM |
| L4 | Admissibility | [axioma-policy](https://github.com/SpeyTech/axioma-policy) | Policy evaluation and operational envelope |
| L3 | Containment | [axioma-oracle](https://github.com/SpeyTech/axioma-oracle) | Oracle Boundary Gateway (LLM containment) |
| L2 | Identity | `certifiable-*` (below) | Deterministic ML computation substrate |
| L1 | Mathematics | libaxilog | DVM arithmetic primitives and fault model |

L0 sits orthogonally to L1–L7. It operates as a pre-admission proxy before L3, curating what the model sees without modifying what L6 records.

Supporting repos: [axioma-spec](https://github.com/SpeyTech/axioma-spec) (specification and SRS documents) · [axioma-verify](https://github.com/SpeyTech/axioma-verify) (verification tooling)

The Axioma Oracle Gateway provides a production deployment surface for regulated AI systems, including EU AI Act Article 9 compliance.

---

## certifiable-*

**The deterministic computation substrate that Axioma builds upon (L2).**

Pure C99. Zero dynamic allocation. Fixed-point arithmetic (Q16.16). Cryptographic audit trails at every stage.

Designed for certification under DO-178C, IEC 62304, ISO 26262, and IEC 61508.

**1,056+ tests passing · 11,840 bench assertions**
**Bit-identical across x86_64, ARM64, and RISC-V**

| Stage | Repo | Tests | What it does |
|-------|------|-------|--------------|
| Data | [certifiable-data](https://github.com/SpeyTech/certifiable-data) | 142 | Deterministic loading, normalisation, shuffling, augmentation |
| Training | [certifiable-training](https://github.com/SpeyTech/certifiable-training) | 223 | Deterministic gradient computation and weight updates |
| Quantisation | [certifiable-quant](https://github.com/SpeyTech/certifiable-quant) | 150 | FP32 → Q16.16 with formal error bounds |
| Deployment | [certifiable-deploy](https://github.com/SpeyTech/certifiable-deploy) | 201 | Cryptographic model packaging and attestation |
| Inference | [certifiable-inference](https://github.com/SpeyTech/certifiable-inference) | 83 | Deterministic forward pass (CNN, MLP) |
| Monitoring | [certifiable-monitor](https://github.com/SpeyTech/certifiable-monitor) | 253 | Runtime drift detection and operational envelope |
| Verification | [certifiable-verify](https://github.com/SpeyTech/certifiable-verify) | 10 suites | Formal verification toolkit |
| Harness | [certifiable-harness](https://github.com/SpeyTech/certifiable-harness) | 4 | End-to-end pipeline integration tests |
| Benchmarks | [certifiable-bench](https://github.com/SpeyTech/certifiable-bench) | 11,840 | Performance characterisation (latency, throughput, WCET) |
| Build | [certifiable-build](https://github.com/SpeyTech/certifiable-build) | — | Deterministic build infrastructure |

**Pipeline:**

```
certifiable-data → certifiable-training → certifiable-quant → certifiable-deploy → certifiable-inference
                                                                                          ↓
                                                                              certifiable-monitor
```

---

## The Book

**C From Scratch: Learn Safety-Critical C the Right Way**

The methodology behind `c-from-scratch` — now as a complete book. Learn to write provably correct C using the Math → Structs → Code approach. Covers closed/total functions, deterministic FSMs, and patterns used in aerospace and medical device software.

[Available on Leanpub →](https://leanpub.com/c-from-scratch)

---

## Educational

| Repo | Description |
|------|-------------|
| [c-from-scratch](https://github.com/SpeyTech/c-from-scratch) | Learn C using the Math → Structs → Code paradigm |
| [fixed-point-fundamentals](https://github.com/SpeyTech/fixed-point-fundamentals) | Fixed-point arithmetic from first principles |

---

## Licensing

Most Axioma and `certifiable-*` repositories are licensed under **AGPLv3** ([AGPL-3.0-or-later](https://www.gnu.org/licenses/agpl-3.0.html)).

See individual repositories for specific terms. All repositories include SPDX identifiers.

Commercial licensing is available for organisations that cannot comply with AGPL terms.

Contact: [william@speytech.com](mailto:william@speytech.com)

---

## Contributing

Contributions are welcome from engineers working in safety-critical domains.

All contributors must sign the [Contributor License Agreement](https://github.com/SpeyTech/.github/blob/master/CONTRIBUTOR-LICENSE-AGREEMENT.md) before contributions can be accepted.

---

## Contact

**William Murray**
Founder, SpeyTech
[william@speytech.com](mailto:william@speytech.com)
[speytech.com](https://speytech.com)

---

*Building deterministic systems for when lives depend on the answer.*
