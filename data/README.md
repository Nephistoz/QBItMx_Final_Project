# data/

This folder must contain the real (or semi-real) 4×4 dataset used by the project,
as `dataset_real_4x4.csv`. It does not exist yet — this is a placeholder describing
the schema the notebook (`proyecto_qubo_qaoa.ipynb`, cell 24) expects.

## Required format (long/tidy table)

```csv
a_id,b_id,score,a_nombre,b_nombre
A1,B1,7.5,<label for a1>,<label for b1>
A1,B2,3.0,<label for a1>,<label for b2>
...
A4,B4,8.0,<label for a4>,<label for b4>
```

- `a_id`, `b_id`: must be exactly `A1..A4` and `B1..B4` (4 elements per side).
- `score`: the justified compatibility/benefit score $S_{ij}$ — must come from an
  explicit, documented formula (see `README.md` at the repo root), not arbitrary values.
- `a_nombre`, `b_nombre`: optional human-readable labels for each entity.
- The table must have exactly 16 rows (4×4, one per pair).

## TODO before the deliverable counts

- [ ] Pick a domain (health, housing, employment, urban services, education — see
      `SPECIFICATION.md` for the recommended Mexican open-data portals).
- [ ] Select exactly 4 elements for set A and 4 for set B, with a reproducible rule.
- [ ] Compute `score` with a documented formula (normalize inputs so no column dominates).
- [ ] Save the table here as `dataset_real_4x4.csv`.
- [ ] Fill in the `README.md` dataset section at the repo root with source, license,
      access date, and the exact score formula.
