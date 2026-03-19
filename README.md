# Product Seed generator skill

> Turn any product idea into a build-ready `product-seed.md` — the starting point for the [create-01x-project](https://github.com/01x-in/create-01x-project) AI agent build system.

---

## What Is a Product Seed?

`product-seed.md` is the single source of truth for the entire create-01x-project pipeline. Five specialist AI agents read it and independently produce a system design, milestone plan, user stories, product brief, and design specification — without you writing a line of code or filling in a template.

The seed is not a form you fill out. It's the output of a real ideation conversation. You think through your idea, pressure-test it, research competitors, debate tradeoffs — and when the idea is fully chalked out, you generate the seed.

**This repo gives you three ways to do that**, depending on which AI you work in.

---

## Three Ways to Generate a Seed

### 1. Custom GPT (ChatGPT)

**→ [Open Product Builder GPT](https://chatgpt.com/g/g-69b85a5ce58481919af354b1b8ccdb62-product-builder)**

A full product ideation workspace. Research competitors, pressure-test your assumptions, explore tradeoffs — then generate the seed when you're ready. Web search enabled.

Best for: users who prefer ChatGPT or want live web research during ideation.

---

### 2. Claude Skill (Claude.ai)

**→ [Download product-seed.skill](./product-seed.skill)**

Install once, available in every Claude conversation. Triggers automatically when your ideation conversation reaches a natural conclusion or when you say "generate the seed".

**To install:**
1. Download `product-seed.skill`
2. In Claude.ai → Settings → Skills → Install from file
3. Start any conversation and ideate normally — the skill activates when you're ready

Best for: Claude users who want seamless seed generation inside their existing workflow.

---

### 3. Universal Prompt (Any AI)

**→ [Copy product-seed-prompt.md](./prompt/product-seed-prompt.md)**

A single copy-paste prompt that works in Gemini, Perplexity, or any AI chat interface. Paste it at the start of a conversation — it transforms the AI into the same ideation workspace with the full seed generation process built in.

**To use:**
1. Open [`prompt/product-seed-prompt.md`](./prompt/product-seed-prompt.md)
2. Copy the entire contents
3. Paste at the start of any new AI conversation
4. Start talking through your idea

Best for: users on Gemini, Perplexity, or any other AI who want the same structured output.

---

## The Full Circle

```
┌─────────────────────────────────────────────────────┐
│                   IDEATE                            │
│                                                     │
│  ChatGPT GPT  ──┐                                   │
│  Claude Skill ──┼──▶  product-seed.md               │
│  Any AI Prompt ─┘                                   │
└─────────────────────────┬───────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────┐
│                   SCAFFOLD                          │
│                                                     │
│  mkdir my-app && cd my-app                          │
│  npx create-01x-project                             │
│                                                     │
│  Drop product-seed.md into agent_docs/              │
└─────────────────────────┬───────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────┐
│                   BUILD                             │
│                                                     │
│  Run the orchestrator agent.                        │
│                                                     │
│  ↳ 5 planning agents run in parallel                │
│  ↳ Review agent validates alignment                 │
│  ↳ Architect scaffolds the repo                     │
│  ↳ Build loop ships story by story                  │
│  ↳ PR review agent handles bot comments             │
└─────────────────────────────────────────────────────┘
```

One idea. Three ways to seed it. One build system to ship it.

---

## What the Seed Produces

When you run `Run the orchestrator agent.` in Claude Code, it reads `product-seed.md` and spawns five planning agents in parallel:

| Agent | Output |
|---|---|
| system-design-agent | Architecture, data model, API surface, tech stack decisions |
| milestone-agent | Phased delivery plan with story IDs and definitions of done |
| user-stories-agent | Acceptance criteria and edge cases per story |
| product-brief-agent | Product positioning, personas, UX principles |
| design-spec-agent | Full design system — tokens, typography, components, motion spec |

These five documents are reviewed by a sixth agent, then passed to the build loop. The build system ships story by story — tests first, then implementation — committing as it goes.

Your total keyboard input for a complete build:

```
Run the orchestrator agent.
proceed with scaffold
proceed with milestone 1
proceed with milestone 2
```

---

## Repo Structure

```
product-seed/
├── product-seed.skill          ← Claude skill (direct install)
├── skill/
│   ├── SKILL.md                ← skill source
│   └── references/
│       └── field-guide.md      ← agent requirements per field
└── prompt/
    └── product-seed-prompt.md  ← universal copy-paste prompt
```

---

## The Nine Seed Fields

Every distribution format produces the same nine-field `product-seed.md`:

| Field | Purpose |
|---|---|
| Problem Statement | The specific pain. Informs architecture scale and data model. |
| Target User | One person in one situation. Scopes Milestone 1. |
| Core Value Proposition | One sentence. The lens for every planning decision. |
| Key Features | Day-one capabilities. Maps to stories and milestones. |
| Tech Preferences | Stack decisions. Respected by the system design agent. |
| Constraints | Non-negotiables that would change the architecture. |
| Out of Scope | Bounds Milestone 1. Prevents feature creep in planning. |
| Additional Context | Competitors, risks, market context — captured before it's lost. |
| Design Direction | Visual personality. Feeds the design spec agent directly. |

---

## About 01x

This tool is part of **[01x](https://01x.in)** — a paid builder environment where you join a cohort, explore an idea, use AI to accelerate, and ship an MVP. Applications are reviewed manually. Cohort sizes are kept small.

---

*From zero to one to scale.*