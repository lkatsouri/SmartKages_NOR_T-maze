# SmartKages_NOR_T-maze
T-maze and NOR analysis from Smart-Kages data

## 1. Smart-Kage NOR analysis

Two notebooks analyse novel object recognition (NOR) data from the Smart-Kage. Run them in this order:

1. `SmartKage_NOR_postprocessing.ipynb`: run once per cohort.
2. `SmartKage_NOR_analysis.ipynb`: combines the cohorts, then makes the plots and statistics.

### How to use

1. **Prepare each cohort folder.**
   - Each cohort folder needs a `DB/` folder (from Smart-Kage) and a `kage_descriptions.csv`.
   - `kage_descriptions.csv` gives each kage's genotype, whether it is included (`NOR_good`), and which
     side holds the novel object in the test phase (`NOR_side`).
2. **Run the postprocessing notebook for each cohort.**
   - Set `COHORT_DIR` in the settings cell.
   - Run all cells.
   - Results are saved to `<cohort>/NOR_processed/`.
3. **Run the analysis notebook.**
   - In section 1, set:
     - `BASE_DIR`: the folder that holds the cohorts;
     - `MASTER_NAME`: a name for the combined dataset;
     - `COHORTS_TO_COMBINE`: the cohort folder names.
   - In section 2, set `GENO_ORDER` and `GENO_COLORS`. Genotype names must match `kage_descriptions.csv`
     exactly.
   - Run sections 1–6.
   - Results are saved to `<BASE_DIR>/NOR_MASTER_<MASTER_NAME>/`.

### What each notebook does

### `SmartKage_NOR_postprocessing.ipynb`

This notebook turns one cohort's raw data into tables:

- It finds the wheel change that starts each phase (sample, ITI baseline, test and, optionally, OiP).
- It excludes kages that failed QC (`NOR_good`).
- It bins object exploration into 1-min bins over each phase.
- It calculates:
  - total and cumulative exploration;
  - the test-phase discrimination index (DI): over time, and one value per mouse for the first 20 min
    and the first 2 h;
  - which object each mouse approached first in the test phase.

### `SmartKage_NOR_analysis.ipynb`

This notebook combines the processed cohorts into master tables and analyses them:

- **Exploration:** totals per phase, exploration over time, exploration around each wheel change, and
  cumulative exploration.
- **Discrimination index:**
  - DI over the test phase;
  - DI at fixed time points;
  - test DI compared with the sample-phase DI (baseline side preference).
- **First approach:** the proportion of mice that went to the novel object first.
- **Statistics:**
  - total exploration compared between genotypes;
  - sample vs test DI within each genotype, with a paired t-test.

DI = (novel − familiar) / (novel + familiar). It runs from −1 (only the familiar object) to +1 (only the
novel object); 0 means no preference.

Each notebook's first cell has more detail.
