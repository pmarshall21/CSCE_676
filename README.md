# Project: Lights, Camera, Data Analysis

## Overview

## Dataset Experimentation: 

## Research Question: Can you use properties of actor/director interaction graphs as predictive tools for determining actor/director success

This question is explored by analyzing the trends and correlations between actor/director succcess and their PageRank value, community size, and proximity to success.

## Project Video: https://youtu.be/ZwpzEHjI--g

## Steps to Reproduce:
For the purpose of reproducing the results identified in `main_notebook.ipynb`, the following steps need to be performed in a Google Colab session (see `requirements.txt` for required libraries prior to reproducing):

1.   Upload the IMDb Non-Commercial Dataset files to a location in your Google Drive. Update the `PROJECT_DIR` and `DATASET_DIRS` variables accordingly in **Environment Setup** portion of the notebook.

2.   In the **Environment Setup** section, set `LOAD_FROM_PKL=False`. If you anticpate that you will rerun experimentation and wish to minimize the compute time associated with graph construction, set `STORE_TO_PKL=True`. Subsequent runs can then be performed with `LOAD_FROM_PKL=True`.

3.   Run the Jupyter notebook. **NOTE:** The amount of RAM requiered for the notebook to run exceeds that which is allocated using a default Google Colab session. It is required to run in a **High-RAM runtime**.

## Key Dependencies and Versions

## Repo Structure

## Key Findings

