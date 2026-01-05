# food-addiction-actimetry-dataset
Anonymized actimetry + psycho-behavioral dataset (78 participants, 6–7 days) for food addiction (FA) and symptom count (SC) analysis.

# Actimetry & Food Addiction Dataset (78 participants)

This repository provides an anonymized dataset used in our study on objective features extracted from wrist actimetry time series for food addiction (FA) and symptom count (SC) analysis with machine learning. :contentReference[oaicite:0]{index=0}

## Overview

- **Participants:** 78
- **Recording duration:** 6–7 days per participant
- **Actimetry:** non-dominant wrist actimeter; activity sampled at 1 Hz and aggregated to **1-minute bins** (arbitrary units).
- **Data components:**
  1) Participant-level anthropometric / psycho-emotional / behavioral features + derived rhythm/sleep metrics  
  2) Minute-level actimetric time series

> **Privacy:** The dataset is anonymized and contains no direct identifiers (e.g., names). Please do not attempt re-identification.

## Repository contents

- `data/dataset.xlsx` — Excel workbook with **two sheets**:
  - **Sheet 1: `participants`** (one row per participant)
  - **Sheet 2: `actimetry`** (minute-level activity)

Optionally (recommended):
- `docs/data_dictionary.md` — data dictionary in Markdown (mirrors Sheet 1 codebook).
- `examples/read_data.ipynb` — minimal example for loading and exploring the data.

## Data description

### Sheet 1: `participants` (participant-level table)

Each row corresponds to one participant. Key columns:

- `No actimeter` — participant/device identifier (anonymized)
- `City` — place of residence/study
- `day`, `month`, `year` — start date of actimetry
- `age`
- `sex` — codes: `1` = female, `2` = male
- `BMI%` — BMI percentile (age/sex corrected)
- `BMIc` — BMI category: `1` underweight, `2` normal, `3` overweight, `4` obese
- `ov/ob` — overweight/obesity indicator: `0` no, `1` yes
- `SJL` — social jetlag
- `SJLc` — social jetlag category: `0` no, `1` yes, `2` yes+
- `SD` — sleep duration
- `SDc` — sleep duration category: `1` inadequate, `2` adequate
- `MSFsc` — chronotype metric
- `CHRc` — chronotype category: `1` early, `2` intermediate, `3` late
- `PSQI` — sleep quality score
- `PSQIc` — sleep quality category: `0` good, `1` bad
- `Depr` — depression score (see study protocol)
- `Deprc` — depression category: `0` no, `1` yes
- `Restr`, `Restrc` — restrained eating (score + category)
- `Extern`, `Externc` — external eating (score + category)
- `Emo`, `Emoc` — emotional eating (score + category)
- `SCFA` — food addiction symptom count (SC), integer
- `FA` — food addiction diagnosis (target): `0` no, `1` yes

Circadian rhythm metrics (computed from actimetry):
- `Mesor`, `Amp24`, `Acr24`, `M10`, `L5v`, `IV`, `IS`

### Targets and class balance

- **Target 1 (binary):** `FA`
  - `FA = 1`: 10 participants
  - `FA = 0`: 68 participants

- **Target 2 (multiclass):** `SCFA` (symptom count), often grouped into:
  - Class 1: 0–1 symptoms (n=33)
  - Class 2: 2 symptoms (n=16)
  - Class 3: 3 symptoms (n=15)
  - Class 4: 4–7 symptoms (n=14)

## Sheet 2: `actimetry` (minute-level time series)

Format:
- Time columns: `year`, `month`, `day`, `h`, `min`
- Participant columns: **each remaining column name is a participant/device ID** (e.g., `6`, `7`, `8`, …).  
  Each cell contains the **minute-summed activity** (arbitrary units) for that participant at that timestamp.

## Notes on numeric formatting

Some numeric values may use a **comma as decimal separator** (e.g., `1,66665`). When exporting to CSV or parsing as text, ensure your tooling uses the correct locale/decimal setting.

## Ethics and consent

The study was conducted under institutional ethics approval and informed consent procedures as described in the associated manuscript. :contentReference[oaicite:1]{index=1}

## License

Choose a license appropriate for data sharing, e.g.:
- **CC BY 4.0** (recommended for open research datasets)  
or
- **CC0** (public domain dedication)

Include a clear “no re-identification” statement if required by your institution.

## Citation

If you use this dataset, please cite the associated paper:

> Borisenkov M., Belyaev M., Sivakumar N.R., Murugappan M., Velichko A., Korzun D., et al.  
> *Objective Features Extracted from Motor Activity Time Series for Food Addiction Analysis Using Machine Learning – A Pilot Study.* :contentReference[oaicite:2]{index=2}

(Replace with the final journal reference / DOI once available.)

## Contact

For questions or collaboration, please open an issue in this repository.
