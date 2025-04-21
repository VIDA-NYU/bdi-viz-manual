---
weight: 300
title: "Perform User Operations"
description: "Interactively evaluate and manage each schema match candidate."
icon: "edit"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-21T11:00:00-04:00"
draft: false
toc: true
---

## Overview

BDIViz provides a streamlined interface for managing match candidates directly within the heatmap view. The **Shortcut Panel**, located at the top-left of the screen, offers essential interactive tools for evaluating and adjusting alignment results.

![shortcut-panel-gif](./images/shortcut-panel.gif)

These operations allow users to mark candidates as accepted, rejected, or discarded, while also providing undo/redo functionality for iterative refinement.

---

## Available Actions

The table below summarizes the core user operations available via the Shortcut Panel:

| Action      | Icon  | Description                                                                 | Visual Indicator       |
|-------------|-------|-----------------------------------------------------------------------------|-------------------------|
| **Accept**  | ✓     | Confirms a source-to-target column pair as a valid schema match             | Cell turns **green**    |
| **Reject**  | ✕     | Flags the candidate as an invalid or incorrect match                        | Cell turns **red**      |
| **Discard** | 🗑️     | Removes the source attribute from matching consideration                    | Attribute grays out     |
| **Undo**    | ⟲     | Reverts the most recent operation                                            | Previous state restored |
| **Redo**    | ⟳     | Reapplies the most recently undone operation                                 | Last change re-applied  |

> All user operations are recorded in the **Timeline Panel** (located on the right), enabling traceability and decision auditing.

---

## Best Practices

- **Leverage Keyboard Shortcuts**: Speed up match decisions using shortcut buttons or hotkeys (where supported).
- **Work Iteratively**: Use **Undo** and **Redo** freely to experiment and refine decisions without permanent impact.
- **Stay Organized**: The **Timeline Panel** logs every action in sequence, helping you track progress or revisit past decisions.
- **Interpret Colors Quickly**:
  - ✅ **Green**: Accepted match
  - ❌ **Red**: Rejected match
  - 🚫 **Gray**: Discarded source attribute

---

## Next Steps

After reviewing and operating on match candidates:

- Review the Timeline Panel to validate key decisions.
- Use filters and the heatmap overview to identify remaining unmatched attributes.
- Proceed to export your confirmed mappings or refine further with the help of the LLM Agent Panel.

For more advanced functionality or customization, refer to the [Usage Guide](/docs/usage) or contact the support team via [Support](/support).
