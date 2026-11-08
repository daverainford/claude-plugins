# Software Documentation

## Overview

A Claude Code plugin that starts the spec-driven development workflow. It asks about your software, then writes four documents to `docs/` and opens a pull request:

| File | Document |
| --- | --- |
| `SRS.md` | Software Requirements Specification |
| `DDS.md` | Detailed Design Specification |
| `SVV.md` | Software Verification and Validation Plan |
| `TM.md` | Traceability Matrix |

The documents are AI-written. Review them before approving the pull request.

## Installation

```
/plugin marketplace add daverainford/claude-plugins
/plugin install software-documentation@daverainford-plugins
```

## Usage

In the repo you want to document, run:

```
/software-documentation:bootstrap-documents
```
