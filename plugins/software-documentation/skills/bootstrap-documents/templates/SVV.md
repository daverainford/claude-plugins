# Software Verification and Validation Plan: {{SOFTWARE_NAME}}
Generated: {{DATE}}

## 1. Introduction

{{What this document is and who uses it: the baseline and framework for testing, verifying, and validating the software.}}

## 2. Testing levels

| Level | What it covers | How | Where it runs | Data |
| --- | --- | --- | --- | --- |
| Unit | Each module's functions and classes: logic, boundary values, fault handling | {{tools}} | {{CI / local}} | Synthetic |
| Integration | Modules and components working together and with external software and systems: data flow, interfacing, inputs, outputs | {{tools}} | {{CI / local}} | Synthetic |
| System | The complete software against the SRS functional requirements | {{tools}} | {{CI / local}} | Synthetic |
| End to end | Manual verification of the functional requirements via pre-built scenarios | Manual | Local | Real-world data and execution |

## 3. Test records

Records from unit, integration, and system tests run in the CI pipeline are kept as GitHub Actions artifacts. End-to-end test records are kept as Markdown files in the repository, with the test results.

## 4. Test cases

| Requirement | Test | Level | Input and procedure | Expected |
| --- | --- | --- | --- | --- |
| REQ-{{COMPONENT}}-{{MODULE}}-001 | TC-{{COMPONENT}}-{{MODULE}}-001 | {{level}} | {{what is done}} | {{expected outcome}} |
