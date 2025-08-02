---
weight: 300
title: "LLM Agent"
description: "Explore schema alignment candidates using the BDIViz LLM Agent."
icon: "zoom_in"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-21T11:00:00-04:00"
draft: false
toc: true
---

## Overview 🔍

BDIViz features an embedded LLM-powered assistant to help you validate, explain, and refine schema alignment candidates. The agent provides contextual insights, interactive feedback, and harmonization support throughout your data mapping workflow.

---

## LLM Validation Panel 🤖

![agent-panel](./images/agent-panel.png)

The LLM Validation Panel offers real-time, context-aware suggestions and explanations for each match candidate:

- **Diagnosis Summary**: Evaluates if a match is likely valid based on metadata, column names, and user history.
- **Explanation Cards**: Highlights key reasons for each suggestion (e.g., name similarity, value overlap).
  - Click to expand for more detail.
  - Provide feedback via 👍/👎 to refine model accuracy.
- **Target Schema Metadata**: Enriched descriptions pulled from sources such as GDC.

---

## Harmonization Assistant 🤖

![harmonization-assistant](./images/harmonization-assistant.png)

The Harmonization Assistant acts as your copilot for schema mapping and harmonization tasks, offering interactive, conversational support.

### How to Access
{{< tabs tabTotal="2">}}

{{% tab tabName="Toggle Top Search Bar" %}}
- Toggle the assistant button on the right side of the search bar.
![harmonization-assistant-open-top](./images/harmonization-assistant-open-top.png)

{{% /tab %}}

{{% tab tabName="Right-click Expanded Node" %}}
- Right-click on a selected or expanded node.
![harmonization-assistant-open-expand](./images/harmonization-assistant-open-expand.png)


{{% /tab %}}

{{< /tabs >}}



---

### Example Q&A Interactions

#### Q: What is this candidate about?  
_A:_ Ask the assistant for a summary or description of the selected candidate.  
_Prompt:_ `What is this candidate about?`
![harmonization-assistant-about](./images/harmonization-assistant-about.png)

#### Q: What are the potential value mappings between the selected source and target attribute?  
_A:_ Request the assistant to show possible value mappings between the source and target attributes.  
_Prompt:_ `What are the potential value mappings between the selected source and target attribute?`  
![harmonization-assistant-values](./images/harmonization-assistant-values.png)

#### Q: Does the candidate I selected make sense? Why?  
_A:_ Ask the assistant to explain the reasoning behind a suggested match.  
_Prompt:_ `Does the candidate I selected make sense? Why?`  
![harmonization-assistant-why](./images/harmonization-assistant-why.png)

#### Q: Can you suggest more candidates from the schema?  
_A:_ Ask the assistant to search for additional candidates from the top recommendations or the entire target schema.  
_Prompt:_ `Besides the current recommendations, show me more candidates related to tumor sites or organs.`  
![harmonization-assistant-more-candidates](./images/harmonization-assistant-more-candidates.png)

#### Q: Can you accept or reject candidates for me?  
_A:_ Let the assistant accept or reject candidates based on chat history and its own suggestions.  
_Prompt:_ `From your memory and our chat, can you accept the candidate that makes the most sense?`  
![harmonization-assistant-accept](./images/harmonization-assistant-accept.png)

#### Q: Can you remember custom notes or metadata for later?  
_A:_ Add custom notes or metadata to the assistant’s memory for future reference.  
_Prompt:_ `Remember this metadata for the source dataset: CCRCC is a common problem among...`  
![harmonization-assistant-metadata](./images/harmonization-assistant-metadata.png)

#### Q: Can you remind me what this task is about?  
_A:_ Ask the assistant to recall the current task or context.  
_Prompt:_ `Recall from your memory, what is the context of this task?`  
![harmonization-assistant-context](./images/harmonization-assistant-context.png)

#### Q: Can you filter or rematch nodes based on criteria?  
_A:_ Start a new task or filter nodes based on clinical or semantic criteria.  
_Prompt:_ `Rematch with nodes related to clinical criteria.`  
![harmonization-assistant-about](./images/harmonization-assistant-about.png)

#### Q: Can you reorder or rescore candidates?  
_A:_ Request the assistant to reorder or rescore candidates (feature in development).  
_Prompt:_ `Reorder the candidates based on relevance to AJCC. Rescore and update them.`  

#### Q: Can you help me create a custom matcher task?  
_A:_ Ask the assistant to help create new matcher tasks (experimental).  
_Prompt:_ `Help me add a matcher using the rapidfuzz library.`  

---

> **Tip:** The Harmonization Assistant learns from your feedback and memory, improving its recommendations over time. Use the thumbs up/down and memory features to tailor the assistant to your project needs.

