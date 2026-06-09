# OASIS–JUMP Drug–Gene Morphological Matching

An exploratory analysis extending the OASIS Cell Painting framework beyond toxicity prediction by linking drug-induced morphological phenotypes to CRISPR gene perturbations from the JUMP Cell Painting consortium.

Please check the full project report: `OASIS-jump exploration_ParulK.pdf` uploaded on this repository.

## Project Overview

Ewald et al. (2026) introduced OASIS, a large-scale Cell Painting resource generated in primary human hepatocytes for cytotoxicity and mechanism-of-action analysis. A key insight from the study is that morphology captures integrated cellular responses rather than direct biochemical target engagement.

This project explores whether morphology-derived similarity can be used to connect drug-induced phenotypes with genetic perturbations across independent Cell Painting datasets.

To investigate this question, I reconstructed the published OASIS preprocessing workflow directly from the repository source code, including metadata generation, MAD normalization, and feature selection. I then integrated OASIS drug profiles with CRISPR knockout profiles from the JUMP Cell Painting consortium and performed morphology-based drug–gene matching.

## What Was Done

* Reproduced the core OASIS preprocessing workflow from source code.
* Recovered chemical identifiers omitted from the released OASIS metadata.
* Mapped OASIS DILI compounds to JUMP compounds using reconstructed InChIKey annotations.
* Downloaded and processed 148 JUMP CRISPR plates containing 7,977 gene knockouts.
* Integrated OASIS and JUMP profiles using PCA and Harmony batch correction.
* Generated a morphology-based drug–gene similarity map spanning 7,977 genetic perturbations.

## Dataset Summary

| Dataset                        | Size                       |
| ------------------------------ | -------------------------- |
| OASIS CellProfiler profiles    | 21,455                     |
| Features after preprocessing   | 833                        |
| JUMP CRISPR perturbation wells | 51,185                     |
| Unique CRISPR knockouts        | 7,977                      |
| Final similarity matrix        | 12 compounds × 7,977 genes |

## Key Findings

Harmony reduced source-specific structure between datasets (source silhouette: **0.338 → 0.102**), enabling cross-dataset comparison of compound and genetic perturbations.

The strongest morphology-based drug–gene relationships were:

| Compound         | Gene  | Similarity | Rank       |
| ---------------- | ----- | ---------- | ---------- |
| Panobinostat     | PLK1  | 0.991      | 1 / 7,977  |
| (E/Z)-Belinostat | MED17 | 0.927      | 31 / 7,977 |

Notably, canonical drug targets were generally not among the strongest matches. Instead, the highest-ranking relationships involved downstream cellular regulators, supporting the idea that Cell Painting captures systems-level cellular responses and pathway-level effects rather than direct target engagement.

## Conclusion

This project demonstrates the feasibility of linking OASIS drug-induced morphological phenotypes to JUMP genetic perturbations through a shared Cell Painting feature space. Beyond reproducing the published OASIS workflow, it extends the framework into a new application area by using morphology to generate mechanistic hypotheses connecting chemical and genetic perturbations.

## References

1. Ewald JD et al. (2026). *Cell Painting for cytotoxicity and mode-of-action analysis in primary human hepatocytes*. Cell Systems, 17(5), 101566.
2. Chandrasekaran SN et al. (2023). *JUMP Cell Painting dataset: morphological impact of chemical and genetic perturbations*.
3. Korsunsky I et al. (2019). *Fast, sensitive and accurate integration of single-cell data with Harmony*. Nature Methods, 16(12), 1289–1296.


## Original Resources

This project builds upon the OASIS Cell Painting resource and associated analysis pipeline:

- OASIS manuscript: Ewald et al. (2026), *Cell Painting for cytotoxicity and mode-of-action analysis in primary human hepatocytes*, Cell Systems.
- Original OASIS repository: https://github.com/jessica-ewald/2024_09_09_Axiom_OASIS
- JUMP Cell Painting Consortium: https://github.com/jump-cellpainting

This repository is an independent exploratory extension and is not affiliated with the OASIS or JUMP projects.
