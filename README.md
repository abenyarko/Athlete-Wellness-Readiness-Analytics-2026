
# 🥍 Athlete Wellness & Readiness Analytics | 2026

**Longitudinal Analytics | Survey Statistics | Data Quality | Statistical Modeling | Decision Support | R**

---
Longitudinal athlete wellness and readiness analytics using R, survey-weighted statistics, individualized Z-scores, and weekly performance monitoring to support evidence-based decision-making.
---

Transforming repeated athlete wellness observations into an evidence-based framework for understanding individual variation, identifying meaningful changes, and supporting operational decision-making.

**Project Status:** 2026 analysis completed; repository documentation and supporting files being organized for publication.

---

## Executive Summary

This project develops a longitudinal athlete wellness analytics framework using repeated survey observations collected throughout the 2026 NCAA Division I men's lacrosse season.

Building upon the [2025 Sports Wellness Analytics Project](https://github.com/abenyarko/Sports-Wellness-Analytics), the 2026 analysis expands the monitoring framework from predominantly Tuesday and Thursday assessments to a more comprehensive view of athlete wellness throughout the training and competition week.

The analysis incorporates **1,445 wellness survey responses**, five core wellness indicators, individualized baseline comparisons, survey-weighted statistical methods, bootstrap estimation, and regression modeling to evaluate patterns in athlete wellbeing.

The project addresses three analytical challenges:

1. **Data integration and comparability:** Organizing repeated observations across athletes, dates, survey measures, and playing positions into a consistent analytical structure.
2. **Statistical interpretation:** Distinguishing absolute wellness scores from deviations relative to each athlete's historical baseline, while accounting for uncertainty and position-specific differences.
3. **Decision support:** Translating complex statistical findings into interpretable information for coaches, athletic trainers, and sports performance professionals.

The resulting analysis provides evidence of meaningful variation across survey days and playing positions and establishes a foundation for individualized longitudinal monitoring.

---

## Business Problem

Athlete wellness is dynamic, multidimensional, and highly individualized.

Traditional monitoring approaches frequently rely on isolated survey responses or team-level averages. Although these measurements provide useful information, they may overlook meaningful differences in individual wellness patterns.

For example, two athletes reporting the same wellness score may have substantially different historical wellness profiles. A score that is typical for one athlete may represent a significant deviation for another.

This creates an operational challenge for sports performance professionals attempting to interpret wellness information and prioritize follow-up.

**The central business problem is how to convert repeated, subjective wellness observations into consistent, interpretable, and actionable information without overstating what those observations can predict.**

This project addresses that challenge through a reproducible analytical framework designed to evaluate group-level patterns, individual deviations, and variation across the training week.

---

## Project Vision

*Develop a scalable longitudinal decision-support framework that moves athlete monitoring beyond isolated observations toward individualized, evidence-based interpretation of wellness changes over time.*

Although developed within collegiate athletics, the underlying analytical principles are relevant to public health surveillance, healthcare utilization monitoring, occupational health, and other settings involving repeated measurements and operational decisions.

---

## Research Questions

The analysis investigates the following questions:

1. How do athlete wellness indicators vary across playing positions?
2. How do wellness scores change throughout the training and competition week?
3. Do individual baseline-relative wellness patterns reveal differences that are not apparent in absolute scores?
4. Are survey-day and playing-position differences statistically significant after accounting for the analytical design?
5. Do interactions between playing position and survey day reveal distinct wellness patterns?
6. How can the resulting evidence support individualized monitoring and recovery planning?

A subsequent longitudinal modeling extension will investigate the proportion of variation attributable to differences between athletes versus changes within athletes.

---

## Data Sources and Analytical Measures

### Athlete Wellness Survey

The primary dataset consists of **1,445 self-reported wellness survey observations** collected during the 2026 season.

The survey evaluates five wellness indicators:

| Indicator | Analytical purpose |
|---|---|
| Sleep Quality | Assess perceived sleep and recovery |
| Overall Stress | Evaluate perceived psychological and general stress |
| Physical Fatigue | Measure self-reported physical fatigue |
| Soreness | Assess perceived muscular soreness |
| Motivation | Evaluate self-reported motivation and readiness |

The analysis also incorporates a composite **Wellbeing Score**, wellness classifications, athlete identifiers, playing positions, and survey dates.

### Monitoring Frequency

The 2026 monitoring framework emphasizes four operational survey periods:

- **Sunday:** Post-competition recovery
- **Tuesday:** Early-week wellness assessment
- **Thursday:** Later-week training and recovery assessment
- **Friday:** Pre-competition readiness assessment

Responses recorded on other days were retained where appropriate for the analysis.

### Playing Positions

The analysis evaluates six playing-position groups:

Attack (A), Offensive Midfield (OM), Defensive Midfield (DM), Defense (D), Goalkeeper (GK), and Faceoff (FO).

### Data Governance and Privacy

Athlete-level records contain potentially sensitive health and performance information. Public repository materials will therefore exclude directly identifiable raw survey data.

Any released examples must be de-identified and reviewed for potential re-identification through combinations of position, date, and other characteristics.

---

## Analytical Methodology

The methodology combines data preparation, descriptive statistics, individualized standardization, survey-weighted inference, and regression modeling.

### 1. Data Preparation and Quality Assessment

The analytical workflow organizes repeated observations into a consistent structure suitable for longitudinal exploration.

Core preparation activities include:

- Standardizing variable names and categorical values
- Validating survey dates and playing-position categories
- Converting wellness responses into numerical analytical measures
- Constructing derived wellness indicators
- Evaluating response distributions and survey participation across days
- Organizing observations by athlete and time
- Reviewing missingness and data coverage before interpretation

Because participation differs across survey days, the analysis explicitly considers uneven observation counts when interpreting weekly patterns.

### 2. Individualized Baseline Standardization

A central advancement in the 2026 project is the use of athlete-specific baseline comparisons.

For athlete \(i\), an observed wellness measure at time \(t\) can be standardized as:

\[
Z_{it} = \frac{X_{it}-\bar{X}_i}{s_i}
\]

Where:

- \(X_{it}\) represents the athlete's observed wellness value.
- \(\bar{X}_i\) represents the athlete-specific baseline mean.
- \(s_i\) represents the athlete-specific standard deviation.
- \(Z_{it}\) represents the standardized deviation from that athlete's baseline.

Standardized values allow wellness observations to be interpreted relative to each athlete's historical distribution rather than solely against team averages.

Indicators are oriented consistently so that higher standardized values reflect more favorable wellness.

**Baseline limitation:** The 2026 analysis uses retrospective, full-season athlete-specific baseline statistics. Consequently, these Z-scores describe historical deviations but are not prospectively validated readiness indicators. Future deployment requires prior-only or rolling baselines to prevent temporal information leakage.

### 3. Survey-Weighted Statistical Analysis

The analysis applies survey-weighted statistical techniques to evaluate wellness patterns across playing positions.

Methods include:

- Position-based weighting through raking to roster composition
- Bootstrap variance estimation using 1,000 replicates
- Weighted descriptive estimates
- Confidence intervals
- Rao–Scott adjusted chi-square testing
- Survey-weighted generalized linear models

These techniques support design-aware comparisons and uncertainty estimation.

Weighting addresses specified differences in position representation; it does not automatically eliminate nonresponse bias, measurement error, or other sources of systematic bias.

### 4. Regression Modeling

Survey-weighted regression models evaluate associations between standardized wellbeing and:

- Day of the week
- Playing position
- Playing-position-by-day interactions

The additive model examines differences associated with survey timing and position, while interaction models investigate whether weekly wellness patterns differ across playing groups.

Regression estimates are interpreted as **associations**, not causal effects.

### 5. Longitudinal Interpretation

The analytical framework emphasizes two distinct forms of variation:

**Between-athlete variation:** Differences in typical wellness levels across athletes.

**Within-athlete variation:** Changes in an athlete's wellness across repeated observations.

The existing baseline-relative analysis provides a foundation for studying individual deviations. A planned multilevel modeling extension will formally partition these sources of variation and estimate the intraclass correlation coefficient (ICC).

---

## Key Analytical Findings

### 1. Weekly Wellness Patterns

Mean absolute Wellbeing Scores varied across the survey week.

| Survey day | Mean Wellbeing Score |
|---|---:|
| Sunday | 32.33 |
| Monday | 33.06 |
| Tuesday | 34.11 |
| Wednesday | 31.68 |
| Thursday | 33.17 |
| Friday | 34.68 |
| Saturday | 31.85 |

Friday demonstrated the highest observed mean Wellbeing Score, followed by Tuesday.

Wednesday showed the lowest mean. However, participation was substantially lower on Wednesday and other non-core survey days, requiring caution when comparing these estimates.

### 2. Baseline-Relative Position Differences

Individualized standardization revealed differences across playing positions that were not necessarily apparent from absolute scores alone.

Notable results included:

- **Defensive Midfielders:** Above-baseline mean wellbeing, with a 95% confidence interval of approximately +0.23 to +0.44.
- **Goalkeepers:** Below-baseline mean wellbeing, with a 95% confidence interval of approximately −0.59 to −0.06.
- **Faceoff Specialists:** Below-baseline mean wellbeing, with a 95% confidence interval of approximately −0.42 to −0.09.

These findings demonstrate the importance of separating absolute wellness levels from relative deviations.

A position may report comparatively favorable absolute scores while displaying a different pattern when evaluated against athlete-specific historical baselines.

### 3. Survey-Weighted Regression Results

The additive model identified statistically significant associations between wellbeing Z-scores and selected survey days and positions.

| Predictor | Estimated coefficient | p-value |
|---|---:|---:|
| Tuesday | +0.360 | .004 |
| Friday | +0.462 | < .001 |
| Defensive Midfield | +0.343 | < .001 |
| Goalkeeper | −0.332 | .024 |
| Faceoff | −0.246 | .016 |

Day coefficients are relative to Sunday, and position coefficients are relative to Attack, holding the other modeled factors constant.

These estimates suggest that both survey timing and playing position are relevant to interpreting standardized wellbeing.

### 4. Position-Specific Weekly Patterns

The interaction analysis identified notable differences in weekly wellness patterns by position.

Statistically significant interaction terms included:

- Faceoff × Wednesday: coefficient −1.315, p = .018
- Defensive Midfield × Thursday: coefficient −0.721, p = .027

These interactions indicate that some position-specific weekly patterns differ from the additive model's expected pattern.

They should be interpreted alongside sample sizes, uncertainty intervals, and descriptive visualizations rather than used as standalone risk thresholds.

---

## Data Visualization and Decision Support

The analysis uses visual reporting to communicate statistical findings to technical and nontechnical audiences.

### Executive Wellness Overview

Provides a summary of wellness distributions, participation patterns, and major differences across the season.

### Weekly Wellness Trends

Compares wellness indicators and composite scores across survey days to identify recurring patterns in training and recovery periods.

### Position-Level Comparisons

Displays weighted estimates, confidence intervals, and standardized wellness patterns by playing position.

### Position-by-Day Readiness Heatmap

Visualizes mean baseline-relative wellness values across positions and survey days to highlight where closer contextual review may be useful.

### Individualized Monitoring Framework

Establishes the methodological foundation for athlete-specific trend charts, baseline comparisons, and future longitudinal monitoring dashboards.

*Dashboard images and analytical figures will be added manually after the final visual assets are prepared.*

---

## Operational Recommendations

### Establish Consistent Monitoring

Maintain Sunday, Tuesday, Thursday, and Friday surveys to capture post-competition recovery, early-week status, later-week response, and pre-competition wellness.

### Prioritize Individual Changes

Interpret athlete wellness relative to personal historical patterns rather than relying exclusively on absolute scores or position averages.

### Incorporate Position Context

Use position-specific analyses to guide questions and follow-up discussions, recognizing that workload, training demands, and reporting patterns may differ.

### Communicate Uncertainty

Include confidence intervals, sample coverage, and methodological limitations when presenting findings to coaches and performance staff.

### Validate Against Independent Outcomes

Future research should evaluate whether wellness trends are associated with independently measured performance outcomes such as countermovement jump (CMJ), reactive strength index (RSI), and external workload metrics.

---

## Business Impact and Transferable Applications

This project demonstrates how an analytics workflow can transform repeated operational observations into structured evidence for decision support.

**Data Management:** Preparing and harmonizing repeated observations across athletes, dates, categories, and survey measures.

**Statistical Analysis:** Applying survey weighting, bootstrap estimation, regression modeling, and baseline standardization.

**Data Quality and Uncertainty:** Evaluating uneven survey participation, limitations of retrospective baselines, and uncertainty surrounding statistical estimates.

**Visualization and Reporting:** Communicating analytical results through tables, trend charts, confidence intervals, and comparative visualizations.

**Operational Decision Support:** Connecting statistical findings with monitoring recommendations while distinguishing evidence from unvalidated predictive claims.

These capabilities are transferable to public health surveillance and other monitoring environments that require consistent data definitions, longitudinal interpretation, transparent methods, and communication with decision-makers.

The project demonstrates an analytical capability, not evidence that a specific intervention improved athlete health or performance.

---

## Methodological Limitations

Several limitations are important to interpreting the results.

**Self-reported measures:** Wellness surveys reflect subjective perceptions and may be influenced by response behavior and contextual factors.

**Uneven participation:** Survey response counts vary by day and position, potentially affecting the stability and comparability of estimates.

**Retrospective baselines:** Full-season athlete-specific means and standard deviations use information from the entire observation period. They should not be treated as valid prospective baselines.

**Composite outcome construction:** The Wellbeing Score is derived from the underlying wellness indicators. Models using those same components to explain the composite may produce largely mechanical relationships and should not be presented as independent predictive validation.

**Observational design:** Statistical associations do not establish causation.

**Repeated-measures dependence:** Survey weighting and bootstrap methods do not automatically resolve within-athlete correlation. Formal longitudinal modeling should explicitly address repeated observations and the corresponding variance structure.

**External validation:** Wellness deviations have not yet been prospectively validated against independent performance or clinical outcomes.

---

## Future Research and Development

### Multilevel Longitudinal Modeling

Develop mixed-effects models to estimate within-athlete and between-athlete variance, ICC, and athlete-specific trajectories.

### Prospective Baseline Validation

Replace retrospective full-season reference values with prior-only or rolling baselines and evaluate performance using time-ordered validation.

### Objective Performance Integration

Link wellness observations with CMJ, RSI, workload, and other performance measures to investigate relationships between subjective wellbeing and independent outcomes.

### Automated Data Pipelines

Develop reproducible data validation, transformation, and reporting workflows to reduce manual processing and improve analytical consistency.

### Interactive Analytics

Expand reporting through Power BI or R Shiny dashboards with athlete-level trends, comparative indicators, and clearly documented analytical definitions.

### Advanced Modeling

Evaluate predictive approaches only after establishing suitable independent outcomes, leakage-safe validation procedures, and operationally meaningful evaluation criteria.

---

## Technologies and Analytical Skills

| Area | Technologies and methods |
|---|---|
| Data preparation | R, tidyverse, data transformation and validation |
| Survey statistics | R `survey` package, raking, bootstrap estimation |
| Statistical inference | Confidence intervals, Rao–Scott tests, survey-weighted GLMs |
| Longitudinal analytics | Repeated measures, individual baselines, Z-scores |
| Visualization | R, ggplot2, comparative statistical charts |
| Decision support | Analytical reporting, monitoring frameworks |
| Version control | Git, GitHub |
| Future development | Multilevel modeling, Power BI, R Shiny, automated pipelines |

---

## Repository Structure

```text
Athlete-Wellness-Readiness-Analytics-2026/
│
├── README.md
│
├── analysis/
│   └── R analysis scripts
│
├── methodology/
│   └── Analytical documentation
│
├── executive-summary/
│   └── Executive reporting
│
├── report/
│   └── Full technical report
│
├── dashboard/
│   └── Dashboard documentation
│
├── visuals/
│   └── Statistical figures and screenshots
│
└── data/
    └── Data dictionary and documentation
```

Supporting files will be uploaded manually. Raw identifiable athlete data will not be published.

---

## Related Analytics Projects

**[Sports Wellness Analytics — 2025](https://github.com/abenyarko/Sports-Wellness-Analytics)**

The foundational project focused on survey-weighted analysis, wellness drivers, position differences, and interactive reporting.

**[Athlete Readiness Predictive Modeling](https://github.com/abenyarko/Athlete-Readiness-Predictive-Modeling)**

A complementary supervised machine learning project examining athlete wellness and objective neuromuscular performance.

Together, these projects demonstrate progression from descriptive analytics to longitudinal monitoring and the evaluation of predictive approaches.

---

## Author

**Anthony Benyarko**

Data Analytics Professional specializing in survey statistics, statistical modeling, business intelligence, and evidence-based decision support.

[LinkedIn](https://linkedin.com/in/anthony-benyarko)

**Core Competencies:** Data Preparation | Statistical Analysis | Survey Methodology | Longitudinal Analytics | Data Quality | Visualization | Reproducible Research | Executive Reporting | Decision Support
