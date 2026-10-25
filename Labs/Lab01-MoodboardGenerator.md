
# 🧪 Lab 01: Getting Started with AI Agents – Moodboard Generator

## AI Agent Workflows

* Hello World!
* My First AI Agent with N8N: Conditional Flow
* Prompt Generator
* Moodboard Agent

---

### Hello World!

This "Hello World" lab is a foundational exercise designed to verify that your n8n environment is correctly installed and configured. By building this simple workflow, you confirm that you can create nodes, configure them, and successfully execute an end-to-end process.

#### 📊 Lab Summary

* **Objective:** Validate your development environment by displaying a "Hello World!" message to provide immediate confirmation that the system is operational.
* **Key Tasks:**
  * Initialize a new workflow within the n8n interface.
  * Add a Manual Trigger node to initiate the workflow manually.
  * Configure a Code node to return the string: `{"message": "Hello World!"}`.
  * Execute the workflow and inspect the output in the n8n interface to verify successful delivery.
* **Why It Matters:** While simple, this exercise is a standard "passing ritual" for developers. It ensures your toolchain (editor, interpreter, and execution environment) is working correctly before you attempt to build more complex, agentic automations.

This lab serves as your first step toward becoming a "flow programmer," helping you get comfortable with the n8n canvas and data flow before you move on to advanced agentic workflows.

🖼️ **Workflow Blueprint:**
* **View DEMO:** HERE
* **View JSON:** HERE

---

### My First AI Agent with N8N: Conditional Flow

In this lab, I walk through the fundamentals of n8n workflow automation by focusing on four key tactical areas:
* **Trigger Management:** Setting up schedules to act as an agent's "heartbeat."
* **Data Transformation:** Using the Code Node to inject and manipulate JSON data.
* **Conditional Logic:** Implementing If nodes to evaluate information.
* **Branching Workflows:** Executing different actions based on real-time data analysis.

The lab is structured as a logical flow, beginning with a Schedule Trigger to define my automation frequency, followed by a Code Node that simulates a data source, such as weather conditions. From there, I utilize an If Node as a logic engine to evaluate that data—for instance, checking if the weather is "sunny"—and finally, I connect Set Nodes to define distinct branching outcomes, such as sending a bright message for sunny days or a calmer one for cloudy conditions.

💡 **The Learning Outcome:** By following these steps, I can visualize how data flows through the system and how my logic dictates the final output. This process ensures that I am not just building a static script, but a dynamic, decision-making workflow that serves as the foundation for the more advanced autonomous agents I plan to build later.

🖼️ **Workflow Blueprint:**
* **View DEMO:** HERE
* **View JSON:** HERE

---

### Prompt Generator

The **Prompt Generator** is an automated AI agent built in **n8n** that transforms simple, high-level style ideas into professionally structured image generation prompts. This lab demonstrates the transition from a basic chatbot to a specialized AI agent by utilizing **System Messages** to define roles and constraints.

#### 🏗️ Workflow Architecture

The workflow follows a linear path from user input to AI-enhanced output:
1. **On Chat Message (Trigger):** Captures user input (e.g., "bohemian rugs") via the n8n chat interface.
2. **AI Agent (Logic):** Processes the input using a specific "Job Description" (System Message).
3. **Google Gemini (Model):** The Large Language Model (LLM) that powers the creativity and text generation.

#### 🌟 Key Features

* **Prompt Engineering:** Automatically expands simple phrases into detailed descriptions covering style, texture, lighting, and color palettes.
* **System Prompting:** Uses a rigorous system message to ensure the AI acts as an "Expert Image Generation Prompt Engineer."
* **Design-Ready Output:** Generates structured prompts specifically optimized for creating high-quality moodboards.

#### 🧪 Prompt Iteration 1: Single Trend Concept

