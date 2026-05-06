# MIMIC NLP: Acute Kidney Injury Entity Extraction

This project applies clinical natural language processing techniques to MIMIC-III discharge summaries for Acute Kidney Injury (AKI), using ICD-9 code `584.9` as the target condition.

The analysis compares general, biomedical, and clinical NLP approaches for extracting medical entities, creating word embeddings, and visualizing entity relationships.

## Project Contents

- `MIMIC_NLP_Assignment.ipynb` - Main notebook with the full analysis pipeline.
- `MIMIC NLP.pdf` - Final presentation slides with charts and results.
- `rebuild_slides.py` - Script used to regenerate the slide deck with notebook charts.

## Methods

The notebook includes:

- Data loading and preprocessing of MIMIC-III `NOTEEVENTS`.
- Filtering for AKI-related discharge summaries.
- Named entity recognition with:
  - SpaCy
  - SciSpaCy
  - MedSpaCy
- MedSpaCy ConText analysis for negation and clinical context.
- Word2Vec embeddings and nearest-neighbor comparison.
- t-SNE and UMAP visualizations.
- ClinicalBERT contextual embedding comparison.

## Key Results

- SciSpaCy provided the broadest biomedical entity coverage.
- MedSpaCy provided the most clinically precise and context-aware extraction.
- SpaCy served as a useful general-purpose baseline but missed many clinical terms.
- SciSpaCy Word2Vec neighbors were more clinically meaningful than SpaCy neighbors.
- The best t-SNE visualization used SciSpaCy embeddings with perplexity `30`, filtered to the top AKI entities.

## Data Access

This project uses MIMIC-III data, which is protected clinical data and is not included in this repository.

To reproduce the notebook, request access to MIMIC-III through PhysioNet:

https://physionet.org/content/mimiciii/

Place `NOTEEVENTS.csv` or `NOTEEVENTS.csv.gz` in the project directory before running the notebook.

## Running the Notebook

1. Install the required Python packages:

```bash
pip install -r requirements.txt
```

2. Download the required SpaCy/SciSpaCy models.
3. Place the MIMIC-III `NOTEEVENTS` file in the project directory.
4. Open and run `MIMIC_NLP_Assignment.ipynb`.

Example SpaCy setup:

```bash
python -m spacy download en_core_web_sm
```

Depending on the environment, additional SciSpaCy model installation may be required.

## Important GitHub Notes

Do not commit or upload raw MIMIC-III data files. The included `.gitignore` excludes `NOTEEVENTS.csv`, `NOTEEVENTS.csv.gz`, and other CSV files by default.

If publishing this repository publicly, review notebook outputs before uploading to ensure no protected note text or data excerpts are included.

## Notes

Raw MIMIC files, generated notebook checkpoints, cache files, and local macOS files are intentionally ignored by Git.
