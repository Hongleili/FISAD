# FISAD: First Impression Static Appearance Dataset

This repository accompanies the Data Descriptor "FISAD: A Large-Scale Full-Body Apparel Dataset for Studying Apparent Personality Trait Perception," submitted to *Scientific Data*. It was first presented (without archived proceedings) at the UK Academy for Information Systems (UKAIS) Conference, 2024, Kent, UK.

## Analysis code

Code for the technical validation reported in the accompanying Data Descriptor (reliability decomposition, predictive baselines, causal screening) is permanently archived on Zenodo: **https://doi.org/10.5281/zenodo.22239807** (MIT licence), linked to the source repository at github.com/Hongleili/FISAD-code (release v1.0.0).

## Permanent archive

This dataset (`FISAD_data.csv`) is permanently archived on Zenodo: **https://doi.org/10.5281/zenodo.22238732** (CC BY 4.0 licence). Please cite this DOI, not just the live GitHub repository, when referencing this dataset — GitHub repositories can be moved, renamed, or deleted, while the Zenodo DOI is permanent.

## Contents of this repository

- `FISAD_data.csv` — annotation and attribute data for all 6,000 images (converted from the original `data.numbers` file for open, tool-independent access)
- `/code` — analysis scripts used for technical validation (reliability decomposition, baseline predictive models) *[to be added — see Outstanding Items below]*

## Where to find the images

**IMPORTANT LICENSING NOTE**: images are derived from the Multi-pose Virtual Try-On (MPV) dataset (Dong et al., 2019), which is distributed by its original authors under a **restricted, non-commercial research-only basis, with no open-source or Creative Commons licence**. The images themselves are **not** redistributed via this repository or any other openly-accessible channel — the `path` column contains an identifier for mapping FISAD's annotations onto the corresponding MPV images, not a licence to freely redistribute those images.

**Update: the `github.com/johnwwwl/imgs` repository has been set to private**, resolving the public-hosting risk. The `path` column values in `FISAD_data.csv` still reference this location, but should now be treated as internal identifiers only, not functional download links for external users.

Researchers wishing to obtain the images should request access to MPV directly from its original authors (Dong et al., 2019) and use the identifiers in `FISAD_data.csv` to align FISAD's annotations with the corresponding MPV images.

The CC BY 4.0 licence on this dataset's Zenodo record (see below) applies only to FISAD's own contributions — the annotations and metadata — not to any MPV-derived image content.

## `FISAD_data.csv` column reference

| Column | Description |
|---|---|
| `id` | Unique image identifier |
| `path` | Image file path/URL |
| `No_compare` | Number of pairwise comparisons the image received during annotation (mean 14.02) |
| `a`, `e`, `o`, `c`, `n` | Big Five trait scores: Agreeableness, Extraversion, Openness, Conscientiousness, Neuroticism (proportion of pairwise "wins," range 0–1) |
| `Tops`, `Bottom` | Garment type annotations |
| `Sleeve` | Sleeve length annotation |
| `Hair Style`, `Hair Color` | Hair attribute annotations |
| `Clothing Color` | Free-text colour description |
| `Tops Color`, `Bottom Color` | Structured colour category fields (completed via vision-based extraction; see "Known data considerations" below) |
| `Dresses`, `Outerwear`, `Activewear` | Additional garment-category fields, populated only where applicable |
| `Clothing pattern` | Pattern-related field, free text (the previously duplicate empty `Clothing Pattern` column has been removed as of this version) |
| `Accessories` | Free-text accessory description |
| `Person`, `Emotion`, `Description` | Additional descriptive fields from the original annotation/labelling pipeline |

## Known data considerations (documented transparently per the Data Descriptor's Technical Validation section)

- **Annotation reliability**: at the current annotation density (mean 14.02 raters/image), estimated inter-rater reliability ranges from 0.116–0.152 across the five traits. See the Data Descriptor's Technical Validation section for the full reliability decomposition and guidance on annotation density needed for stronger reliability.
- **`Tops Color` / `Bottom Color`**: populated via vision-based extraction (Claude Haiku 4.5), using the already-confirmed `Tops`/`Bottom` garment-type labels as context. Validated against manual visual inspection on spot-checked images, and cross-checked against an independent, earlier extraction run for consistency (both runs agree that Black, not Blue, is the most common Tops colour — differing from the originally published category distribution, which may have conflated overall/primary garment colour with top-garment-specific colour; this discrepancy is noted for transparency and discussed in the Data Descriptor's Technical Validation section).
- **`Tops` (garment type) cleaning**: the originally released `Tops` column contained 43 near-duplicate categories (e.g., "T-Shirts", "T-shirts", "T-Shirt" as separate values) and some literal AI-generated hedge text (e.g., "Turtleneck (not listed, closest match would be Sweaters)"), inherited from the raw ChatGPT-4.0 output. This has been cleaned to 10 canonical categories, which closely reproduce the originally published category distribution (see the Data Descriptor's Figure 3).

## Outstanding items before final release

- [x] **RESOLVED**: the `johnwwwl/imgs` GitHub repository has been set to private, since it hosted MPV-derived images restricted to non-commercial research use only. Note: the `path` column in `FISAD_data.csv` now points to a private repository and is no longer usable by external researchers as a direct download link - it should be treated as an internal reference identifier only. Researchers wishing to obtain the images should request MPV directly from its original authors.
- [x] Confirm and populate final canonical `Tops Color` / `Bottom Color` values — done via vision-based extraction; see "Known data considerations" above for the noted discrepancy with the originally published distribution.
- [x] Resolve the `Clothing Pattern` / `Clothing pattern` duplicate-column issue — done; the duplicate empty column has been removed.
- [x] Add analysis code (`/code`) for reliability decomposition and baseline predictive modelling reported in the Data Descriptor — done (https://doi.org/10.5281/zenodo.22239807, MIT licence)
- [x] Create a Zenodo-archived DOI snapshot of the annotation CSV — done (https://doi.org/10.5281/zenodo.22238732, CC BY 4.0, covering annotations/metadata only, not images).
- [ ] Reconcile annotation count figures (2,211 participants x 18 retained comparisons vs. 84,129 total annotations vs. sum of No_compare = 84,120) — these do not currently reconcile cleanly; needs clarification of exact definitions from the original data collection team.
- [ ] Add LICENSE file (CC BY 4.0 for annotations/metadata; explicitly note this does NOT cover any MPV-derived image content)

## Citation

If you use this dataset, please cite:

[Full citation to be added upon publication of the Scientific Data Descriptor.]

Wang, J., Li, H., & Woo, W.L. (2024). Apparel Matters? A New First-Impression Static Appearance Dataset. Presented at the UK Academy for Information Systems (UKAIS) Conference, Kent, UK.

## Contact

Corresponding author: Honglei Li, School of Computer Science, Northumbria University.
