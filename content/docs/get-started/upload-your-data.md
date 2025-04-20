---
weight: 100
title: "Upload Your Data"
description: "Start a new schema matching task by upload your data files."
icon: "upload"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-19T13:38:17-04:00"
draft: false
toc: true
---

## Start a New Matching Task

Click the rightmost button labeled "New Matching Task" to begin. This will open the file upload interface (see screenshot below).

![new-matching-task-gif](images/new-matching-task.gif)

You will see three drop boxes stacked from top to bottom:

- **Source CSV File** – for your raw dataset

- **Target CSV File** – for the reference standard dataset

- **Target Schema JSON File** – for metadata and attribute definitions

To begin exploring schema matches, you’ll first need to upload these three types of files. These provide the information needed to visualize and compare your source dataset with a standardized target schema.

## Upload Source CSV File

Select a local .csv file that contains your raw or unaligned biomedical dataset.

Example:

| Case_ID | Gender  | Ethnicity_Self_Identify | Path_Stage_Reg_Lymph_Nodes_pN |
|---------|---------|-------------------------|-------------------------------|
| C1234   | Male    | Asian                   | pN1                           |
| C5678   | Female  | White                   | pN2                           |
| C1111   | Unknown | Unknown                 | pNX                           |


