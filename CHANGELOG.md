# Changelog

All notable changes to the mistral-agents repository will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

**agents/CODE-REVIEW.md — New Code Review Agent for Theme Repositories:**
- Added comprehensive code review agent adapted from aludra's methodology
- Supports branch mode (review diffs) and audit mode (review files in place)
- Project-specific checklists for Elayne (FSE), Nynaeve (Sage 11), and imagewize.com
- WordPress security and correctness checks (escaping, sanitization, guards, etc.)
- CSS and frontend validation rules aligned with existing REVIEWER.md
- Git integration for automatic file discovery and categorization
- Structured CONFIRMED/PLAUSIBLE finding labels with verification discipline
- Architecture review for duplication, boundaries, and reachability

**agents/REVIEWER.md — Enhanced with Verification Discipline:**
- Added behavior rules: never skip checks, explicit failure listing, re-run after fixes
- Added verification discipline: try to disprove findings before reporting
- Added CONFIRMED/PLAUSIBLE labels for findings with failure scenarios
- Updated output format to include Target description and finding labels
- Clarified that findings without verifiable failure scenarios should be dropped

### Changed

**README.md — Updated Agent Table and Structure:**
- Added CODE-REVIEW.md to Available Agents table with role, focus, and audience
- Updated repository structure tree to include CODE-REVIEW.md
- Clarified REVIEWER.md as "Frontend Code Reviewer" for HTML/CSS output analysis

**.vibe/prompts/vibe.md — Updated Agent Documentation:**
- Added CODE-REVIEW.md section with role, scope, projects, and key features
- Updated REVIEWER.md section to clarify its specific focus on frontend output
- Updated repository structure tree to include CODE-REVIEW.md

## [1.3.2] - 2026-04-11

### Changed

**agents/REVIEWER.md — Handoff Notes and Visual Completeness Refinements:**
- Updated Handoff Notes check: if handoff notes are absent entirely, agent now adds a Critical Failure ("Handoff notes missing — resubmit with component mapping included") and lists it first before all other findings — previously only marked as FAIL and halted
- Updated behavior rule to match: missing handoff notes trigger a listed Critical Failure rather than an immediate silent halt
- Added Visual Completeness clarification: a `div` with a background color or gradient used as an image placeholder is correct and expected — only `url()` references in CSS should be flagged as hardcoded background image violations

## [1.3.1] - 2026-04-11

### Added

**prompts/reviewer/ — First Reviewer Agent Example Run:**
- Added `prompts/reviewer/elayne-hero-block/` — first example run using `agents/REVIEWER.md` agent
  - `PROMPT.md` — raw HTML input (Elayne hero block) submitted to the REVIEWER agent for code review
  - `OUTPUT.md` — structured review report with critical failures, warnings, and passed checks
    - Critical failures: invalid `--wp--preset--border-radius--*` namespace and single-dash spacing variable references
    - Warnings: generic placeholder text and hardcoded background color in mockup
    - Verdict: FAIL — documents exactly the categories of errors the REVIEWER agent is designed to catch

### Changed

**README.md — Repository Structure and Example Runs:**
- Updated structure tree to include `prompts/reviewer/elayne-hero-block/` alongside existing `frontend-dev/` entry
- Updated Example Agent Runs table: added reviewer run row with FAIL verdict; made frontend-dev path more specific (`frontend-dev/elayne-hero-block/`)

## [1.3.0] - 2026-04-11

### Added

**agents/ — Dedicated Agent Directory:**
- Added `agents/` directory to house all agent prompt files (previously stored in root)
- Added `agents/REVIEWER.md` — new Code Review Agent specializing in WordPress FSE frontend code review
  - Runs a structured checklist: CSS variable integrity, layout rules, visual completeness, FSE/WordPress conventions
  - Flags critical failures with file location and precise fix guidance
  - Outputs a pass/fail report with categorized severity levels

### Changed

**Repository Structure — Agent Files Moved to `agents/`:**
- Moved `FRONTEND-DEV.md` from repo root to `agents/FRONTEND-DEV.md`
- Updated `README.md` quick start, structure tree, agent table, and adding-agents guide to reference `agents/` path
- Updated `.vibe/prompts/vibe.md` structure tree and workflow patterns to reference `agents/` directory

**prompts/ — Example Runs Reorganized by Agent:**
- Moved `prompts/elayne-hero-block/` → `prompts/frontend-dev/elayne-hero-block/`
- Example runs are now grouped under agent-named subdirectories (e.g., `prompts/frontend-dev/`) for scalability
- Updated `README.md` example runs table to reflect new path

