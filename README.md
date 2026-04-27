# Project: Lights, Camera, Data Analysis

## Overview
The world of cinema and TV is a cut-throat market. Actors and directors must look for any edge they can to get ahead and stay ahead relative to their peers and make a name for themselves. The analysis conducted in `main_notebook.py` utilizes the **IMDb Non-Commercial Dataset** collection to link actors and directors to the works they contributed to as well as the ratings associated with such works. The experimentation evaluates interaction graphs of both the director and actor populations, where edges between individuals (nodes) represent that these individuals collaborated on at least one work. The experiments conducted explored how various properties of nodes in these interaction graph could be correlated to actor/director success.

## Experimentation: https://github.com/pmarshall21/CSCE_676/blob/main/notebooks/main_notebook.ipynb

## Research Question: Can you use properties of actor/director interaction graphs as predictive tools for determining actor/director success

This question is explored by analyzing the trends and correlations between actor/director succcess and their PageRank value, community size, and proximity to success.

## Project Video: https://youtu.be/ZwpzEHjI--g

## Datasets
-  IMDb Non-Commercial Datasets
   - Source: https://datasets.imdbws.com/
   - Preprocessing: Early data analysis in `checkpoint_1.ipynb` indicated that the files in this dataset are well-maintained with little to no need for preprocessing of contents.

## Steps to Reproduce:
For the purpose of reproducing the results identified in `main_notebook.ipynb`, the following steps need to be performed in a Google Colab session (see `requirements.txt` for required libraries prior to reproducing):

1.   Upload the IMDb Non-Commercial Dataset files to a location in your Google Drive. Update the `PROJECT_DIR` and `DATASET_DIRS` variables accordingly in **Environment Setup** portion of the notebook. If using the IMDb dataset found in `data/` (rather than downloading directly from the source), you will need to have Git LFS configured.

2.   In the **Environment Setup** section, set `LOAD_FROM_PKL=False`. If you anticpate that you will rerun experimentation and wish to minimize the compute time associated with graph construction, set `STORE_TO_PKL=True`. Subsequent runs can then be performed with `LOAD_FROM_PKL=True`.

3.   Run the Jupyter notebook. **NOTE:** The amount of RAM requiered for the notebook to run exceeds that which is allocated using a default Google Colab session. It is required to run in a **High-RAM runtime**.

## Key Dependencies and Versions
- Key Dependendencies:
  - google 3.0.0
  - mlxtend 0.23.4
  - networkx 3.6.1
  - numpy 2.0.2
  - pandas 2.2.2
  - scipy 1.16.3
  - sklearn-compat 0.1.5
  - sklearn-pandas 2.2.0
- Python Version: 3.12.13

## Repo Structure
├── checkpoints
│   ├── checkpoint_1.ipynb
│   └── checkpoint_2.ipynb
├── data
│   ├── name.basics.tsv.gz
│   ├── title.akas.tsv.gz
│   ├── title.basics.tsv.gz
│   ├── title.crew.tsv.gz
│   ├── title.episode.tsv.gz
│   ├── title.principals.tsv.gz
│   └── title.ratings.tsv.gz
├── notebooks
│   └── main_notebook.ipynb
├── .gitattributes
├── .gitignore
├── README.md
└── requirements.txt

## Key Findings
#### PageRank
<table style="width:100%; border-collapse: collapse;">
  <tr>
    <th style="text-align:left; border: 1px solid #dddddd; padding: 8px; width: 15%;">Population</th>
    <th style="text-align:left; border: 1px solid #dddddd; padding: 8px; width: 85%;">Findings</th>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd; padding: 8px;"><strong>Director</strong></td>
    <td style="border: 1px solid #dddddd; padding: 8px;">No significant correlation was found between a director's structural importance (PageRank) and their career success (average ratings).</td>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd; padding: 8px;"><strong>Actor</strong></td>
    <td style="border: 1px solid #dddddd; padding: 8px;">Similar to directors, global graph metrics like PageRank were not strong predictors of individual success.</td>
  </tr>
</table>

<br>

#### Community Size
<table style="width:100%; border-collapse: collapse;">
  <tr>
    <th style="text-align:left; border: 1px solid #dddddd; padding: 8px; width: 15%;">Population</th>
    <th style="text-align:left; border: 1px solid #dddddd; padding: 8px; width: 85%;">Findings</th>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd; padding: 8px;"><strong>Director</strong></td>
    <td style="border: 1px solid #dddddd; padding: 8px;">No significant correlation was found between the size of their professional community and their career success.</td>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd; padding: 8px;"><strong>Actor</strong></td>
    <td style="border: 1px solid #dddddd; padding: 8px;">Similar to directors, community size was not a strong predictor of individual success.</td>
  </tr>
</table>

<br>

### Proximity to Success
<table style="width:100%; border-collapse: collapse;">
  <tr>
    <th style="text-align:left; border: 1px solid #dddddd; padding: 8px; width: 15%;">Population</th>
    <th style="text-align:left; border: 1px solid #dddddd; padding: 8px; width: 85%;">Findings</th>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd; padding: 8px;"><strong>Director</strong></td>
    <td style="border: 1px solid #dddddd; padding: 8px;">While directors who collaborated with top-tier (90th percentile) directors generally had higher ratings, a longitudinal analysis showed no significant improvement in ratings <em>after</em> the collaboration.<br><br>This suggests a <strong>selection bias</strong>: high-performing directors are simply more likely to be chosen for collaborations with other top directors.</td>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd; padding: 8px;"><strong>Actor</strong></td>
    <td style="border: 1px solid #dddddd; padding: 8px;">Unlike the director population, actors showed a <strong>statistically significant increase</strong> in their average ratings following their first collaboration with a top-10% actor.<br><br><strong>Control Comparison:</strong> When compared against a control group (actors who never worked with top-tier peers), the difference was stark: the 'treatment' group saw a rating bump, while the control group's ratings typically declined in the latter half of their careers.<br><br>This suggests that for actors, proximity to successful peers may be a genuine catalyst for career success.</td>
  </tr>
</table>
