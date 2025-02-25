This document explains how to update the JSON data file used by [Paymentology Technology Radar](https://radar.thoughtworks.com/?documentId=https%3A%2F%2Fraw.githubusercontent.com%2FPaymentology%2Ftech-radar%2Frefs%2Fheads%2Fmain%2Fdata.json). By following these instructions, you can add new “blips,” update existing ones, and ensure your changes display correctly on the radar visualization.

# 1. Overview

The Technology Radar is powered by radar.thoughtworks.com and generated from a JSON file that contains an array of blip objects. Each blip represents a technology, tool, technique, or practice and includes details such as its name, the radar ring it belongs to, the quadrant (category), a description, and optionally, movement status information.

Key Points:
- File Location: The file is typically named data.json and is referenced by the radar visualization application.
- Source of Truth: This file is the single source of content for the radar. Ensure any changes are validated before deployment.

# 2. JSON File Structure

The file should contain a JSON array where each element (object) represents one blip. Below is an example template:

```
[
  {
    "name": "Example Technology",
    "ring": "Adopt",
    "quadrant": "Tools",
    "isNew": "TRUE",
    "description": "A brief description of the technology.",
    "status": "New"  // Optional: Acceptable values are "New", "Moved In", "Moved Out", or "No Change"
  },
  {
    "name": "Another Tool",
    "ring": "Trial",
    "quadrant": "Platforms",
    "isNew": "FALSE",
    "description": "This tool is under evaluation.",
    "status": "No Change"
  }
]
```

**Field Details**
- name (string): The display name of the technology.
- ring (string): Must be one of the predefined values:
  - Adopt
  - Trial
  - Assess
  - Hold
Note: The value is case sensitive.
 - quadrant (string): Must be one of the following categories:
  - Techniques
  - Platforms
  - Tools
  - Languages & Frameworks
Note: Spelling and case are important.
- isNew (string): Indicates whether this is a new blip on the radar. Use "TRUE" or "FALSE".
- description (string): A brief explanation or rationale behind the blip.
- status (string, optional): Indicates movement of the blip. Allowed values (case insensitive):
  - New
  - Moved In
  - Moved Out
  - No Change

# 3. Guidelines for Editing

## Adding a New Blip
- Copy a Template Object: Start with an object similar to the example provided above.
- Fill in All Required Fields:
  - Ensure that ring and quadrant exactly match the allowed values.
  - Use "TRUE" for isNew if the technology is appearing for the first time.
  - Provide a concise yet informative description.
- Optional Movement Information: If you have data on whether the blip has moved since the previous radar edition, add the status field. This helps indicate trends such as “Moved In” (improving) or “Moved Out” (declining).

## Updating an Existing Blip
- Modify Values: Change any field as necessary (e.g., update the description or change the ring if the technology’s maturity has evolved).
- Preserve Consistency: Double-check that any modifications adhere to the allowed values and formatting guidelines.

## Removing a Blip
- Simply delete the corresponding JSON object from the array.
- Ensure the final JSON remains valid (i.e., proper comma placement between objects).

# 4. Validation and Testing

Before deploying your changes, follow these steps:
- Validate JSON Syntax: Use a JSON validator (e.g., JSONLint) to ensure your file is well-formed.
- Check Field Values: Verify that each blip’s ring and quadrant fields match the allowed values exactly.
- Preview Your Changes: If possible, load your updated JSON into a local instance of the radar visualization (using ThoughtWorks’ build-your-own-radar tool or your internal deployment) to confirm that the blips display as expected.
- Version Control: Commit your changes to your version control system. This allows you to track modifications and revert if needed.

# 5. Common Pitfalls
- Case Sensitivity:
Incorrect capitalization in ring or quadrant will cause the radar to misinterpret the data.
- Extra Whitespace:
Remove leading or trailing spaces in field values.
- Invalid JSON:
Ensure that each object is properly separated by commas and the overall array is correctly formatted.
- Omitting Required Fields:
Every blip must have at least the name, ring, quadrant, isNew, and description fields.

# 6. Additional Resources
- ThoughtWorks Build-Your-Own-Radar GitHub Repository – for source code and additional documentation.
- Radar Visualization FAQ – for troubleshooting common issues.
- JSON Schema Basics – to learn more about defining and validating JSON data.

By following this guide, you should be able to safely and effectively edit the data.json file and submit a PR with your proposed changes. Then contact your Engineering Manager to attend the next available AWG meeting to present the changes. If approved following AWG discussion, the PR will be merged and the changes reflected on the Paymentology Technology Radar, ensuring that the Technology Radar remains accurate and up-to-date.

If you have any questions or run into issues, please contact the TAG team.

Happy editing!
