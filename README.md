# Character Creator Workflow Documentation

This repository contains the documentation and resources for the Character Creator Workflow.

## Workflow Diagram

The workflow diagram is created using Mermaid. You can view it in several ways:

1. **GitHub Preview**: GitHub automatically renders Mermaid diagrams in markdown files. You can see it below:

```mermaid
flowchart TD
    %% Documents using speech bubble style nodes
    A[Character Description Input]:::humanInLoop ---> B
    B>"Character Description"]:::document ---> C
    C[Character Attribute Extraction]:::aiAgent ---> D
    D>"Character Attributes"]:::document ---> E
    E[Character Profile Enhancement]:::aiAgent ---> F
    F>"Enhanced Character Profile"]:::document ---> G
    F -.-> N
    G[Consistency Seed Generation]:::integration ---> H
    H>"Character Profile with Consistency Seed"]:::document ---> I1
    H ---> I2
    H ---> I3
    
    subgraph "Facial Expression Generation"
    I1[Expression Prompt Engineering]:::aiAgent ---> J1
    J1>"Expression Prompts"]:::document ---> K1
    K1[Expression Image Generation]:::integration ---> L1
    L1>"Expression Images"]:::document ---> M
    end
    
    subgraph "Facial Perspective Generation"
    I2[Perspective Prompt Engineering]:::aiAgent ---> J2
    J2>"Perspective Prompts"]:::document ---> K2
    K2[Perspective Image Generation]:::integration ---> L2
    L2>"Perspective Images"]:::document ---> M
    end
    
    subgraph "Full Body Generation"
    I3[Full Body Prompt Engineering]:::aiAgent ---> J3
    J3>"Full Body Prompts"]:::document ---> K3
    K3[Full Body Image Generation]:::integration ---> L3
    L3>"Full Body Images"]:::document ---> M
    end
    
    subgraph "Clothing Style Generation"
    I4[Clothing Style Prompt Engineering]:::aiAgent ---> J4
    J4>"Clothing Style Prompts"]:::document ---> K4
    K4[Clothing Style Image Generation]:::integration ---> L4
    L4>"Clothing Style Images"]:::document ---> M
    end
    
    H ---> I4
    
    M[Image Review]:::humanInLoop ---> O
    O>"Reviewed Images"]:::document ---> N
    
    %% Feedback loop from Image Review to Prompt Refinement
    M -- "Rejected with Feedback" --> P
    P[Prompt Refinement]:::aiAgent ---> Q
    Q>"Refined Prompts"]:::document ---> R
    R[Image Regeneration]:::integration ---> M
    
    N[Metadata Structuring]:::aiAgent ---> S
    S>"Structured Metadata"]:::document ---> T
    O ---> T
    T[Airtable Storage]:::integration ---> U
    U>"Stored Character Library"]:::document ---> V
    V[Character Library Presentation]:::integration ---> W
    W>"Character Visual Library (UI)"]:::document
    
    classDef aiAgent fill:#c9e4de,stroke:#000,stroke-width:1px
    classDef integration fill:#bde0fe,stroke:#000,stroke-width:1px
    classDef humanInLoop fill:#ffcfd2,stroke:#000,stroke-width:1px
    classDef document fill:#f1f1f1,stroke:#000,stroke-width:1px
```

2. **Mermaid Live Editor**: You can also view and edit the diagram using the [Mermaid Live Editor](https://mermaid.live). Just copy the contents of the `workflow-diagram.mmd` file and paste it there.

## Color Code Legend

- 🟦 Blue (#bde0fe): Integration Nodes
- 🟩 Green (#c9e4de): AI Agent Nodes
- 🟥 Red (#ffcfd2): Human in the Loop Nodes
- ⬜ Gray (#f1f1f1): Documents/Data

## Styles

The `styles.css` file contains the styling information for the Google Doc version of this documentation.