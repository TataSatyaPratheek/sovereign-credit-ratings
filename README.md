# Granularity Matters: Machine Learning and Sovereign Credit Ratings

**Not "which model is best," but a controlled study of a prior question: *at what data granularity
should sovereign credit ratings be modelled at all* — tested, not assumed.**

![Degree](https://img.shields.io/badge/MSc-Data%20Analytics%20%26%20AI-1f6feb)
![Institution](https://img.shields.io/badge/EDHEC-Business%20School-6f42c1)
![Year](https://img.shields.io/badge/2024-May-brightgreen)
![Approach](https://img.shields.io/badge/hypothesis--tested-comparison-orange)

> MSc thesis, Department of Data Science (Data Analytics and Artificial Intelligence),
> EDHEC Business School, Lille, France — May 2024.

📄 **[Read the thesis (PDF)](./Granularity-Matters-Sovereign-Credit-Ratings.pdf)**

---

## The thesis, in one idea

Sovereign-rating models often rest on a narrow, low-frequency snapshot of a country. This thesis
argues the opposite — that **granularity matters**: the depth and comprehensiveness of the data, and
*which* indicators you include, are what drive prediction. Testing this directly across two agencies
(S&P and Fitch), it finds that **granular, long-term data combined with governance indicators
substantially improves accuracy over economic data alone** — and it earns that claim with a
hypothesis test, not a leaderboard.

## What makes it distinctive — the *manner* of analysis

- **A designed comparison, not a bake-off.** The core object of study is a **factor** (annual vs
  monthly granularity), held against everything else, so the effect of granularity can be isolated
  and attributed. The models are instruments; the *comparison* is the contribution.
- **The claim is tested statistically.** Annual and monthly models are compared with a **paired
  t-test** and a **Wilcoxon signed-rank test** across rating agencies — a parametric and a
  non-parametric check — so the granularity claim must survive its own null hypothesis rather than
  resting on a single RMSE gap.
- **Two agencies, cross-validated framing.** Ratings from both **Standard & Poor's** and **Fitch**
  are modelled, so a finding has to hold across two independent labelling systems to count.
- **Attribution over prediction.** The analysis reads *which* indicator families carry the signal —
  separating **governance** (political stability, regulatory quality, rule of law, from the World
  Development Indicators) from **economic** fundamentals (GDP growth, inflation, unemployment) — and
  reports what each contributes, rather than treating the model as a black box.
- **Granularity built honestly.** Careful temporal interpolation/aggregation and preprocessing turn
  mismatched-frequency sources into a clean monthly-vs-annual comparison without leaking information
  between them.

## What it found

- **Which indicators you include is the biggest lever.** Folding governance indicators (political
  stability, regulatory quality, rule of law, from the World Development Indicators) in alongside
  economic ones (GDP growth, inflation, unemployment) consistently and substantially beats
  economics-only models — across both S&P and Fitch. This is the clearest, most robust result.
- **Granular, long-term data enhances prediction.** The thesis's hypothesis — that rating changes
  reflect *sustained, long-term shifts best captured in granular data* — is borne out: the most
  accurate models exploit granular (monthly) data to track dynamic changes in a country's conditions.
- **Non-linear models on granular governance data win.** The best specification is a **decision tree
  on monthly governance data** (`dt_2008_m_wgi`, RMSE ≈ 0.0295), capturing non-linear
  governance–economics–rating relationships that linear and time-series baselines miss.
- **The takeaway — the title, earned:** *granularity and indicator choice both matter.* Comprehensive,
  granular, long-term data plus the right governance indicators is what carries the predictive signal.

## The analytical pipeline

| Stage | The manner of it |
|:--|:--|
| Question | Frame granularity as the *treatment* whose effect on predictability is to be measured |
| Data | U.S. economic, governance (WDI), political, social and bond-market indicators, assembled at both annual and monthly frequency |
| Models | Linear & ridge regression, ARMA, ARMAX, decision trees — used as comparable *instruments*, not as the point |
| Test | Paired t-test + Wilcoxon signed-rank comparing annual vs monthly, across S&P and Fitch |
| Read-out | RMSE / MAE for accuracy; coefficient and feature attribution for *why* |

*See the PDF for the full literature positioning, data construction, model specifications, statistical
tests, and results tables.*

## Scope & limitations

- **Single sovereign (United States).** Findings speak to *within-country temporal granularity*, not
  cross-country rating prediction, and the U.S. rating is a near-constant target — an easy series.
- **Small annual samples.** The very low annual-model RMSEs should be read with caution (short annual
  series invite overfitting); treat the headline error magnitudes as relative, not absolute.
- **Granularity is not just frequency.** The head-to-head annual-vs-monthly test alone is nuanced;
  the granularity that pays off is the *depth and comprehensiveness* of the data (and the governance
  indicators), not merely a higher sampling rate.

**Who should read this:** anyone modelling sovereign ratings who assumes economic indicators alone
suffice — the governance dimension and granular, long-term coverage are where the accuracy is.

## Citation

```bibtex
@mastersthesis{tata2024granularity,
  title  = {Granularity Matters: Machine Learning and Sovereign Credit Ratings},
  author = {Tata, Satya Pratheek},
  school = {EDHEC Business School, Lille, France},
  type   = {MSc thesis, Department of Data Science (Data Analytics and AI)},
  year   = {2024},
  month  = may
}
```

## Author & supervision

**Satya Pratheek Tata** — [satyapratheek2000@gmail.com](mailto:satyapratheek2000@gmail.com)
· [github.com/TataSatyaPratheek](https://github.com/TataSatyaPratheek)
· [LinkedIn](https://linkedin.com/in/satyapratheek-tata)

Supervised by **Prof. Mario Hernandez Tinoco**, with thanks to **Prof. Arnaud Dufays** (time series)
and **Prof. Jérémy Leymarie** (econometrics).

## License

© 2024 Satya Pratheek Tata. Text and figures shared for scholarly reading and citation; please cite
rather than redistribute modified copies.
