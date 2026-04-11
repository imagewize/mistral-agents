# Vibe Agents Repository

## Overview

This is the **vibe-agents** repository, a centralized collection of Mistral Vibe agent prompts, configurations, and skills for the Imagewize development workflow. It serves as a prompt library and configuration hub for Vibe CLI agents used across Imagewize projects.

## Repository Purpose

- **Agent Prompt Library**: Store and version-control specialized agent prompts (e.g., FRONTEND-DEV.md)
- **Vibe CLI Configuration**: Centralized `.vibe/config.toml` with model settings, tool permissions, and project context
- **Skill Management**: Reference and enable Vibe skills (currently linked to Elayne theme skills)
- **Prompt Inheritance**: Base prompts that can be extended by project-specific configurations

## Current Structure

```
vibe-agents/
├── .vibe/
│   ├── config.toml          # Vibe CLI configuration
│   └── prompts/
│       └── vibe.md          # This file - repository-level prompt details
├── README.md                # Minimal repository description
├── FRONTEND-DEV.md          # Frontend Developer Agent prompt
└── (future agent prompts)
```

## Available Agent Prompts

### FRONTEND-DEV.md
- **Role**: Senior Frontend Developer specializing in WordPress theme development
- **Scope**: HTML/CSS components, page templates, block patterns
- **Projects**: 
  - imagewize.com (company/blog site)
  - Nynaeve (Sage 11 hybrid theme)
  - Elayne (FSE block theme)
- **Key Features**: 
  - Production-ready code output (not descriptions)
  - Full page builds with component extraction
  - Developer handoff notes with WordPress mappings
  - Critical rules for Elayne FSE and Nynaeve Sage conventions

## Vibe CLI Configuration Highlights

### Active Model
- **Model**: `devstral-2` (Mistral Vibe CLI latest)
- **Provider**: Mistral API
- **Temperature**: 0.2 (low for deterministic output)

### Tool Configuration
- **Search/Replace**: Ask permission, fuzzy matching enabled
- **Bash**: Allowlist includes git commands, file inspection
- **Grep**: Always allowed, with smart exclusions
- **Read/File**: Always allowed, max 64KB per file
- **Write/File**: Ask permission, creates parent dirs
- **Todo**: Always allowed, max 100 todos

### Project Context
- **Max Characters**: 40,000
- **Default Commit Count**: 5
- **Max Depth**: 3 directory levels
- **Max Files**: 1000 per session
- **Timeout**: 2 seconds

### Skill Integration
- **Skill Paths**: `~/code/imagewize.com/demo/web/app/themes/elayne/.vibe/skills`
- **Enabled Skills**: `design` (for Elayne theme design system)

## Workflow Patterns

### For Agent Prompt Creation
1. Create new `.md` files in the root for major agent roles
2. Use clear role-based naming (e.g., `BACKEND-DEV.md`, `DEVOPS.md`)
3. Include critical rules, output format expectations, and project-specific constraints
4. Reference shared configurations in this vibe.md when applicable

### For Using This Repository
1. Clone or symlink agent prompts where needed
2. Reference prompts via Vibe's `--prompt` or `--prompt-file` flags
3. Extend base prompts with project-specific context
4. Keep the central repository updated with improvements

## Imagewize Project Context

This repository supports development across three main Imagewize projects:

### 1. imagewize.com
- Main company and blog site
- Professional consultancy aesthetic
- Content-forward design
- Target: Marketing and company presence

### 2. Nynaeve Theme
- Sage 11 hybrid theme
- Blade templating + ACF Composer
- Sage Native Blocks (React)
- Target: Premium WordPress clients
- Aesthetic: Crafted, intentional, avoids generic SaaS look
- Colors: Primary blue `#017cb6`, accent orange `#f97316`

### 3. Elayne Theme
- WordPress Full Site Editing (FSE) block theme
- Pattern-based with custom Gutenberg blocks
- Theme.json-driven styling
- Target: End users with block editor
- Aesthetic: Clean, modern, block-composable
- Critical: All layouts must map to stackable/nestable Gutenberg blocks
- CSS: Use `--wp--preset--color--*` custom properties

## Critical Rules (Applied Across All Projects)

1. **No Placeholders**: Always deliver full, production-ready code. Never use "replace with X" or placeholder labels like "Illustration", "Preview"
2. **No Centered Overlay Heroes**: Explicitly forbidden as the most common failure mode
3. **No Hardcoded Background Images**: Flag for Cover block implementation in handoff notes
4. **Responsive First**: Mobile-first approach required
5. **Realistic Content**: Use relevant WordPress agency dummy content, never lorem ipsum walls

## Handoff Notes Requirements

Every component must include developer handoff notes specifying:
- **Target Project**: Which Imagewize project it's for
- **Implementation Mapping**:
  - Nynaeve: Gutenberg block, ACF Composer field group, or Blade partial
  - Elayne: FSE pattern, custom block, or theme.json-driven style
  - imagewize.com: Page template or reusable component
- **FSE Compatibility**: For Elayne, confirm the layout can be built with stacked/nested blocks
- **Field Control**: For Nynaeve, note which parts would be ACF-controlled

## Version Control Conventions

- Use semantic commit messages (e.g., "feat: add backend dev agent prompt")
- **NEVER** add "Generated by Mistral Vibe" or "Co-Authored-By" attribution to commits
- Always create a new branch before pushing code — direct commits to `main` are not recommended
- Keep agent prompts versioned alongside code they support
- Document breaking changes to prompts that affect agent behavior

## Future Enhancements

- [ ] Add BACKEND-DEV.md for PHP/WordPress backend development
- [ ] Add DEVOPS.md for deployment and infrastructure
- [ ] Add CONTENT-STRATEGY.md for content planning
- [ ] Create project-specific prompt extensions
- [ ] Add prompt testing and validation scripts
- [ ] Document prompt inheritance patterns

---

*This file provides Vibe with context about the vibe-agents repository structure, purpose, and conventions. It should be kept up-to-date as new agent prompts and configurations are added.*
