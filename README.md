# Legislative Attention to Social Determinants of Mental Health
## ITEC/SIS-724 Final Project — American University, Spring 2026

This repository contains the code report and analysis files for my final project in
Advanced Text Analytics with AI and Machine Learning (Prof. Cogburn).

## Research Questions

**RQ1. How frequently do state mental health bills mention specific social determinant
domains, and which domains are most prominent?**
- RQ1a. Which domain terms are most frequent by TF?
- RQ1b. Which terms are most distinctive by TF-IDF?
- RQ1c. Which bigrams and trigrams recur most often within each domain?

**RQ2. How does the use of social determinant domain language vary by state, session
year, and party control?**
- RQ2a. Which states use the highest share of neighborhood/built environment or
  discrimination, equity, and rights language?
- RQ2b. Does domain language increase or decrease over time?
- RQ2c. Are certain domains more common under Democratic, Republican, or divided
  party control?

**RQ3. What terms, phrases, and named entities distinguish bills with high versus low
levels of social determinant language?**
- RQ3a. Which words and phrases are most distinctive in high-domain bills?
- RQ3b. Which organizations, agencies, programs, or place names appear most often
  in high-domain bills?
- RQ3c. Do high-domain bills reference schools, housing authorities, Medicaid, or
  local governments more often than low-domain bills?

**RQ4. What latent themes emerge in mental health bills, and how do those themes
relate to concrete social determinant domains?**
- RQ4a. Which topics are most common in the corpus?
- RQ4b. Which topics co-occur with high neighborhood/built environment, education
  access, or discrimination/equity/rights scores?
- RQ4c. Do some states or session years show stronger topic-domain combinations
  than others?

## Data

- **Corpus:** 3,169 introduced mental health bills from 10 U.S. states (2021–2024)
- **States:** New York, Illinois, Texas, Florida, California, Pennsylvania,
  Washington, Georgia, Wisconsin, Ohio
- **Sessions:** Regular sessions with comparisons centered on 2021 vs. 2023
  session starts (Florida's annual sessions aligned for comparability)
- **Source:** LegiScan state bill data (JSON format)

## Methods

### Inductive (Exploratory)
- **Term Frequency (TF) and TF-IDF** — keyword frequency analysis at the bill
  level and class level (high vs. low SDOH bills) to identify prominent and
  distinctive domain terms
- **N-gram analysis** — bigram and trigram frequency including domain-matched
  phrase counts to surface recurring multi-word expressions
- **Named Entity Recognition (NER)** — spaCy via spacyr; extracted people,
  places, organizations, acronyms, and currency references; analysis focused on
  ORG and GPE entities (LAW excluded due to citation/format artifacts)

### Deductive (Confirmatory)
- **Categorization via Dictionary Development** — custom SDOH domain dictionary
  (unigrams, bigrams, and trigrams) developed to score and flag bills by domain
  (education, healthcare, community, equity, neighborhood, etc.)
- **Sub-Group Comparisons** — domain language shares compared across state,
  session year (2021 vs. 2023), and party control (Democratic, Republican,
  divided)

### Advanced Method
- **LDA Topic Modeling** — topicmodels package; k=20 topics, with procedural/
  artifact topics excluded from substantive comparisons; topic-domain correlations
  and state/year breakdowns used to address RQ4

## Key Finding

I find that all six social determinant domains are referenced in the corpus, but with uneven frequency and distribution. Bills with high social determinant content disproportionately reference public payers and health and human-services agencies, and topic models suggest that upstream concerns are often channeled through education, advisory bodies, and justice-system themes rather than narrowly clinical topics. These patterns highlight uneven but measurable legislative attention to upstream determinants in state mental health policy.

## Repository Contents

- `project_code_template.qmd` — Quarto code report (source)
- `project_code_template.pdf` — Rendered PDF of the code report
- `project_paper_template.qmd` — HICSS-format paper (source)
- `project_paper_template.pdf` — Rendered PDF of the paper
- `data/` — Processed analysis outputs (CSV files, one per RQ)
- `output/figures/` — Generated visualizations (PNG)
- `references.bib` — Bibliography
- `hicss_quarto.tex` — HICSS LaTeX template
- `apa.csl` — Citation style file

## Tools & Languages

R, Python, Quarto · tidytext, quanteda, topicmodels, spacyr (spaCy), ggplot2