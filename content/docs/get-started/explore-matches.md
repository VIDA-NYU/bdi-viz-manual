---
weight: 200
title: "Explore Matches"
description: "Once the files finished loading, you will be presented with the main BDIViz interface."
icon: "zoom_in"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-19T13:38:17-04:00"
draft: false
toc: true
---

> Once your files are uploaded, BDIViz will load the full interface for exploring match candidates between your source and target datasets.

## Interactive Heatmap

This is the central visual of BDIViz. Each cell in the heatmap represents a match candidate between a source attribute (on the y-axis) and a target attribute (on the x-axis).

![heatmap-gif](./images/interactive-heatmap.gif)


### Heatmap Components

{{< tabs tabTotal="4">}}
{{% tab tabName="Heatmap Nodes" %}}

Each cell in the heatmap represents a match candidate between a source attribute (on the y-axis) and a target attribute (on the x-axis).

- Color intensity represents match strength: darker = higher match score.
- Green indicates accepted matches; red indicates rejected ones.
- Click on a node to inspect further details.

{{% /tab %}}
{{% tab tabName="X-Axis" %}}

![schema-hierarchy-gif](./images/schema-hierarchy.gif)

The x-axis of the heatmap represents the target schema’s attribute space in a structured, hierarchical layout—specifically designed to support the complexity of biomedical data models like the Genomic Data Commons (GDC).

This hierarchy includes:

- **Categories** (e.g., "clinical," "biospecimen")
- **Nodes** (e.g., "diagnosis," "treatment")
- **Target Attributes** as leaf nodes

Color coding helps differentiate between categories, while curved connectors visually represent hierarchical relationships. Users can hover over any part of the hierarchy to highlight supercategories, specific categories, or individual columns, aiding navigation and contextual understanding.


{{% /tab %}}
{{% tab tabName="Expandable Node" %}}

Once you click on a heatmap node, the node expand and shows a stacked heatmap.

- **The upper histogram** shows the distribution of values from the source column.

- **The lower histogram** shows the distribution from the target column.

These visuals help assess whether the values in the two columns are statistically or categorically aligned. For example, if both columns share similar categories with comparable frequency distributions, it suggests a strong match.

_**Interpretation Tip:** Matching distributions with similar peaks (e.g., a high frequency of "Male" and "Female" values) may indicate semantic alignment. Dissimilar distributions can signal a mismatch or a need for closer inspection._

![embedded-node](./images/embedded-node.png)

{{% /tab %}}
{{% tab tabName="Top Tabs (above heatmap)" %}}

![upper-tab](./images/upper-tab.png)

- **All:** Displays all potential matches.

- **Accepted:** Shows only those that have been manually confirmed.

- **Unmatched:** Lists only those source attributes with no confirmed match.

- **Expand On Hover:** _This toggle controls if the expandable node will be expanded on mouse hover or not(on click)._

{{% /tab %}}
{{< /tabs >}}

## Filters and Search Tools

BDIViz provides several ways to customize and narrow your view:

{{< tabs tabTotal="4">}}
{{% tab tabName="Source Attribute" %}}

Lets you choose which column to focus on.

![source-attribute](./images/source-attribute.png)

Once click you will able to see this dropdown menu showing all the source attributes:
- **All:** Shows all source attributes in a paginatable manner.
- **Attributes in green:** The attributes that already have at least one accpeted candidate.
- **Attributes in grey:** The attributes that is discarded by user.

![source-attribute-drop](./images/source-attribute-drop.png)

{{% /tab %}}
{{% tab tabName="Similarity Threshold" %}}

Adjusts the minimum score a candidate must meet to appear. Values range from 0 (show all) to 1 (only highest similarity).

{{% /tab %}}
{{% tab tabName="Similar Attributes" %}}

Determines how many similar source columns appear in the y-axis for better comparative context.

**Note:** This only apply when **Source Attribute** is not set to **All**.


{{% /tab %}}
{{% tab tabName="Search Bar" %}}

Lets you highlight specific target attributes by name or keyword.


{{% /tab %}}
{{< /tabs >}}


## Lower Panel Visuals

When a node is selected from the heatmap, the bottom panels expand to provide deeper insights:

{{< tabs tabTotal="2">}}
{{% tab tabName="Value Comparisons" %}}

![value-comparisons](./images/value-comparisons.png)

Visual representation of fuzzy-matched value pairs between the selected source and target columns.

Each row shows a unique source value and its closest string-matched counterpart(s) from the target.

Helps validate or question whether two attributes should be considered a match.

{{% /tab %}}
{{% tab tabName="UpSet Plot" %}}

![upset-plot](./images/upset-plot.png)

the UpSet Plot provides a detailed breakdown of how each individual matcher contributed to the overall score of the selected candidate.

Each matcher is represented as a row, and each column represents a candidate match. A dot is shown where a matcher supports a given match.

{{% /tab %}}
{{< /tabs >}}

## LLM Agent Panel

![agent-panel](./images/agent-panel.png)

- **Overview Diagnosis:** Summarizes whether the current match is likely valid or not, based on metadata, column names, and prior interactions.

- **Explanation Cards:**

  - Each card explains one rationale (e.g., shared terms, similar distributions, matching patterns).

  - Click to expand each explanation.

  - Feedback Buttons: Let you provide a **thumbs-up** or **thumbs-down** to help improve the model’s future reasoning.

- **Target Schema Descriptions:** Additional metadata from sources like GDC are displayed for further context.