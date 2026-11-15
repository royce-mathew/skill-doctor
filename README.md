<div align="center">

# skill-doctor

Audit agent skills and prompt instructions. Review the evidence before you change a rule.

[![skills.sh](https://skills.sh/b/royce-mathew/skill-doctor?style=flat-square)](https://skills.sh/royce-mathew/skill-doctor/skill-doctor)

[Install](#install-the-skill) · [Run an audit](#audit-your-skill-library) · [Audit reference](docs/reference.md) · [Report a bug](https://github.com/royce-mathew/skill-doctor/issues)

</div>

## Install the skill

With Node.js 22.20 or later and npm installed, run:

```sh
npx skills add royce-mathew/skill-doctor --skill skill-doctor
```

Choose your agent and install location when the [skills CLI](https://skills.sh/docs/cli) asks. Start a new agent session after installation.

To install for Codex in every project without prompts, run:

```sh
npx skills add royce-mathew/skill-doctor --skill skill-doctor -g -a codex -y
```

For other agents and install options, use the [skills CLI reference](https://skills.sh/docs/cli).

## Audit your skill library

Replace `./skills` with the skill directory you want to inspect. Ask your agent:

```text
Use skill-doctor to audit ./skills. Check skill health and prompt quality.
Report the findings and proposed patches. Do not edit files.
```

Review the scope and coverage in the report. For each proposed change, check the cited file, evidence, expected effect, and confidence.

For an instruction-only audit, name the instruction file:

```text
Use skill-doctor in prompt-audit mode on ./AGENTS.md.
Report conflicts, repeated rules, and unclear instructions. Do not edit files.
```

For a skill-health-only audit, ask:

```text
Use skill-doctor to audit skill health in ./skills.
Check discovery, routing, references, usage evidence, and context cost.
Report findings and proposed patches. Do not edit files.
```

To apply a repair, approve the exact proposed changes and files. Keep unapproved changes out of the patch.

See the [audit reference](docs/reference.md) for checks, report fields, approval rules, and limits.

## Use an agent without skill discovery

Clone the repository into a directory you control:

```sh
git clone https://github.com/royce-mathew/skill-doctor.git
```

Give your agent the path to `skill-doctor/SKILL.md` and ask it to read that file. Keep the `references` directory beside `SKILL.md`.

For example, from the directory that contains the clone, ask:

```text
Read ./skill-doctor/SKILL.md and follow it to audit ./my-project/skills.
Report findings and proposed patches. Do not edit files.
```

## Report a bug or propose a change

[Open an issue](https://github.com/royce-mathew/skill-doctor/issues) with your agent, model, audit scope, expected result, and actual result. Remove secrets and private instructions from examples.

For a pull request, describe the behavior you change and the scenario you checked. Include a nearby case that must stay unchanged when you alter routing or instruction wording.