## [1.2.0] - 2026-04-11

### Added

**prompts/ — Example Agent Runs:**
- Added `prompts/` directory to hold real agent run examples (prompt → output → canvas → feedback)
- Added `prompts/elayne-hero-block/` — first example run using FRONTEND-DEV.md agent
  - `PROMPT.md` — input prompt used for the run
  - `OUTPUT.md` — raw agent output
  - `canvas.html` — generated Elayne hero block (split layout, CSS Grid, browser mockup)
  - `FEEDBACK.md` — review notes covering two real bugs: spacing CSS variable dash bug and invalid border-radius namespace

**FRONTEND-DEV.md — Elayne critical rules:**
- Added rule: never use `--wp--preset--border-radius--*` — WordPress does not expose border radius as a `--wp--preset--` namespace; use theme-prefixed custom properties or hardcoded values instead

**README.md — Example Agent Runs section:**
- Added `Example Agent Runs` section documenting the `prompts/` directory purpose and structure
- Added table listing available example runs with agent and review status
- Updated Repository Structure tree to include `prompts/` with annotated contents

## [1.0.3] - 2025-06-26

### Added

**.vibe/prompts/vibe.md - Release Workflow Documentation:**
- Added Release Workflow section documenting branch management requirements
- Specified semantic versioning tag format (e.g., `v1.0.2`) without additional prefixes/suffixes
- Clarified tags must be created after merging changes into `main`, never on feature branches
- Required GitHub release creation with details after tagging
- Required CHANGELOG.md update before tagging

## [1.0.2] - 2025-06-26

### Changed

**FRONTEND-DEV.md - CSS Variable Validation:**
- Added critical rule: Must verify every `var(--...)` reference exactly matches a defined `:root` variable including all dashes before HTML output
- Added critical rule: `--wp--preset--` spacing and font-size Variables must be referenced with exact name matching including all dashes (e.g., `var(--wp--preset--spacing--40)` not `var(--wp--preset--spacing-40)`)

## [1.0.1] - 2025-06-25

### Changed

**README.md - Repository Rebranding:**
- Rebranded from WordPress/Imagewize-specific to general-purpose agent library
- Added origin story clarifying Imagewize roots while emphasizing adaptability
- Updated title from "mistral-agents" to "Mistral Agents"

**README.md - Structure & Content:**
- **Added**: Quick Start section with step-by-step setup instructions
- **Removed**: Configuration section (redundant with Quick Start)
- **Renamed**: "Imagewize Projects" → "WordPress Context (Optional)" to make it optional reading
- **Renamed**: "Adding New Agent Prompts" → "Adding Your Own Agents" with enhanced guidance
- **Renamed**: "Critical Rules (All Agents)" → "Universal Critical Rules" for broader applicability
- **Restructured**: Available Agents as a clear table with role, focus, and audience columns
- **Restructured**: WordPress project table simplified (removed Target Audience column)
- **Updated**: Contributing section to explicitly welcome non-WordPress contributions
- **Updated**: Resources section - removed internal theme directory links
- **Updated**: Planned Agents from checklist format to list format
- **Updated**: Footer from "Maintained by Imagewize for internal" to "Originally created by Imagewize; now maintained for the Mistral Le Chat community"

## [1.0.0] - 2025-04-11

### Added

**Repository Structure:**
- Created `mistral-agents` repository for Mistral Le Chat agent prompts
- Added `.vibe/config.toml` for optional Vibe CLI configuration
- Added `.vibe/prompts/` directory for prompt files
- Added `CHANGELOG.md` following Keep a Changelog format

**Frontend Developer Agent:**
- Added `FRONTEND-DEV.md` - Senior Frontend Developer agent prompt
- Specialized for WordPress theme development (HTML/CSS, page templates, block patterns)
- Covers three Imagewize projects: imagewize.com, Nynaeve, Elayne
- Includes critical rules for production-ready code output
- Defines workflow: full page build → component extraction → developer handoff notes

**Repository Documentation:**
- Added `.vibe/prompts/vibe.md` with comprehensive repository-level prompt details
- Documents repository purpose, structure, and conventions
- Describes Imagewize project context (imagewize.com, Nynaeve, Elayne)
- Outlines critical rules, handoff notes requirements, and workflow patterns

**Repository Documentation:**
- Added `README.md` with detailed repository documentation
- Available Agents section listing FRONTEND-DEV.md
- Imagewize project context table with type, audience, and tech stack
- Agent naming conventions and quality guidelines
- Usage instructions for Vibe CLI
- Contributing guidelines and future enhancements list

---

*This is the first tracked release of the vibe-agents repository.*
