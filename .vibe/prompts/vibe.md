# Mistral Agents Repository

## Overview

This is the **mistral-agents** repository, a centralized collection of Mistral Le Chat agent prompts and configurations for the Imagewize development workflow. It serves as a prompt library for Le Chat agents used across Imagewize projects.

## Repository Purpose

- **Agent Prompt Library**: Store and version-control specialized agent prompts (e.g., FRONTEND-DEV.md)
- **Le Chat Agents**: Prompts are loaded as system prompts when creating agents in Mistral Le Chat
- **Prompt Inheritance**: Base prompts that can be extended by project-specific configurations

## Current Structure

```
mistral-agents/
├── .vibe/
│   ├── config.toml          # Optional Vibe CLI configuration
│   └── prompts/
│       └── vibe.md          # This file - repository-level prompt details
├── agents/                  # Agent prompt files
│   ├── FRONTEND-DEV.md      # Frontend Developer Agent prompt
│   ├── REVIEWER.md          # Code Reviewer Agent prompt
│   └── (future agent prompts)
├── prompts/                 # Example agent runs (prompt → output → feedback)
│   └── frontend-dev/        # FRONTEND-DEV agent runs
│       └── elayne-hero-block/   # Example run: Elayne hero block
│           ├── PROMPT.md        # Input prompt used
│           ├── OUTPUT.md        # Raw agent output
│           ├── FEEDBACK.md      # Review notes and issues found
│           └── canvas.html      # Generated HTML canvas
├── README.md                # Repository description
└── CHANGELOG.md             # Version history
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

## Le Chat Agent Usage

To use a prompt as a Mistral Le Chat agent:

1. Go to [chat.mistral.ai](https://chat.mistral.ai) → **Agents**
2. Create a new agent and paste the `.md` file contents as the **System prompt**
3. Set the model (`mistral-large-latest` or `devstral` recommended)
4. Save and use the agent

## Workflow Patterns

### For Agent Prompt Creation
1. Create new `.md` files in the `agents/` directory for major agent roles
2. Use clear role-based naming (e.g., `BACKEND-DEV.md`, `DEVOPS.md`)
3. Include critical rules, output format expectations, and project-specific constraints
4. Reference shared configurations in this vibe.md when applicable

### For Using This Repository
1. Clone the repository
2. Copy prompt contents into Le Chat agent system prompt field
3. Extend base prompts with project-specific context as needed
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

## Release Workflow

- **Branch Management**: Always create a new branch for each update, then merge it into `main` via PR or direct merge
- **Tagging**: Create tags using semantic versioning format only (e.g., `v1.0.2`) — do not include additional prefixes or suffixes
- **Tag Timing**: Tags must be created **after** merging changes into `main`, never on feature branches
- **Release Creation**: After tagging, always create a corresponding GitHub release with details summarizing the changes included in that version
- **CHANGELOG**: Update `CHANGELOG.md` with every version, documenting changes under the appropriate version header before tagging

## Future Enhancements

- [ ] Add BACKEND-DEV.md for PHP/WordPress backend development
- [ ] Add DEVOPS.md for deployment and infrastructure
- [ ] Add CONTENT-STRATEGY.md for content planning
- [ ] Create project-specific prompt extensions
- [ ] Add prompt testing and validation scripts
- [ ] Document prompt inheritance patterns

---

*This file provides context about the mistral-agents repository structure, purpose, and conventions. It should be kept up-to-date as new agent prompts are added.*
