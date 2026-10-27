# Moodboard AI Agent — Design Document

**Architecture:** n8n + Google Gemini + Cloudflare Workers AI  
**Status:** Prototype

## 1. System Overview

The Moodboard AI Agent transforms a short interior design idea into a detailed image-generation prompt, then generates a moodboard image using an AI image model.

**Design objective:** Turn creative intent into visual inspiration through an automated, modular AI workflow.

### High-Level Architecture

```mermaid
flowchart TD
    U(["User Input"])
    T["n8n Chat Trigger"]
    A["AI Agent"]
    L["Google Gemini"]
    C["Clean Prompt"]
    I["Cloudflare Workers AI<br/>FLUX.1 Schnell"]
    O["Extract Image Data"]
    R(["Moodboard JPEG"])

    U --> T --> A --> C --> I --> O --> R
    L -. "Language model" .-> A

    style U fill:#e8f1ff,stroke:#5284c4
    style A fill:#f1e8ff,stroke:#9270c4
    style I fill:#e5f5e8,stroke:#559966
    style R fill:#e8f1ff,stroke:#5284c4
```


## 2. Agent Workflow and Responsibilities

 ![AI-generated Moodboard](images/MoodBoardAgent.png)



| Stage | Component | Responsibility |
|---|---|---|
| 1 | Chat Trigger | Accepts a design idea |
| 2 | AI Agent + Gemini | Expands the idea into a descriptive prompt |
| 3 | Clean Prompt | Normalizes prompt text |
| 4 | Cloudflare Workers AI | Generates an image using FLUX.1 Schnell |
| 5 | Output Processing | Extracts Base64 image data and prepares `moodboard.jpg` |

# Moodboard AI Agent — Design Document

**Architecture:** n8n + Google Gemini + Cloudflare Workers AI  
**Status:** Prototype

## 1. System Overview

The Moodboard AI Agent transforms a short interior design idea into a detailed image-generation prompt and then generates a moodboard image.

The workflow uses n8n to orchestrate the steps, Google Gemini to refine the user's idea, and Cloudflare Workers AI with FLUX.1 Schnell to generate the image.

## 2. High-Level Architecture

```mermaid
flowchart TD
    U(["1. User Input"]) --> T["2. Chat Trigger"]
    T --> A["3. AI Agent"]
    L["Google Gemini"] -. "Generates text" .-> A
    A --> C["4. Clean Prompt"]
    C --> I["5. Image Generation API"]
    I --> O["6. Process Image Output"]
    O --> R(["Moodboard JPEG"])

    style A fill:#f1e8ff,stroke:#9270c4
    style I fill:#e5f5e8,stroke:#559966
```

## 3. Step-by-Step Workflow

### Step 1 — Receive the Design Idea

**Node:** `When chat message received`  
**Purpose:** Starts the workflow when the user submits a message through the n8n chat interface.

**Input example:** `Bohemian rugs, neutral tones`

**Output:** The user's message becomes the input for the AI Agent.

### Step 2 — Interpret and Expand the Idea

**Node:** `AI Agent`  
**Model:** Google Gemini Chat Model

The AI Agent acts as an image-generation prompt engineer. It takes the user's short description and expands it into a more detailed visual concept.

Its instructions emphasize:
- Interior design style and atmosphere.
- Color palettes and material textures.
- Close-up material details and styled interior spaces.
- Complementary decor and visual consistency.

**Input:** The original design idea.  
**Output:** A detailed, image-ready text prompt.

The agent is configured to retry up to three times, waiting five seconds between retries. These settings do not guarantee that every failure will be recovered.

### Step 3 — Clean the Generated Prompt

**Node:** `Clean Prompt`  
**Technology:** Python code node

The generated prompt may contain line breaks or Markdown formatting. This node prepares the text for the image-generation request by:
1. Reading the agent's `output` field.
2. Joining multiple lines into a single line.
3. Removing Markdown asterisks.
4. Replacing double quotes with single quotes.

**Input:** The AI Agent's text output.  
**Output:** A cleaned prompt stored in the `prompt` field.

This is text normalization, not a semantic quality check; it does not verify that the prompt accurately reflects the user's intent.

### Step 4 — Generate the Moodboard Image

**Node:** `Cloudflare Image Generator`  
**Service:** Cloudflare Workers AI  
**Model:** `@cf/black-forest-labs/flux-1-schnell`

This node sends an HTTP POST request to the image-generation API. The request includes the cleaned prompt, limited to 2,000 characters, and a generation setting of four steps.

The API processes the prompt and returns a response containing image data when successful.

**Input:** The cleaned prompt and generation parameters.  
**Output:** The API response, which is passed to the next node.

### Step 5 — Extract and Prepare the Image

**Node:** `View Output File`  
**Technology:** Python code node

The final node searches for image data in the response's `result.image` field or the nested `body.result.image` field.

It then prepares an output item containing:
- **Filename:** `moodboard.jpg`
- **MIME type:** `image/jpeg`
- **Image data:** The returned Base64 string in the configured binary output field.

If image data is missing, the node raises an error instead of preparing the file.

The binary output format and actual file delivery should be verified with an end-to-end test in the deployed n8n version.

**[PLACEHOLDER: Insert your generated Moodboard image here]**

`![Generated Moodboard](images/MoodBoardAgent.png)`

## 4. Data Flow at a Glance

| Stage | Data received | Data produced |
|---|---|---|
| Chat Trigger | User message | Workflow input |
| AI Agent | Design idea | Detailed prompt |
| Clean Prompt | Agent output | Normalized prompt |
| Image API | Prompt and settings | API response with image data |
| Output Processing | API response | Prepared JPEG file |

## 5. Reliability, Evaluation and Security

**Reliability:** Test empty inputs, API failures, missing image data, and successful image delivery. The configured agent retries apply to that node and should not be assumed to handle all downstream errors.

**Evaluation:** Measure workflow success rate, prompt relevance, visual alignment with the requested design, and end-to-end generation time. Establish baselines using actual test results before setting targets.

**Security:** Store API tokens in n8n credentials or an appropriate secrets manager. Remove credentials from public workflow exports and rotate any token that has already been exposed.

## 6. Future Improvements

- Add input validation and clearer error messages.
- Introduce style presets and user-controlled color palettes.
- Generate multiple image variations.
- Evaluate output quality against a consistent set of test prompts.

## Summary

This workflow demonstrates an end-to-end AI pipeline: capturing a design idea, refining it with a language model, normalizing the prompt, generating an image, and preparing the output file. Each node has a distinct responsibility, making the prototype easier to test, debug, and extend.
