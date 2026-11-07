# Software Requirements Specification: {{SOFTWARE_NAME}}
Generated: {{DATE}}

## 1. Introduction

{{What this document is and who uses it: the baseline for design, implementation and testing.}}

## 2. Software decomposition

| Component | Module | Responsibility |
| --- | --- | --- |
| {{name}} | {{name}} | {{what it is responsible for}} |

## 3. System overview

{{How the software's components interact within the system and how the modules interact within the component. External systems that the software integrates or communicates with.}}

*Diagram: system context.*

```mermaid
%%{init: {"flowchart": {"curve": "step", "nodeSpacing": 60, "rankSpacing": 70}}}%%
flowchart LR
  ES[{{External System}}] --> S[{{System}}] --> C[{{Component}}] --> M[{{Module}}]
```

## 4. Requirements

| ID | Type | Requirement |
| --- | --- | --- |
| REQ-{{COMPONENT}}-{{MODULE}}-001 | Functional | {{requirement statement}} |
| REQ-{{COMPONENT}}-{{MODULE}}-002 | Non-functional | {{requirement statement}} |
