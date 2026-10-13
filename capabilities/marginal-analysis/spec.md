---
type: spec
capability: marginal-analysis
engagement: perfect-competition
date: 2026-10-13
status: draft            # draft | built | audited
built_with: ""
---

# <Capability> — model specification

## Purpose
This model finds the best combination of tomatoes, carrots, and mesclun to maximize the farm's total seasonal profit in a perfectly competitive market. It also considers the farm's limits, including a maximum of 64 beds and 6,480 labor hours per season.

## Inputs — the named contract
| Name | Value | Unit | Source |
|---|---|---|---|
| `TOM_PRICE` | 8800 | USD per bed | Case scenario, crop table |
| `TOM_FERT` | 880 | USD per bed | Case scenario, crop table |
| `TOM_BASE_HRS` | 2.5 | hours per week per bed | Case scenario, crop table |
| `TOM_DIM_PCT` | 10% | percentage penalty | Case scenario, crop table |
| `TOM_MAX_BEDS` | 20 | beds | Case scenario, crop table |
| `CAR_PRICE` | 2094 | USD per bed | Case scenario, crop table |
| `CAR_FERT` | 440 | USD per bed | Case scenario, crop table |
| `CAR_BASE_HRS` | 0.833 | hours per week per bed | Case scenario, crop table |
| `CAR_DIM_PCT` | 2.5% | percentage penalty | Case scenario, crop table |
| `CAR_MAX_BEDS` | 20 | beds | Case scenario, crop table |
| `MES_PRICE` | 2700 | USD per bed | Case scenario, crop table |
| `MES_FERT` | 880 | USD per bed | Case scenario, crop table |
| `MES_BASE_HRS` | 1.25 | hours per week per bed | Case scenario, crop table |
| `MES_DIM_PCT` | 1.25% | percentage penalty | Case scenario, crop table |
| `MES_MAX_BEDS` | 30 | beds | Case scenario, crop table |
| `WEEKS` | 36 | weeks per season | Case scenario, farm constraints |
| `FARM_MAX_BEDS` | 64 | beds | Case scenario, farm constraints |
| `OWNER_HRS_CAP` | 720 | hours | Case scenario, labor constraints |
| `OWNER_RATE` | 34.72 | USD per hour | Case scenario, labor constraints |
| `TEMP_HRS_CAP` | 5760 | total hours for 4 temporary workers | Case scenario, labor constraints |
| `TEMP_RATE` | 17.36 | USD per hour | Case scenario, labor constraints |
| `TOTAL_LABOR_CAP` | 6480 | hours | Case scenario, labor constraints |

## Structure
Each sheet or region, and what it is for.

## Calculation logic
In named-range notation, never cell addresses:

  LABOR_HRS(q) = q x HRS_PER_BED x WEEKS x (1 + DIM_PCT)^q

"Column D times column E" is not a specification — it describes a spreadsheet
that does not exist yet.

## Conventions
The rules that are not visible in the formulas: costing order, allocation basis,
rounding, what happens at the boundaries. State all of them. A convention you
leave out is a convention the builder invents.

## Validation rules
The conditions the finished artifact must satisfy — check figures as acceptance
criteria, hand calculations, and structural rules ("every calculated cell
contains a formula", "no error cells").

## Outputs
Each result the model reports, by name.

## Audit findings
Added AFTER the build. For each check: what you checked, what you found, what
you did about it.