* **Chat Input:** White Rug
* **Generated Image Prompt Block:** "Interior design moodboard for premium white and ivory rugs, a curated collection of high-end textures and minimalist lifestyle imagery. The board includes: a macro close-up of tactile plush wool and boucle fibers, a wide-angle shot of a sun-drenched modern living room featuring a large cream-colored area rug on light oak flooring, a detail shot of hand-carved geometric patterns in white-on-white pile, and a flat-lay of complementary materials like raw linen, travertine stone, and dried pampas grass. Color palette: alabaster, eggshell, soft cream, and warm sand. Soft natural lighting with airy shadows, clean grid layout, professional editorial aesthetic, 8k resolution."

🖼️ **Execution Outputs:**
* **Moodboard Output:** (Insert Moodboard Image Output Here)
* **Prompt Output:** (Insert Prompt Panel Screenshot Here)

📝 **Reflection:**  
I wanted to see if I could take a super basic idea like "White Rug" and build it out into a detailed, professional image prompt for a single, solid moodboard concept. Looking at the result, I noticed the AI did a great job of turning that minimal input into a really rich, visual description—blending close-up material textures like bouclé with wide-angle room shots. By sticking to a tight color palette and a clean grid layout, the output felt very intentional and editorial. It showed me that if you give the model clear rules about lighting, camera angles, and matching materials, it can easily flesh out a single, focused vision without getting off track.

#### 🧪 Prompt Iteration 2: Multi-Style Framework Expansion

* **Chat Input:** White Rug
* **Generated Image Prompt Block:** "A high-end professional interior design moodboard titled 'The White Rug Collection,' organized into a clean grid layout showcasing 5 distinct styles. 1. Nordic Minimalist: featuring a high-pile cream wool rug, light oak wood, and functional soft-grey furniture. 2. Bohemian Chic: a Moroccan-inspired white shag rug with tassels, paired with terracotta pots and dried pampas grass. 3. Modern Opulence: a shimmering silk-blend white rug with subtle high-low carving, accented by gold hardware and white marble. 4. Organic Earthy: a chunky braided white cotton rug, paired with raw linen fabrics and smooth stone textures. 5. Architectural Linear: a low-profile white rug with geometric 3D patterns, matte black metal accents, and concrete walls. The moodboard includes macro close-ups of fiber textures (bouclé, silk, jute, wool) alongside styled room vignettes. Soft natural daylight, professional studio lighting, 8k resolution, clean aesthetic, inspiration-ready for a design team."

🔍 **Breakdown of the 5 Integrated Styles:**
* **Nordic Minimalist (The "Hygge" Look):** Focuses on warmth and simplicity. It emphasizes heavy wool textures and light woods to make a white rug feel cozy rather than sterile.
* **Bohemian Chic (The "Global" Look):** Focuses on "shag" and fringe. It uses the white rug as a neutral base for tactile elements like macramé, pampas grass, and warm ceramics.
* **Modern Opulence (The "Luxury" Look):** Focuses on sheen and light reflection. This style uses materials like viscose or silk to give the white rug a "glow," paired with high-end materials like marble and brass.
* **Organic Earthy (The "Handcrafted" Look):** Focuses on raw, chunky weaves. It highlights the "perfectly imperfect" nature of hand-braided fibers and natural linens.
* **Architectural Linear (The "Gallery" Look):** Focuses on shadow and depth. It uses 3D patterns (carved piles) to create visual interest through shadows rather than color, paired with high-contrast black accents.

🖼️ **Execution Outputs:**
* **Moodboard Output:** (Insert 5-Style Grid Moodboard Image Here)
* **Prompt Output:** (Insert Multi-Prompt Panel Screenshot Here)

📝 **Reflection:**  
I wanted to push the model further by forcing it to break that same trend down into five completely different design styles. What stood out to me here was how introducing those specific categories—like Nordic, Boho, and Modern Opulence—completely changed how the AI organized the information. Instead of just writing a pretty description, it built a structured, highly functional collection that actually compares different materials, like raw jute versus shiny silk. This version proved that when you explicitly ask for specific layouts and themes, the model stops acting like a creative writer and starts acting like a strategic design tool.
