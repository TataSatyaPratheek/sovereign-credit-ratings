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

Most credit-rating models take their data frequency for granted and then race to a better estimator.
This thesis inverts that: it asks whether the **granularity of the data itself** — annual versus
monthly — changes how well U.S. sovereign ratings can be predicted, and it **answers the question the
way an experiment should be answered: with a hypothesis test, not a leaderboard.** The finding that
"granularity matters" is earned through paired statistical testing, not asserted.

## What makes it distinctive — the *manner* of analysis

- **A designed comparison, not a bake-off.** The core object of study is a **factor** (annual vs
  monthly granularity), held against everything else, so the effect of granularity can be isolated
  and attributed. The models are instruments; the *comparison* is the contribution.
- **The claim is tested statistically.** Annual and monthly models are compared with a **paired
  t-test** and a **Wilcoxon signed-rank test** across rating agencies — a parametric and a
  non-parametric check — so the "monthly is better" conclusion survives its own null hypothesis
  rather than resting on a single RMSE gap.
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

- **Monthly granularity wins — and the win is significant.** Finer-grained data yields materially
  better predictions, confirmed by the paired t-test and Wilcoxon tests, for both S&P and Fitch.
- **Governance data is not optional.** Models that fold in governance indicators alongside economic
  ones consistently beat economics-only models; political stability, regulatory quality, and rule of
  law repeatedly surface as top predictors.
- **Non-linear structure matters.** The best-performing specification was a **decision tree on
  monthly governance data** (best S&P model, `dt_2008_m_wgi`, RMSE ≈ **0.0295**, MAE ≈ 0.0268),
  capturing non-linear relationships that linear and time-series baselines miss.

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

**Satya Pratheek Tata** — [github.com/TataSatyaPratheek](https://github.com/TataSatyaPratheek)
· [LinkedIn](https://linkedin.com/in/satyapratheek-tata)

Supervised by **Prof. Mario Hernandez Tinoco**, with thanks to **Prof. Arnaud Dufays** (time series)
and **Prof. Jérémy Leymarie** (econometrics).

## License

© 2024 Satya Pratheek Tata. Text and figures shared for scholarly reading and citation; please cite
rather than redistribute modified copies.
