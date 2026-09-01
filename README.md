# FISAD: First Impression Static Appearance Dataset

This repository accompanies the Data Descriptor "FISAD: A Large-Scale Full-Body Apparel Dataset for Studying Apparent Personality Trait Perception," submitted to *Scientific Data*. It was first presented (without archived proceedings) at the UK Academy for Information Systems (UKAIS) Conference, 2024, Kent, UK.

## Permanent archive

This dataset (`FISAD_data.csv`) is permanently archived on Zenodo: **https://doi.org/10.5281/zenodo.22238732** (CC BY 4.0 licence). Please cite this DOI, not just the live GitHub repository, when referencing this dataset — GitHub repositories can be moved, renamed, or deleted, while the Zenodo DOI is permanent.

## Contents of this repository

- `FISAD_data.csv` — annotation and attribute data for all 6,000 images (converted from the original `data.numbers` file for open, tool-independent access)
- `/code` — analysis scripts used for technical validation (reliability decomposition, baseline predictive models) *[to be added — see Outstanding Items below]*

## Where to find the images

All 6,000 images are accessible via the `path` column in `FISAD_data.csv`, which links directly to each image hosted at `github.com/johnwwwl/imgs`. No separate download step is needed — each row's `path` value is a direct, publicly-accessible URL to that image.

Images are derived from a filtered subset of the Multi-pose Virtual Try-On (MPV) dataset (Dong et al., 2019); see the Data Descriptor for full sourcing and filtering criteria.

**Note on repository permanence**: GitHub repositories do not carry a persistent DOI by default, and Scientific Data's data policy recommends dedicated data repositories (e.g., Figshare, Dryad) or an archived, DOI-bearing snapshot for exactly this reason. Creating a Zenodo-archived release of the `johnwwwl/imgs` repository (a lightweight, free integration that assigns a persistent DOI to a GitHub repository snapshot) is recommended before final submission, so the image set has a citable, permanent reference rather than relying on the live GitHub URL alone.

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
| `Tops Color`, `Bottom Color` | Structured colour category fields *[NOTE: verify completeness/canonical source before final release — see Outstanding Items]* |
| `Dresses`, `Outerwear`, `Activewear` | Additional garment-category fields, populated only where applicable |
| `Clothing pattern` | Pattern-related field, free text (the previously duplicate empty `Clothing Pattern` column has been removed as of this version) |
| `Accessories` | Free-text accessory description |
| `Person`, `Emotion`, `Description` | Additional descriptive fields from the original annotation/labelling pipeline |

## Known data considerations (documented transparently per the Data Descriptor's Technical Validation section)

- **Annotation reliability**: at the current annotation density (mean 14.02 raters/image), estimated inter-rater reliability ranges from 0.116–0.152 across the five traits. See the Data Descriptor's Technical Validation section for the full reliability decomposition and guidance on annotation density needed for stronger reliability.
- **`Tops Color` / `Bottom Color`**: populated via vision-based extraction (Claude Haiku 4.5), using the already-confirmed `Tops`/`Bottom` garment-type labels as context. Validated against manual visual inspection on spot-checked images, and cross-checked against an independent, earlier extraction run for consistency (both runs agree that Black, not Blue, is the most common Tops colour — differing from the originally published category distribution, which may have conflated overall/primary garment colour with top-garment-specific colour; this discrepancy is noted for transparency and discussed in the Data Descriptor's Technical Validation section).

## Outstanding items before final release

- [x] Confirm and populate final canonical `Tops Color` / `Bottom Color` values — done via vision-based extraction; see "Known data considerations" above for the noted discrepancy with the originally published distribution.
- [x] Resolve the `Clothing Pattern` / `Clothing pattern` duplicate-column issue — done; the duplicate empty column has been removed.
- [ ] Add analysis code (`/code`) for reliability decomposition and baseline predictive modelling reported in the Data Descriptor
- [x] Create a Zenodo-archived DOI snapshot of the annotation CSV — done (https://doi.org/10.5281/zenodo.22238732, CC BY 4.0). **Still pending**: an equivalent persistent archive for the `johnwwwl/imgs` image repository, and for any analysis code, since neither is covered by this DOI.
- [ ] Add LICENSE file (note: the Zenodo dataset deposit is licensed CC BY 4.0; confirm this repository's own LICENSE file matches, or specify separately if code/data are licensed differently)

## Citation

If you use this dataset, please cite:

[Full citation to be added upon publication of the Scientific Data Descriptor.]

Wang, J., Li, H., & Woo, W.L. (2024). Apparel Matters? A New First-Impression Static Appearance Dataset. Presented at the UK Academy for Information Systems (UKAIS) Conference, Kent, UK.

## Contact

Corresponding author: Honglei Li, School of Computer Science, Northumbria University.
