# Mistral Agents

**A library of specialized Mistral Le Chat agent prompts for developers, designers, and creators.**

This repository provides production-ready agent system prompts that you can load directly into [Mistral Le Chat](https://chat.mistral.ai) to get consistent, high-quality output for specific roles and workflows.

Imagewize originally created this for WordPress theme development (Elayne, Nynaeve), but the prompts are designed to be **adaptable to any project**. Use as-is, extend, or fork to fit your needs.

---

## ✨ Quick Start

1. Copy any `.md` file from the `agents/` directory (e.g., `agents/FRONTEND-DEV.md`)
2. Paste into Le Chat → **Agents** → New Agent → **System Prompt**
3. Set model to `mistral-large-latest` or `devstral`
4. Start chatting!

> **Tip**: All prompts follow a consistent structure - you can easily modify them for your tech stack.

---

## 📂 Repository Structure

```
mistral-agents/
├── .vibe/
│   ├── config.toml          # Optional Vibe CLI config
│   └── prompts/
│       └── vibe.md          # Repository context
├── agents/                  # Agent prompt files
│   ├── FRONTEND-DEV.md      # Frontend Developer (WordPress-focused)
│   ├── REVIEWER.md          # Code Reviewer
│   └── (add your own!)
├── prompts/                 # Example agent runs (prompt → output → feedback)
│   ├── frontend-dev/        # FRONTEND-DEV agent runs
│   │   └── elayne-hero-block/   # Example run: Elayne hero block
│   │       ├── PROMPT.md        # Input prompt used
│   │       ├── OUTPUT.md        # Raw agent output
│   │       ├── FEEDBACK.md      # Review notes and issues found
│   │       └── canvas.html      # Generated HTML canvas
│   └── reviewer/            # REVIEWER agent runs
│       └── elayne-hero-block/   # Example run: Elayne hero block review
│           ├── PROMPT.md        # HTML input submitted for review
│           └── OUTPUT.md        # Structured review report (FAIL)
├── README.md
├── CHANGELOG.md
└── LICENSE.md
```

---

## 🎯 Available Agents

| Agent | Role | Focus | Best For |
|-------|------|-------|----------|
| [FRONTEND-DEV.md](/agents/FRONTEND-DEV.md) | Senior Frontend Developer | WordPress themes, HTML/CSS, block patterns | WordPress devs, theme authors |
| [REVIEWER.md](/agents/REVIEWER.md) | Code Reviewer | Code analysis, quality assessment | All developers |

**Planned Agents:**
- `BACKEND-DEV.md` - PHP/WordPress & general backend development
- `DEVOPS.md` - Deployment, infrastructure, and CI/CD
- `CONTENT-STRATEGY.md` - Content planning and SEO
- `UI-UX.md` - User interface and experience design
- `QA-TESTING.md` - Quality assurance and testing strategies
- `ACCESSIBILITY.md` - WCAG compliance and a11y best practices

> **Note on WordPress Agents**: The current `FRONTEND-DEV.md` is tailored for Imagewize's Elayne (FSE block theme) and Nynaeve (Sage 11 hybrid theme). See [WordPress Context](#-wordpress-context) below for details.

---

## 🌐 WordPress Context (Optional)

*For users of the WordPress-specific agents:*

This repository originated to support these Imagewize projects:

| Project | Type | Tech Stack |
|---------|------|------------|
| **Elayne** | FSE Block Theme | Gutenberg, theme.json, patterns |
| **Nynaeve** | Sage 11 Hybrid | Blade, ACF Composer, React blocks |
| **imagewize.com** | Site | Enterprise WordPress |

**The WordPress agents include:**
- Full page builds with component extraction
- Developer handoff notes with WP implementation mappings
- Project-specific conventions (FSE block compatibility, ACF fields, etc.)

*You can ignore this section if you're using the agents for non-WordPress work.*

---

## 🧪 Example Agent Runs

The `prompts/` directory contains real agent runs — input prompt, raw output, canvas, and review feedback — so you can see how each agent performs in practice and what to watch out for.

| Run | Agent | Status |
|-----|-------|--------|
| [frontend-dev/elayne-hero-block](/prompts/frontend-dev/elayne-hero-block/) | FRONTEND-DEV | Reviewed — see FEEDBACK.md |
| [reviewer/elayne-hero-block](/prompts/reviewer/elayne-hero-block/) | REVIEWER | FAIL — CSS variable namespace + dash syntax errors |

Each run folder contains:
- **PROMPT.md** — the exact input sent to the agent
- **OUTPUT.md** — raw agent response
- **canvas.html** — generated HTML/CSS output
- **FEEDBACK.md** — review notes: what worked, what failed, fixes needed

---

## 📝 Adding Your Own Agents

1. **Create**: New `.md` file in the `agents/` directory (e.g., `agents/BACKEND-DEV.md`)
2. **Name it well**: Use role-based naming like `ROLE-SPECIALIZATION.md`
3. **Structure your prompt**:
   - Role description and scope
   - Critical rules (do's and don'ts)
   - Output format expectations
   - Examples of expected output
   - Project-agnostic instructions where possible

**Naming Convention:**
```
{ROLE}-{SPECIALIZATION}.md    e.g., BACKEND-PHP.md
{ROLE}.md                    e.g., DEVOPS.md
{TEAM}-{ROLE}.md             e.g., FRONTEND-DEV.md
```

**Quality Checklist:**
- [ ] Clear, specific instructions (no "you should probably")
- [ ] Examples of expected output
- [ ] Do's and don'ts explicitly stated
- [ ] Project-agnostic where possible (add variants for specific stacks)
- [ ] Follows existing formatting in other prompts

---

## 🏗 Universal Critical Rules

*Applied across all agents in this repository:*

1. **Production-ready output only** - No placeholders, descriptions, or "replace with X" comments
2. **Mobile-first** - All output must be responsive by default
3. **No centered overlay heroes** - This is the most common failure pattern to avoid
4. **Realistic content** - Use relevant dummy content, never lorem ipsum or placeholder text
5. **Consistent formatting** - Follow the repository's style guidelines

---

## 🔗 Resources

- [Mistral Le Chat](https://chat.mistral.ai)
- [Mistral Agent Documentation](https://docs.mistral.ai/capabilities/agent/)
- [Imagewize](https://imagewize.com) - Original creators of this repository

---

## 🤝 Contributing

1. Fork this repository
2. Create a new branch for your agent prompt
3. Add your `.md` file following the naming convention
4. Update the README with your agent's details
5. Submit a pull request

We welcome contributions for any domain - not just WordPress!

---

*Originally created by Imagewize; now maintained for the Mistral Le Chat community.*
