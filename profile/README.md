# SpeyTech

**Deterministic computing for safety-critical systems.**

---

## What is this?

Open source tools and libraries for building systems where reproducibility and correctness are non-negotiable. Fixed-point arithmetic, deterministic ML inference, and safety kernel patterns — all designed to support certification under DO-178C, ISO 26262, and IEC 62304.

## Why does it exist?

Floating-point non-determinism, hidden race conditions, and opaque ML models don't belong in systems that control aircraft, medical devices, or vehicles. These projects demonstrate that deterministic alternatives exist — and can be practical.

---

## 📖 The Book

<table>
<tr>
<td width="120">
<a href="https://leanpub.com/c-from-scratch">
<img src="https://speytech.com/images/c-from-scratch-book-launch.svg" alt="C From Scratch book cover" width="100">
</a>
</td>
<td>
<strong><a href="https://leanpub.com/c-from-scratch">C From Scratch: Learn Safety-Critical C the Right Way</a></strong><br><br>
The methodology behind <code>c-from-scratch</code> — now as a complete book. Learn to write provably correct C using the <em>Math → Structs → Code</em> approach. Covers closed/total functions, deterministic FSMs, and patterns used in aerospace and medical device software.<br><br>
<a href="https://leanpub.com/c-from-scratch">Available on Leanpub →</a>
</td>
</tr>
</table>

---

## Projects

### Certifiable ML Pipeline

| Repository | Description |
|------------|-------------|
| [certifiable-data](https://github.com/SpeyTech/certifiable-data) | Deterministic data pipelines |
| [certifiable-training](https://github.com/SpeyTech/certifiable-training) | Reproducible ML training with Merkle audit trails |
| [certifiable-quant](https://github.com/SpeyTech/certifiable-quant) | Model quantization with error certificates |
| [certifiable-inference](https://github.com/SpeyTech/certifiable-inference) | Fixed-point neural network inference |
| [certifiable-deploy](https://github.com/SpeyTech/certifiable-deploy) | Cryptographic model packaging |
| [certifiable-monitor](https://github.com/SpeyTech/certifiable-monitor) | Runtime drift detection |
| [certifiable-verify](https://github.com/SpeyTech/certifiable-verify) | Formal verification tooling |
| [certifiable-harness](https://github.com/SpeyTech/certifiable-harness) | End-to-end test harness |
| [certifiable-bench](https://github.com/SpeyTech/certifiable-bench) | Performance benchmarking |

### Education

| Repository | Description |
|------------|-------------|
| [c-from-scratch](https://github.com/SpeyTech/c-from-scratch) | Learn C using Math → Structs → Code |
| [fixed-point-fundamentals](https://github.com/SpeyTech/fixed-point-fundamentals) | Fixed-point arithmetic from first principles |

### Tools

| Repository | Description |
|------------|-------------|
| [C-Sentinel](https://github.com/SpeyTech/c-sentinel) | Semantic security monitoring |

---

## How do I use it?

Each repository includes documentation in `docs/` with requirements, build instructions, and examples. Clone, build, run the tests.
```bash
git clone https://github.com/SpeyTech/c-from-scratch.git
cd c-from-scratch
make test
```

## How do I contribute?

All contributions require signing the [Contributor License Agreement](https://github.com/SpeyTech/.github/blob/master/CONTRIBUTOR-LICENSE-AGREEMENT.md) before a pull request can be merged. See [CONTRIBUTING.md](https://github.com/SpeyTech/.github/blob/master/CONTRIBUTING.md) for the full process.

---

## Learn more

**[speytech.com](https://speytech.com)** — Technical articles, product details, and the complete certifiable-* documentation.

---

<sub>© 2026 The Murray Family Innovation Trust</sub>
