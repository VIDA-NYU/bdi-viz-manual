---
weight: 200
title: "Dataset to GDC Schema Alignment"
description: "Comprehensive guide for mapping biomedical datasets to the GDC schema standard"
icon: "prescriptions"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-19T13:38:17-04:00"
draft: false
toc: true
---

## Installation 🛠️

For system-specific installation instructions:
- AMD64 architecture: Follow the [Linux/Unix installation guide]({{% relref "/docs/installation/install-on-linux" %}})
- ARM64 architecture (Apple Silicon): Follow the [MacOS installation guide]({{% relref "/docs/installation/install-on-macos" %}})

## Introduction 📚

This guide demonstrates the process of aligning a biomedical dataset with the Genomic Data Commons (GDC) schema using BDIViz. The GDC maintains standardized data repositories that require specific formatting and schema compliance for successful data submission and integration.

## Step 1: Dataset Preparation and Task Initialization 🚀

1. Download the [Clark et al. sample dataset](https://drive.google.com/file/d/1N3rbTHtnVDe19kMNei0opy_g-8Hr_Hl5/view?usp=drive_link)
2. Navigate to `http://localhost:3000` in your web browser
3. Select **"New Matching Task"** from the navigation bar
4. Upload the Clark dataset CSV file to the **Source CSV File** drop zone
5. Leave the **Target CSV File** and **Target Schema JSON File** fields empty to utilize the default GDC v3.3.0 schema
6. Click **"Import CSV"** to initiate the matching process

![new-matching-task-gif](images/new-matching-task.gif)

## Step 2: Validating High-Confidence Matches ✅

The system automatically identifies and suggests high-confidence matches, indicated by darker cells in the heatmap. Review these initial suggestions:

1. **Direct Attribute Matches**:
   - Locate the matching candidate **Gender** (source) -> **gender** (GDC) in the heatmap cell
   - Click the heatmap cell to expand the embedded node
   - The embedded node contains unique value distributions for both attributes
   - Verify that both attribute names and values align (Male → Male, Female → Female)
   - **Note that high-confidence matches are pre-accepted (indicated by green cells with checkmarks)**

   ![clark-gender-gif](images/clark-gender.gif)

2. **Numerical Attribute Alignment**:
   - Examine the matching candidate **BMI** (source) -> **bmi** (GDC) in the heatmap cell
   - Click the heatmap cell to expand the embedded node
   - The embedded node shows value bin distributions for numerical data
   - Observe that both attribute names and numerical distributions correspond appropriately
   - **This match should also be pre-accepted (green cell with checkmark)**

   ![clark-bmi-gif](images/clark-bmi.gif)

## Step 3: Explore Complex Attribute Matches 🧩

Address more nuanced matching scenarios that require human judgment:

1. **Evaluating Semantic Differences**:
   - Locate the matching candidate **Ethnicity_Self_Identify** (source) -> **ethnicity** (GDC) in the heatmap cell
   - Click the heatmap cell to expand the embedded node
   - Scroll down to check the value comparisons table in the embedded node
   - Note the significant value discrepancies:
     - Source values include "Asian", "White", etc.
     - GDC ethnicity values include "hispanic or latino", "not hispanic or latino", etc.
   - Click the **Reject** (✕) button on the top left Shortcut Panel to invalidate this incorrect match

2. **Identifying Cross-Category Matches**:
   - Examine the matching candidate **Ethnicity_Self_Identify** (source) -> **race** (GDC) in the heatmap cell
   - Click the heatmap cell to expand the embedded node
   - Scroll down to check the value comparisons table in the embedded node
   - Confirm that the values correspond appropriately:
     - "Asian" in source aligns with "asian" in GDC
     - "White" in source aligns with "white" in GDC
   - Click the **Accept** (✓) button on the top left Shortcut Panel to confirm this cross-category match

   ![clark-ethnicity-gif](images/clark-ethnicity.gif)

## Step 4: Leverage the LLM Agent for Complex Matching Decisions 🤖

The integrated LLM Agent provides valuable insights for challenging attribute matches:

1. **Evaluating Pathological Staging to Lymph Node Count**:
   - Examine the potential match **Path_Stage_Reg_Lymph_Nodes_pN** (source) -> **lymph_nodes_positive** (GDC)
   - Consult the Agent Panel on the left side of the interface
   - Review the "Semantic No Match" card which indicates:
     - Source attribute represents a classification system (pN0, pN1, etc.)
     - Target attribute represents a numerical count of positive lymph nodes
   - Based on this analysis, reject this match using the Shortcut Panel

2. **Distinguishing Staging from Testing Metrics**:
   - Evaluate the potential match **Path_Stage_Reg_Lymph_Nodes_pN** (source) -> **lymph_nodes_tested** (GDC)
   - Expand the "Pattern No Match" card in the Agent Panel
   - Note the critical insight that source values (pN0, pN1, pNX) represent staging categories
   - Confirm these do not align with the expected numeric values for lymph nodes tested
   - Reject this match using the Shortcut Panel

3. **Identifying Non-Obvious Semantic Equivalence**:
   - Assess the potential match **Path_Stage_Reg_Lymph_Nodes_pN** (source) -> **ajcc_pathologic_n** (GDC)
   - Despite different naming conventions, examine the value distributions
   - Consult the "Semantic Match" card in the Agent Panel
   - Verify that both attributes represent pathological lymph node staging in cancer systems
   - Accept this match using the Shortcut Panel

![clark-pn-gif](./images/clark-pn.gif)

## Step 5: Systematic Review of All Source Attributes 🔍

Methodically evaluate each remaining source attribute:

1. Prioritize heatmap cells with darker shading (indicating stronger match candidates)
2. Click each heatmap cell to expand the embedded node and evaluate both attribute names and value distributions
3. Utilize the top left Shortcut Panel to:
   - **Accept** (✓) valid and appropriate matches
   - **Reject** (✕) invalid or misaligned matches
   - **Discard** (🗑️) attributes that should be excluded from the mapping process


## Step 6: Exporting the GDC-Compliant Dataset 📤

After completing the evaluation process:

1. Select the **Export** button from the top left Shortcut Panel
2. Choose CSV format to generate a dataset with GDC-compliant column names
3. Save the transformed file to your local system

![export-matches-gif](./images/export-matches.gif)

## Further Resources 📖

For advanced functionality and detailed operational guidance, please refer to the comprehensive [User Manual]({{% relref "/docs/manual/_index" %}}).
