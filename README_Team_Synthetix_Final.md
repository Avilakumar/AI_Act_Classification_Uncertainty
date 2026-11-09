# Team Synthetix — AI Act Screening: Formal Consistency & Uncertainty Propagation

**Research title:** Formal Consistency and Uncertainty Propagation in Rule-Based AI Act Screening: A Reproducible Synthetic Benchmark  
**Group:** 12 · **Team:** Synthetix  
**Researchers:** Avila Kumar Rajaboina · Manideep Galipelli  
**Target journal:** *Computer Law & Security Review* (Elsevier)  
**Study type:** Reproducible computational experiment with synthetic scenarios and draft rules

> **Research boundary:** This project tests the *formal behavior of software*, not the legal correctness of classifications under the EU AI Act. It is not a legal advice system, compliance certificate, or claim of journal acceptance. The 19 rules are illustrative and have not received legal approval.

## Overview

This study compares a closed-world binary rule baseline with a three-valued uncertainty-aware screening engine. The latter explicitly preserves unknown or missing factual inputs, produces auditable rule traces, and routes cases to provisional classification, requests for information, or review. A separately implemented Boolean-completion oracle and automated invariants evaluate whether the implementation follows its specified logic.

The study uses **140 hypothetical AI-use cases in 70 controlled A/B pairs**, **19 draft rule identifiers**, and **280 classifier decisions**. Each A/B pair differs in exactly one factual value. All benchmark inputs are embedded inside the notebook: no dataset download, API key, or external legal reviewer is required to reproduce the **formal experiments**.

## Research questions

1. **RQ1 — Perturbation sensitivity:** Which one-fact changes alter provisional screening outcomes and routing actions?
2. **RQ2 — Uncertainty preservation:** How does three-valued logic behave relative to a closed-world binary baseline when relevant facts are unknown or absent?
3. **RQ3 — Formal trace consistency:** Do the rule-engine outcomes and generated traces agree with an independently implemented mathematical reference oracle?
4. **RQ4 — Automated routing:** How do missing information and draft-rule uncertainty affect the system's routing decisions?

## Research design

| Component | Description |
|---|---|
| Benchmark | 140 synthetic cases; 70 A/B pairs with one controlled factual change |
| Rule codebook | 19 illustrative draft rule IDs; not legally approved |
| Binary baseline | Closed-world evaluation; unknown/absent predicates treated as false for comparison |
| Uncertainty-aware engine | Three-valued TRUE / FALSE / UNKNOWN predicate reasoning |
| Output actions | `CLASSIFY`, `REQUEST_MISSING_INFORMATION`, `ESCALATE_FOR_LEGAL_REVIEW` |
| Rule traces | Candidate rule, factual predicates, evidence status, outcome and reason |
| Formal oracle | Separate Boolean-completion implementation of the declared rule semantics |
| Outputs | 16 exhibits: 8 figures and 8 tables, plus audit and verification files |

The routing label `ESCALATE_FOR_LEGAL_REVIEW` is an **experimental software output**. No specialist actually reviews the cases as part of this formal study.

## Repository contents

A suggested GitHub layout (the executed notebook itself is self-contained):

```text
team-synthetix/
├── README.md
├── Team_Synthetix_Final_Executed_Automated_Study.ipynb
├── results/                         # generated after Run All (optional to commit)
│   ├── automated_validation_summary.json
│   ├── automated_truth_table_validation.csv
│   ├── automated_oracle_trace_validation.csv
│   ├── automated_metamorphic_validation.csv
│   ├── automated_routing_validation.csv
│   ├── final_computational_audit.json
│   ├── exhibit_manifest.json
│   └── ...                         # 8 PNG + 8 PDF figures, 8 CSV + 8 TEX tables
└── docs/                            # proposal and presentation (optional)
```

## Requirements

- Python **3.10+** (tested with the standard scientific Python notebook environment)
- `pandas`, `matplotlib`, `IPython`, and Jupyter / Kaggle Notebooks
- Python standard library modules including `csv`, `json`, `zipfile`, `hashlib`, and `itertools`

Install locally if needed:

```bash
python -m pip install notebook pandas matplotlib ipython
```

## Run on Kaggle (recommended)

