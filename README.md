# Action, Internalization, and the Lagrangian

### Interactive Mathematical Appendix to Paper 7 of the Admissibility Physics Framework

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18439513.svg)](https://doi.org/10.5281/zenodo.18439513) [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Ethan-Brooke/APF-Paper-7-Action-Internalization-Lagrangian/blob/main/APF_Reviewer_Walkthrough.ipynb)

[Interactive Derivation DAG](https://ethan-brooke.github.io/APF-Paper-7-Action-Internalization-Lagrangian/) · [Theorem Map](#theorem-mapping-table) · [Reviewers' Guide](REVIEWERS_GUIDE.md) · [The full APF corpus](#the-full-apf-corpus) · [Citation](#citation)

> **AI agents:** start with [`START_HERE.md`](START_HERE.md) — operational checklist that loads the framework context in 5–10 minutes. The corpus inventory and full file map are in [`ai_context/repo_map.json`](ai_context/repo_map.json).

---

## Why this codebase exists

Five Parts: Quantum of Action (minimum-action theorem, Isolation of Zero, k! multi-record); Partition Function (closed-form Z_0, gapped-ground-state regime, saturation factorisation); Spectral Action = APF Partition Function (the structural pivot — Connes spectral action equals APF partition function at Boltzmann cutoff; Seeley-DeWitt expansion produces cosmological constant + Einstein-Hilbert + Yang-Mills + Higgs); Geometric Internalization (Lovelock, Coleman-Mandula, HKM, Malament); SM Lagrangian Extensions (one-loop beta coefficients, Type-I seesaw, Pauli-Jordan, McKean-Singer, Tannaka-Krein).

This repository is the executable proof.

The codebase is a faithful subset of the canonical APF codebase v6.9 (frozen 2026-04-18; 355 verify_all checks, 342 bank-registered theorems across 19 modules + `apf/standalone/`). Each theorem in the manuscript traces to a named `check_*` function in `apf/core.py`, which can be called independently and returns a structured result.

The codebase requires Python 3.8+ and NumPy / SciPy (some numerical lemmas use them; see `pyproject.toml`).

## How to verify

Three paths, in order of increasing friction:

**1. Colab notebook — zero install.** [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Ethan-Brooke/APF-Paper-7-Action-Internalization-Lagrangian/blob/main/APF_Reviewer_Walkthrough.ipynb) Every key theorem is derived inline, with annotated cells you can inspect and modify. Run all cells — the full verification takes under a minute.

**2. Browser — zero install.** Open the [Interactive Derivation DAG](https://ethan-brooke.github.io/APF-Paper-7-Action-Internalization-Lagrangian/). Explore the dependency graph. Hover any node for its mathematical statement, key result, and shortest derivation chain to A1. Click **Run Checks** to watch all theorems verify in topological order.

**3. Local execution.**

```bash
git clone https://github.com/Ethan-Brooke/APF-Paper-7-Action-Internalization-Lagrangian.git
cd APF-Paper-7-Action-Internalization-Lagrangian
pip install -e .
python run_checks.py
```

Expected output:

```
      Paper 7 (Action, Internalization, and the Lagrangian): 21 passed, 0 failed, 21 total — verified in <minutes>
```

**4. Individual inspection.**

```python
from apf.bank import get_check
r = get_check('check_T_eps')()
print(r['key_result'])
```

For reviewers, a [dedicated guide](REVIEWERS_GUIDE.md) walks through the logical architecture, the structural assumptions, and the anticipated objections.

---

## Theorem mapping table

This table maps every result in the manuscript to its executable verification.

| Check | Type | Summary |
|-------|------|---------|
| `check_T_eps` | Theorem |  |
| `check_T9` | Theorem | T9: L3-mu Record-Locking -> k! Inequivalent Histories. |
| `check_L_irr` | Lemma | L_irr: Irreversibility from Admissibility Physics. |
| `check_T0_4_prime_BFS` | Theorem |  |
| `check_T9` | Theorem | T9: L3-mu Record-Locking -> k! Inequivalent Histories. |
| `check_L_self_exclusion` | Lemma | L_self_exclusion: Self-Correlation Excluded from Microstate Counting [P]. |
| `check_L_singularity_resolution` | Lemma | L_singularity_resolution: Big Bang Singularity Avoidance [P]. |
| `check_T_deSitter_entropy` | Theorem | T_deSitter_entropy: de Sitter Entropy from Capacity Microstate Counting [P]. |
| `check_L_spectral_action_internal` | Lemma | L_spectral_action_internal: Spectral Action = APF Partition Function [P]. |
| `check_L_normalization_coefficient` | Lemma | L_normalization_coefficient: The ½ on Tr(κ†κ) from KO-Dimension 6 [P]. |
| `check_L_scalar_potential_form` | Lemma | L_scalar_potential_form: Scalar Potential from Spectral Invariance + A1 [P]. |
| `check_L_V_enforcement` | Lemma |  |
| `check_L_kolmogorov_internal` | Lemma | L_kolmogorov_internal: Continuum Limit from Finite Capacity + R3 [P]. |
| `check_L_chartability` | Lemma | L_chartability: Smooth Atlas from Lipschitz Cost + Compactness [P]. |
| `check_L_lovelock_internal` | Lemma | L_lovelock_internal: Uniqueness of Einstein Equations from Admissibility [P]. |
| `check_L_coleman_mandula_internal` | Lemma | L_coleman_mandula_internal: Direct-Product Structure from Admissibility [P]. |
| `check_T6B_beta_one_loop` | Theorem | T6B_beta_one_loop: 1-Loop SM Beta Functions from APF Content [P]. |
| `check_L_seesaw_type_I` | Lemma | L_seesaw_type_I: Type-I Seesaw from APF Dirac Operator [P]. |
| `check_L_Pauli_Jordan` | Lemma | L_Pauli_Jordan: Pauli-Jordan Function Reflection Symmetry [P]. |
| `check_L_McKean_Singer_internal` | Lemma | L_McKean_Singer_internal: McKean-Singer Index Formula Internalized [P]. |
| `check_L_Tannaka_Krein` | Lemma | L_Tannaka_Krein: Compact Group Recovered from Symmetric Tensor Category [P]. |

All check functions reside in `apf/core.py`. Every function listed above can be called independently and returns a structured result including its logical dependencies and the mathematical content it verifies.

---

## The derivation chain

```
  Level 0: T_eps · T9 · L_irr · T0_4_prime_BFS · L_self_exclusion · L_singularity_resolution · T_deSitter_entropy · L_spectral_action_internal · L_normalization_coefficient · L_scalar_potential_form · L_V_enforcement · L_kolmogorov_internal · L_chartability · L_lovelock_internal · L_coleman_mandula_internal · T6B_beta_one_loop · L_seesaw_type_I · L_Pauli_Jordan · L_McKean_Singer_internal · L_Tannaka_Krein
```

The [interactive DAG](https://ethan-brooke.github.io/APF-Paper-7-Action-Internalization-Lagrangian/) shows the full graph with hover details and animated verification.

---

## Repository structure

```
├── README.md                              ← you are here
├── START_HERE.md                          ← AI operational checklist; read-first for AI agents
├── REVIEWERS_GUIDE.md                     ← physics-first walkthrough for peer reviewers
├── interactive_dag.html                   ← interactive D3.js derivation DAG (also served at docs/ via GitHub Pages)
├── repo_map.json                          ← machine-readable map of this repo (root copy of ai_context/repo_map.json)
├── theorems.json                          ← theorem catalog (root copy of ai_context/theorems.json)
├── derivation_graph.json                  ← theorem DAG as JSON (root copy of ai_context/derivation_graph.json)
├── ai_context/                            ← AI onboarding pack (corpus map, theorems, glossary, etc.)
│   ├── AGENTS.md                          ← authoritative entry point for AI agents
│   ├── FRAMEWORK_OVERVIEW.md              ← APF in 5 minutes
│   ├── GLOSSARY.md                        ← axioms, PLEC primitives, epistemic tags
│   ├── AUDIT_DISCIPLINE.md                ← engagement posture for critique/proposal
│   ├── OPEN_PROBLEMS.md                   ← catalog of open problems + verdicts
│   ├── repo_map.json                      ← machine-readable map of this repo
│   ├── theorems.json                      ← machine-readable theorem catalog
│   ├── derivation_graph.json              ← theorem DAG as JSON
│   └── wiki/                              ← bundled APF wiki (concepts, papers, codebase)
├── apf/
│   ├── core.py                            ← 21 theorem check functions
│   ├── apf_utils.py                       ← exact arithmetic + helpers
│   └── bank.py                            ← registry and runner
├── docs/
│   └── index.html                         ← interactive derivation DAG (GitHub Pages)
├── APF_Reviewer_Walkthrough.ipynb         ← Colab notebook
├── run_checks.py                          ← convenience entry point
├── pyproject.toml                         ← package metadata
├── zenodo.json                            ← archival metadata
├── Paper_7_Action_Internalization_Lagrangian_v2.0.tex                ← the paper
├── Paper_7_Action_Internalization_Lagrangian_Supplement_v1.0.tex                ← Technical Supplement

└── LICENSE                                ← MIT
```

---

## What this paper derives and what it does not

**Derived:** (see Theorem mapping table above)

**Not derived here:** Specific results outside this paper's scope live in companion papers — see the corpus table below for the full 9-paper series.

---

## Citation

```bibtex
@software{apf-paper7,
  title   = {Action, Internalization, and the Lagrangian},
  author  = {Brooke, Ethan},
  year    = {2026},
  doi     = {10.5281/zenodo.18439513},
  url     = {https://github.com/Ethan-Brooke/APF-Paper-7-Action-Internalization-Lagrangian}
}
```

For the full citation lineage (concept-DOI vs version-DOI, related identifiers, bibtex for all corpus papers), see [`ai_context/CITING.md`](ai_context/CITING.md).

---

## The full APF corpus

This repository is **one paper-companion** in a 9-paper series. Each paper has its own companion repo following this same layout. The full corpus, with canonical references:

| # | Title | Zenodo DOI | GitHub repo | Status |
|---|---|---|---|---|
| 0 | What Physics Permits | [10.5281/zenodo.18439523](https://doi.org/10.5281/zenodo.18439523) | [`APF-Paper-0-What-Physics-Permits`](https://github.com/Ethan-Brooke/APF-Paper-0-What-Physics-Permits) | public |
| 1 | The Enforceability of Distinction | [10.5281/zenodo.18439200](https://doi.org/10.5281/zenodo.18439200) | [`APF-Paper-1-The-Enforceability-of-Distinction`](https://github.com/Ethan-Brooke/APF-Paper-1-The-Enforceability-of-Distinction) | public |
| 2 | The Structure of Admissible Physics | [10.5281/zenodo.18439274](https://doi.org/10.5281/zenodo.18439274) | [`APF-Paper-2-The-Structure-of-Admissible-Physics`](https://github.com/Ethan-Brooke/APF-Paper-2-The-Structure-of-Admissible-Physics) | public |
| 3 | Ledgers | [10.5281/zenodo.18439363](https://doi.org/10.5281/zenodo.18439363) | [`APF-Paper-3-Ledgers-Entropy-Time-Cost`](https://github.com/Ethan-Brooke/APF-Paper-3-Ledgers-Entropy-Time-Cost) | public |
| 4 | Admissibility Constraints and Structural Saturation | [10.5281/zenodo.18439397](https://doi.org/10.5281/zenodo.18439397) | [`APF-Paper-4-Admissibility-Constraints-Field-Content`](https://github.com/Ethan-Brooke/APF-Paper-4-Admissibility-Constraints-Field-Content) | public |
| 5 | Quantum Structure from Finite Enforceability | [10.5281/zenodo.18439433](https://doi.org/10.5281/zenodo.18439433) | [`APF-Paper-5-Quantum-Structure-Hilbert-Born`](https://github.com/Ethan-Brooke/APF-Paper-5-Quantum-Structure-Hilbert-Born) | public |
| 6 | Dynamics and Geometry as Optimal Admissible Reallocation | [10.5281/zenodo.18439445](https://doi.org/10.5281/zenodo.18439445) | [`APF-Paper-6-Dynamics-Geometry-Spacetime-Gravity`](https://github.com/Ethan-Brooke/APF-Paper-6-Dynamics-Geometry-Spacetime-Gravity) | public |
| 7 | Action, Internalization, and the Lagrangian **(this repo)** | [10.5281/zenodo.18439513](https://doi.org/10.5281/zenodo.18439513) | [`APF-Paper-7-Action-Internalization-Lagrangian`](https://github.com/Ethan-Brooke/APF-Paper-7-Action-Internalization-Lagrangian) | public |
| 13 | The Minimal Admissibility Core | [10.5281/zenodo.18361446](https://doi.org/10.5281/zenodo.18361446) | [`APF-Paper-13-The-Minimal-Admissibility-Core`](https://github.com/Ethan-Brooke/APF-Paper-13-The-Minimal-Admissibility-Core) | public |
| — | Canonical codebase (v6.9) | [10.5281/zenodo.18529115](https://doi.org/10.5281/zenodo.18529115) | [`APF-Codebase`](https://github.com/Ethan-Brooke/APF-Codebase) | pending |

The canonical computational engine — the full bank of 342 theorems across 19 modules — is the **APF Codebase** ([Zenodo](https://doi.org/10.5281/zenodo.18529115)). Every per-paper repo is a faithful subset of that engine.

---

## License

MIT. See [LICENSE](LICENSE).

---

*Generated by the APF `create-repo` skill on 2026-04-19. Codebase snapshot: v6.9 (frozen 2026-04-18; 355 verify_all checks, 342 bank-registered theorems, 48 quantitative predictions).*
