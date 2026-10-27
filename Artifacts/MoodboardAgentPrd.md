# 🖼️ Moodboard Generator AI Agent
### Product Requirements Document (PRD)

> **Lab 01 · Workflow Automation & AI Moodboard Design**  
> Building a generative AI workflow that transforms simple design ideas into detailed prompts and downloadable moodboard images.

![Status](https://img.shields.io/badge/Project-Prototype-blue)
![AI](https://img.shields.io/badge/AI-Google%20Gemini-4285F4)
![Automation](https://img.shields.io/badge/Automation-n8n-orange)
![Processing](https://img.shields.io/badge/Processing-Python-yellow)

---

## 📌 1. Product Overview

The **Moodboard Generator AI Agent** is a generative AI workflow designed to turn a short design request into a detailed visual prompt and a downloadable moodboard image.

The prototype combines workflow automation, prompt engineering, Python-based prompt processing, and an image-generation service to explore how AI can support creative ideation.

For example, a user enters:

**Input:** `White Rug`

The AI expands the request into a richer creative direction that can include materials, textures, interior design aesthetics, and visual composition. The processed prompt is then passed to an image-generation service to produce a moodboard.

### Product vision

Help users move from a rough design idea to a visual starting point with less manual prompt-writing effort.

---

## 🎯 2. Problem Statement

A user may know what they want to see but struggle to describe the details required to generate a compelling visual.

A request such as *“White Rug”* leaves several creative questions unanswered:

- What material or texture should the rug have?
- Should the aesthetic be minimalist, bohemian, luxurious, or natural?
- What type of interior should surround the product?
- What lighting, composition, and atmosphere should the image convey?

Manually creating a detailed image-generation prompt can introduce friction into the creative process.

**Product hypothesis:** An AI agent that expands short design requests into structured visual prompts can make it easier for users to explore design concepts.

*This is a product hypothesis to validate through user testing, not a measured customer outcome.*

---

## 👤 3. Target User

### Primary target-user hypothesis: Inspiration-seeking home shopper

A person exploring home décor who has a general idea of the style or product they want but needs help turning it into a more specific visual direction.

**Potential user needs**

- Explore different interior design aesthetics.
- Translate a simple idea into a detailed visual description.
- Generate a moodboard without manually writing complex prompts.
- Compare creative directions before deciding what they like.

**Validation needed:** User interviews and usability testing should confirm whether this audience experiences the problem and finds the generated output useful.

---

## 💡 4. Product Goals and Non-Goals

### Goals

- Accept a short design idea through a chat interface.
- Use Google Gemini to generate a detailed image-generation prompt.
- Process and sanitize the prompt using Python.
- Send the processed prompt to an image-generation service.
- Process the image-generation response.
- Return a downloadable moodboard image.
- Experiment with different prompt styles for the same input.

### Non-goals

The initial prototype does not aim to:

- Recommend specific purchasable products.
- Retrieve live product prices or inventory.
- Guarantee exact visual representation of real products.
- Replace professional interior design services.
- Provide persistent user profiles or saved design histories.
- Demonstrate production readiness or proven business impact.

---

## 🏗️ 5. System Workflow

The lab was developed incrementally, moving from basic workflow validation to an end-to-end image-generation pipeline.

### Phase 1 — Workflow validation

**Workflow:** Manual Trigger → Code Node

The initial workflow verified that n8n could execute a basic task and return an expected response.

Example output:

```json
{
  "message": "Hello World!"
}
```

**Objective:** Validate the environment and establish a baseline before adding more complex workflow logic.

### Phase 2 — Conditional workflow logic

**Workflow concept:** Trigger → Condition → IF Branch

A conditional workflow experiment used a variable, such as whether the weather was sunny, to route execution toward a custom layout or a fallback path.

**Objective:** Explore conditional execution and understand how workflow logic can direct tasks along different paths.

### Phase 3 — AI prompt engineering

**Workflow:** Chat Input → AI Agent → Google Gemini

This phase focused on expanding a short input into a more descriptive creative prompt.

For the input `White Rug`, two approaches were explored.

**Approach A: Single-aesthetic concept**

A focused creative direction emphasizing premium white and ivory rugs, high-end textures, and minimalist lifestyle imagery.

**Approach B: Multi-style concept matrix**

A collection concept called **“The White Rug Collection”**, exploring five distinct aesthetics:

| Design style | Creative direction |
|---|---|
| Nordic Minimalist | Raw wool, clean lines, restrained simplicity |
| Boho Chic | Shag textures, fringe, relaxed styling |
| Modern Opulence | Silk-like textures, marble-inspired surroundings |
| Organic Earthy | Cotton braids, natural materials |
| Architectural Linear | Geometric details, dimensional shadows |

**Objective:** Explore how prompt structure influences creative direction and supports different visual concepts from the same initial request.

### Phase 4 — End-to-end moodboard generation

The final workflow connects prompt generation, Python processing, and image generation.

```text
Chat Trigger
     ↓
Google Gemini — Prompt Builder
     ↓
Python — Prompt Processing
     ↓
Image-Generation Service
     ↓
Process Image Response
     ↓
Downloadable moodboard.jpg
```

**Expected output:** A generated moodboard image based on the user's original design request.

**Implementation note:** Verify the exact image-generation provider and node configuration before documenting the provider name. The confirmed workflow notes establish image-generation integration but do not conclusively establish the provider.

---

## ⚙️ 6. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | Accept a design request through the chat trigger. | Must have |
| FR-02 | Expand the request into a detailed visual prompt using Google Gemini. | Must have |
| FR-03 | Process and sanitize the prompt using Python. | Must have |
| FR-04 | Send the processed prompt to an image-generation service. | Must have |
| FR-05 | Process the image-generation response. | Must have |
| FR-06 | Return a downloadable moodboard image. | Must have |
| FR-07 | Support experiments with different creative prompt directions. | Should have |

---

## 🧑‍💻 7. User Stories & Acceptance Criteria

### US-01 — Submit a design idea

**As a** home décor inspiration seeker,  
**I want to** enter a short design idea,  
**so that** I can begin generating a visual concept.

**Acceptance criteria**

- [ ] The chat trigger receives the user's design input.
- [ ] The workflow passes the input to the prompt-generation stage.
- [ ] Missing or invalid input is handled clearly. *(To implement or verify.)*

### US-02 — Enrich the prompt

**As a** user with a rough design idea,  
**I want** the AI to expand it into a detailed visual prompt,  
**so that** the image-generation service receives useful creative direction.

**Acceptance criteria**

- [ ] Google Gemini generates the expanded prompt.
- [ ] The expanded prompt preserves the original subject.
- [ ] Relevant details such as style, material, texture, and composition are included where appropriate.
- [ ] The generated prompt is passed to the Python processing stage.

### US-03 — Generate a moodboard

**As a** user exploring visual inspiration,  
**I want** the workflow to generate a moodboard from my idea,  
**so that** I can review the resulting visual concept.

**Acceptance criteria**

- [ ] The processed prompt is sent to the configured image-generation service.
- [ ] A successful response is processed into an image artifact.
- [ ] The moodboard is made available for download.
- [ ] Generation failures are communicated clearly. *(Error handling to verify.)*

### US-04 — Explore different aesthetics

**As a** user who is uncertain about a design style,  
**I want to** explore alternative creative directions,  
**so that** I can compare possible visual concepts.

**Acceptance criteria**

- [ ] The same input can be used to experiment with different prompt directions.
- [ ] The resulting prompts can be compared for style, material, texture, and composition.
- [ ] The five-style White Rug Collection can serve as an evaluation example.

*Note: The multi-style matrix was explored as a prompt experiment. A user-facing style selector is a potential future feature, not an assumed implemented capability.*

---

## 📐 8. Non-Functional Requirements

These requirements guide further validation; they are not claims that the prototype already meets them.

| Area | Requirement |
|---|---|
| Reliability | Handle invalid inputs and failed API calls gracefully. |
| Usability | Allow users to start with a simple design idea. |
| Output integrity | Ensure the returned artifact is a valid, accessible image. |
| Maintainability | Keep prompt generation, Python processing, image generation, and response handling identifiable as separate stages. |
| Security | Store API credentials securely and never commit secrets to GitHub. |
| Efficiency | Measure generation time and cost before making performance claims. |

---

## 🧪 9. AI Evaluation Strategy

A successful workflow run is necessary, but it does not automatically mean the generated output is useful or high quality.

The next step is to evaluate both the workflow and its creative output.

### Proposed evaluation dimensions

| Dimension | Evaluation question |
|---|---|
| Intent fidelity | Does the output preserve the user's original idea? |
| Style adherence | Does the visual direction match the requested aesthetic? |
| Visual relevance | Is the generated image relevant to the requested subject? |
| Prompt quality | Does the expanded prompt contain useful visual details? |
| Artifact validity | Is the image accessible and usable? |
| Workflow completion | Does the workflow reach the expected output? |
| Error handling | Are failures communicated clearly? |

### Suggested test inputs

| Test | Input | Purpose |
|---|---|---|
| T-01 | `White Rug` | Test a short, broad request. |
| T-02 | `Minimalist ivory rug for a bright living room` | Test a style-specific request. |
| T-03 | `Natural wool rug with a soft texture` | Test material-specific details. |
| T-04 | `Something cozy` | Explore an ambiguous request. |
| T-05 | Empty input | Test input validation. |
| T-06 | Simulated image-generation API failure | Test failure handling where feasible. |

*These are proposed test cases. Record results only after running the tests.*

---

## 📊 10. Success Metrics

The following metrics are proposed for future validation.

### Workflow performance

- Successful moodboard generation rate.
- End-to-end workflow completion rate.
- Image-generation failure rate.
- Average end-to-end generation time.
- Cost per successful generation.

### Creative quality

- Intent fidelity score.
- Style adherence score.
- Visual relevance score.
- Human reviewer rating of prompt usefulness.

### Potential user value

- Percentage of users who find the moodboard useful.
- Percentage of users interested in exploring another style.
- User-reported ease of turning an idea into a visual concept.

**Measurement principle:** Establish baselines and targets after initial testing. No quantitative performance or customer-impact results are claimed at this stage.

---

## ⚠️ 11. Risks & Mitigations

| Risk | Potential mitigation |
|---|---|
| AI prompt drifts away from the user's intent | Preserve the original subject and evaluate intent fidelity. |
| Different styles produce similar results | Test distinct style directions using consistent input. |
| Image-generation API fails | Add appropriate error handling and retries where supported. |
| Returned image is invalid or inaccessible | Validate the response and output artifact. |
| Generated imagery misrepresents a real product | Present the moodboard as inspiration, not an exact product representation. |
| API credentials are exposed | Use managed credentials and exclude secrets from version control. |
| Output quality is subjective | Apply a consistent rubric and use multiple reviewers where possible. |

---

## 🚀 12. Roadmap

### Phase 1 — Prototype foundation

- [x] Validate basic n8n workflow execution.
- [x] Experiment with conditional workflow logic.
- [x] Explore prompt generation with Google Gemini.
- [x] Assemble an end-to-end image-generation workflow.
- [x] Process the image response and return a downloadable artifact.

### Phase 2 — Reliability and evaluation

- [ ] Test a representative set of design prompts.
- [ ] Verify error handling and output validity.
- [ ] Record generation latency and cost.
- [ ] Compare focused prompts with multi-style prompts.

### Phase 3 — Product experience improvements

- [ ] Explore a user-facing style selection capability.
- [ ] Allow users to refine generated concepts.
- [ ] Improve feedback for invalid input and generation failures.
- [ ] Validate usability with representative users.

### Phase 4 — Potential e-commerce extensions

- [ ] Explore connections between visual inspiration and product discovery.
- [ ] Investigate whether moodboards can support shopping exploration.
- [ ] Validate user value before considering product recommendations.

*Roadmap items in Phases 2–4 are proposed work, not completed features.*

---

## ✅ 13. Definition of Done

The initial prototype is ready for a portfolio demonstration when the following have been verified:

- [ ] The chat trigger accepts a design request.
- [ ] Google Gemini generates a detailed prompt.
- [ ] Python processes the prompt.
- [ ] The configured image-generation service returns a response.
- [ ] The workflow processes the response into an image.
- [ ] The generated moodboard is accessible to the user.
- [ ] At least one successful end-to-end run is captured.
- [ ] The repository includes a workflow screenshot and sample output.
- [ ] Implemented functionality is clearly distinguished from future proposals.

---

## 📝 14. Product Management Takeaways

This lab demonstrates an incremental approach to building a generative AI workflow:

1. **Validate the foundation:** Confirm that the automation environment works before adding complexity.
2. **Explore workflow logic:** Understand how conditions can control execution paths.
3. **Experiment with prompts:** Compare how different prompt structures influence creative direction.
4. **Integrate the components:** Connect the AI prompt builder, Python processing, and image generation.
5. **Plan for evaluation:** Define how quality, reliability, and potential user value should be measured.

From a Technical GenAI Product Management perspective, this project creates a foundation for discussing product hypotheses, requirements, workflow architecture, prompt quality, evaluation, technical risks, and future product opportunities.

---

## 📌 Final Summary

The Moodboard Generator AI Agent explores how generative AI can transform a short design request into a more detailed prompt and a downloadable visual artifact.

The prototype combines **n8n workflow automation, Google Gemini prompt generation, Python-based prompt processing, and image-generation integration**.

The next step is to validate output quality and workflow reliability systematically, then use the results to prioritize product improvements.

