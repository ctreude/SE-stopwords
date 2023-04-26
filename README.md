[![DOI](https://zenodo.org/badge/632726416.svg)](https://zenodo.org/badge/latestdoi/632726416)

# SE Stopwords

## Overview

This repository contains stopword lists specifically tailored for natural language processing (NLP) tasks applied to software development documents. It aims to enhance the efficiency and accuracy of NLP applications on various types of software documentation, including bug reports, commit messages, and API documentation.

## Background and Motivation

Stop words, deemed non-predictive, are often eliminated in NLP tasks. However, the definition of uninformative vocabulary remains vague, leading most algorithms to use general knowledge-based stop lists. The effectiveness of stop word elimination, particularly in domain-specific settings, is debated among academics.

In a recent [paper](https://arxiv.org/abs/2303.10439), we investigated the usefulness of stop word removal in a software engineering context. To achieve this, we replicated and experimented with three software engineering research tools from related work. A corpus of software engineering domain-related text was constructed from 10,000 Stack Overflow questions, and 200 domain-specific stop words were identified using traditional information-theoretic methods.

The results demonstrated that using domain-specific stop words significantly improved the performance of research tools compared to a general stop list. Moreover, 17 out of 19 evaluation measures showed better performance.

## Performance Comparison Table

The table below summarizes the performance improvements when using different stopword lists compared to the baseline across 19 metrics.

<table>
  <thead>
    <tr>
      <th>Stop word list</th>
      <th colspan="3">Comparison to baseline across 19 metrics</th>
    </tr>
    <tr>
      <th></th>
      <th>Better</th>
      <th>Worse</th>
      <th>Same</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>SE Domain (TF-IDF) (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/tfidf_approach.txt">link</a>)</td>
      <td align="right">17</td>
      <td align="right">1</td>
      <td align="right">1</td>
    </tr>
    <tr>
      <td>SE Domain (Poisson) (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/possion_approach.txt">link</a>)</td>
      <td align="right">12</td>
      <td align="right">5</td>
      <td align="right">2</td>
    </tr>
    <tr>
      <td>Technology Domain (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/technology_domain_stopwords.txt">link</a>)</td>
      <td align="right">9</td>
      <td align="right">9</td>
      <td align="right">1</td>
    </tr>
    <tr>
      <td>Large (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/large_stopwords.txt">link</a>)</td>
      <td align="right">11</td>
      <td align="right">8</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td>Medium (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/medium.txt">link</a>)</td>
      <td align="right">11</td>
      <td align="right">7</td>
      <td align="right">1</td>
    </tr>
    <tr>
      <td>Small (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/small.txt">link</a>)</td>
      <td align="right">13</td>
      <td align="right">5</td>
      <td align="right">1</td>
    </tr>
    <tr>
      <td>Very Small (<a href="https://github.com/ctreude/SE-stopwords/blob/main/stopwords_lists/very_small.txt">link</a>)</td>
      <td align="right">10</td>
      <td align="right">7</td>
      <td align="right">2</td>
    </tr>
    <tr>
      <td>No Stop Words</td>
      <td align="right">4</td>
      <td align="right">12</td>
      <td align="right">3</td>
    </tr>
  </tbody>
</table>


## Usage Instructions

These stopword lists can be used to filter out uninformative words from software development documents, thereby improving the understanding and analysis of textual data in the software development domain.

To use these lists in your NLP tasks, simply import them into your project and apply them as filters during the pre-processing stage.

## Folder Structure

```
SE-stopwords
|-- data_for_replications (contains all the required data for replicating software engineering tools)
|   |-- Maalej_Dataset (original data for app review tool)
|   `-- queries (queries used for RACKTool)
|-- stackoverflow_questions (more than 10k top reviewed questions on stackoverflow)
|-- stopwords_lists (all the stoplists)
|-- replications
`-- stackoverflow (code for creating the domain-specific corpus)
```

## Detailed Results for the Three Replicated Tools

The results may vary by a small fraction depending on the trial, but they should be approximately the same as the tables below.

### Tool 1 (App Review)

|              	|    **PD &emsp;(bug report)** 	|       **RT &emsp;(rating)**     |     **FR &emsp;(feature request)**     |     **UE &emsp;(user experience)**     |
|:----------	|:---------------	|:---------------  |:---------------	|:---------------	|
|              	|    Pre&emsp;&emsp;Rec&emsp;&emsp;F1 	|       Pre&emsp;&emsp;Rec&emsp;&emsp;F1     |     Pre&emsp;&emsp;Rec&emsp;&emsp;F1     |     Pre&emsp;&emsp;Rec&emsp;&emsp;F1     |
|**SE domain (Poisson)** |      10.0%&emsp;37.5%&emsp;15.8%     |       72.1%&emsp;78.0%&emsp;74.9%  	|        7.1%&emsp;29.8%&emsp;11.5%     |      11.6%&emsp;32.0%&emsp;17.0%       |
|**SE domain (TF-IDF)** |      10.7%&emsp;40.2%&emsp;16.9%     |       72.2%&emsp;78.2%&emsp;75.1%  	|        7.9%&emsp;33.3%&emsp;12.8%     |      11.7%&emsp;32.5%&emsp;17.2%       |

### Tool 2 (RACK)

|              	|    **Top-10** 	|       **MRR@10**     |     **MAP@10**     |     **MR@K**     |
|:----------	|:---------------	|:---------------  |:---------------	|:---------------	|
|**SE domain (Poisson)** |     83.85%     |       52.29%  	|        43.27%     |      54.47%       |
|**SE domain (TF-IDF)** |      84.17%     |       53.20%  	|        45.82%     |      56.8%       |

### Tool 3 (Requirements Change Impact Analysis)

|              	|    **SE domain (Poisson)** 	|       **SE domain (TF-IDF)**     |
|:----------	|:---------------	|:---------------  |
|**Query 2**	|0.588	|0.588 |
|**Query 4**	|0.981	|0.981 |
|**Query 5**	|0.602	|0.602 |

## Citation

If you make use of this work, please cite:

```
@inproceedings{fan2023stop,
  title={Stop Words for Processing Software Engineering Documents: Do they Matter?},
  author={Yaohou Fan and Chetan Arora and Christoph Treude},
  booktitle={2023 IEEE/ACM 2nd International Workshop on Natural Language-Based Software Engineering (NLBSE)},
  year={2023},
  organization={IEEE}
}
```
