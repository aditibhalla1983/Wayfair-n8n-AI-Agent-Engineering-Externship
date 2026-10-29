# Wayfair — AI Agent Engineering Externship

**Product:** AI-Powered Market Intelligence System | **Focus:** Trend Discovery, Competitive Intelligence & Workflow Automation | **Role:** AI Agent Engineering Extern

I worked on building AI-powered agents and automated workflows using n8n to address e-commerce challenges for Wayfair. The project spans visual moodboard generation, market trend discovery, competitor benchmarking, AI-generated insights, and a unified market intelligence dashboard.

The goal is to transform fragmented product and market data into structured insights and visual outputs that support business decision-making.

---

## 🔎 The Product Workflow

Style Prompt → Moodboard Generation → Market Trend Discovery → Competitor Benchmarking → AI Insights & Content Generation → Unified Market Intelligence Dashboard

---

## 💡 Project Milestones & Capabilities

| Project | Core Focus | Intended Outcome |
| :--- | :--- | :--- |
| **1. Moodboard Agent** | Convert style prompts into visual outputs. | Support visual exploration and creative ideation. |
| **2. Market Trend Discovery Agent** | Collect and analyze product and social media data. | Identify emerging trends and potential market opportunities. |
| **3. Competitor Monitoring Agent** | Track competitor product launches and pricing. | Identify competitive gaps and market whitespace. |
| **4. AI Insight & Content Agent** | Use Gemini to transform research signals into insights and content ideas. | Generate campaign concepts and marketing content. |
| **5. Market Intelligence Dashboard** | Organize findings in an auto-updating Google Sheets dashboard. | Make market intelligence easier to review and use. |

---

## 🎯 Target Users

- **Primary:** Business and product teams evaluating market trends and product opportunities.
- **Secondary:** Creative, marketing, merchandising, and supply chain teams using trend insights, competitor data, and structured reports.

*The exact primary user should be confirmed with the project stakeholders, particularly for the final dashboard.*

---

## ⚠️ Problems Addressed

- **Fragmented market data:** Product and social signals are spread across multiple sources.
- **Manual research:** Collecting and organizing market information takes time.
- **Limited competitor visibility:** Pricing and product launches require ongoing monitoring.
- **Unstructured insights:** Raw data needs to be transformed into useful trends, visual concepts, and content.
- **Scattered reporting:** Teams need a consistent way to access and review findings.

---

## 🚀 Technical Implementation

- **AI Agent Orchestration:** Built multi-step workflows using n8n.
- **LLM Integration:** Used Google Gemini and explored Mistral for prompt engineering and model benchmarking.
- **Data Processing:** Automated data collection, attribute extraction, classification, and structured output processing.
- **Generative Media:** Integrated FLUX through Hugging Face for AI-generated visual assets.
- **Dashboard Automation:** Used the Google Sheets API to organize and present workflow outputs.
- **Infrastructure:** Ran n8n in a Docker-based local environment.

---

## 📊 Success Metrics

| Metric | What It Measures |
| :--- | :--- |
| **Idea Value Rate** | Percentage of generated insights that stakeholders consider useful. |
| **Opportunity Adoption** | Percentage of identified opportunities selected for further evaluation. |
| **Sales Impact** | Sales associated with opportunities identified and pursued through the system. |
| **Research Time Saved** | Reduction in manual research and reporting effort. |
| **Data & Classification Accuracy** | Correctness of collected data, product attributes, and trend classifications. |
| **Workflow Reliability** | Successful execution and completeness of automated workflows. |

These metrics provide a proposed evaluation framework; actual targets and business impact should be established through testing and stakeholder feedback.

---

## 📁 Project Artifacts & Deliverables

- Moodboard Agent design document, PRD, and demo.
- Market Trend Discovery Agent.
- Competitor Monitoring Agent.
- AI Insight & Content Agent.
- Unified Market Intelligence Dashboard prototype.
- n8n workflow JSON files and implementation artifacts.
- Google Sheets reporting integration.
- Technical documentation and project demonstrations.

---

## 🎯 Key Learnings

