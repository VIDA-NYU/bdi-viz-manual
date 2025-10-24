---
weight: 300
title: "Verify Value Matching"
description: "Verify the curated source attrbute value to target attribute value mappings"
icon: "match"
date: "2025-10-24T17:58:00-00:00"
lastmod: "2025-10-24T17:58:00-00:00"
draft: false
toc: true
---

## Installation 🛠️

For system-specific installation instructions:
- AMD64 architecture: Follow the [Linux/Unix installation guide]({{% relref "/docs/installation/install-on-linux" %}})
- ARM64 architecture (Apple Silicon): Follow the [MacOS installation guide]({{% relref "/docs/installation/install-on-macos" %}})

## Overview ✅

This guide walks you through verifying value mappings after schema alignment. You will enable Developer Mode, upload a ground truth CSV for value mapping verification, and use the heatmap and Data Wrangler to confirm results.

---

## Start a New Session 🗂️

![new-session](images/new-session.png)

- On the far left of the top navbar, enter a name in the **New session** text input to create a new session.
- The new session inherits data from the default session, so you can proceed without re-uploading.



![value-mapping-init](images/value-mapping-init.gif)


## Toggle Developer Mode 🧰

- **How to open**: Click the arrow icon on the top-left corner to open the side panel, then toggle **Developer Mode**.
- **What it enables**:
  - **Upload pre-annotated ground truth for schema matching** (attribute pairs)
  - **Upload pre-annotated ground truth for value mappings** (value-to-value)
  - **Upload custom matchers** (not covered here)

Developer Mode surfaces additional upload slots and debugging panels designed for power users and evaluators.

---

## Prepare Data and Start the Task 📦

For verifying value mappings, prepare the following:

- **Source table (required)**: your raw dataset CSV, e.g., `Cao.csv`.
- **Target table (not needed)**: leave empty to use the built-in **GDC** schema as target.
- **Ground truth CSV (required for verification)**: a file with exactly four columns:
  - `source_attribute`
  - `target_attribute`
  - `source_value`
  - `target_value`

**Example (subset):**

```csv
source_attribute,target_attribute,source_value,target_value
FIGO_stage,figo_stage,IA,Stage IA
FIGO_stage,figo_stage,IIIC1,Stage IIIC1
Ethnicity,ethnicity,Hispanic or Latino,hispanic or latino
Race,race,White,white
Gender,gender,Female,female
```

After files are ready, click the blue **Start Value Matching** button at the bottom-right to launch the verification task.

---

## Review Schema Matches on the Heatmap 🔥

- The heatmap displays candidate matches between source (y-axis) and GDC target attributes (x-axis). Ground-truth schema pairs included in your CSV should appear as heatmap cells.
- **Hover** a cell to preview details; **click** to expand the embedded node with distributions and comparisons.
- Use the control panel filters to narrow candidates by similarity, attribute, or status.

![interactive-heatmap](images/interactive-heatmap.gif)

> Need a refresher on filters and controls? See {{% relref "/docs/manual/explore-matches" %}}.

---

## Verify in the Data Wrangler 📊

When you click a heatmap node:

- The lower **DATA WRANGLER** view focuses on the selected source attribute (highlighted with a blue background).
- The matched target attribute appears appended to the right of the source attribute.
- If a value mapping is provided in your ground truth, the target column shows the mapped target values applied to each source value.
- If no value mapping is provided for a source value, the corresponding cell in the target column will be empty.

Use this view to scan for mismatches, missing mappings, or unexpected blanks. Adjust your ground truth and rerun if needed.

![data-wrangler](images/data-wrangler.gif)

---

## Edit and Correct Mapped Values ✏️

If a mapped value looks incorrect:

- **Hover the cell** in the mapped target column within the **DATA WRANGLER** table.
- Choose one of the following:
  - **Inline edit**: Click the current mapped value to edit directly, then press Enter to apply.  
  ![inline-edit](images/data-wrangler-inline-edit.png)  
  - **Edit via popover**: Click the edit icon on the right side of the cell to open a popover listing all available target schema values as selectable chips. Click a chip to apply it.
  ![inline-edit](images/data-wrangler-popover-edit.png)

**Note:** When you change the mapped value for a specific `source_value`, the update is applied to all rows in this source attribute that share the same `source_value`.

---

## Export Mapping Results 📤

After applying all changes, export your finalized value mappings:

- Open the **Shortcut Panel** (top-left).
- Click **Export Matching Results**.
- In the format options, select **CSV 4-column** to generate a ground truth-like file.

The exported CSV contains four columns:

- `source_attribute`
- `target_attribute`
- `source_value`
- `target_value`

![export-matches](images/export-matches.gif)

