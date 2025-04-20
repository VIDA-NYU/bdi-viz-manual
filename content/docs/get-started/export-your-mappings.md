---
weight: 400
title: "Export Your Mappings"
description: "Export your matching result."
icon: "export"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-19T13:38:17-04:00"
draft: false
toc: true
---

![export-matches-gif](./images/export-matches.gif)

## Exporting Your Results

After completing your schema matching process, you can export your validated mappings for downstream use.

### Export Process

1. Locate the **Export** button in the Shortcut Panel at the top-left corner of the interface
2. Click the button to initiate the export process
3. A dialog will appear with format options

### Available Export Formats

{{< tabs tabTotal="2">}}
{{% tab tabName="CSV Format" %}}

The CSV export provides a transformed dataset with your source data mapped to the target schema.

**Features:**
- Source columns are renamed to their matched target attributes
- Only accepted matches are included
- Ready for immediate use in analytics or data submission

**Example CSV Output:**
| submitter_id | gender | race  | ajcc_pathologic_n |
|--------------|--------|-------|-------------------|
| C1234   | Male    | Asian                   | pN1                           |
| C5678   | Female  | White                   | pN2                           |
| C1111   | Unknown | Unknown                 | pNX                           |


This format is ideal for:
- Data integration workflows
- Direct uploads to target systems
- Documentation of transformations
{{% /tab %}}
{{% tab tabName="JSON Format" %}}

The JSON export provides a structured representation of your mapping decisions with additional metadata.

**Features:**
- Complete mapping information including scores and timestamps
- Includes metadata about the matching process
- Suitable for programmatic processing

**Example JSON Output:**
```json
[
  {
    "sourceColumn": "Tumor_Focality",
    "targetColumn": "tumor_focality",
    "valueMatches": [
      {
        "from": "Multifocal",
        "to": "Multifocal"
      },
      {
        "from": "Unifocal",
        "to": "Unifocal"
      }
    ]
  },
  {
    "sourceColumn": "Ethnicity",
    "targetColumn": "ethnicity",
    "valueMatches": [
      {
        "from": "Hispanic or Latino",
        "to": "hispanic or latino"
      },
      {
        "from": "Not reported",
        "to": "not reported"
      },
      {
        "from": "Not-Hispanic or Latino",
        "to": "not hispanic or latino"
      }
    ]
  },
]
```

{{% /tab %}}
{{< /tabs >}}