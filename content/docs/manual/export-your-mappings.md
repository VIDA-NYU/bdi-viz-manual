---
weight: 500
title: "Export Your Mappings"
description: "Export the results of your schema matching task in multiple formats for downstream integration and analysis."
icon: "ios_share"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-21T11:00:00-04:00"
draft: false
toc: true
---

## Overview 📊

Once your schema matching task is complete, BDIViz enables you to export the validated mappings for use in data integration pipelines, reporting workflows, or system submissions.

![export-matches-gif](./images/export-matches.gif)

---

## How to Export 📤

To begin exporting your results:

1. Navigate to the **Shortcut Panel** (top-left corner of the interface).
2. Click the **Export** button.
3. A dialog will appear prompting you to select your preferred export format (CSV or JSON).

---

## Export Formats 📋

BDIViz supports two export options designed for different use cases:

{{< tabs tabTotal="2">}}

{{% tab tabName="CSV Format" %}}

The CSV export transforms your original dataset using only the accepted column mappings.

### Key Features:
- Source columns are renamed to their matched target attributes
- Only accepted matches are included
- Resulting dataset is ready for immediate analysis or upload

### Example Output:

| submitter_id | gender | race  | ajcc_pathologic_n |
|--------------|--------|-------|-------------------|
| C1234        | Male   | Asian | pN1               |
| C5678        | Female | White | pN2               |
| C1111        | Unknown| Unknown| pNX              |

### Best For:
- Data harmonization pipelines
- Uploads to repositories (e.g., GDC, PDC)
- Sharing aligned datasets with collaborators

{{% /tab %}}

{{% tab tabName="JSON Format" %}}

The JSON export provides a structured record of all mapping operations with detailed metadata.

### Key Features:
- Includes column-level mappings and value-level match pairs
- Records additional metadata like match scores and timestamps
- Machine-readable for downstream processing or reproducibility

### Example Output:

```json
[
  {
    "sourceColumn": "Tumor_Focality",
    "targetColumn": "tumor_focality",
    "valueMatches": [
      { "from": "Multifocal", "to": "Multifocal" },
      { "from": "Unifocal", "to": "Unifocal" }
    ]
  },
  {
    "sourceColumn": "Ethnicity",
    "targetColumn": "ethnicity",
    "valueMatches": [
      { "from": "Hispanic or Latino", "to": "hispanic or latino" },
      { "from": "Not reported", "to": "not reported" },
      { "from": "Not-Hispanic or Latino", "to": "not hispanic or latino" }
    ]
  }
]
```

### Best For:
- Programmatic ingestion and audit trails
- Reuse in automated systems
- Reconstructing or refining schema alignment processes

{{% /tab %}}
{{< /tabs >}}

## Final Notes 📝
- Ensure all intended mappings are **accepted** before exporting; rejected and discarded mappings will not be included.
- Use the **Timeline Panel** to review decisions prior to export.
- Both formats can be downloaded directly to your local machine.
