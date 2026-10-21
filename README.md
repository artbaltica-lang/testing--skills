# Testing Skills

A repository for creating, reviewing, and validating Agent Skills used by AI agents.

## Goals

- Keep skills clear, focused, and maintainable.
- Review skill metadata, instructions, and supporting files.
- Catch structural and safety issues before a skill is used.
- Build repeatable tests for skill quality over time.

## Repository layout

```text
.
├── README.md
├── skills/
│   ├── skill-reviewer/
│   │   └── SKILL.md
│   └── miestu-oras/
│       └── SKILL.md
└── tests/
    └── README.md
```

Each skill lives in its own directory under `skills/` and has a `SKILL.md` file at that directory's root. Optional resources can be added when a skill needs them.

## Current skills

| Skill | Purpose |
|---|---|
| [skill-reviewer](skills/skill-reviewer/SKILL.md) | Reviews Agent Skills for format, clarity, completeness, and safety. |
| [miestu-oras](skills/miestu-oras/SKILL.md) | Returns temperature and weather conditions for five major Lithuanian cities using Meteo.lt. |

## Basic review workflow

1. Read the skill's metadata and instructions.
2. Check that its name, directory, and stated purpose are consistent.
3. Evaluate clarity, scope, workflow, expected output, and edge cases.
4. Check for unsafe or overbroad instructions and unnecessary access.
5. Report findings with evidence, severity, and actionable suggestions.
6. Re-check the revised skill.

A review is an assessment, not proof that the skill will behave correctly in every runtime. Behavioral testing should use representative tasks in the intended agent environment.

## Adding a skill

1. Create a directory under `skills/` using a short, lowercase, hyphen-separated name.
2. Add a `SKILL.md` file with YAML frontmatter containing `name` and `description`.
3. Make the description explain what the skill does and when it should be used.
4. Write concrete, ordered instructions. Include expected output and important limitations.
5. Add references, scripts, or tests only when they materially help the skill.
6. Review the skill with `skill-reviewer` and test it in its target environment.

## Status

This repository is at an initial stage. Automated validation and executable test cases have not yet been added.
