# 🌐 Product Overview

## 1. Product description

BizRadar Insights is a browser-based business opportunity exploration and feasibility-analysis tool. Its interface helps users choose a location and business category, inspect opportunity suggestions, understand a composite BizScore, review competitors and forecasts, and retain selected ideas through Supabase-backed user features.

The product is implemented as a React single-page application. It uses local TypeScript engines for several calculations and Supabase Edge Functions for selected model-backed tasks.

## 2. Problem statement

Early-stage founders often make location and category decisions using incomplete information. The application attempts to structure the conversation around:
- Local demand assumptions.
- Competition density and quality.
- Category characteristics.
- Population and economic indicators.
- Financial viability assumptions.
- Risks, recommendations and comparison.

It should be treated as a hypothesis-generation and decision-support interface, not an oracle that predicts business success.

## 3. Primary user groups

| User group | User need | Main application area |
|---|---|---|
| First-time entrepreneur | Turn an idea into a testable business hypothesis | Idea Analyzer and Feasibility Report |
| Local business owner | Explore adjacent locations or categories | Opportunities |
| Business analyst | Compare scoring dimensions and competitor indicators | Advanced Analytics |
| Returning user | Store and revisit candidate ideas | Saved Ideas |
| Researcher/reviewer | Understand assumptions and model behavior | Reports and methodology docs |

## 4. Value proposition

The intended value is a single workflow combining structured idea input, location context, comparable score dimensions, feasibility outputs and saved decision artifacts. The actual evidence quality depends on the source dataset and the correctness of the scoring assumptions.

## 5. Product capabilities

### Opportunity discovery
The user searches for a place, selects a category, and triggers generation of candidate opportunity cards. In current source, location search is implemented in a service module and market data/opportunity suggestions are produced through local engines.

### Feasibility analysis
The report builder combines demand, competition, category, location and financial assumptions into a report object. Advanced panels add competitor-quality heuristics, rent estimates, customer persona matching, seasonal projections, risk indices, idea enhancements and failure-risk indicators.

### AI-assisted idea analysis
The `parse-idea` function sends user-provided idea text to a configured AI gateway and requests structured JSON. The `generate-insights` function asks for a short consultant-style summary. The authenticated `ai-assistant` function reads/writes per-user conversation history.

### Saved ideas and comparison
Authenticated users can persist analysis outputs in Supabase tables and review candidate records on the Saved Ideas and Compare pages.

## 6. Product boundaries

The code does not establish:
- A validated country-wide business registry.
- Verified live demand transactions.
- Audited competitor coverage or ratings.
- A trained or back-tested business-failure model.
- Verified property/rent quotations.
- Regulator-approved business or financial advice.
- Guaranteed accuracy of AI outputs.
- A production SLA or independently audited security posture.

## 7. Product success measures to consider

These are proposed metrics, not currently instrumented guarantees:
- Search-to-report completion rate.
- Report generation latency and error rate.
- Percentage of reports with traceable source data.
- Saved-idea reuse rate.
- Comparison completion rate.
- AI function success, refusal and rate-limit rates.
- User-reported usefulness after a real-world validation step.
- False-confidence incidents caused by unsupported estimates.

## 8. Responsible product language

Prefer “estimated,” “modeled,” “heuristic,” “synthetic,” “illustrative,” or “AI-generated” when appropriate. Do not call a synthetic score “real-time market intelligence.” See [Data sources](data-sources.md) and [Analytics methodology](analytics-methodology.md).
