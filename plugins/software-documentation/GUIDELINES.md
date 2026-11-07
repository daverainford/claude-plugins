# Guidelines

## Dependencies
- Claude Code plugin: `github@claude-plugins-official`

## Plugin structure
```yaml
GUIDELINES.md: null
README.md: null
.claude-plugin:
  - plugin.json
agents:
  - doc-planner.md
  - doc-writer.md
  - doc-reviewer.md
skills:
  bootstrap-documents:
    - SKILL.md
    - templates:
        - DDS.md
        - SRS.md
        - SVV.md
        - TM.md
```

## Git Guidelines
- Use the `github@claude-plugins-official` plugin for any communication to and from GitHub.
- Create `feature/software_documentation` if it does not exist. All work is done on this feature branch.
- Prefix all commits with one of the following: `feat:`, `fix:`, `refactor:`, `chore:`, `docs:`.
- Write short commit messages in simple, straightforward, easy to understand language. Only add a commit message body if it is needed to describe the changes.
- The PR description is a handful of sentences in paragraph form describing the document changes. Use simple, easy to understand language that is succinct and clear.
- Set PRs to squash commits and delete source branch by default.
- Gate the PRs by my approval.

## Document Writing Guidelines
- Use simple, easy to understand language that is succinct and clear. Add technical terms and jargon only when absolutely necessary.
- No `TBD` or placeholders. Documents shall be complete. The only exception: in `TM.md`, the Implementation and Test Implementation columns read `Not implemented` until the code exists.
- Never assume. If you are unsure of something, ask the user any open questions with AskUserQuestion.
- Requirements shall cover only critical behavior of the software.
- Requirements shall use formal language.
- All functional requirements shall have one or more test cases covering them.
- All requirements and test cases shall have IDs with the following structure: `<REQ/TC>-<Software component>-<Software module>-<Auto increment 001, 002, etc.>`
- Test cases shall cover four levels of testing: unit, integration, system, and end to end.
- Test cases shall be simply written and describe: the requirement they are linked to, input, procedure, and expected behavior.
- Write requirements and test cases in simple language that is clear, succinct, and testable.
- Every requirement, design element, and test case shall trace directly to a requirement. Template boilerplate is exempt.
- If a simpler design meets the requirements, always default to that.
- Use simple, straightforward, and basic design. Only introduce complexity when absolutely necessary.
- Software decomposition goes: System -> Component -> Module.
- Software components and modules shall be loosely coupled when practical.
- Follow the software document templates exactly.
