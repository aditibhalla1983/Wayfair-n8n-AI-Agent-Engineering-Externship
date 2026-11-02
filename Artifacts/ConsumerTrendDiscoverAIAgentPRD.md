# 📊 Consumer Trend Discovery AI Agent
### Product Requirements Document (PRD)

> Workflow Automation & AI-Powered Market Intelligence  
> Building an AI workflow that transforms product-category requests into structured trend insights, illustrative moodboards, and downloadable market intelligence reports.

![Status](https://img.shields.io/badge/Project-Prototype-blue)
![AI](https://img.shields.io/badge/AI-OpenRouter-purple)
![Automation](https://img.shields.io/badge/Automation-n8n-orange)
![Processing](https://img.shields.io/badge/Processing-Python%20%2B%20JavaScript-yellow)
![Image Generation](https://img.shields.io/badge/Images-Cloudflare%20Workers%20AI-F38020)

---

# Product Requirements Document: Consumer Trend Discovery AI Agent

Project Type: AI Product Prototype  
Platform: n8n, OpenRouter Chat Models, External Product and Trend APIs, Cloudflare Workers AI  
Status: Prototype

## 1. Product Overview

The Consumer Trend Discovery AI Agent transforms a user's product-category request into a structured market intelligence report.

The workflow retrieves product listings, social media text signals, blog content, and market research information. It classifies relevant products, standardizes product attributes, identifies aesthetic micro-segments, generates illustrative moodboards, and prepares a downloadable HTML report.

The initial prototype focuses on rug categories, including Area Rug, Outdoor Rug, Hallway Runner, and Shag Rug.

The product supports category exploration and decision preparation. It does not independently verify consumer demand, forecast sales, or replace commercial judgment.

## 2. Problem Statement

Category research requires users to gather and interpret information from product listings, social platforms, blogs, and market reports. These sources use inconsistent terminology and present evidence in different formats.

Users must manually identify recurring attributes, connect them to aesthetic themes, prepare visual references, and summarize potential actions. This process can be time-consuming and difficult to reproduce consistently.

Product hypothesis: Automating evidence collection, attribute normalization, trend synthesis, and report preparation can reduce research effort and help users identify opportunities worth validating.

## 3. Target Users

- Category managers exploring category composition and potential assortment opportunities.
- Merchandising teams evaluating materials, colors, patterns, sizes, and price positioning.
- Product strategy teams developing hypotheses for category growth.
- Marketing teams identifying aesthetic themes and messaging directions.
- Design and sourcing teams translating trend descriptions into visual concepts.

These audiences are initial hypotheses and have not yet been validated through user research.

## 4. Product Goals and Scope

### Goals

- Accept a category and optional focus through a conversational interface.
- Retrieve relevant product, social, blog, and market research records.
- Filter products that do not belong to the requested category.
- Normalize product attributes for comparison.
- Identify two to three distinct aesthetic micro-segments when evidence supports them.
- Generate moodboards that illustrate the identified style directions.
- Produce a structured, downloadable HTML report.
- Make missing data, sample limitations, and source boundaries visible.

### Initial Scope

- Area Rug
- Outdoor Rug
- Hallway Runner
- Shag Rug

### Out of Scope

- Verified sales forecasting or purchase-demand prediction.
- Automated purchasing or assortment changes.
- Guaranteed coverage of competitor catalogs or the overall market.
- Direct image-based trend recognition in the current prototype.
- Professional product specifications or manufacturing instructions.
- Persistent project storage, user accounts, and collaborative editing.
- Wayfair catalog-gap analysis in the supplied workflow version.

## 5. User Journey

1. The user enters a category and optional focus, such as:
   `Outdoor Rug, focus: weather-resistant weaves`.

2. The workflow validates the category and provides guidance when the input is unsupported.

3. External APIs return Amazon product listings, Instagram and Pinterest records, blog articles, and market research content.

4. An AI classification agent evaluates whether each product belongs to the selected category.

5. Relevant product records are standardized into attributes such as size, color, material, pattern, style, pile height, and price bucket.

6. A trend agent combines product attributes with social and blog text signals to identify aesthetic micro-segments.

7. A prompt-generation agent describes each style direction, and Cloudflare Workers AI generates illustrative moodboards.

8. Report-writing agents prepare the research sections, risks, and proposed recommendations.

9. The workflow assembles the HTML, embeds images, records structural validation results, and prepares a downloadable file.

### High-Level Flow

Category Input → Evidence Retrieval → Product Classification → Attribute Standardization → Trend Discovery → Moodboard Generation → Report Writing → HTML Export

## 6. Functional Requirements

Implementation statuses describe the supplied workflow configuration. End-to-end behavior requires validation.

| ID | Requirement | Implementation |
|---|---|---|
| FR-01 | Accept a category and optional focus through chat. | Configured via n8n Chat Trigger and input parser |
| FR-02 | Validate supported categories and guide invalid requests. | Configured via parser, IF node, and error response; category matching needs cleanup |
| FR-03 | Retrieve category-specific Amazon product records. | Configured via an external product API |
| FR-04 | Retrieve social, blog, and market research records. | Configured via external APIs |
| FR-05 | Normalize source records and retain available metadata. | Partially configured; original and fallback timestamps need distinction |
| FR-06 | Classify products and remove irrelevant or low-confidence matches. | Configured via an AI classifier and filtering code |
| FR-07 | Standardize product attributes. | Configured via an AI extraction agent |
| FR-08 | Calculate attribute distributions accurately. | Model-generated summaries exist; deterministic calculations and checks are required |
| FR-09 | Identify evidence-supported aesthetic micro-segments. | Configured via a trend agent; fallback segments require clear labeling |
| FR-10 | Generate illustrative moodboards. | Configured via prompt generation and Cloudflare Workers AI; multi-item behavior requires validation |
| FR-11 | Extract material, sizing, buyer, style, and care knowledge from blogs. | Configured via a knowledge-extraction agent |
| FR-12 | Generate the required report sections. | Configured via sequential writing agents; completeness checks require strengthening |
| FR-13 | Assemble images and sections into a downloadable HTML file. | Configured via JavaScript assembly and binary packaging |
| FR-14 | Display insufficient-data states without inventing distributions or market gaps. | Additional safeguards required |
| FR-15 | Connect material claims to supporting evidence. | Citation metadata partially prepared; final traceability is not enforced |
| FR-16 | Detect incomplete or inconsistent reports before publication. | Basic structural validation exists; release-blocking checks required |
| FR-17 | Handle API, parsing, and image-generation failures transparently. | Partial fallbacks exist; broader recovery requires implementation and testing |

### Required Report Sections

| Section | Content |
|---|---|
| Executive Summary | Key insight, principal findings, limitations, and proposed action |
| Scope of Research | Category, sources, sample counts, dates, and applicable market scope |
| Market Research | Market context, buyer profile, and expert guidance |
| Category Deep Dive | Category definition, use cases, micro-segments, and sizing |
| Product Attribute Analysis | Observed material, size, color, pattern, and price distributions |
| Visual Trend Analysis | Caption-derived aesthetic themes, moodboards, and social references |
| Trend Risks Assessment | Risk ratings, rationale, and mitigation suggestions |
| Demand Signals and Recommendations | Evidence interpretation, proposed tests, quick wins, and watch list |

### Missing-Data Requirements

- Show “Unavailable” or “Insufficient data” when usable records are missing.
- Do not represent an empty sample as a measured 0% distribution.
- Do not interpret missing sample matches as proof that a category or competitor lacks an offering.
- Label social-led opportunities as hypotheses requiring validation.
- Distinguish observed findings from proposed commercial actions.

## 7. Non-Functional Requirements

- Usability: Keep category entry simple and make report limitations easy to understand.
- Reliability: Test valid requests, invalid input, empty datasets, malformed responses, timeouts, and partial failures.
- Performance: Measure end-to-end and stage-level execution time before establishing targets.
- Evidence integrity: Preserve source identity, original collection dates, sample counts, and applicable market definitions.
- Statistical integrity: Calculate distributions consistently, disclose denominators, and account for missing attributes.
- Security: Store credentials securely and remove active secrets from shared workflow exports.
- Maintainability: Keep retrieval, classification, analysis, image generation, and export modular.
- Observability: Record source counts, stage outcomes, parsing failures, image failures, and validation warnings.
- Cost awareness: Track language-model and image-generation usage per report.
- Output quality: Check required sections, count consistency, image MIME types, and unresolved placeholders.

Wait nodes pace execution in the current prototype. They do not provide automatic retry recovery.

## 8. Success Metrics and Evaluation

The prototype should be evaluated using representative category requests and manually reviewed source samples.

| Metric | Evaluation Question |
|---|---|
| Category parsing accuracy | Does the system identify the requested supported category? |
| Product classification quality | Does it retain relevant products and reject irrelevant listings? |
| Attribute accuracy | Do normalized attributes match the source records? |
| Statistical consistency | Do reported distributions match calculations from validated records? |
| Evidence traceability | Can reviewers inspect the evidence supporting material claims? |
| Micro-segment usefulness | Are the identified segments distinct, coherent, and supported? |
| Moodboard alignment | Do images reflect the segment's palette, materials, style, and use case? |
| Report completeness | Are all applicable sections present and sufficiently developed? |
| Workflow success rate | How often does a valid report return without manual intervention? |
| Research efficiency | How much effort is saved compared with a manual research baseline? |
| Generation time and cost | What duration and service usage are required per report? |
| User satisfaction | Do users find the report useful for preparing category decisions? |

Baseline measurements and success thresholds are yet to be established.

## 9. Risks and Future Improvements

### Key Risks

- Empty or unrepresentative samples may produce misleading conclusions.
- Model-generated statistics may introduce unsupported precision.
- Caption-derived observations may be incorrectly presented as direct image analysis.
- Parsing failures may produce empty data or generic fallback segments.
- Multi-item handling may produce fewer moodboards than intended.
- Stale records may be presented as current market evidence.
- Synthetic images may be mistaken for available products.
- External API failures may interrupt report generation.
- Exposed credentials may compromise connected services.

### Mitigations and Next Steps

- Add evidence-availability gates before analysis and publication.
- Calculate distributions from validated records in code.
- Preserve source URLs, collection dates, and market scope.
- Label fallback content and AI-generated images clearly.
- Test item-wise moodboard generation.
- Add explicit error messages, controlled retries, and recovery behavior.
- Strengthen validation so incomplete or inconsistent reports are flagged or blocked.
- Rotate exposed credentials and use managed credential storage.

### Future Improvements

- Confidence and evidence-strength labels.
- Clickable citations and claim-level source tracking.
- Configurable geography and research periods.
- Historical trend comparisons and saved reports.
- Additional product categories.
- Multiple moodboard variations.
- User feedback on trend relevance.
- Validated catalog-comparison capabilities.
- Direct image analysis as a separately evaluated capability.

## 10. Definition of Done

The prototype is ready for portfolio demonstration when:

- A supported category request completes a successful end-to-end test.
- Invalid input returns clear, useful guidance.
- Retrieved and retained product counts are accurate.
- Empty-data scenarios do not create false distributions or market-gap claims.
- Displayed statistics match validated records.
- Micro-segments distinguish evidence from interpretation.
- Moodboards are labeled illustrative and render correctly.
- Every applicable report section is present.
- Material claims have inspectable supporting evidence.
- The HTML report opens without unresolved image placeholders.
- Failures and validation warnings remain visible.
- Public documentation and shared exports contain no active API secrets.

A successful demonstration does not, by itself, establish production readiness.

---

Product Summary: The Consumer Trend Discovery AI Agent demonstrates how AI-assisted workflow automation can combine product evidence, social text signals, structured analysis, and image generation into a category research report. Its value is faster synthesis and clearer exploration—not autonomous proof of demand.
