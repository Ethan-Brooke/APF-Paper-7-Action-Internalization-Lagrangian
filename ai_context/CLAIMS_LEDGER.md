# Claims Ledger — Paper 7

| # | Claim | Status | Proof location | Code check | Failure mode |
|---|---|---|---|---|---|
| 1 | Partition function well-defined at saturation | standard | Supp §1 | `check_L_partition_Z` | non-convergent $Z$ |
| 2 | Saturation factorisation | structural (framed as factorisation) | Supp §2 | `check_L_saturation_factorization` | composition law violated |
| 3 | $L_{\rm spectral\_action\_internal}$: spectral action = partition function at Boltzmann cutoff | nontrivial (load-bearing) | Supp §3 | `check_L_spectral_action_internal` | non-matching coefficients at cutoff |
| 4 | $a_0 = 61$ (Seeley-DeWitt) | arithmetic + structural | Supp §4 | `check_L_spectral_a0` | SM matter count doesn't give 61 |
| 5 | $a_2 \approx 21.985$ | arithmetic | Supp §4 | `check_L_spectral_a2` | curvature couplings drift |
| 6 | $a_4 \approx 87.201$ | arithmetic | Supp §4 | `check_L_spectral_a4` | higher-derivative terms drift |
| 7 | Coleman-Mandula internalized | standard + framing | Supp §5 | `check_L_CM_internal` | CM evaded inside admissibility |
| 8 | HKM integration | standard + framing | Supp §5 | `check_L_HKM` | HKM-inconsistent admissibility |
| 9 | I4 action-thermo identity | nontrivial (receiver) | Supp v1.1 §I4_register | `check_T_ACC_unification` (Paper 8) | $\beta \to 0$ divergence |
| 10 | $\pi_A$ factory | nontrivial | Supp v1.1 §Z0 | `check_T_ACC_unification` | $Z$ doesn't match $\pi_A$ |
| 11 | Triple reading $a_0 = 61$ (Seeley-DeWitt / $\pi_F$ / $\pi_C$) | structural | Supp v1.1 | `check_L_a0_triple_reading` | readings disagree |
| 12 | H1 spectral-triple ansatz | hypothesis (flagged) | Supp §3 hypotheses | — | H1 falsified by future data |

## Attack surface priority

Claims 3, 4, 9, 11. Claim 3 is the structural pivot — if spectral action ≠ partition function at Boltzmann cutoff, Paper 7's contribution collapses.

---

*17 bank-registered checks verify this paper in this repo.*
