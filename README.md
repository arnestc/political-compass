[![DOI](https://sandbox.zenodo.org/badge/758604966.svg)](https://sandbox.zenodo.org/doi/10.5072/zenodo.29436)

# Navigating Multidimensional Ideologies with Reddit’s Political Compass: Economic Conflict and Social Affinity

This repository contains code and data to reproduce our results from ***"Navigating Multidimensional Ideologies with Reddit’s Political Compass: Economic Conflict and Social Affinity"*** by Ernesto Colacrai, Federico Cinus, Gianmarco De Francisci Morales and Michele Starnini, published at [ACM Web Conference 2024 (WWW'24)]([https://www2023.thewebconf.org](https://www2024.thewebconf.org/)). If you use the provided data or code, we would appreciate a citation to the paper:

```
_citation_
```

Here you will find (i) the (anonymized) Reddit dataset we presented in the paper and (ii) the code to reproduce our experiments.

## Reddit Data Set

[You can download our anonymized Reddit `r/PoliticalCompass` (and `/r/PoliticalCompassMemes`) data sets from here](https://github.com/arnestc/political-compass/releases/download/Latest/data.zip).

Each username is consistently replaced with an anonymized number.

- `blacklist_anonymized.joblib`: list of users (anonymized) classified as [bots](https://doi.org/10.1007/978-3-031-19097-1_1).

For each of the analyzed subreddits (`/r/PoliticalCompass` as `PC` and `/r/PoliticalCompassMemes` as `PCM`), the data set contains these CSV files.

- `submissions_anonymized_SUBREDDIT.csv`: each line corresponds to a submission on the SUBREDDIT, including the anonymized username of its author, flair associated with the author (ideology on the Political Compass), and the time of creation (UTC format) of the submission. Data go from 2012 to 2022, and in [code/notebooks/0.1-Data-Pre-Processing-PC-PCM.ipynb] are selected only data in the period 2020-2022 (included).
- `comments_anonymized_SUBREDDIT.csv`: each line corresponds to a comment on the SUBREDDIT, including the anonymized username of its author, flair associated with the author (ideology on the Political Compass), and the time of creation (UTC format) of the submission. Data go from 2012 to 2022, and in [code/notebooks/0.1-Data-Pre-Processing-PC-PCM.ipynb] are selected only data in the period 2020-2022 (included).
- `edges_anonymized_SUBREDDIT.csv`: each line corresponds to a comment on the SUBREDDIT done during 2020-2022. The file lists the author of the comment, the author of the parent comment to which this comment is replying, and the sentiment of the text of the interaction. This can be seen as a weighted graph among users.
- `popularity_anonymized_SUBREDDIT.csv`: each line corresponds to the author and the list of the scores associated with each of his comments in the SUBREDDIT. Those data are used to analyze possible confounding effects of Reddit.
- `socio_demographics_anonymized_SUBREDDIT.csv`: for each Reddit user of the SUBREDDIT included in the analysis, this file reports their anonymized username and their score on the age, gender, partisan, and affluence axes (included also ideologies flairs for analysis). Scores are quantile-normalized, so that i.e. a score of 0.25 indicates the 25th percentile. The axes respectively correspond to the probability of being young (low) or old (high), male or female, poor or rich, and left-leaning or right-leaning.
- `edges_anonymized_with_toxicity_SUBREDDIT.csv`: each line corresponds to an edge of the interaction network of the SUBREDDIT with the author of the comment, the author of the parent comment to which this comment is replying to, the body (as empty string for anonymization reasons), the social and economic ideologies of both the author and the parent author, and the toxicity value get from the original body of the comment.

See the paper for more details about how we extracted this information.
The total number of considered users and comments is

| SUBREDDIT     | /r/PC   | /r/PCM  |
|---------------|---------|---------|
| N. nodes      | 18135   | 173672  |
| N. edges      | 215111  | 6197901 |

## Reproducibility

To reproduce our experiments, we provide all our notebooks to generate the analysis and the plot from the data set. In particular, you have to:

- [download the data set](https://github.com/arnestc/political-compass/releases/download/Latest/data.zip) and unzip its content in `data/raw/`;
- create the [Conda environment](https://github.com/arnestc/political-compass/blob/main/environment.yml): `conda env create -f environment.yml`;
- you can reproduce the analysis and generate the plots from the paper using the [provided notebooks] (link_to_notebooks_folder).

For further information or needed data, please contact me: `ernesto.colacrai@gmail.com`.
