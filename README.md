# Agents Library

A place to store Copilot Studio agent documents. Each agent has its own branch containing all files related to that agent.

```text
README.md
CHANGELOG.md
instructions/
  instruction.md
skills/                    Optional skill files, folders, and ZIP packages
  skill.md                 Template for Markdown skill instructions
  <skill-name>/            Example: skill folder with supporting files
  <skill-name>.zip         Example: packaged skill
knowledge/                 Optional source links and reference notes
examples/                  Optional sample requests, outputs, and screenshots
tools/                     Optional descriptions of tools and flows
```

`instructions/instruction.md` holds the agent's core instructions: its role, responsibilities, response style, and boundaries.

`skills/` is optional and holds all of the agent's skills. A skill can be a standalone `.md` file, a folder containing instructions and supporting files, or a `.zip` package. Multiple Markdown files, skill folders, and ZIP packages can live alongside each other in this folder. The example folder and ZIP names above illustrate these options.

## Use it

1. Create a branch from `main`, named `agents/<agent-name>`, such as `agents/booklet-agent`.
2. Fill in the [instruction template](instructions/instruction.md). Update this README with the agent's name, purpose, owner, scope, and Copilot Studio link.
3. If the agent has skills, add their Markdown files, folders, or ZIP packages under `skills/`. Use the [skill template](skills/skill.md) when writing Markdown instructions. Add knowledge references, examples, tool notes, and any other related files on that same branch as needed.
4. Add a short dated note to [CHANGELOG.md](CHANGELOG.md) for important updates, then commit your changes. Git history keeps the full record in GitHub or GitLab.

Keep `main` as the blank starting point. Each agent's documents and updates stay on its own branch.

Each agent branch has its own change log. Replace its placeholder title with the agent's name and record only changes to that agent, newest first.
