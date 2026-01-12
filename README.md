# Measuring CRINK Alignment in the UN

This repository contains python code for measuring the political alignment of China, Russia, Iran, and North Korea (CRINK) in the United Nations voting record. The data can be used to replicate the findings of the accompanying research article "Emerging Bloc or Fragmented Coalition? Voting Behavior of China, Russia, Iran, and North Korea at the UN" (forthcoming 2026). 

## Overview

This research examines the frequency, configuration, and issue-specific contours of CRINK voting alignment using United Nations General Assembly (UNGA) plenary from 1991-2024 and First Committee voting records from 2003-2024. The analysis situates CRINK alignment relative to Western democracies and the UN majority, providing a systematic assessment of whether these four countries constitute a cohesive authoritarian bloc or a fragmented coalition.

## Summary

We find a marked consolidation of collective voting in the plenary since the early 2000s, alongside a simultaneous decline in alignment with the UN majority. This pattern does not extend to the First Committee: on security and disarmament issues, alignment remains substantially lower, volatile, and without a sustained upward trajectory. Across both arenas, alignment is not primarily dyadic; group-of-four and triadic voting dominate, and the China–Russia dyad is neither the strongest nor the most consistent. China occupies an anchoring position, with Russia, Iran, and North Korea aligning more frequently with China than with one another.

Issue-specific analyses reveal cohesion on outer-space security and state-centric cyber governance, but fragmentation on humanitarian and arms-control agendas. A systematic comparison with Western democracies shows parallel trends of rising intra-group cohesion and declining majority alignment, underscoring a broader pattern of polarization in contemporary international politics.

## Expected Output Files

After executing both notebooks, the following files will be generated in the `results/` directory:

### Figures (PNG format, 300 DPI)

- `Figure 1_Share_of_Group_Votes_and_Alignment_with_UN_Majority_UNGA.png` - CRINK voting alignment trends in UNGA Plenary (1991-2024)
- `Figure 2_Share_of_Group_Votes_and_Alignment_with_UN_Majority_First_Committee.png` - CRINK voting alignment in First Committee (2003-2024)
- `Figure 3_Share_of_CRINK_Coalition_Sizes_by_Year_UNGA.png` - Coalition size distribution over time (UNGA)
- `Figure 4_Share_of_Identical_Votes_per_Dyad_UNGA.png` - Pairwise voting alignment within CRINK (UNGA)
- `Figure 5_Share_of_CRINK_Coalition_Sizes_by_Year_First_Committee.png` - Coalition size distribution (First Committee)
- `Figure 6_Share_of_Identical_Votes_per_Dyad_First_Committee.png` - Pairwise voting alignment (First Committee)
- `Figure 7_Voting_Alignment_Against_the_United_States_UNGA.png` - Anti-US voting patterns (UNGA)
- `Figure 8_Voting_Alignment_Against_the_United_States_First_Committee.png` - Anti-US voting patterns (First Committee)
- `Figure 9_Share_of_Western_Democracies_Votes_and_Alignment_with_UN_Majority_UNGA.png` - Western democracies comparison (UNGA)

### Tables (LaTeX format)

- `Table_2_Topic_Distribution_of_Resolutions_where_CRINK_States_Fully_Aligned_in_the_UNGA_Plenary_1991-2024.tex` - Topic distribution of CRINK-aligned resolutions
- `Table3_dyad_alignment_table_China_UNGA.tex` - China-centric dyadic alignment (UNGA)
- `Table4_dyad_alignment_table_China_First_Committee.tex` - China-centric dyadic alignment (First Committee)
- `Table5_dyad_alignment_table_US_UNGA.tex` - US-centric dyadic alignment comparison

