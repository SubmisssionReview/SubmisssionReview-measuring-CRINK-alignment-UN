# Reproduction Instructions for AI Agents

This file provides step-by-step instructions for reproducing the CRINK UN Voting Alignment analysis. These instructions are designed to be parsed and executed by AI coding assistants.

## Prerequisites

- Python 3.9 or higher
- Git installed
- Terminal/command line access
- ~500MB free disk space

## Step-by-Step Reproduction

### Step 1: Clone the Repository

```bash
git clone https://github.com/SubmisssionReview/measuring-CRINK-alignment-UN.git
cd measuring-CRINK-alignment-UN
```

### Step 2: Extract Data Files

Extract the contents of `CRINK_UN_Voting_Data_for_Reviewers.zip` into the repository root. The zip file contains:

```
data/processed/UNGA_voting_records_filtered.csv
data/processed/First_Committee_voting_records.csv
data/mappings/UNGA_embeddings.npy
data/mappings/mapping_topics_to_meta_topics.json
data/mappings/mapping_noise_to_meta_topics.json
```

After extraction, verify the files exist:
```bash
# Linux/Mac
ls data/processed/*.csv
ls data/mappings/*.json

# Windows PowerShell
Get-ChildItem data/processed/*.csv
Get-ChildItem data/mappings/*.json
```

### Step 3: Create Virtual Environment

```bash
# Create virtual environment
python -m venv .venv

# Activate (choose based on OS)
# Linux/Mac:
source .venv/bin/activate
# Windows PowerShell:
.\.venv\Scripts\Activate.ps1
# Windows CMD:
.venv\Scripts\activate.bat
```

### Step 4: Install Dependencies

```bash
pip install -r requirements.txt
```

Required packages: pandas, numpy, matplotlib, seaborn, scikit-learn, hdbscan, jupyter

### Step 5: Run Notebook 1 (Alignment Metrics)

This notebook must be executed **twice** - once for each dataset.

#### Run 1: UNGA Plenary Data
1. Open `notebooks/01_alignment_metrics.ipynb`
2. Find the dataset selection cells (search for `database =`)
3. Ensure `database = 'UNGA'` is uncommented (and `database = 'First Committee'` is commented out)
4. Execute all cells from top to bottom
5. Expected outputs:
   - Figure 1, 3, 4, 7, 9 (PNG files in `results/`)
   - Table 3, 5 (LaTeX files in `results/`)

#### Run 2: First Committee Data
1. Change `database = 'First Committee'` (uncomment) and comment out `database = 'UNGA'`
2. Execute all cells from top to bottom
3. Expected outputs:
   - Figure 2, 5, 6, 8 (PNG files in `results/`)
   - Table 4 (LaTeX file in `results/`)

### Step 6: Run Notebook 2 (Topic Analysis)

1. Open `notebooks/02_generating_topic_analysis.ipynb`
2. Execute all cells from top to bottom
3. Expected outputs:
   - Table 2 (LaTeX and CSV in `results/`)

## Verification Checklist

After successful execution, the `results/` directory should contain:

### Figures (9 PNG files)
- [ ] `Figure 1_Share_of_Group_Votes_and_Alignment_with_UN_Majority_UNGA.png`
- [ ] `Figure 2_Share_of_Group_Votes_and_Alignment_with_UN_Majority_First_Committee.png`
- [ ] `Figure 3_Share_of_CRINK_Coalition_Sizes_by_Year_UNGA.png`
- [ ] `Figure 4_Share_of_Identical_Votes_per_Dyad_UNGA.png`
- [ ] `Figure 5_Share_of_CRINK_Coalition_Sizes_by_Year_First_Committee.png`
- [ ] `Figure 6_Share_of_Identical_Votes_per_Dyad_First_Committee.png`
- [ ] `Figure 7_Voting_Alignment_Against_the_United_States_UNGA.png`
- [ ] `Figure 8_Voting_Alignment_Against_the_United_States_First_Committee.png`
- [ ] `Figure 9_Share_of_Western_Democracies_Votes_and_Alignment_with_UN_Majority_UNGA.png`

### Tables (4 LaTeX files)
- [ ] `Table_2_Topic_Distribution_of_Resolutions_where_CRINK_States_Fully_Aligned_in_the_UNGA_Plenary_1991-2024.tex`
- [ ] `Table3_dyad_alignment_table_China_UNGA.tex`
- [ ] `Table4_dyad_alignment_table_China_First_Committee.tex`
- [ ] `Table5_dyad_alignment_table_US_UNGA.tex`

## Troubleshooting

### Import Errors
If you see `ModuleNotFoundError`, ensure the virtual environment is activated and run:
```bash
pip install -r requirements.txt
```

### File Not Found Errors
Verify data files were extracted correctly:
```bash
python -c "from pathlib import Path; print('OK' if Path('data/processed/UNGA_voting_records_filtered.csv').exists() else 'MISSING')"
```

### Memory Issues
The UNGA dataset is large (~300MB). If you encounter memory errors:
- Close other applications
- Restart the Jupyter kernel between notebook runs

## No API Keys Required

All embeddings and topic mappings are pre-computed. No OpenAI API key or internet connection is required for reproduction.

## Expected Runtime

- Notebook 1 (per dataset): ~2-5 minutes
- Notebook 2: ~1-2 minutes
- Total: ~10-15 minutes

## Contact

For issues with reproduction, open an issue on the GitHub repository.
