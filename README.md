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
  

## 2. Smart-Kage T-maze analysis
descriptions to be added