> **Note:** LaTeX tables require a TeX editor (e.g., [Overleaf](https://www.overleaf.com/) or [Papeeria](https://papeeria.com/)) to render properly.

### Intermediate Files (`results/intermediate/`)

- `resolutions_with_metatopics_UNGA.csv` - Full dataset with topic assignments per resolution
- `table_dyadic_alignment_*.csv` - Dyadic alignment matrices
- `table_pair_statistics_*.csv` - Pairwise voting statistics
- `Table*_*.html` - HTML previews of tables (for browser viewing)

## Data Sources

### Primary Data
- **UNGA Plenary Votes**: UN General Assembly voting records (1991-2024) from the [UN Digital Library](https://digitallibrary.un.org/record/4060887?ln=en)
- **First Committee Votes**: UN General Assembly First Committee voting data (2003-2024) on security, disarmament, and arms control issues from the [UNODA Resolutions Database](https://resolutions.unoda.org/)

### Data Availability
Raw UNGA voting records are publicly available from the UN. Processed datasets and First Committee data will be available through a ZIP archive for the review process and [Harvard Dataverse](https://dataverse.harvard.edu/) after publication for reproducibility.

## Repository Structure

```
measuring-CRINK-alignment-UN/
├── README.md                           # This file
├── LICENSE                             # MIT License
├── requirements.txt                    # Python dependencies
├── .gitignore                          # Git ignore patterns
├── .env.example                        # Template for environment variables
│
├── data/
│   ├── raw/                           # Original data files (not in repo)
│   ├── processed/                     # Cleaned/processed datasets
│   ├── mappings/                      # Pre-computed embeddings and topic mappings
│   └── metadata.json                  # Data provenance and versions
│
├── notebooks/
│   ├── 01_alignment_metrics.ipynb     # CRINK alignment metrics (Figures 1-9; Tables 3-5)
│   └── 02_generating_topic_analysis.ipynb  # Topic-level voting analysis (Table 2)
│
├── src/
│   ├── __init__.py
│   ├── data_processing.py             # Data loading and cleaning
│   ├── alignment_metrics.py           # Alignment calculation functions
│   └── visualization.py               # Plotting functions
│
├── config/
│   ├── config.yaml                    # Analysis configuration (no secrets)
│   └── .env.example                   # Template for environment variables
│
├── results/                           # Output directory for publication files
│   ├── Figure 1-9 (*.png)             # Publication figures
│   ├── Table 2-5 (*.tex)              # LaTeX tables for publication
│   └── intermediate/                  # Working files (CSVs, HTML previews)
│
└── docs/
    ├── methodology.md                 # Detailed methodology
    ├── data_dictionary.md             # Data column descriptions
    └── troubleshooting.md             # Common issues and solutions
```

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/SubmisssionReview/measuring-CRINK-alignment-UN.git
cd measuring-CRINK-alignment-UN
```

### 2. Set Up Python Environment

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Configure API Access

Create a `.env` file in the project root with your OpenAI API key:

```
OPEN_AI_API=your_api_key_here
```

See `.env.example` for the template.

### 4. Download Data

Download the processed datasets from Harvard Dataverse (link to be provided upon publication). Place them in the `data/processed/` directory.

### 5. Run Notebooks

Open and execute the notebooks in order:

```bash
jupyter notebook notebooks/01_alignment_metrics.ipynb
jupyter notebook notebooks/02_generating_topic_analysis.ipynb
```

> **Important:** Notebook `01_alignment_metrics.ipynb` must be executed **twice** - once for each dataset:
> 
> 1. **First run (UNGA Plenary):** In the dataset selection cell, ensure `database = 'UNGA'` is uncommented
> 2. **Second run (First Committee):** Change to `database = 'First Committee'`
> 
> The dataset selection appears in two cells (for tables and figures). Search for `database =` to find them.
> 
> This generates separate figures and tables for each dataset (Figures 1-4, 7, 9 for UNGA; Figures 2, 5-6, 8 for First Committee).

## Reproducibility

The analysis in this project is reproducable if the following settings are kept stable. 

- **Fixed random seeds** for all stochastic operations
- **Pinned package versions** in `requirements.txt`
- **Documented configurations** with commented values used in published research

### Environment

- **Python**: 3.9+
- **OpenAI API**: Required for topic mapping (gpt-4o-mini model)
- **Data**: Pre-computed embeddings cached to avoid redundant API calls

## Analysis Configuration

Key parameters (used in published research):

```python
# Topic analysis
EMBEDDING_MODEL = ─text-embedding-3-large─
HDBSCAN_MIN_CLUSTER_SIZE = 10
TARGET_META_TOPICS = 20

# Geographic groups (hard-coded)
CRINK_COUNTRIES = [
    'CHINA',
    'RUSSIAN FEDERATION',
    'IRAN (ISLAMIC REPUBLIC OF)',
    ─DEMOCRATIC PEOPLE'S REPUBLIC OF KOREA─
]

WESTERN_COUNTRIES = [
    'UNITED STATES',
    'GERMANY',
    'FRANCE',
    'UNITED KINGDOM'
]

# Analysis periods (configurable but documented)
UNGA_START_YEAR = 1991
FIRST_COMMITTEE_START_YEAR = 2003
END_YEAR = 2024
```

## Documentation

- **[Methodology](docs/methodology.md)**: Detailed explanation of data sources, processing steps, and analytical approach
- **[Data Dictionary](docs/data_dictionary.md)**: Complete description of all dataset columns and variables
- **[Troubleshooting](docs/troubleshooting.md)**: Solutions to common issues

## Citation

Citation information will be provided upon publication.

## Data Availability

Processed datasets and reproducible notebooks will be available at:
- **GitHub**: [Repository URL to be added upon publication]
- **Harvard Dataverse**: [Link to be added] (DOI: TBD)

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## Contact

For questions or issues, please open an issue on the repository.
