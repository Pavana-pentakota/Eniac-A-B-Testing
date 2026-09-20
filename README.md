# ENIAC Homepage A/B Test (Phase 3)

Chi-square test comparing four versions of the Eniac homepage call-to-action button, using click-through rates to find the winning version — Python (pandas, scipy, seaborn)

> 📌 **Part 3.** This project continues from **Phase 2: ENIAC Discount Strategy** — https://github.com/Pavana-pentakota/ENIAC-Discount-Strategy-Analysis
> Phase 2 recommended how much to discount and when. Phase 3 tests how to present deals on the homepage.



## Business Context

- Eniac's homepage promotes the iPhone 13 with a call-to-action (CTA) button. The team wanted to know whether the button's wording and colour change how many visitors click. Four versions were tested:
  - Version A: white "SHOP NOW"
  - Version B: red "SHOP NOW"
  - Version C: white "SEE DEALS"
  - Version D: red "SEE DEALS"
- This connects to Phase 2: "SEE DEALS" tests whether promotion-focused wording drives more engagement than neutral wording.

!Versions (screenshots/test_versions.png)

## Business Question Answered

- Which version of the CTA button gets the highest click-through rate, and is the difference between versions real or just random variation?

## Hypotheses

- **H0:** The click-through rate is equal for all four versions.
- **HA:** The click-through rate of at least one version differs.
- Significance level: α = 0.05

## Dataset & Sources

- Source: Eniac homepage experiment data — one file per version (`eniac_a.csv` to `eniac_d.csv`)
- Each version was shown to about 25,000 visitors over a 14-day test
- Metric: click-through rate (CTR) = button clicks ÷ visits
- Key Features: element name, number of clicks, snapshot information (visits and test dates)

## Approach

- Extracted button clicks and total visits for each version.
- Built a contingency table (click vs no-click) for the four versions.
- Ran a chi-square test of independence to check whether the versions perform equally.
- Compared click-through rates to identify the winning versions.

## Key Findings & Results

| Version | Button | Visits | Clicks | CTR |
|---|---|---|---|---|
| A | White, SHOP NOW | 25,326 | 512 | 2.02% |
| B | Red, SHOP NOW | 24,747 | 281 | 1.14% |
| C | White, SEE DEALS | 24,876 | 527 | 2.12% |
| D | Red, SEE DEALS | 25,233 | 193 | 0.76% |

- **Chi-square test:** chi-square = 224.0, p-value far below 0.05 — reject H0. The four versions do not perform equally.
- **Winners:** Version C (2.12%) and Version A (2.02%) have the highest click-through rates.
- **Colour:** both red versions (B: 1.14%, D: 0.76%) have clearly lower click-through rates than the white versions.
- **Recommendation:** use a white button. Version C ("SEE DEALS") had the highest CTR, so it suits promotional periods such as Black Friday and the holidays identified in Phase 2, while Version A ("SHOP NOW") is a strong default. Avoid the red button.

## Limitations

- The versions ran at different times: Version A started on 14 Sep 2021 and B, C and D on 27 Oct 2021, so seasonality or traffic differences could partly affect the comparison.
- CTR measures clicks only, not purchases or revenue, so a follow-up should test conversion.

## Tools Used

- Python — pandas for data preparation, scipy for the chi-square test, seaborn for visualisation
- Google Colab — notebook environment

## Project Structure

```
eniac-ab-testing/
├── README.md
├── data/
│   ├── eniac_a.csv
│   ├── eniac_b.csv
│   ├── eniac_c.csv
│   └── eniac_d.csv
├── notebooks/
│   └── Eniac_Testing_versions.ipynb
└── screenshots/
    └── Versions.png
```

## How to Use This Project

- Download this repository.
- Open the notebook in `notebooks/` in Google Colab.
- When the notebook asks you to upload files, select the four CSVs from the `data/` folder.
- Run all cells to reproduce the results.

## Author
- Pavana Pentakota
- linkdn : www.linkedin.com/in/pavanapentakota
