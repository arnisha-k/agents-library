# Agents Library

A place to store Copilot Studio agent documents. Each agent has its own branch containing all files related to that agent.

```text
README.md
CHANGELOG.md
instructions/
  instruction.md
skills/
  skill.md
```

## Use it

1. Create a branch from `main`, named `agents/<agent-name>`, such as `agents/booklet-agent`.
2. Fill in the [instruction template](instructions/instruction.md) and [skill template](skills/skill.md). Update this README with the agent's name and purpose.
3. Add any other files your agent needs on that branch. For additional skills, copy `skills/skill.md` to a descriptive filename in the same folder.
4. Add a short dated note to [CHANGELOG.md](CHANGELOG.md) for important updates, then commit your changes. Git history keeps the full record in GitHub or GitLab.

Keep `main` as the blank starting point. Each agent's documents and updates stay on its own branch.

Each agent branch has its own change log. Replace its placeholder title with the agent's name and record only changes to that agent, newest first.
