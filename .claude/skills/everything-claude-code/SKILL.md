# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This codebase is a comprehensive multi-platform AI coding assistant system that provides skills, rules, and configurations for Claude, Cursor, Codex, and OpenCode platforms. It's built with JavaScript and focuses on cross-platform compatibility, multi-language documentation, and extensive skill management for AI-powered development workflows.

## Coding Conventions

### File Naming
- Use **camelCase** for file names
- Skill files follow pattern: `skills/{name}/SKILL.md`
- Test files use pattern: `*.test.js`
- Rule files use descriptive names: `rules/{lang}/coding-style.md`

### Import/Export Style
- Mixed import styles accepted (ES6 modules and CommonJS)
- Mixed export styles supported

### Directory Structure
```
skills/                 # Main skill definitions
.agents/skills/         # Agent-specific skill configs
.cursor/skills/         # Cursor IDE integration
.codex/                # Codex platform configs
.opencode/             # OpenCode platform configs
rules/                 # Language-specific coding rules
docs/                  # Multi-language documentation
scripts/               # Automation scripts
hooks/                 # Development workflow hooks
```

## Workflows

### Add New Skill
**Trigger:** When adding a new skill capability to the system
**Command:** `/add-skill`

1. Create main skill file in `skills/{name}/SKILL.md`
2. Add corresponding skill file in `.agents/skills/{name}/SKILL.md`
3. Add OpenAI agent config in `.agents/skills/{name}/agents/openai.yaml`
4. Add skill file in `.cursor/skills/{name}/SKILL.md`
5. Update `.codex/AGENTS.md`
6. Update `.opencode/README.md`
7. Update main `README.md` skill listing and count
8. Update `skills/configure-ecc/SKILL.md`

**Example skill structure:**
```markdown
# Skill Name

## Overview
Brief description of what this skill does

## Usage
How to use this skill

## Examples
Code examples and use cases
```

### Version Release
**Trigger:** When creating a new version release
**Command:** `/release`

1. Update version in `package.json`
2. Update version in `.opencode/package.json`
3. Update version in `.claude-plugin/plugin.json`
4. Update version in `.claude-plugin/marketplace.json`
5. Update `README.md` with new stats/features
6. Run `scripts/release.sh`

**Version update example:**
```json
{
  "version": "1.2.3",
  "name": "everything-claude-code"
}
```

### Cross-Platform Skill Sync
**Trigger:** When updating skills to work across Claude, Cursor, Codex, and OpenCode
**Command:** `/sync-platforms`

1. Update base skill in `skills/` directory
2. Sync to `.agents/skills/` with `openai.yaml` config
3. Sync to `.cursor/skills/` for Cursor compatibility
4. Update `.codex/AGENTS.md` for Codex
5. Update `.opencode/` configurations
6. Update main `README.md`

**Platform config example:**
```yaml
# .agents/skills/{name}/agents/openai.yaml
name: skill-name
description: Skill description
model: gpt-4
temperature: 0.1
```

### Documentation Localization
**Trigger:** When updating documentation that needs multi-language support
**Command:** `/localize-docs`

1. Update main `README.md`
2. Update `README.zh-CN.md` for Chinese
3. Update `docs/zh-CN/README.md`
4. Update `docs/zh-TW/README.md` for Traditional Chinese
5. Update `docs/ja-JP/README.md` for Japanese
6. Update corresponding skill files in each locale

**Localization structure:**
```
docs/
├── zh-CN/
│   ├── README.md
│   └── skills/{name}/SKILL.md
├── zh-TW/
└── ja-JP/
```

### Add Programming Language Rules
**Trigger:** When adding support for a new programming language
**Command:** `/add-language-support`

1. Create `rules/{lang}/coding-style.md`
2. Create `rules/{lang}/hooks.md`
3. Create `rules/{lang}/patterns.md`
4. Create `rules/{lang}/security.md`
5. Create `rules/{lang}/testing.md`
6. Create corresponding `.cursor/rules/{lang}-*.md` files
7. Update `rules/README.md`

**Rule file template:**
```markdown
# {Language} Coding Style

## Naming Conventions
- Variables: camelCase
- Functions: camelCase
- Classes: PascalCase

## Code Organization
[Language-specific patterns]
```

### Hooks and Scripts Update
**Trigger:** When modifying development workflow hooks
**Command:** `/update-hooks`

1. Update `hooks/hooks.json` configuration
2. Add or modify scripts in `scripts/hooks/`
3. Update `.cursor/hooks.json` if applicable
4. Update `hooks/README.md` documentation

**Hook configuration example:**
```json
{
  "pre-commit": {
    "script": "scripts/hooks/pre-commit.js",
    "description": "Run linting and tests"
  }
}
```

## Testing Patterns

- Test files use `*.test.js` pattern
- Framework not specified (flexible testing approach)
- Tests likely focus on skill validation and cross-platform compatibility

## Commit Patterns

- Use conventional commit prefixes: `feat:`, `fix:`, `test:`, `chore:`
- Keep commit messages around 72 characters
- Focus on clear, descriptive commit messages

## Commands

| Command | Purpose |
|---------|---------|
| `/add-skill` | Add a new skill with multi-platform support |
| `/release` | Create a new version release |
| `/sync-platforms` | Synchronize skills across all AI platforms |
| `/localize-docs` | Update documentation in multiple languages |
| `/add-language-support` | Add comprehensive rules for a new programming language |
| `/update-hooks` | Modify development workflow hooks and scripts |