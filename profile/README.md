# SpeyTech

**Deterministic and verifiable systems for software and AI.**

For engineers building systems where correctness must be provable.

**SpeyTech is the engineering brand; [Spey Systems Ltd](https://speysystems.com/) (SC889983) is the
company.** All repositories, specifications, and associated assets are
held by Spey Systems Ltd, a Scottish software and systems engineering
company based in Inverness.

Built in the Scottish Highlands. Priority of the core specifications is
anchored by OpenTimestamps into the Bitcoin blockchain (first anchor:
block 956672), a deliberate choice of timestamped defensive publication
over patents.

---

## Axioma

**A verifiable AI execution framework: evidence you can check, claims
you can kill.**

Axioma makes claims about AI systems falsifiable and their evidence
adversarially verifiable. It wraps non-deterministic AI behind formal
oracle boundaries, records every model interaction in tamper-evident
hash-chained ledgers, and publishes results as categorical verdicts
against pre-committed refutation conditions that any third party can
execute.

The proof record, not the pitch:

- **FCC-001**, the Falsifiable Claim Calculus: specification frozen at
  v0.4.1 after four adversarial scrutiny rounds. Claims commit their
  metric, acceptance band, exact finite-sample error bounds
  (Clopper-Pearson), data-exclusion rules, and an executable refutation
  condition before any outcome exists.
- **fcc-verify**: the deterministic verdict program. Stdlib Python,
  exact rational arithmetic, no floating point in any verdict decision,
  hand-derived conviction vectors. Claimant and refuter run the same
  program on the same evidence and must reach the same verdict.
- **Dual-attested evidence**: every model call committed by two
  independently written ledgers (runner and gateway), cross-bound per
  call.
- **Serving-determinism witness**: reconstructs recorded calls from
  committed evidence, re-fires them under the same pin and snapshot,
  and refuses certification when the serving layer cannot be trusted.
  Deployed and exercised against a live frontier API: byte-identical
  output at maximum context depth across batch-separated fires,
  verified against the gateway's own per-request record.
- The instrument does not trust its own serving. No other evaluation
  harness we are aware of treats its serving layer as an adversary.

| Layer | Concern | Repo | Role |
|-------|---------|------|------|
| L0 | Epistemic containment | [axioma-l0](https://github.com/SpeyTech/axioma-l0) | Pre-admission proxy ensuring no regime-identifying information crosses the model boundary |
| L7 | Accountability | [axioma-governance](https://github.com/SpeyTech/axioma-governance) | Proof-carrying governance and compliance reporting |
| L6 | Truth | [axioma-audit](https://github.com/SpeyTech/axioma-audit) | Cryptographic audit ledger with total ordering (libaxilog, the single SHA-256 substrate across all layers) |
| L5 | Behaviour | [axioma-agent](https://github.com/SpeyTech/axioma-agent) | Agent totality contracts and health FSM |
| L4 | Admissibility | [axioma-policy](https://github.com/SpeyTech/axioma-policy) | Policy evaluation and operational envelope |
| L3 | Containment | [axioma-oracle](https://github.com/SpeyTech/axioma-oracle) | Oracle Boundary Gateway: LLM containment, per-call attestation, ledger export |
| L2 | Identity | `certifiable-*` (below) | Deterministic ML computation substrate |
| L1 | Mathematics | [axioma-audit](https://github.com/SpeyTech/axioma-audit) | DVM arithmetic primitives and fault model |

L0 sits orthogonally to L1 to L7. It operates as a pre-admission proxy
before L3, curating what the model sees without modifying what L6
records.

Supporting repos:
[axioma-spec](https://github.com/SpeyTech/axioma-spec) (framework
specification, DVEC-001, SRS documents) ·
[axioma-verify](https://github.com/SpeyTech/axioma-verify)
(verification tooling) ·
[axioma-sdk](https://github.com/SpeyTech/axioma-sdk) (client SDKs:
Rust, TypeScript, Python) ·

The gateway provides a production deployment surface for regulated AI
systems: tamper-evident record-keeping and third-party-checkable
conformity evidence of the kind the EU AI Act's record-keeping and
accuracy provisions presuppose.

---

## EXP-1 and the evidence tooling

The calculus is not a proposal; it is being used on its own author.
EXP-1 is a pre-registered experiment whose result will publish as a
categorical verdict against a committed band, with the refutation
condition public before the data exists.

| Repo | What it is |
|------|------------|
| [fcc-verify](https://github.com/SpeyTech/fcc-verify) | The deterministic verdict program and the FCC-001 specification and claim algebra under `spec/` |
| [exp1-runner](https://github.com/SpeyTech/exp1-runner) | The experiment harness: evidence chain, oracle adapters, serving-determinism witness and checker, workload-determinism harness, mock-gateway probe suites |

Every result in this estate is designed to be re-executed, not
believed. Start with the conviction vectors in fcc-verify and the
witness vectors in exp1-runner/tests.

---

## certifiable-*

**The deterministic computation substrate that Axioma builds upon
(L2).**

Pure C99. Zero dynamic allocation. Fixed-point arithmetic (Q16.16).
Cryptographic audit trails at every stage.

Designed for certification under DO-178C, IEC 62304, ISO 26262, and
IEC 61508.

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
| Build | [certifiable-build](https://github.com/SpeyTech/certifiable-build) | n/a | Deterministic build infrastructure |

**Pipeline:**

```
certifiable-data → certifiable-training → certifiable-quant → certifiable-deploy → certifiable-inference
                                                                                          ↓
                                                                              certifiable-monitor
```

---

## Where to start

- **The calculus**: [fcc-verify](https://github.com/SpeyTech/fcc-verify),
  read FCC-001 under `spec/`, then run the verifier against its
  conviction vectors.
- **The instrument**: [exp1-runner](https://github.com/SpeyTech/exp1-runner),
  run the serving-determinism witness vectors.
- **The architecture**: [axioma-spec](https://github.com/SpeyTech/axioma-spec).
- **Deterministic ML in practice**: [certifiable-inference](https://github.com/SpeyTech/certifiable-inference),
  run a forward pass and verify bit-identical output.

This page curates; it does not catalogue. The full estate
of 43 public repositories is in the
[repositories tab](https://github.com/orgs/SpeyTech/repositories).

---

## Educational

| Repo | Description |
|------|-------------|
| [c-from-scratch](https://github.com/SpeyTech/c-from-scratch) | Learn C using the Math → Structs → Code paradigm |
| [fixed-point-fundamentals](https://github.com/SpeyTech/fixed-point-fundamentals) | Fixed-point arithmetic from first principles |

**The book**:
[C From Scratch: Learn Safety-Critical C the Right Way](https://leanpub.com/c-from-scratch),
the methodology as a complete text. Closed/total functions,
deterministic FSMs, and patterns used in aerospace and medical device
software.

---

## Licensing

Most Axioma and `certifiable-*` repositories are licensed under
**AGPLv3**
([AGPL-3.0-or-later](https://www.gnu.org/licenses/agpl-3.0.html)). See
individual repositories for specific terms. All repositories include
SPDX identifiers.

Commercial licensing is available from Spey Systems Ltd for
organisations that cannot comply with AGPL terms.

Contact: [william@speysystems.com](mailto:william@speysystems.com)

---

## Contributing

Contributions are welcome from engineers working in safety-critical
domains.

All contributors must sign the
[Contributor License Agreement](https://github.com/SpeyTech/.github/blob/master/CONTRIBUTOR-LICENSE-AGREEMENT.md)
before contributions can be accepted.

---

## Contact

**William Murray**
Founder, Spey Systems Ltd (SC889983)
[william@speysystems.com](mailto:william@speysystems.com)
[speysystems.com](https://speysystems.com) · [speytech.com](https://speytech.com)

---

*Building deterministic systems for when lives depend on the answer.*
