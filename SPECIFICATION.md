# Project Specification: QUBO-QAOA Bipartite Matching (4×4)

Course: Qubit.mx — QMexico Summer School 2026
Assignment source: `proyecto_final_ss26.ipynb`
Deliverable repo: https://github.com/Nephistoz/QBItMx_Final_Project

## 1. Objective

Take a real (or well-justified semi-real) dataset, reduce it to a **4×4 bipartite
matching** problem, formulate it as a **QUBO**, and solve a small instance with
**local QAOA**. Running on real IBM Quantum hardware is optional/advanced.

## 2. Grading breakdown

| Weight | Component |
|---|---|
| ~80% | Finding, justifying, and documenting a real or semi-real 4×4 dataset |
| ~20% | Correctly implementing `QUBO → classical validation → local QAOA` |
| Extra (only if authorized) | Comparison against real IBM Quantum hardware |

The bundled molecular-compatibility instance in the notebook is a worked example only
— it does **not** count as the submitted dataset. It must be replaced by the team's
own dataset for the project to be gradable.

## 3. Mathematical model

- Two sets of size 4: `A = {a1..a4}`, `B = {b1..b4}`.
- Binary decision variable `x_ij = 1` iff `a_i` is matched to `b_j`.
- Score matrix `S ∈ R^(4x4)`, `S_ij` = benefit/compatibility of matching `a_i, b_j`.
- Objective: maximize `Σ S_ij x_ij` subject to each `a_i` and each `b_j` being used
  exactly once (one-to-one assignment / bipartite matching).
- QUBO form: `E(x) = -Σ S_ij x_ij + λ_A Σ_i(Σ_j x_ij - 1)^2 + λ_B Σ_j(Σ_i x_ij - 1)^2`,
  with penalties `λ_A, λ_B` large enough that infeasible assignments are never optimal.

## 4. Required pipeline (Part B/C of the notebook)

1. Build `A_df`, `B_df`, `S` (4×4) from the team's dataset.
2. Validate shapes/finiteness of the instance.
3. Build the QUBO matrix `Q` + offset from `S` and the penalties.
4. Solve exactly by brute force over all `2^16 = 65536` binary configurations
   (classical ground truth).
5. Cross-check against the 24 feasible one-to-one permutations.
6. Run local QAOA (numpy/scipy only, no Qiskit needed) with `p=1` to start:
   uniform initial state → cost phase → standard X-mixer → classical parameter
   optimization (COBYLA) → sample bitstrings → compare energy/feasibility/score
   against the classical optimum.
7. (Optional, advanced) Run the same QAOA circuit on IBM Quantum hardware via
   Qiskit Runtime `SamplerV2`, and/or apply classical repair of infeasible samples
   as a documented hybrid post-processing step. Keep `USAR_IBM_QUANTUM = False`
   for the ordinary submission.

## 5. Dataset requirements

A dataset is admissible only if it can answer all of:

| Criterion | Question |
|---|---|
| Two identifiable sides | What is A, what is B? |
| Reducible to 4×4 | How exactly are 4 elements per side selected? |
| Justifiable score | How is `S_ij` computed from observable columns or explicit rules? |
| Binary decision | What does `x_ij = 1` mean? |
| Clear constraints | Exactly-one, at-most-one, or capacities? |
| Legitimate source | Source, institution, URL, license, and access date documented? |
| Controlled ethical risk | No sensitive personal data; no simulation of real high-impact decisions |

Suggested Mexican open-data sources (see notebook §5 for details): Plataforma
Nacional de Datos Abiertos (datos.gob.mx), CENATRA/Secretaría de Salud, INEGI
Banco de Indicadores/API, SNIIV/SEDATU, Datos Abiertos CDMX, Data México.

Applicable domains: health/transplants (use aggregated/synthetic profiles only,
never real patient data), housing, employment, urban services, education.

## 6. Deliverable: required repo structure

```text
QBItMx_Final_Project/
├── data/
│   └── dataset_real_4x4.csv
├── README.md
└── proyecto_qubo_qaoa.ipynb
```

- `data/dataset_real_4x4.csv`: the real/semi-real dataset (long format:
  `a_id,b_id,score[,a_nombre,b_nombre]`, 16 rows).
- `README.md`: justifies the dataset, explains the QUBO formulation, and reports
  classical-vs-QAOA results (template already in place at repo root).
- `proyecto_qubo_qaoa.ipynb`: must open in Google Colab and run top-to-bottom via
  `Runtime → Run all` with no errors, reading the CSV automatically (no manual steps).
- No personal tokens, credentials, or sensitive data may be committed.
- The molecular example may be kept as a backup (`proyecto_final_ss26.ipynb`) but
  is not the graded artifact.

## 7. Ethics constraints

- No names, CURP, case files, addresses, phone numbers, or personal identifiers.
- No sensitive individual-level data — prefer data aggregated by municipality,
  institution, or category.
- Document potential biases in the dataset.
- Never present QAOA output as a real policy/clinical/resource-allocation recommendation.
- For high-impact domains (health, etc.), use synthetic or aggregated profiles only.

## 8. Acceptance checklist

- [ ] Repo created from the student's/team's own GitHub account (or representative).
- [ ] `data/` exists at repo root with `dataset_real_4x4.csv` (or clearly documented equivalent).
- [ ] `README.md` exists at repo root.
- [ ] `README.md` documents source, institution, URL, license/terms, and access date.
- [ ] `README.md` defines A, B, x_ij, S_ij, and the constraints.
- [ ] `README.md` explains why the problem is bipartite matching.
- [ ] `README.md` explains why it's reasonable to formulate as a QUBO.
- [ ] `README.md` compares the exact classical solution against local QAOA.
- [ ] If IBM Quantum was used, `README.md` compares local QAOA vs. real hardware.
- [ ] If classical repair was used, `README.md` reports it as hybrid post-processing.
- [ ] `.ipynb` opens in Google Colab and runs end-to-end with no intermediate errors.
- [ ] No tokens, credentials, or sensitive data anywhere in the repo.
- [ ] The example molecular instance was replaced by the team's real/semi-real dataset.
- [ ] Ethical warnings and model limitations are stated explicitly.

## 9. Open items / next steps

- [ ] Choose the dataset domain and source (see §5) — currently unset.
- [ ] Build `A_df`, `B_df`, `S` from the chosen dataset and replace the molecular
      example in `proyecto_qubo_qaoa.ipynb` (§14 "Punto de reemplazo").
- [ ] Fill in `data/dataset_real_4x4.csv` and the root `README.md`.
- [ ] Run the notebook end-to-end in Colab and record results in `README.md`.
- [ ] Decide whether to attempt the optional IBM Quantum hardware comparison.
- [ ] Confirm submission deadline with the instructor and track it here.
