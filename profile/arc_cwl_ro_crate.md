# ISA RO-Crate Profile

* Version: 0.1
* Permalink: 
* Authors
  *  - https://orcid.org/

## Overview

```mermaid
flowchart TD

```

## Requirements

| Property | Required | Expected Type | Description |
|----------|----------|---------------|-------------|
| | | | |

## Example ro-crate-metadata.json

### Workflow

```json
{ "@context": "https://w3id.org/ro/crate/1.1/context",
  "@graph": [
    {
      "@type": "CreativeWork",
      "@id": "ro-crate-metadata.json",
      "conformsTo": { "@id": "https://w3id.org/ro/crate/1.1" },
      "about": { "@id": "./" }
    },
    {
      "@id": "./workflows",
      "@type": "Dataset",
      "hasPart": [
        { "@id": "workflows/workflow.cwl" }
      ]
    },
    {
      "@id": "workflows/workflow.cwl",
      "@type": [ "File", "SoftwareSourceCode", "ComputationalWorkflow" ],
      "conformsTo": { "@id": "https://bioschemas.org/profiles/ComputationalWorkflow/0.5-DRAFT-2020_07_21/" },
      "name": "Column Addition",
      "programmingLanguage": [
        { "@id": "#FSharp" },
        { "@id": "https://w3id.org/workflowhub/workflow-ro-crate#cwl" }
      ],
      "creator": { "@id": "#timo" },
      "dateCreated": "2024-02-05",
      "input": [
        { "@id": "#1" },
        { "@id": "#2" }
      ],
      "output": [
        { "@id": "#3" }
      ]
      "about": [
        # TODO add some example metadata
        # Lab process
      ]
    },
    {
      "@id": "#1",
      "@type": "FormalParameter",
      "conformsTo": { "@id": "https://bioschemas.org/profiles/FormalParameter/0.1-DRAFT-2020_07_21/" },
      "name": "intensity_table",
      "valueRequired": true,
      "additionalType": { "@id": "http://edamontology.org/data_2976" },
      "format": { "@id": "http://edamontology.org/format_3752" }
    },
    {
      "@id": "#2",
      "@type": "FormalParameter",
      "conformsTo": { "@id": "https://bioschemas.org/profiles/FormalParameter/0.1-DRAFT-2020_07_21/" },
      "name": "file_name"
    },
    {
      "@id": "#3",
      "@type": "FormalParameter",
      "conformsTo": { "@id": "https://bioschemas.org/profiles/FormalParameter/0.1-DRAFT-2020_07_21/" },
      "name": "summed_intensities",
      "additionalType": { "@id": "http://edamontology.org/data_2976" },
      "encodingFormat": { "@id": "http://edamontology.org/format_3475" }
    },
    {
      "@id": "https://w3id.org/workflowhub/workflow-ro-crate#cwl",
      "@type": "computerlanguage",
      "name": "common workflow language",
      "alternatename": "cwl",
      "identifier": {
        "@id": "https://w3id.org/cwl/v1.2/"
      },
      "url": {
        "@id": "https://www.commonwl.org/"
      }
    },
    {
      "@id": "#FSharp",
      "@type": "ProgrammingLanguage",
      "name": "F Sharp",
      "alternateName": "F#",
      "url": "https://dotnet.microsoft.com/en-us/languages/fsharp",
      "version": "6.0"
    },
    {
      "@id": "#timo",
      "@type": "Person",
      "name": "Timo Mühlhaus"
    },
    {
      "@id": "http://edamontology.org/format_3752",
      "@type": "Thing",
      "name": "Comma-separated values"
    },
    {
      "@id": "http://edamontology.org/format_3475",
      "@type": "Thing",
      "name": "Tab-separated values"
    }
}
```

### Workflow Invocation

```json
{ "@context": [
    "https://w3id.org/ro/terms/workflow-run/context"
  ],
  "@graph": [
    {
        "@id": "#wfrun-1",
        "@type": "CreateAction",
        "name": "CWL workflow run 1",
        "endTime": "",
        "instrument": {"@id": "workflows/workflow.cwl"},
        "subjectOf": {"@id": ""},
        "object": [
            {"@id": "#1"},
            {"@id": "#2"}
        ],
        "result": [
            {"@id": "#3"}
        ]
    },
    {
        "@id": "#1",
        "@type": "Raw Data File",
        "description": "Number columns in csv format",
        "encodingFormat": "text/plain",
        "name": "intensity_table",
        "exampleOfWork": {"@id": "#1"}
    },
    {
        "@id": "##2",
        "@type": "Text",
        "exampleOfWork": {"@id": "#2"},
        "name": "file_name",
        "value": "result.csv"
    },
    {
        "@id": "#3",
        "@type": "Data",
        "name": "summed_intensities",
        "description": "Summed intensity columns",
        "encodingFormat": "text/plain",
        "exampleOfWork": {"@id": "#3"}
    },
    {
        "@id": "cwltool",
        "@type": "CreativeWork",
        "encodingFormat": "text/html",
        "datePublished": "",
        "name": "Workflow Execution Example Workflow"
    }
]
}
```