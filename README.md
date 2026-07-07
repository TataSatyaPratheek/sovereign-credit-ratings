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
way an experiment should be answered: with a hypothesis test, not a leaderboard.** And the honest
answer subverts the title: across paired statistical tests, **granularity mostly does not move
predictive accuracy** — what moves it is *which* indicators you include (governance), not their
frequency. A cleanly reported null is the contribution.

## What makes it distinctive — the *manner* of analysis

- **A designed comparison, not a bake-off.** The core object of study is a **factor** (annual vs
  monthly granularity), held against everything else, so the effect of granularity can be isolated
  and attributed. The models are instruments; the *comparison* is the contribution.
- **The claim is tested statistically.** Annual and monthly models are compared with a **paired
  t-test** and a **Wilcoxon signed-rank test** across rating agencies — a parametric and a
  non-parametric check — so any granularity claim must survive its own null hypothesis rather than
  resting on a single RMSE gap. (Here, most comparisons fail to reject the null — see below.)
- **Two agencies, cross-validated framing.** Ratings from both **Standard & Poor's** and **Fitch**
  are modelled, so a finding has to hold across two independent labelling systems to count.
- **Attribution over prediction.** The analysis reads *which* indicator families carry the signal —
  separating **governance** (political stability, regulatory quality, rule of law, from the World
  Development Indicators) from **economic** fundamentals (GDP growth, inflation, unemployment) — and
  reports what each contributes, rather than treating the model as a black box.
- **Granularity built honestly.** Careful temporal interpolation/aggregation and preprocessing turn
  mismatched-frequency sources into a clean monthly-vs-annual comparison without leaking information
  between them.

## What it found (the honest, and more interesting, answer)

- **Granularity mostly did *not* move the needle — and that is the finding.** Across paired t-tests
  and Wilcoxon signed-rank tests on S&P and Fitch, **7 of 8 comparisons showed no significant
  difference** between annual and monthly models. The one significant result (Fitch MAE) favoured
  **annual** data. So for U.S. sovereign ratings, finer temporal granularity is *not* where the
  predictive gains are — the thesis title is the question, and the answer is largely a null.
- **Governance data is where the signal is.** Models that fold in governance indicators (political
  stability, regulatory quality, rule of law, from the World Development Indicators) consistently
  beat economics-only models — the clearest, most robust result in the study.
- **Estimator and frequency interact.** A decision tree on monthly governance data was the strongest
  *monthly* specification (`dt_2008_m_wgi`, RMSE ≈ 0.0295), while **annual ARMAX** models achieved
  the lowest errors overall — a reminder that model class and data frequency are not independent
  choices.
- **The thesis's own conclusion:** long-term data is crucial, and a **dual approach** (long-term
  structure plus event-driven short-term signals) is the most defensible reading of the evidence.

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
- **Title vs. answer.** *"Granularity Matters"* frames the question; the evidence returns a largely
  null answer, which is reported as such rather than dressed up.

**Who should read this:** anyone tempted to chase higher-frequency data before checking whether
frequency is actually the binding constraint — here it wasn't; feature *content* was.

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
