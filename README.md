# Story Attributes and Movie-Rating Prediction

CS 7375 · Fall 2026

This project investigates whether story attributes extracted from movie plot summaries improve prediction of users' 1–5 ratings beyond user/movie identities and genres.

## Notebook

`semester_project.ipynb` defines the provisional story-attribute vocabulary, locates the raw datasets, checks their record counts and identifiers, and calculates SHA-256 hashes for reproducibility. Dataset matching, attribute extraction, and model evaluation are planned extensions.

## Experiment design

Compare a factorization machine with three sets of inputs:

| Version | Inputs |
|---|---|
| A | User ID + movie ID |
| B | User ID + movie ID + MovieLens genres |
| C | User ID + movie ID + MovieLens genres + story attributes |

The main comparison is C versus B. All versions will use the same retained ratings and train/validation/test partitions, with comparable tuning. RMSE is the primary metric; MAE is secondary.

MovieLens movies will be linked to CMU summaries using normalized titles and exact release years. Ambiguous matches will be excluded. A provisional minimum of 100 words per summary will be used to retain sufficient text for attribute extraction.

Each extracted attribute must have a meaningful role in the story and supporting evidence in the summary. An initial pilot of 20 summaries, with three extraction runs per summary, will assess evidence quality, repeatability, and processing cost before the vocabulary and procedure are finalized.

## Datasets

Raw datasets are excluded from Git. Place the following folders alongside the notebook:

- `MovieLens 1M Dataset/ml-1m/`: `movies.dat`, `ratings.dat`, `users.dat`, and the original `README`. [MovieLens 1M](https://grouplens.org/datasets/movielens/1m/) contains 1,000,209 ratings from 6,040 users, covering 3,706 rated movies. Its movie metadata contains 3,883 records.
- `CMU Movie Summary Corpus/MovieSummaries/`: the extracted [CMU corpus](https://www.cs.cmu.edu/~ark/personas/), including `movie.metadata.tsv` and `plot_summaries.txt`. The corpus contains 81,741 movie metadata records and 42,306 summaries. Preserve the included README and attribution.

The [CMU archive](https://www.cs.cmu.edu/~ark/personas/data/MovieSummaries.tar.gz) has SHA-256:

`6c3bd3d42046c4b87e2267f2e2599ba6f651b8ad23a8998237c3d2bb338ac559`

The notebook records hashes for the input files and reads the raw data without modifying them.

## Environment

The current notebook cells use Python's standard library and were verified with Python 3.12.6. Open the notebook in a Jupyter-compatible editor, select a Python kernel, and use the project directory or its parent as the working directory.

## References

- Abdollahpouri et al. (2021). *User-centered Evaluation of Popularity Bias in Recommender Systems*. UMAP, 119–129. [DOI](https://doi.org/10.1145/3450613.3456821). Local copy: `Evaluation of Popularity Bias/ALS.pdf`.
- Harper and Konstan (2015). *The MovieLens Datasets: History and Context*.
- Bamman, O'Connor, and Smith (2013). *Learning Latent Personas of Film Characters*. ACL.
