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

## Upload Source CSV File (Required)

Select a local .csv file that contains your raw or unaligned biomedical dataset.

Example:

| Case_ID | Gender  | Ethnicity_Self_Identify | Path_Stage_Reg_Lymph_Nodes_pN |
|---------|---------|-------------------------|-------------------------------|
| C1234   | Male    | Asian                   | pN1                           |
| C5678   | Female  | White                   | pN2                           |
| C1111   | Unknown | Unknown                 | pNX                           |


## Upload Target CSV File

> If this is empty, we use GDC v3.3.0 by defualt.

Select a .csv file that represents the standardized biomedical data format (e.g., GDC or PDC).

Example:

| submitter_id | gender | race  | ajcc_pathologic_n |
|--------------|--------|-------|-------------------|
| T001         | Male   | Asian | N1                |
| T002         | Female | White | N2                |

## Upload Target Schema JSON File
> If this is empty, we use GDC v3.3.0 by defualt.

Choose the corresponding .json file that describes the structure and metadata of the target schema.

Example:
```json
{
    "age_at_index": {
        "column_name": "age_at_index",
        "category": "clinical",
        "node": "demographic",
        "type": "integer",
        "description": "The patient's age (in years) on the reference or anchor date used during date obfuscation.",
        "minimum": 0
    },
    "education_level": {
        "column_name": "education_level",
        "category": "clinical",
        "node": "demographic",
        "type": "enum",
        "description": "The years of schooling completed in graded public, private, or parochial schools, and in colleges, universities, or professional schools.",
        "enum": [
            "College Degree",
            "High School Graduate or GED",
            "Professional or Graduate Degree",
            "Some High School or Less",
            "Vocational College or Some College",
            "Unknown",
            "Not Reported"
        ]
    },
}
```

## Launch Matching Task

After uploading your files, click the **"Import CSV"** button to initiate the matching process. The system will begin processing your data, which may take a few minutes to complete. 

During this time, our matching algorithm analyzes your input files and generates recommendations for schema alignment. A loading indicator will display the progress as the system works to identify potential matches between your source data and the target schema.
