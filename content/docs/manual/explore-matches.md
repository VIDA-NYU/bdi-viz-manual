---
weight: 200
title: "Explore Matches"
description: "Explore schema alignment candidates using the BDIViz interactive heatmap interface."
icon: "zoom_in"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-21T11:00:00-04:00"
draft: false
toc: true
---

## Overview 🔍

After uploading your files, BDIViz launches its main interface, allowing you to visually explore match candidates between your source dataset and the target schema.

---

## Interactive Heatmap 🔥

The heatmap is the primary visualization tool in BDIViz. Each cell represents a match candidate between a source attribute (y-axis) and a target attribute (x-axis).

![heatmap-gif](./images/interactive-heatmap.gif)

### Key Features

{{< tabs tabTotal="4">}}

{{% tab tabName="Heatmap Cells" %}}

Each cell corresponds to a potential match:

- **Color intensity** indicates similarity score (darker = stronger match).
- **Green** = accepted match, **Red** = rejected match.
- Click on a cell to inspect match details.

{{% /tab %}}

{{% tab tabName="X-Axis Hierarchy" %}}

![schema-hierarchy-gif](./images/schema-hierarchy.gif)

The x-axis displays the target schema's structure as a semantic hierarchy:

- **Category Level**: e.g., `clinical`, `biospecimen`
- **Node Level**: e.g., `diagnosis`, `treatment`
- **Leaf Nodes**: individual target attributes

Color and curved connectors help clarify relationships and improve navigation.

{{% /tab %}}

{{% tab tabName="Expandable Nodes" %}}

Clicking a heatmap node reveals a stacked histogram panel:

- **Top Chart**: Source column value distribution
- **Bottom Chart**: Target column value distribution

Use this to evaluate whether the two columns share meaningful overlap.

**Tip:** Similar distributions (e.g., shared categories like "Male" and "Female") often suggest semantic alignment.

![embedded-node](./images/embedded-node.png)

{{% /tab %}}

{{% tab tabName="Heatmap Top Tabs" %}}

![upper-tab](./images/upper-tab.png)

The top-level filter tabs help narrow your focus:

- **All**: View all candidate matches
- **Accepted**: Only show confirmed matches
- **Unmatched**: Only show source columns with no confirmed match
- **Expand on Hover**: Toggle whether expanded histograms appear on hover or click

{{% /tab %}}

{{< /tabs >}}

---

## Filters and Search Controls 🔍

Fine-tune the heatmap view using a suite of filters:

{{< tabs tabTotal="4">}}

{{% tab tabName="Source Attribute Selector" %}}

Select a specific source column to examine.

![source-attribute](./images/source-attribute.png)

Dropdown key:

- **Green**: Already matched
- **Grey**: Manually discarded
- **All**: Show all source attributes

![source-attribute-drop](./images/source-attribute-drop.png)

{{% /tab %}}

{{% tab tabName="Similarity Threshold" %}}

Set a minimum similarity score for visible candidates. Range: `0.0 – 1.0`.

- `0.0`: Show all matches
- `1.0`: Show only perfect matches

{{% /tab %}}

{{% tab tabName="Similar Attributes Displayed" %}}

Controls how many similar source attributes appear on the heatmap when a single source column is selected.

> Note: Only applies when Source Attribute ≠ "All".

{{% /tab %}}

{{% tab tabName="Search Bar" %}}

Quickly locate and highlight target attributes by name or keyword.

{{% /tab %}}

{{< /tabs >}}

---

## Lower Panel: Match Details 🔎

Clicking on any heatmap node reveals deeper insights below:

{{< tabs tabTotal="2">}}

{{% tab tabName="Value Comparisons" %}}

![value-comparisons](./images/value-comparisons.png)

Visualizes string-based fuzzy matching between source and target values.

- Each row: one source value + its closest matches
- Use to validate whether mapping is semantically and syntactically justified

{{% /tab %}}

{{% tab tabName="UpSet Plot" %}}

![upset-plot](./images/upset-plot.png)

Visualizes how different matchers contributed to the candidate match score.

- Each row: a matcher
- Each column: a candidate
- Dots indicate support from that matcher

{{% /tab %}}

{{< /tabs >}}

---

## LLM Agent Panel 🤖

![agent-panel](./images/agent-panel.png)

An embedded LLM-powered assistant provides contextual insights:

- **Diagnosis Summary**: Determines if a match is likely valid based on metadata, column names, and user history
- **Explanation Cards**: Highlight key reasons (e.g., name similarity, value overlap)
  - Click to expand for more detail
  - Provide feedback via 👍/👎 to refine model accuracy
- **Target Schema Metadata**: Enriched descriptions pulled from sources such as GDC

---

## What's Next? 🚀

After reviewing the matches:

- Accept or reject individual match suggestions
- Use filtering to prioritize high-confidence matches
- Proceed to export, refine, or apply your matched schema for downstream harmonization tasks