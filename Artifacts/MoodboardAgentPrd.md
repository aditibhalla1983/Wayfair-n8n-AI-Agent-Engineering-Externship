# 🖼️ Moodboard Generator AI Agent
### Product Requirements Document (PRD)

> **Lab 01 · Workflow Automation & AI Moodboard Design**  
> Building a generative AI workflow that transforms simple design ideas into detailed prompts and downloadable moodboard images.

![Status](https://img.shields.io/badge/Project-Prototype-blue)
![AI](https://img.shields.io/badge/AI-Google%20Gemini-4285F4)
![Automation](https://img.shields.io/badge/Automation-n8n-orange)
![Processing](https://img.shields.io/badge/Processing-Python-yellow)

---

# Product Requirements Document: Moodboard AI Agent

**Project Type:** AI Product Prototype  
**Platform:** n8n, Google Gemini, Cloudflare Workers AI  
**Status:** Prototype

## 1. Product Overview

The Moodboard AI Agent transforms a user's simple interior design idea into a refined image-generation prompt and generates a visual moodboard using an AI image-generation model. The workflow combines language-model reasoning, prompt cleanup, and image generation to help users explore design styles and visual directions.

## 2. Problem Statement

Users may have a general design idea but struggle to translate it into a detailed prompt that produces a cohesive visual result. Writing effective prompts requires describing colors, materials, textures, styling, and the overall atmosphere.

**Product hypothesis:** Automating prompt refinement can make moodboard creation easier and reduce the effort required to turn an initial idea into a visual concept.

## 3. Target Users

- **Interior design enthusiasts** exploring styles, palettes, and decor combinations.
- **Designers and creative professionals** developing early-stage visual concepts.
- **Design-focused users** who need inspiration from a short text description.

These audiences are initial hypotheses and have not yet been validated through user research.

## 4. Product Goals and Scope

**Goals**
- Convert brief design inputs into detailed, image-ready prompts.
- Generate a moodboard image from the refined prompt.
- Automate the workflow from chat input to image output.
- Provide a foundation for evaluating prompt quality and output relevance.

**Out of scope**
- Professional-grade design specifications or floor plans.
- Direct purchasing, product recommendations, or inventory integration.
- Persistent project storage, user accounts, and collaborative editing.

## 5. User Journey

1. The user enters a design idea, such as “bohemian rugs, neutral tones.”
2. Google Gemini powers an AI Agent that expands the idea into a detailed prompt covering style, colors, textures, and complementary decor.
3. A code node cleans the generated prompt for downstream processing.
4. Cloudflare Workers AI generates an image using the Flux Schnell model.
5. The final workflow node extracts the returned image data as a JPEG file.

## 6. Functional Requirements

| ID | Requirement | Implementation |
|---|---|---|
| FR-01 | Accept a design idea through chat. | Implemented via n8n Chat Trigger |
| FR-02 | Expand input into a detailed visual prompt. | Implemented via AI Agent and Gemini |
| FR-03 | Clean the prompt before generation. | Implemented via Code node |
| FR-04 | Generate a moodboard image. | Implemented via Cloudflare Workers AI |
| FR-05 | Extract generated image data into a file. | Implemented in final Code node; requires end-to-end validation |
| FR-06 | Handle failures and retry model requests. | AI Agent retry settings configured; broader error handling requires validation |

## 7. Non-Functional Requirements

- **Usability:** Keep the input experience simple and conversational.
- **Reliability:** Test the workflow across varied prompts and API failure scenarios.
- **Performance:** Measure end-to-end generation time during testing.
- **Security:** Store API credentials securely and remove secrets from public workflow exports.
- **Maintainability:** Keep workflow stages modular so prompts, models, and output handling can be updated independently.

## 8. Success Metrics and Evaluation

The prototype should be evaluated using a representative set of design prompts. Proposed metrics include:

- **Prompt relevance:** Does the refined prompt preserve the user's original intent?
- **Visual alignment:** Does the generated image reflect the requested style, palette, and materials?
- **Workflow success rate:** How often does a valid image return without manual intervention?
- **Generation time:** How long does the workflow take from input to output?
- **User satisfaction:** Can users use the result as a helpful starting point for design inspiration?

Baseline measurements and success thresholds are yet to be established.

## 9. Risks and Future Improvements

**Key risks:** Vague user inputs may produce generic prompts; generated images may not fully match the intended design; external API failures may interrupt the workflow; exposed credentials could compromise service access.

**Mitigations and next steps:** Test diverse prompts, add clearer error messages and validation, evaluate output quality against defined criteria, and secure credentials before sharing the workflow publicly. Future iterations could add style presets, adjustable visual preferences, multiple moodboard variations, and user feedback.

## 10. Definition of Done

The prototype is ready for portfolio demonstration when a user can submit a design idea, receive a refined prompt, generate an image, and retrieve the resulting file in a successful end-to-end test. Public documentation and workflow exports must not contain active API secrets.

---

**Product Summary:** The Moodboard AI Agent demonstrates how an AI-powered workflow can turn an early-stage design idea into a visual starting point by combining prompt engineering, orchestration, and image generation.

