# 📊 Analytics Methodology and BizScore

## Purpose

Analytics modules transform location/category inputs into scores, opportunity descriptions, forecasts, competitor indicators, risk factors and financial estimates. The current implementation is primarily heuristic and formula-driven, not a trained model with published validation.

## Input dimensions

Code references metrics such as:
- Demand index.
- Competition index, count and density.
- Population density.
- Average income.
- Internet penetration.
- Literacy rate.
- Category ease/difficulty.
- Location/economic inputs.

Not every input originates from a live provider. See [Data Sources](data-sources.md).

## BizScore

Scoring services return an overall value and dimension-level values such as demand, competition, location and economy. Some report flows apply category ease and competition density adjustments.

Before changing formulas, inspect `src/services/scoring.ts`, `src/lib/categoryEngine.ts`, `src/lib/decisionMatrixEngine.ts` and related code.

Required methodology record for formula changes:
1. List every component input.
2. Document normalization and weighting.
3. Define missing-value behavior.
4. Define score caps and floors.
5. Add boundary/unit tests.
6. Add worked examples.
7. Version the methodology.
8. Explain impact on historical score comparisons.

## Opportunity generation

`src/services/marketData.ts` uses city-tier multipliers, category templates and random variation. Identical requests may result in different synthetic values. The opportunity names are template-driven, not proof of measured local demand.

## Forecast engine

`src/services/forecastEngine.ts` uses fixed category annual growth rates to project six- and twelve-month indices. The implementation caps values and derives trend direction from score differences.

This is formula extrapolation, not a trained predictive model. The repository does not establish a training corpus, backtest, prediction intervals or calibrated confidence.

## Finance and risk

Finance, risk and failure-prediction modules are rule-based calculations unless separately evidenced otherwise. Estimates need currency, time period, assumptions, range, data source and uncertainty. Do not present model outputs as quotes or guarantees.

## Competitor intelligence

Competition scanning and competitor quality analysis may use provider-derived and/or generated attributes. For each metric, identify actual data origin, freshness, coverage and missing-data behavior. Map pins alone do not prove complete competitor coverage.

## Explainability requirements

Future reports should expose input values, source type/freshness, methodology version, component scores, assumptions, missing data, AI-generated text labels, and sensitivity to changed assumptions.
