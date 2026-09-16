# Codex Skills

Personal skills for AI coding agents, organized as standalone directories that follow the Agent Skill format:

```text
skills/
└── software-architecture/
    └── SKILL.md
```

## Skills

### `software-architecture`

Architecture-first routing skill for designing, structuring, or refactoring software systems. It establishes a decision order based on business capabilities, responsibility boundaries, and dependency direction before selecting patterns or abstractions.

Use it when:

- Deciding application layers or dependency boundaries
- Balancing Clean Architecture, SOLID, DDD, design patterns, 12-Factor, and testing priorities
- Evaluating whether an abstraction, interface, or architectural layer is justified
- Avoiding overengineering in CRUD, small services, or standalone programs

Core rule: introduce an abstraction only for a real dependency boundary, a second implementation, test isolation, domain independence, or a meaningful business concept.

## Installation

Clone this repository and copy the desired skill directory into your Codex skills directory:

```bash
git clone git@github.com:zhengxiongzhao/skills.git
mkdir -p ~/.codex/skills
cp -R skills/software-architecture ~/.codex/skills/
```

For tools that use a different skills or instructions directory, copy the same `software-architecture/` directory into the location they scan.

After installation, start a new Codex task so the skill list is refreshed. The skill is triggered by architecture, module boundary, dependency direction, and architecture-tradeoff tasks.
