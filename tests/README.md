# Skill Tests

This directory describes the testing strategy for skills in this repository. Executable tests and automated validation are not implemented yet.

## Test layers

### 1. Structural checks

Check that:
- Each skill directory contains a root-level `SKILL.md`.
- Frontmatter can be parsed.
- Required metadata fields are present and non-empty.
- The metadata name matches the directory name and naming rules.
- Local files referenced by a skill exist.

### 2. Content review

Review whether:
- The skill's purpose and activation context are clear.
- Instructions are actionable and internally consistent.
- Inputs, outputs, limitations, and failure cases are covered where relevant.
- Safety and data-handling expectations are appropriate.
- Supporting resources are necessary and correctly referenced.

### 3. Behavioral evaluation

Run the skill in its intended agent environment with representative tasks. Include:
- A normal task the skill is designed to handle.
- A task outside its intended scope.
- An ambiguous or incomplete input.
- A relevant edge case or unsafe request.

Define expected outcomes before running tests. Record the environment and observed results. Do not infer behavioral success from valid metadata alone.

## Suggested test case record

For each case, record:
- **Case ID**
- **Skill and version/commit**
- **Input or scenario**
- **Expected behavior**
- **Observed behavior**
- **Pass/fail**
- **Notes and follow-up**

## Current status

At this stage, this file is documentation only. The next implementation step is to add a small validator for skill directories and frontmatter, then add fixtures for valid and invalid metadata. Behavioral tests can follow once the target agent runtime is selected.
