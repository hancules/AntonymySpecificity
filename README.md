# Antonymy Co-occurrence Features Dataset

This repository provides a dataset of **semantic relation word pairs** with their co-occurrence statistics, derived from the [Corpus of Contemporary American English (COCA)](https://www.english-corpora.org/coca/).

---

## Dataset Overview

Each row corresponds to a word **lemma pair** (target, relatum), annotated with:

- its **semantic relation** (e.g., antonymy, synonymy),
- its **part of speech** (POS),
- and **co-occurrence statistics** measured from COCA.

The dataset includes both semantically related pairs and unrelated (`UNR`) control pairs.

---

## Example Fields

| Column Name       | Description |
|-------------------|-------------|
| `target`          | Target word lemma |
| `target_freq`     | Sentence frequency of the target |
| `target_form`     | Target word form (only for co-occurrence-features-wf.csv) |
| `relatum`         | Relatum word lemma |
| `relatum_freq`    | Sentence frequency of the relatum |
| `relatum_form`    | Relatum word form (only for co-occurrence-features-wf.csv) |
| `pos`             | Shared part of speech (`NOUN`, `VERB`, `ADJ`, `ADV`) |
| `relation`        | Semantic relation: `ANT`, `SYN`, `HYP-HPO`, `HOL-MER`, `UNR`. Note all are symmetric. |
| `relatum_is`      | Role of the relatum to the target word (`ANT`, `SYN`, `HYP`, `HPO`, `HOL`, `MER`, `UNR`). Unlike `relation`, this column preserves directionality — for example, `HYP` and `HPO` are treated as distinct |
| `g_square_score`  | G² (log-likelihood ratio) score for sentence-level co-occurrence |
| `g_pvalue`        | p-value for G² significance test |
| `order`           | Average word order: +1 (target precedes), -1 (relatum precedes), 0 (no preference) |
| `order_pvalue`    | p-value for binomial test of word order |
| `distance`        | Average number of tokens between the two words in co-occurring sentences |

---

## Notes

- Co-occurrence is measured at the **sentence level**.
- Words in relations are matched using **COCA’s lemma and PoS annotations**.
- co-occurrence-features.csv includes **31,522 lemma pairs**, spanning **four parts of speech** and **five relations**.
- co-occurrence-features-wf.csv includes **123,755 word form pairs**, which present information regarding co-occurrence of word forms, i.e. with inflection considered, supporting analysis with in a finer level.
- `UNR` (unrelated) pairs are randomly sampled with frequency and length filtering.



