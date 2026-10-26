# 🧪 Lab 01: Workflow Automation & AI Moodboard Design

## 🗺️ Architectural Paths
* Phase 1: Environment Handshake (Hello World)
* Phase 2: Logic-Driven Branching Layouts
* Phase 3: Context-Aware Prompt Engineering
* Phase 4: Autonomous Vision Engine (Moodboard Agent)

---

### Phase 1: Environment Handshake (Hello World)
* **Goal:** Verify local n8n installation, database memory, and canvas compiling nodes before building larger workflows.
* **Setup:** Connected a Manual Trigger node to a JavaScript Code node returning `{"message": "Hello World!"}`.
* **Why it Matters:** Cuts down on hidden runtime and schema errors early in the development pipeline.
* **Schematics:** [Demo Interface Link](LINK_HERE) | [Raw JSON Blueprint](LINK_HERE)

---

### Phase 2: Logic-Driven Branching Layouts
* **Goal:** Build an evaluation gate that teaches the system to react dynamically to changing input variables.
* **Mechanics:** A timed trigger adds metrics (e.g., `weather: "sunny"`) to an array passed through an IF logic gate.
* **Outcome:** Matches route to a custom layout node, while non-matches trigger a system backup path.
* **Schematics:** [Demo Interface Link](LINK_HERE) | [Raw JSON Blueprint](LINK_HERE)

---

### Phase 3: Context-Aware Prompt Engineering
* **Goal:** Enforce structural role constraints onto language models to scale raw keywords into deep image briefs.
* **Pipeline:** User Chat Input ➔ AI Agent Persona Mask ➔ Google Gemini Prompt Generation.

#### 🧪 Variant 1: Single-Aesthetic Concept
* **Input:** White Rug
* **AI Output:** "Interior design moodboard for premium white and ivory rugs, a curated collection of high-end textures and minimalist lifestyle imagery..."
* **Evaluation:** Successfully turned a two-word idea into a rich scene brief, balancing fiber macro views with wide space styling.
* **Logs:** [Generated Image](LINK_HERE) | [Model Input Data Panel](LINK_HERE)

#### 🧪 Variant 2: Multi-Style Matrix Framework
* **Input:** White Rug
* **AI Output:** "A high-end professional interior design moodboard titled 'The White Rug Collection,' organized into a clean grid layout showcasing 5 distinct styles..."
* **The 5 Styles:** Nordic Minimalist (Raw Wool), Boho Chic (Shag Fringe), Modern Opulence (Silk/Marble), Organic Earthy (Cotton Braids), Architectural Linear (3D Shadows).
* **Evaluation:** Explicit grouping rules forced the AI to act as a system tool, isolating conflicting design rules cleanly.
* **Logs:** [Generated Image](LINK_HERE) | [Model Input Data Panel](LINK_HERE)

---

### Phase 4: Autonomous Vision Engine (Moodboard Agent)
* **Goal:** Link text models and diffusion generation engines to synthesize final asset images hands-free.
* **Pipeline:** Chat Trigger ➔ Gemini Prompt Builder ➔ JavaScript String Sanitizer ➔ Hugging Face FLUX API.
* **Key Takeaway:** Custom script nodes are critical to scrub markdown formatting code so strings don't crash external API schemas.
* **Logs:** [Workflow Blueprint](LINK_HERE) | [Live Execution Logs](LINK_HERE) | [Final High-Fidelity Image](LINK_HERE)
