# Lando Labs Plugin Marketplace - Documentation Draft

> **For Content Team**: This is a draft for the docs site. Adjust tone, add screenshots, and polish as needed.

---

## Overview

The Lando Labs Plugin Marketplace provides production-ready plugins for Claude Code that extend its capabilities for AI-assisted development, agent management, and creative workflows.

### Available Plugins

| Plugin | Category | Description |
|--------|----------|-------------|
| [CAMI](#cami) | Agent Management | Scout, create, and deploy Claude Code agents |
| [AIgile Dev](#aigile-dev) | Development | AI-native agile with sprint planning and full-stack agents |
| [Model Bridge](#model-bridge) | AI Tools | Expert prompting for image/video generation models |
| [Audit Kit](#audit-kit) | Quality | Educational codebase auditing agents |

### Installation

```bash
# Install from marketplace
claude plugin install lando-labs/cami
claude plugin install lando-labs/aigile-dev
claude plugin install lando-labs/model-bridge
claude plugin install lando-labs/audit-kit

# Or install the entire marketplace
claude plugin add-marketplace lando-labs/claude-plugins
```

---

# CAMI

**Claude Agent Management Interface**

CAMI is your scout for discovering, creating, and deploying Claude Code agents across projects. Think of it as a package manager for AI capabilities.

## Key Features

- **Agent Discovery**: Find agents that match your project needs
- **Deployment**: Deploy agents from sources (guilds) to your projects
- **Creation**: Build new agents with guided architecture
- **Cross-Project Management**: Track what's deployed where

## Getting Started

```
You: hey cami

CAMI: Hey! I'm CAMI, your agent scout. I can help you:
      • Find agents for your project
      • Deploy agents from sources
      • Create custom agents

      What are you working on?
```

## Core Commands

| Command | Description |
|---------|-------------|
| `hey cami` | Start a conversation with CAMI |
| `list agents` | Show available agents |
| `deploy [agent]` | Deploy an agent to current project |
| `create agent` | Start the agent creation wizard |
| `list sources` | Show configured agent sources |

## Concepts

### Agents
Specialized AI personas with domain expertise. Each agent has:
- A focused role (frontend-lead, security-auditor, etc.)
- Specific tools it can use
- Knowledge embedded in its system prompt

### Sources (Guilds)
Collections of related agents. Examples:
- `fullstack-guild` - Web development agents
- `game-dev-guild` - Game development agents
- `audit-kit` - Auditing agents

### Skills
Reusable workflows that agents can invoke. Skills are task-focused (commit code, run tests) while agents are role-focused (frontend lead, QA engineer).

## Example Workflows

### Finding Agents for a New Project

```
You: I'm starting a new React + Node project. What agents would help?

CAMI: For a React + Node stack, I'd recommend:

      Frontend:
      • frontend-lead - UI architecture and component design

      Backend:
      • api-architect - API design and Node.js patterns
      • data-modeler - Database schema design

      Quality:
      • qa-lead - Test strategy and coverage

      Want me to deploy any of these?
```

### Creating a Custom Agent

```
You: create an agent for reviewing PRs

CAMI: I'll help you create a PR review agent. Let me ask a few questions:

      1. What aspects should it focus on?
         □ Code quality
         □ Security
         □ Performance
         □ Style/conventions

      2. Should it be strict or advisory?

      3. Any team-specific conventions to enforce?
```

---

# AIgile Dev

**AI-Native Agile Development**

AIgile Dev brings structured agile workflows to AI-assisted development. Plan sprints, execute with specialized agents, validate with research, and ship with confidence.

## Key Features

- **Sprint Planning**: Analyze issues, group by feature, target semantic versions
- **Full-Stack Agents**: Specialized agents for each development discipline
- **Market Research**: Validate ideas before building
- **Structured Close-out**: Tests, tagging, releases

## Getting Started

```
You: Help me plan my first sprint

AIgile: Let's plan your sprint! First, I'll check your project:

        ✓ Found 12 open issues
        ✓ Detected: React + TypeScript + Node
        ✓ Current version: 0.3.2

        I've grouped your issues into potential sprints...
```

## Skills

### vibecoding-sprint

The core sprint workflow skill.

**Planning Phase**
```
You: plan my next sprint

AIgile: Analyzing your issues...

        Sprint 1 (v0.4.0) - User Authentication
        ├── #23 Add login page
        ├── #24 JWT token handling
        └── #25 Password reset flow

        Sprint 2 (v0.5.0) - Dashboard
        ├── #30 Dashboard layout
        └── #31 Analytics widgets

        Ready to create the sprint manifest?
```

**Execution Phase**
```
You: start the sprint

AIgile: Starting Sprint 1 (v0.4.0)...

        ✓ Created branch: sprint/v0.4.0
        ✓ Hydrated manifest with full issue details

        Current task: #23 Add login page
        Assigned agents: frontend-lead, api-architect
```

**Close-out Phase**
```
You: close out the sprint

AIgile: Running pre-close verification...

        ✓ All tests passing (47/47)
        ✓ Build successful
        ✓ Lint clean

        Ready to tag v0.4.0 and create release?
```

### market-research

Research skills for product validation.

| Skill | Output |
|-------|--------|
| `competitive-analysis` | Competitor matrix with features/pricing |
| `market-sizing` | TAM/SAM/SOM estimates with sources |
| `user-story-brief` | Validated user stories with evidence |
| `feature-design-doc` | Technical design with market context |

## Agents

| Agent | Role |
|-------|------|
| **frontend-lead** | UI architecture, component design, UX patterns |
| **api-architect** | API design, backend services, error handling |
| **data-modeler** | Database schemas, relationships, migrations |
| **devops-guide** | Deployment, CI/CD, environment configuration |
| **qa-lead** | Test strategy, coverage decisions, quality gates |
| **research-lead** | Market research coordination and synthesis |
| **product-skeptic** | Validates research, detects BS, challenges assumptions |

## Configuration

Create `.claude/sprint.config.json`:

```json
{
  "scm": {
    "provider": "github"
  },
  "closeout": {
    "test": "npm test",
    "build": "npm run build",
    "lint": "npm run lint"
  },
  "versioning": {
    "strategy": "semver"
  }
}
```

---

# Model Bridge

**Expert Prompting for AI Media Generation**

Model Bridge helps you craft effective prompts for image and video generation models. Rather than generating images directly, it teaches you the patterns and techniques that make each model perform its best.

## Key Features

- **Model-Specific Patterns**: Optimized prompts for each model's architecture
- **Concrete Examples**: Real prompts you can adapt
- **DO/DON'T Guidance**: Learn what works and what doesn't
- **Educational Focus**: Understand why prompts work

## Supported Models

### Local Models (Apple Silicon / MLX)

| Model | Strength | Speed |
|-------|----------|-------|
| **FLUX.1** | Text rendering, photorealism | 20-80s |
| **SDXL** | Fast iteration, LoRA ecosystem | ~8s |
| **LTX Video** | Camera movements, motion | ~17s |

### Cloud Models (Google Vertex AI)

| Model | Strength | Requirement |
|-------|----------|-------------|
| **Imagen 4** | Editorial compositions, spatial control | GCP + Vertex AI |

## Skills

### flux-prompt

FLUX excels at natural language understanding and text rendering.

```
You: I need a product shot with the text "DAWN BREW" on coffee packaging

Model Bridge: Here's an optimized FLUX prompt:

              Minimalist coffee packaging on marble surface, the text
              "DAWN BREW" in elegant copper foil sans-serif typography
              at center, steam rising from cup in soft focus background,
              warm morning light from left, color #8B4513 brown and
              #D4AF37 gold accents, commercial product photography

              Key patterns used:
              • Text in quotes for rendering
              • HEX colors for precision
              • Single style anchor (product photography)
              • Lighting direction specified
```

**DO:**
- Use natural language descriptions
- Put text in quotes: `the text "HELLO"`
- Specify HEX colors: `color #FF6B35`
- Include camera/lens for realism

**DON'T:**
- Use prompt weights (not supported)
- Use negative prompts (not supported)
- Stack multiple styles

### sdxl-prompt

SDXL offers speed and the LoRA ecosystem.

```
You: Fantasy castle for rapid iteration

Model Bridge: SDXL prompt with negative:

              Positive: Ancient stone castle on cliff edge, dramatic
              storm clouds, lightning in distance, fantasy art style,
              highly detailed, 8K resolution

              Negative: blurry, low quality, watermark, signature

              Weights: (castle:1.2), (lightning:1.1)
```

**When to use SDXL over FLUX:**
- Rapid iteration (~8s vs 80s)
- Need negative prompts
- Using LoRAs
- Style transfer experiments

### ltx-video-prompt

LTX Video thinks like a director, not a photographer.

```
You: Product reveal video for headphones

Model Bridge: LTX Video shot note:

              WIDE SHOT establishing sleek product packaging on
              reflective black surface. SLOW DOLLY IN over 3 seconds
              as lid lifts revealing headphones. HOLD on product
              hero shot, subtle rotation 5 degrees. Soft rim lighting,
              minimal shadows, premium tech aesthetic.

              Duration: 5 seconds (short, focused)
              Camera: Dolly + subtle rotation
```

**Key concepts:**
- Think in shots, not frames
- Specify camera movements (dolly, pan, tilt, orbit)
- Match complexity to duration
- Use cinematography terminology

### imagen-prompt

Imagen 4 excels at complex compositions with spatial control.

```
You: Editorial image showing economic impact

Model Bridge: Imagen spatial zone prompt:

              LEFT: Red oil tankers at port terminal, cargo cranes
              silhouetted against golden hour sky.

              CENTER: Working-class family at gas station, father's
              hand on pump showing $6.89/gallon.

              RIGHT: LED ticker displaying "OIL $118" in amber.

              Painterly editorial illustration style, dramatic
              golden hour lighting, 16:9 composition.

              Key: Use spatial positions (LEFT, CENTER, RIGHT)
              to control element placement.
```

**DO:**
- Use concrete spatial zones
- Name specific elements
- Include human reactions
- Single style anchor

**DON'T:**
- Use abstract concepts ("thought-provoking")
- Overload with 10+ elements
- Stack style references

### vertex-setup

Get configured for Google Cloud and Vertex AI.

```
You: Help me set up Vertex AI for Imagen

Model Bridge: Let's get you configured:

              Phase 1: gcloud CLI
              └── gcloud auth login
              └── gcloud config set project YOUR_PROJECT

              Phase 2: Enable APIs
              └── gcloud services enable aiplatform.googleapis.com

              Phase 3: Authentication
              └── gcloud auth application-default login

              Phase 4: Verify
              └── [test script provided]
```

---

# Audit Kit

**Educational Codebase Auditing**

Audit Kit provides agents that teach you how to assess codebases systematically. Rather than just running checks, these agents explain what they're looking for, why it matters, and how you can audit independently.

## Philosophy

**Learn to Audit** - Each agent:
1. Explains before acting
2. Shows its methodology
3. Teaches the patterns

This approach works for:
- **Consulting**: Demonstrate expertise while delivering value
- **Learning**: Build skills to audit independently
- **Teams**: Transfer knowledge across the organization

## Agents

### security-auditor

Assesses security posture across five domains.

```
You: Run a security audit

Security Auditor: Starting security assessment...

                  METHODOLOGY
                  I'll check five domains:
                  1. Secrets - Exposed API keys, tokens, passwords
                  2. Configuration - Debug modes, permissive settings
                  3. Dependencies - Known vulnerabilities
                  4. Authentication - Session handling, token storage
                  5. Data Handling - Input validation, output encoding

                  FINDINGS

                  [CRITICAL] Exposed API Key
                  File: src/config/api.js:12
                  Pattern: STRIPE_SK_LIVE_... (masked)

                  Why this matters: API keys in source control
                  persist in git history even after removal...

                  Recommendation: Move to environment variables,
                  rotate the exposed key immediately.
```

### dependency-auditor

Assesses supply chain health.

```
You: Audit our dependencies

Dependency Auditor: Analyzing package ecosystem...

                    METHODOLOGY
                    Four dimensions assessed:
                    1. Vulnerabilities - CVEs and security advisories
                    2. Maintenance - Last update, open issues, bus factor
                    3. Version Currency - How far behind latest
                    4. Depth - Transitive dependency risks

                    HEALTH DASHBOARD
                    ┌─────────────────────────────────┐
                    │ Total packages: 847             │
                    │ Direct: 42 | Transitive: 805    │
                    │ Vulnerabilities: 3 (1 high)     │
                    │ Outdated: 12 packages           │
                    └─────────────────────────────────┘

                    [HIGH] lodash@4.17.15
                    CVE-2021-23337: Prototype pollution
                    Fix: Upgrade to 4.17.21
```

### codebase-auditor

Assesses project structure and health.

```
You: Analyze this codebase

Codebase Auditor: Examining project structure...

                  METHODOLOGY
                  Five dimensions assessed:
                  1. Structure - Directory organization, conventions
                  2. Documentation - README, inline docs, API docs
                  3. Organization - Code grouping, module boundaries
                  4. Testing - Coverage, test organization
                  5. Infrastructure - Build tools, CI/CD

                  PROJECT PROFILE
                  ┌─────────────────────────────────┐
                  │ Framework: Next.js 14           │
                  │ Size: 12,847 lines              │
                  │ Test coverage: 67%              │
                  │ Documentation: Partial          │
                  └─────────────────────────────────┘

                  FINDINGS

                  [MEDIUM] God File Detected
                  File: src/utils/helpers.js (847 lines)

                  Why this matters: Large utility files become
                  dumping grounds that are hard to navigate...
```

### standards-auditor

Checks consistency and convention compliance.

```
You: Check our coding standards

Standards Auditor: Analyzing patterns for consistency...

                   METHODOLOGY
                   Five consistency dimensions:
                   1. Naming - Files, variables, functions
                   2. Organization - Imports, exports, structure
                   3. Patterns - Error handling, async, state
                   4. Configuration - ESLint, TypeScript, etc.
                   5. Documentation - Comments, JSDoc, README

                   CONSISTENCY DASHBOARD
                   ┌─────────────────────────────────┐
                   │ Naming: 94% consistent          │
                   │ Error handling: 3 patterns      │
                   │ Import style: 2 competing       │
                   └─────────────────────────────────┘

                   [LOW] Inconsistent Error Handling

                   Pattern A (67%): try/catch with logging
                   Pattern B (33%): .catch() without logging

                   Recommendation: Standardize on Pattern A
                   for better debugging in production.
```

## Severity Levels

| Level | Meaning | Response |
|-------|---------|----------|
| **Critical** | Immediate risk | Fix now |
| **High** | Significant issue | Fix this week |
| **Medium** | Should address | Plan to fix |
| **Low** | Minor improvement | Consider fixing |
| **Info** | Observation | Good to know |

## Reference Materials

Audit Kit includes supporting documentation:

- **audit-patterns.md** - Universal audit methodology
- **severity-guide.md** - How to assess and prioritize
- **remediation-patterns.md** - Common fixes for common findings

---

# Support

- **Issues**: Report bugs at each plugin's GitHub repository
- **Feedback**: feedback@landolabs.co
- **Documentation**: https://landolabs.co/docs

---

*Built by Lando Labs • All plugins MIT licensed*