1. Open [Kaggle Code](https://www.kaggle.com/code) and choose **New Notebook**.
2. Use **File → Import Notebook** to import `Team_Synthetix_Final_Executed_Automated_Study.ipynb` (or upload the notebook using Kaggle's import interface).
3. Select a **Python** session. Internet access and GPU acceleration are **not needed** for the embedded synthetic benchmark.
4. Choose **Run All**. Check that the final audit cell completes and prints `formal_checks: 1427` and `formal_failures: 0`.
5. Choose **Save Version → Save & Run All** to preserve a reproducible hosted run.
6. Download `Team_Synthetix_Automated_Formal_Results.zip` from the Kaggle **Output** panel. Generated files are stored under `/kaggle/working/synthetix_outputs/`.

### Run locally

```bash
jupyter notebook Team_Synthetix_Final_Executed_Automated_Study.ipynb
```

Run the cells in order using **Kernel → Restart & Run All**. The notebook uses `/kaggle/working` when available and a local fallback directory otherwise; check the printed output path for your machine.

## Recorded execution results

The supplied executed notebook records the following successful checks. These numbers describe the **synthetic software benchmark**, not legal accuracy:

| Automated check | Recorded tests | Recorded failures |
|---|---:|---:|
| Exhaustive three-valued truth-table cases | 507 | 0 |
| Case–rule comparisons with independent formal oracle | 270 | 0 |
| Metamorphic information-monotonicity checks | 510 | 0 |
| Routing invariants | 140 | 0 |
| **Total** | **1,427** | **0** |

Additional recorded counts: **70/70** controlled pairs validated, **19/19** executed code cells without saved exceptions, **16/16** research exhibits produced, and **280** classifier decisions. The uncertainty-aware prototype reports **91** information requests, **30** provisional classifications and **19** review-routing actions across 140 cases. These counts are implementation-specific and should be regenerated after any code or data changes.

## Output artifacts and interpretation

- **Figures:** 8 publication-style charts, each exported as `.png` and `.pdf`.
- **Tables:** 8 descriptive tables, each exported as `.csv` and `.tex`.
- **Audit trail:** `all_decisions_audit.csv`, `prototype_summary.json` and `exhibit_manifest.json`.
- **Formal evaluation:** truth-table, oracle, metamorphic and routing CSV reports, plus `automated_validation_summary.json`.
- **Reproducibility:** embedded-input hashes, file manifest, computational audit JSON and zipped outputs.

The 16 exhibits are organized as **four per research question**. They describe controlled perturbations, classifier behavior, structural traceability and routing patterns. They do **not** measure correctness of legal interpretations.

## Reproducibility checks

A successful run should satisfy:

```text
Cases = 140
Controlled pairs = 70
Draft rules = 19
Decisions = 280
Exhibits = 16 (8 figures + 8 tables)
Formal checks = 1427
Formal failures = 0
```

The final notebook cells also check the output archive's ZIP integrity. For an independently reproducible release, include the notebook, environment details, checksums, and the Kaggle version URL or Git commit hash. Do not describe saved notebook outputs as a fresh rerun unless you actually execute them.

## Methodological boundaries and limitations

- **Formal correctness is not legal correctness.** The oracle tests a mathematical specification shared with the experimental rule semantics; it does not determine whether the rules accurately reflect Regulation (EU) 2024/1689.
- **Synthetic benchmark.** Cases are deliberately constructed; performance does not generalize automatically to real deployment settings.
- **Draft rules.** All 19 rule IDs remain experimental and unapproved. No legal classification accuracy, precision, recall, or false-positive rate against expert-adjudicated legal labels is reported.
- **Review action is simulated.** A routing recommendation is not a human specialist judgment.
- **Publication readiness.** Successful execution and automated checks do not establish novelty, journal fit, legal validity, peer-review success, or acceptance by *Computer Law & Security Review*.

No independent human legal adjudication is needed to reproduce the **defined formal software experiments**. It would be needed for stronger claims about legal interpretation or real-world regulatory decision quality.

## References and context

1. European Parliament and Council. **Regulation (EU) 2024/1689 (Artificial Intelligence Act)**. Official text: https://eur-lex.europa.eu/eli/reg/2024/1689/oj/eng
2. **Rebuilding the pyramid: The AI Act’s risk-based approach using a binary decision diagram** (2025), *Computer Law & Security Review*. DOI: https://doi.org/10.1016/j.clsr.2025.106189

The regulation and related literature motivate the research context; they are **not** an independent certification of the notebook's draft rules.

## Citation and reuse

If publishing this repository, add a release date, Git commit hash, software license, and (if available) a Zenodo DOI. Cite the final archived release rather than an unversioned notebook link. No DOI has been assigned in this README.

## Authors

**Team Synthetix — Group 12**  
Avila Kumar Rajaboina · Manideep Galipelli

**Research use only.**
