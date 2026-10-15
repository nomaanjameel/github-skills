# GitHub Skills

A collection of reusable [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli) agent skills to streamline and improve development workflows.

## What are skills?

Skills are folders of instructions, scripts, and resources that Copilot CLI loads when relevant to improve its performance in specialized tasks. Each skill lives in its own directory containing a `SKILL.md` file.

## Available skills

| Skill | Description |
|-------|-------------|
| [testing](./testing/) | Review and generate code coverage reports, and write unit tests |

## Installation

### Install a single skill into a project

Copy the skill directory into your repository's `.github/skills/` folder:

```bash
cp -r testing /your-repo/.github/skills/testing
```

### Install a single skill for personal use (all projects)

Copy the skill directory to your home skills folder:

```bash
cp -r testing ~/.copilot/skills/testing
```

### Install via GitHub CLI (recommended)

```bash
gh skill install NomaanJameelSword/github-skills/testing
```

## Usage

Once installed, ask Copilot to use a skill by name:

```
use my testing skill to review code coverage
```

Or invoke it explicitly with a `/` prefix:

```
Use the /testing skill to write unit tests for the auth module
```

You can also manage skills from within a Copilot CLI session:

```
/skills list          # see all available skills
/skills info testing  # details about the testing skill
/skills reload        # pick up newly added skills without restarting
```

## Skill authoring guidelines

- **One skill per directory** — each directory under the repo root is a self-contained skill
- **Lowercase, hyphen-separated** directory and skill names (e.g. `code-review`, `api-testing`)
- **`SKILL.md` is required** — must include `name` and `description` frontmatter
- **Keep descriptions precise** — Copilot uses the description to decide *when* to invoke the skill; vague descriptions lead to missed or incorrect invocations
- **Include scripts when helpful** — add helper scripts alongside `SKILL.md` and reference them in instructions
- **Use `allowed-tools` sparingly** — only pre-approve `shell`/`bash` for scripts you fully trust
- **Version your skills** — use Git tags (e.g. `v1.0.0`) to pin stable releases

## Contributing

1. Create a new directory with a lowercase, hyphen-separated name
2. Add a `SKILL.md` following the template below
3. Test the skill in a real Copilot CLI session before submitting a PR

### SKILL.md template

```markdown
---
name: your-skill-name
description: One sentence explaining what this skill does and when Copilot should use it.
---

## Overview

Brief description of the skill's purpose.

## Instructions

Step-by-step instructions for Copilot to follow when this skill is invoked.

1. Step one
2. Step two
...
```

## License

MIT
