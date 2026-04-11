# mistral-agents

Mistral Le Chat Agent Prompts for Imagewize Development

## Overview

This repository contains **specialized agent prompts** for Mistral Le Chat, configured for use across Imagewize projects. It serves as a centralized library of role-specific instructions that guide Le Chat agents when working on different types of tasks.

## Repository Structure

```
mistral-agents/
├── .vibe/
│   ├── config.toml          # Vibe CLI configuration (optional, for local dev)
│   └── prompts/
│       └── vibe.md          # Repository-level prompt context
├── README.md                # This file
├── FRONTEND-DEV.md          # Frontend Developer Agent
└── (future agent prompts)
```

## Available Agents

### 📱 [FRONTEND-DEV.md](/FRONTEND-DEV.md)
**Role**: Senior Frontend Developer  
**Scope**: WordPress theme development (HTML/CSS components, page templates, block patterns)  
**Projects**: imagewize.com, Nynaeve, Elayne  
**Output**: Production-ready code with developer handoff notes

*See [FRONTEND-DEV.md](/FRONTEND-DEV.md) for full specifications.*

## Imagewize Projects

This repository supports development across three main projects:

| Project | Type | Target Audience | Tech Stack |
|---------|------|-----------------|------------|
| **imagewize.com** | Company/Blog Site | Marketing | WordPress |
| **Nynaeve** | Theme | Premium Clients | Sage 11, Blade, ACF Composer, React |
| **Elayne** | Theme | End Users | FSE, Gutenberg Blocks, theme.json |

## Adding New Agent Prompts

When adding a new agent to this repository:

1. **Create a new markdown file** in the root directory
2. **Use role-based naming**: `ROLE-DEV.md`, `ROLE-SPECIALIST.md`, etc.
3. **Include the following sections**:
   - Role description and scope
   - Critical rules (do's and don'ts)
   - Output format expectations
   - Project-specific constraints
   - Handoff notes requirements
4. **Update this README** with the new agent in the Available Agents section
5. **Reference in vibe.md** for Vibe CLI context

### Agent Naming Convention

```
{ROLE}-{SPECIALIZATION}.md    e.g., BACKEND-WORDPRESS.md
{ROLE}.md                    e.g., DEVOPS.md
{TEAM}-{ROLE}.md             e.g., FRONTEND-DEV.md
```

## Usage

### With Mistral Le Chat

1. Go to [Le Chat](https://chat.mistral.ai) and open **Agents**
2. Create a new agent or edit an existing one
3. Copy the contents of the relevant `.md` file (e.g. `FRONTEND-DEV.md`) into the **System prompt** field
4. Set the model (recommended: `mistral-large-latest` or `devstral`)
5. Save and start chatting

## Planned Agents

- [ ] **BACKEND-DEV.md** - PHP/WordPress backend development
- [ ] **DEVOPS.md** - Deployment, infrastructure, and CI/CD
- [ ] **CONTENT-STRATEGY.md** - Content planning and SEO
- [ ] **UI-UX.md** - User interface and experience design
- [ ] **QA-TESTING.md** - Quality assurance and testing strategies
- [ ] **ACCESSIBILITY.md** - WCAG compliance and a11y best practices

## Configuration

The `.vibe/config.toml` file is kept for optional local Vibe CLI use. See `.vibe/prompts/vibe.md` for repository-level context documentation.

## Contributing

1. Fork this repository
2. Create a new branch for your agent prompt
3. Add your `.md` file following the naming convention
4. Update the README with your agent's details
5. Submit a pull request

### Quality Guidelines

- ✅ **Be specific**: Clear, unambiguous instructions
- ✅ **Be actionable**: Tell the agent WHAT to do and HOW
- ✅ **Include examples**: Show expected output formats
- ✅ **Document constraints**: List what NOT to do
- ✅ **Project-aware**: Tailor to Imagewize conventions
- ❌ **Avoid vagueness**: No "you should probably..."
- ❌ **Avoid placeholders**: No lorem ipsum or TODOs in agent outputs

## Critical Rules (All Agents)

These rules apply across all agent prompts in this repository:

1. **Production-ready output only** - No placeholders, descriptions, or "replace with X" comments
2. **Mobile-first** - All output must be responsive
3. **No centered overlay heroes** - This is the most common failure mode
4. **Realistic content** - Use relevant dummy content, never lorem ipsum
5. **Project-specific conventions** - Honor each project's tech stack and aesthetic

## Resources

- [Mistral Le Chat](https://chat.mistral.ai)
- [Mistral Le Chat Agents Docs](https://docs.mistral.ai/capabilities/agent/)
- [Imagewize](https://imagewize.com)
- [Elayne Theme](~/code/imagewize.com/demo/web/app/themes/elayne/)
- [Nynaeve Theme](~/code/imagewize.com/demo/web/app/themes/nynaeve/)

---

*Maintained by Imagewize for internal development workflows.*
