# Skills

A collection of AI agent skill definitions for software engineering and tutoring workflows.

## Skills

| Skill | Description |
|---|---|
| [42 C Tutor](skills/42-c-tutor/SKILL.md) | Tutors 42 Common Core students on C programming through guided questioning, code review, and Norm checking. |

## Usage

Each skill is self-contained in a subdirectory under `skills/`. Load a skill's `SKILL.md` into an AI agent to constrain its behaviour for the given task. Reference documents (e.g. the 42 Norm) are included alongside each skill definition.

### Install skills from this repo

```sh
npx skills add https://github.com/simonlau/skills
```

The first command installs all skills in the repo. The second installs a specific skill by name.

## Adding a new skill

```
skills/<skill-name>/
├── SKILL.md    # Skill definition (required)
└── ...         # Supporting reference files
```

## License

MIT
