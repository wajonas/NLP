# Sentiment Analysis of Austrian Parliamentary Speeches (ParlaMint-AT)

This repository contains the code and notebooks for our NLP project on sentiment in Austrian parliamentary speeches.

## Research question

> How has the linguistic sentiment in Austrian parliamentary speeches evolved between 1996 and 2022, and how does it differ across political parties?

## Data

The analysis is based on the **ParlaMint-AT** corpus (Austrian parliament), which is part of the ParlaMint project.  
The corpus was downloaded from the CLARIN.SI repository:

https://clarin.si/repository/xmlui/handle/11356/2005

Raw data are not included in this repository due to size and licensing.  
Locally, the ParlaMint-AT files are placed under `data/ParlaMint-AT.txt/` and are then converted into a cleaned, speech-level dataset that is saved as a Parquet file.

## What the project does

- loads and merges text and metadata from ParlaMint-AT  
- builds a tidy dataset with one row per speech (text, date, speaker, party, role, topic, …)  
- applies a **German sentiment model** (`oliverguhr/german-sentiment-bert`) to each speech  
- computes average sentiment over
  - years
  - parties
  - selected “peak years” with particularly negative sentiment (2000, 2018, 2021–2022)  
- creates visualizations of sentiment trends and party differences

## Main files

- `01_load_and_explore.ipynb` – data loading, cleaning and first exploration  
- `02_sentiment_analysis.ipynb` – full sentiment pipeline on all speeches  
- `03_visualization.ipynb` – plots and descriptive analyses  

## Requirements

The project is implemented in Python (Jupyter). Typical packages include:

- `pandas`, `pyarrow`
- `transformers`, `torch`
- `matplotlib`, `tqdm`, `jupyter`
