# 📊 Competitor Monitoring AI Agent
### Product Requirements Document (PRD)

> Workflow Automation & AI-Powered Competitive Intelligence  
> Building an AI workflow that compares marketplace product listings, analyzes competitor pricing and assortment, and generates structured competitive intelligence reports with automated quality evaluation.

![Status](https://img.shields.io/badge/Project-Prototype-blue)
![AI](https://img.shields.io/badge/AI-OpenRouter-purple)
![Automation](https://img.shields.io/badge/Automation-n8n-orange)
![Marketplaces](https://img.shields.io/badge/Marketplaces-Wayfair%20%7C%20Amazon%20%7C%20Walmart-green)
![Evaluation](https://img.shields.io/badge/Quality-AI%20Evaluation-yellow)

---

# Product Requirements Document: Competitor Monitoring AI Agent

**Project Type:** AI Product Prototype  
**Platform:** n8n, OpenRouter Chat Models, Marketplace Data Sources  
**Status:** Prototype

## 1. Product Overview

The Competitor Monitoring AI Agent automates competitive research across Wayfair, Amazon, and Walmart.

The workflow retrieves rug product listings, calculates marketplace-level pricing and rating statistics, compares competitor assortments, identifies potential pricing opportunities, and generates a structured HTML report with strategic recommendations.

The initial prototype covers Area Rugs, Outdoor Rugs, Hallway Runners, and Shag Rugs.

A separate AI evaluation process assesses report quality and records evaluation results for tracking.

The workflow supports competitive research and decision preparation. It does not independently measure sales, profitability, or actual consumer demand.

## 2. Problem Statement

Competitive marketplace research requires analysts to collect product listings, compare prices and ratings, review assortment differences, and identify potential market opportunities.

Manual research is time-consuming and can produce inconsistent comparisons, unsupported conclusions, and incomplete reports.

**Product hypothesis:** Automating marketplace data collection, statistical analysis, competitor comparison, and report evaluation can reduce research effort and improve the consistency of competitive intelligence.

## 3. Target Users

- Category managers monitoring competitor assortments and pricing.
- Merchandising teams evaluating product positioning.
- Product strategy teams identifying potential assortment gaps.
- E-commerce analysts preparing marketplace comparisons.
- Sourcing teams exploring potential supplier opportunities.

These audiences are initial hypotheses and have not yet been validated through user research.

## 4. Product Goals and Scope

### Goals

- Accept a product category and optional research focus through chat.
- Retrieve product listings from Wayfair, Amazon, and Walmart.
- Calculate marketplace-level price, rating, review, and assortment statistics.
- Compare competitor pricing and product positioning.
- Identify potential assortment opportunities and whitespace.
- Generate strategic recommendations and supplier suggestions.
- Produce a structured downloadable HTML report.
- Evaluate report quality and store evaluation results.

### Initial Scope

- Area Rug
- Outdoor Rug
- Hallway Runner / Runner Rug
- Shag Rug

### Out of Scope

- Individual SKU sales or profitability scoring.
- Verified consumer demand forecasting.
- Real-time inventory monitoring.
- Automated pricing or purchasing decisions.
- Complete marketplace catalog coverage.
- Verified supplier relationships or sourcing availability.

## 5. User Journey

1. The user enters a category and optional focus, such as `Area Rug, focus: premium pricing`.
2. The workflow parses the request and identifies the category and research focus.
3. Product listings are retrieved from Wayfair, Amazon, and Walmart.
4. Product records are reshaped into marketplace-specific datasets.
5. A statistics calculator calculates price ranges, averages, ratings, reviews, and price-band distributions.
6. AI agents generate the executive summary, competitor analysis, side-by-side comparison, pricing and whitespace analysis, strategic recommendations, and supplier identification.
7. The workflow assembles the report into downloadable HTML.
8. An evaluation agent scores report quality across seven dimensions.
9. Evaluation results and report data are stored in an n8n Data Table.

### High-Level Flow

Category Input → Marketplace Data Retrieval → Data Normalization → Statistical Analysis → Competitor Comparison → AI Insights → HTML Report → Quality Evaluation → Results Storage

## 6. Functional Requirements

Implementation statuses describe the supplied workflow configuration. End-to-end behavior requires validation.

| ID | Requirement | Implementation |
|---|---|---|
| FR-01 | Accept category and optional focus through chat. | Configured via n8n Chat Trigger and InputParser |
| FR-02 | Retrieve competitor product listings. | Configured for Wayfair, Amazon, and Walmart |
| FR-03 | Normalize marketplace product data. | Configured via reshape nodes; some fields are lost |
| FR-04 | Calculate marketplace-level statistics. | Configured via VerifiedStatsCalculator |
| FR-05 | Generate executive summaries and competitor analysis. | Configured via AI agents |
| FR-06 | Compare pricing, ratings, reviews, and assortment. | Configured via comparison agents |
| FR-07 | Identify pricing opportunities and assortment whitespace. | Configured via Pricing & Whitespace Analysis |
| FR-08 | Generate strategic recommendations and supplier suggestions. | Configured via AI agents; findings require verification |
| FR-09 | Assemble and export a structured HTML report. | Configured via HTML Assembler and output nodes |
| FR-10 | Evaluate report accuracy, completeness, and quality. | Configured via AI Evaluation |
| FR-11 | Generate improvement recommendations. | Configured via AI Improvement Recommendation |
| FR-12 | Calculate evaluation scores and quality bands. | Configured via Calculate Metrics |
| FR-13 | Store evaluation results for tracking. | Configured via n8n Data Tables; run tracking needs improvement |

### Required Report Sections

| Section | Content |
|---|---|
| Executive Summary | Key findings and competitive overview |
| Competitor Analysis | Marketplace-level assortment and positioning |
| Side-by-Side Comparison | Comparison of Wayfair, Amazon, and Walmart |
| Pricing & Whitespace Analysis | Price ranges, price bands, and potential opportunities |
| Strategic Recommendations | Suggested actions based on available evidence |
| Supplier Identification | Potential supplier information and sourcing leads |

### Statistical Requirements

- Product count uses the raw number of retrieved records.
- Price statistics use valid positive prices.
- Rating averages use valid positive ratings.
- Total review count is calculated from available review values.
- Price bands: Budget below $100; Mid $100–$300; Premium above $300.
- Discount data is identified when original/list price exceeds current price.
- Statistical denominators and missing values must be disclosed.

## 7. Non-Functional Requirements

- **Reliability:** Handle missing data, malformed responses, API failures, and incomplete marketplace results.
- **Accuracy:** Validate calculated statistics against retrieved product records.
- **Evidence integrity:** Preserve source information and distinguish observed data from AI interpretation.
- **Security:** Store API credentials securely and remove exposed secrets from shared workflow exports.
- **Maintainability:** Keep retrieval, calculation, analysis, evaluation, and reporting modular.
- **Observability:** Record execution outcomes, marketplace data counts, and evaluation failures.
- **Performance:** Measure workflow execution time before establishing targets.
- **Output quality:** Validate required report sections, figures, and source links.

## 8. Success Metrics and Evaluation

The workflow includes an AI evaluation framework that scores report quality across seven dimensions.

| Evaluation Dimension | What It Measures |
|---|---|
| Factual Accuracy | Whether report claims match available data |
| Completeness | Whether required report sections are included |
| Data Consistency | Whether figures and comparisons are consistent |
| Relevance | Whether findings address the requested category |
| Insight Quality | Whether analysis and recommendations are useful |
| HTML Quality | Whether the generated report is properly structured |
| Source Link Verification | Whether included source links are valid and accessible |

**Scoring:** Each dimension receives a score from 1–5. The overall score is the average of seven dimensions, rounded to two decimal places.

| Quality Band | Score |
|---|---:|
| Excellent | ≥ 4.5 |
| Good | ≥ 3.5 |
| Average | ≥ 2.5 |
| Poor | ≥ 1.5 |
| Very Poor | Below 1.5 |

Evaluation results are stored with issue counts and improvement recommendations. The current results table does not map the source-link verification score, and some issue counts are not yet based on verified classifications.

## 9. Risks and Future Improvements

### Key Risks

- Marketplace samples may be incomplete or unrepresentative.
- Reshape nodes may discard fields required by downstream analysis.
- AI-generated recommendations may contain unsupported claims.
- Marketplace data may be inconsistent or outdated.
- Evaluation results may not fully capture report quality.
- Hard-coded run numbers limit historical tracking.
- API failures may result in incomplete reports.

### Future Improvements

- Preserve all relevant source fields during normalization.
- Add claim-level evidence and source verification.
- Improve evaluation issue classification and score storage.
- Add unique run IDs and workflow version tracking.
- Expand regression testing beyond the current two-row limit.
- Add controlled retries and clearer failure handling.
- Track historical report quality and improvement trends.
- Validate supplier suggestions against independent sources.

## 10. Definition of Done

The prototype is ready for portfolio demonstration when:

- A supported category request completes successfully.
- Product listings are retrieved from all configured marketplaces.
- Marketplace statistics match calculations from valid source records.
- Comparisons clearly disclose sample limitations.
- All required report sections are generated.
- Unsupported claims and missing information are identified.
- The HTML report opens and displays correctly.
- Evaluation scores and recommendations are stored.
- Known workflow limitations are documented.
- Shared workflow exports contain no active API secrets.

A successful demonstration does not, by itself, establish production readiness.

---

**Product Summary:** The Competitor Monitoring AI Agent demonstrates how AI-powered workflow automation can transform marketplace product listings into structured competitive intelligence. It combines automated data collection, statistical comparison, AI-generated insights, HTML reporting, and report-quality evaluation. Its purpose is to improve the speed and consistency of competitor research—not to independently prove commercial performance or market demand.
