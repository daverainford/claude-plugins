---
name: bootstrap-documents
description: Generate software documentation when none exists for the software
disable-model-invocation: true
---

## Rules

- Planner, writers and reviewer strictly follow the document writing and Git guidelines in `${CLAUDE_PLUGIN_ROOT}/GUIDELINES.md`.

## Prerequisites

If this is not met, it is a hard stop and the user must fix it before continuing:
- Authentication to GitHub and the repo using `github@claude-plugins-official`.

## Steps

### 1. Repo

If the working directory is not a git repo:
1. Ask the user for the GitHub repo URL. If there is no repo, ask the user to create it first. Wait for confirmation.
2. After confirmation, clone the repo with SSH into the working directory. If the working directory is not empty, ask the user where to clone it and work there. If the clone fails, stop and ask the user to fix it.
3. After the clone is successful, continue to step 2.

If the working directory is a git repo:
1. Continue to step 2.

### 2. Branch

If the repo is completely empty:
1. Create a `main` branch with a README.md and push it to the remote.
2. Create `feature/software_documentation` from `main` and check it out.
3. Continue to step 3.

If `feature/software_documentation` exists:
1. Check it out.
2. Continue to step 3.

If `feature/software_documentation` does not exist:
1. Create it from `main` and check it out.
2. Continue to step 3.

### 3. Existing documentation

If `docs/` contains any documents, stop. This skill only creates new documentation. Existing documentation is edited with the `edit-documents` skill.

Otherwise, continue to step 4.

### 4. Requirements and design questions

Ask the user these questions in a single message and wait for the answers:

1. **Software overview:** Describe the software, its purpose, and its users in detail. This will be used to write requirements, so the more detail the better.
2. **Language(s):** What language or languages is this software written in?
3. **Packaging, deployment, and environment:** How is this software packaged and deployed? Where does it run? How is its environment managed?
4. **Config and secrets:** Where does the software store and fetch its configuration and secrets?
5. **General:** Is there anything else about the software that is important to know for writing requirements, design, and test cases?

Hold the answers as **software overview** and pass them to the planner and writers.

### 5. Plan (Opus)

Run the `doc-planner` agent (Opus) with **software overview** and `${CLAUDE_PLUGIN_ROOT}/GUIDELINES.md` as input. It reads the inputs, plans the requirements, decomposes the software into components and modules, plans the test cases, and returns a structured plan held in **document plan**. If the planner returns open questions, ask the user and return the responses to the planner.

### 6. Write (Sonnet)

Run four `doc-writer` agents (Sonnet) in parallel, one each for `SRS`, `DDS`, `SVV`, and `TM`, with **document plan**, **software overview**, the matching template from `${CLAUDE_PLUGIN_ROOT}/skills/bootstrap-documents/templates/`, and `${CLAUDE_PLUGIN_ROOT}/GUIDELINES.md` as input. Each reads the inputs and writes its document in accordance with the **document plan**. If a writer returns open questions, ask the user and return the responses to that writer.

### 7. Check and review (Opus)

Run the `doc-reviewer` agent (Opus) with **document plan**, the four documents written to `docs/` by the writers, and `${CLAUDE_PLUGIN_ROOT}/GUIDELINES.md` as input. It checks accuracy, uniformity, cross-references, template adherence, the rules, simple design, simple language, and clarity and length across all four documents together. If the reviewer returns open questions, ask the user and return the responses to the reviewer.

If the reviewer returns `None`, continue to step 8. If the reviewer returns a findings report, pass each document's findings to a `doc-writer` for that document to apply the fixes exactly as described. After the writers apply the fixes, continue to step 8.

### 8. Create PR

1. Commit the four files: `docs: add software documentation`.
2. Push the `feature/software_documentation` branch.
3. Create a PR targeting the `main` branch with the following format:

   | | |
   | --- | --- |
   | Title | `Feature: Software Documentation` |
   | Description | Follow the `git guidelines` in `${CLAUDE_PLUGIN_ROOT}/GUIDELINES.md` |

### 9. Report

Give a brief summary of the work done and the four documents written. Include a link to the PR and the four documents in `docs/`.