- **Agentic Workflow Design:** Break complex business tasks into coordinated, reusable AI workflows.
- **Prompt Engineering:** Design and refine prompts for consistent, task-specific model outputs.
- **Data Engineering:** Transform unstructured market signals into structured information.
- **Human-Centered Product Thinking:** Connect AI-generated insights to stakeholder needs and business decisions.
- **Workflow Reliability:** Use logging, merging, error handling, and containerized infrastructure to support dependable automation.





# Wayfair n8n AI Agent Engineering Externship

![Project Status](https://img.shields.io/badge/Project-In_Progress-yellow)

This repository documents an 8-week technical externship focused on building autonomous AI agents to solve high-scale e-commerce challenges for **Wayfair**.

---

## 🎯 Project Milestones & Labs

### 🖼️ Project 1: Moodboard Agent (The Creative Foundation)
*Transforming style prompts into curated visual outputs.*

### 📂 Artifacts

* **Design:** [Moodboard Generator AI Agent](Artifacts/MoodboardAgentDesignDocument.md)

* **PromptGenerator:** [Prompt Generator](Artifacts/PromptGenerator.pdf)

* **PRD:** [Product Requirement Document](Artifacts/MoodboardAgentPrd.md)

* **DEMO:** [Watch the Demo](https://youtu.be/SoBe0uOeaNg)

### 🔍 Project 2: Market Trend Discovery
*Building agents to scrape and analyze product data and social media.*
* **Lab 02:** Discovery AI Agent
* **Artifacts:** [Product Requirement Document](#)

### 📊 Project 3: Competitor Benchmarking (Monitoring Agent)
*Tracking competitor launches and pricing to identify "whitespace" opportunities.*
* **Lab 03:** Competitor Monitoring AI Agent
* **Artifacts:** [Product Requirement Document](#)

### 💡 Project 4: AI Insight & Content Agent
*Using Gemini to turn raw signals into marketing content and campaign ideas.*
* **Lab 04:** Content Strategy AI Agent
* **Artifacts:** [Product Requirement Document](#)

### 📈 Project 5: Unified Market Intelligence Dashboard
*Designing a live, auto-updating Google Sheets tool for supply chain managers.*
* **Lab 05:** Final AI Agent
* **Demos & Prototypes:**
  * [DEMO: UI Prototype Walkthrough using Base44](#)
  * [Read about Prototype](#)
  * [PRD Case Study DEMO](#) | [PRD Case Study Presentation PDF](#)
* **Final Deliverables:**
  * [EXTERNSHIP PROJECT DEMO](#)
  * [View JSON: Updated Market Trend AI Agent](#)
  * [View JSON: Updated Competitor Monitoring AI Agent](#)
  * [View JSON: Dashboard Builder AI Agent](#)

🚀 **View All Labs & Artifacts:** [Agentic Workflow Hub](#)

---

## 🛠️ Skills Gained

* **AI Agent Development & Orchestration:** Building autonomous, multi-agent systems and complex agentic workflows using n8n.
* **LLM Implementation:** Advanced prompt engineering and model benchmarking with Gemini 2.0 and Mistral. Designing high-fidelity prompts for Gemini to ensure brand-aligned outputs.
* **Market Intelligence & Data Engineering:** Automated web scraping, attribute extraction, and structured data processing to find market whitespace.
* **Generative Media:** Integration of vision-language models (FLUX via Hugging Face) for automated asset creation.
* **Dashboard Design:** Visualizing real-time data pipelines for business stakeholders.
* **Infrastructure & DevOps:** Deploying and managing Docker containers to maintain a consistent, isolated development environment for n8n.

---

## ⚙️ Technical Specifications

| Component | Technology Stack |
| :--- | :--- |
| **Automation Engine / Orchestration** | n8n (Self-hosted via Docker) |
| **Large Language Models (LLM)** | Google Gemini (via Google AI Studio) |
| **Data & Dashboarding** | Google Sheets API |
| **Memory & Logic** | Logging, Wait, and Merge/Code Nodes |
| **Infrastructure** | Docker (Containerized workflow management) |
| **Hardware Baseline** | Local execution (8GB RAM / Intel i3 or above) |
