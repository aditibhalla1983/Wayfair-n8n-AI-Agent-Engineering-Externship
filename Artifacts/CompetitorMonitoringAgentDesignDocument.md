# 📊 Competitor Monitoring AI Agent — Design Document

**Architecture:** n8n + OpenRouter Chat Models + Marketplace Product APIs  
**Status:** Prototype  
**Marketplaces:** Wayfair, Amazon, Walmart  
**Initial Categories:** Area Rug, Outdoor Rug, Hallway Runner, Shag Rug

---

## 1. System Overview

The Competitor Monitoring AI Agent transforms a rug-category request into a structured competitive intelligence report comparing Wayfair, Amazon, and Walmart.

The workflow retrieves marketplace product listings, normalizes product data, calculates pricing and rating statistics, compares competitor assortments, identifies potential pricing opportunities, and generates strategic recommendations.

A separate AI evaluation process assesses the quality of generated reports, identifies potential issues, produces improvement recommendations, and stores evaluation results in an n8n Data Table.

The workflow uses Wayfair as the primary comparison baseline and evaluates Amazon and Walmart as competitors.

**Design Objective:** Automate marketplace research and transform fragmented product listing data into structured competitive insights, with an additional quality evaluation process to improve report reliability.

### 1.1 High-Level System Architecture

```mermaid
flowchart TD
    U(["User: Category + Optional Focus"])
    T["n8n Chat Trigger"]
    P["InputParser"]
    V{"Valid Category?"}
    E["Return Input Guidance"]

    subgraph DATA["Marketplace Data Collection"]
        W["Wayfair Product API"]
        A["Amazon Product API"]
        M["Walmart Product API"]
    end

    subgraph PROCESS["Data Processing"]
        RW["Reshape Wayfair"]
        RA["Reshape Amazon"]
        RM["Reshape Walmart"]
        MG["Merge Marketplace Data"]
        ST["VerifiedStatsCalculator"]
    end

    subgraph AI["AI Analysis and Report Generation"]
        EX["Executive Summary"]
        CA["Competitor Analysis"]
        SC["Side-by-Side Comparison"]
        PW["Pricing & Whitespace Analysis"]
        SR["Strategic Recommendations"]
        SI["Supplier Identification"]
    end

    subgraph OUTPUT["Report Generation"]
        SG["ScopeGenerator"]
        HA["HTML Assembler"]
        CL["Clean AI Output"]
        HR(["Downloadable HTML Report"])
    end

    subgraph EVAL["Report Evaluation"]
        ET["Evaluation Trigger"]
        EV["AI Evaluation"]
        IR["AI Improvement Recommendation"]
        CM["Calculate Metrics"]
        DB[("Evaluation Results Data Table")]
    end

    U --> T --> P --> V
    V -->|Invalid| E
    V -->|Valid| W
    V -->|Valid| A
    V -->|Valid| M

    W --> RW
    A --> RA
    M --> RM

    RW --> MG
    RA --> MG
    RM --> MG
    MG --> ST

    ST --> EX
    ST --> CA
    ST --> SC
    ST --> PW
    ST --> SR
    ST --> SI

    EX --> SG
    CA --> SG
    SC --> SG
    PW --> SG
    SR --> SG
    SI --> SG

    SG --> HA --> CL --> HR

    ET --> EV
    HR -. "Generated report and source data" .-> EV
    EV --> IR --> CM --> DB

    style U fill:#e8f1ff,stroke:#5284c4
    style V fill:#fff4d6,stroke:#c99b32
    style ST fill:#e5f5e8,stroke:#559966
    style EX fill:#f1e8ff,stroke:#9270c4
    style HR fill:#e8f1ff,stroke:#5284c4
    style EV fill:#fff4d6,stroke:#c99b32
    style DB fill:#e5f5e8,stroke:#559966
