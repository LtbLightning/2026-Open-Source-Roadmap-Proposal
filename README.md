# AI Enablement & Bindings Modernisation Proposal
## Extension to BDK/LDK Node Bindings Work

---

## Executive Summary

**What:** Two distinct workstreams that together make Bitcoin and Lightning development libraries better for every developer — whether they use AI coding tools or not.

**Part 1 — AI Enablement:** Make BDK, LDK, and LDK Node discoverable and usable by AI coding assistants (Claude, Cursor, GitHub Copilot, Replit) so developers can build Bitcoin applications faster and with fewer errors.

**Part 2 — Bindings Modernisation & Automation:** Update UniFFI to the latest approach and replace manual, error-prone release processes with a fully automated CI/CD pipeline across all platforms.

**Scope:** BDK, LDK, and LDK Node across all platforms (Rust, Android, iOS, React Native, Flutter, Python)

---

---

# PART 1 — AI Enablement

---

## The Problem

### AI Coding Tools Are Now Mainstream

- **The majority of developers** now use AI coding assistants as a standard part of their workflow
- Tools like Claude Code, Cursor, GitHub Copilot, and Replit AI generate code from natural language
- Developers increasingly say: *"If AI can't help me use it, I'll find something else"*

### Bitcoin/Lightning Libraries Are Invisible to AI

When a developer asks an AI assistant:
> *"Add Lightning payments to my mobile app"*

The AI either:
- Doesn't know about BDK/LDK/LDK Node
- Generates outdated or incorrect code
- Misses critical steps (like calling `start()` before operations)
- Uses wrong patterns (hardcoded paths, insecure mnemonic storage)

---

## The Solution

Make our libraries **discoverable** and **usable** by AI coding tools through:

### 1. Discovery Files (How AI Finds Us)

| File | Purpose |
|------|---------|
| `llms.txt` | AI-readable library summary (like robots.txt for AI) |
| `AGENTS.md` | Instructions for coding agents |
| `CLAUDE.md` | Claude-specific guidance |
| `.cursor/rules.md` | Cursor IDE integration |

### 2. Claude Skills (Direct AI Integration)

Packaged instruction files (`.skill`) that users upload to Claude.ai. Once uploaded, Claude knows exactly how to use the library correctly.

### 3. MCP Server (AI Tool Access)

Model Context Protocol server that lets AI agents directly interact with running nodes — create invoices, check balances, open channels through natural language.

### 4. Structured Documentation

- JSON schemas for all data types
- API references optimised for AI parsing
- Example code with expected outputs

**Result:** Developer asks "create a Lightning invoice" → AI generates correct, working code.

---

## Scope

### Libraries
- **BDK** (Bitcoin Development Kit)
- **LDK** (Lightning Development Kit)
- **LDK Node** (Ready-to-go Lightning node)

### Platforms

| Platform | Bindings | AI Enablement Deliverables |
|----------|----------|---------------------------|
| Rust | Core | `llms.txt` · `AGENTS.md` · `CLAUDE.md` · Claude Skill · JSON schemas |
| Android | Kotlin (UniFFI) | Same + Kotlin-specific examples |
| iOS | Swift (UniFFI) | Same + Swift-specific examples |
| React Native | JavaScript/TypeScript | Same + RN-specific examples |
| Flutter | Dart | Same + Dart-specific examples |
| Python | UniFFI | Same + Python-specific examples |

---

## Part 1 Work Items

Per library, per platform:

- [ ] `llms.txt` — AI discovery file
- [ ] `AGENTS.md` — Coding agent instructions
- [ ] `CLAUDE.md` — Claude-specific hints
- [ ] `.cursor/rules.md` — Cursor IDE rules
- [ ] `library.skill` — Claude Skill package
- [ ] JSON schemas for all data types
- [ ] Platform-specific examples with expected outputs

### Quick Wins (Can Start Immediately)

These require no code changes — just documentation that AI tools can read:

1. **`llms.txt` for all libraries**
2. **`AGENTS.md` files**
3. **Claude Skills**
4. **GitHub metadata optimisation**

---

---

# PART 2 — Bindings Modernisation & Automation

---

## UniFFI Bindings Modernisation

### What is UniFFI?

A tool that automatically generates language bindings (Android, iOS, Python, etc.) from Rust code. One Rust implementation → multiple language SDKs.

### Current State

- Manual or semi-automated binding generation
- Inconsistent release processes across platforms
- Version mismatches between platforms
- Slow to update when Rust code changes

### Proposed Work

- [ ] Adopt latest UniFFI patterns and best practices
- [ ] Standardise binding generation scripts across all libraries
- [ ] Ensure consistent API surface across all platforms
- [ ] Document the binding creation process

---

## Automated Build & Release Pipeline

### Current Pain Points

- Manual binary compilation for each platform
- Release delays due to manual processes (weeks between code change and publish)
- Difficulty keeping all platforms in sync

### Proposed Solution

```
Git Push → CI/CD Pipeline → Automated Builds → Published Packages
                ↓
     ┌─────────────────────────────────┐
     │  • Rust crates (crates.io)      │
     │  • Android (Maven)              │
     │  • iOS (CocoaPods/SPM)          │
     │  • React Native (npm)           │
     │  • Flutter (pub.dev)            │
     │  • Python (PyPI)                │
     └─────────────────────────────────┘
```

### Benefits

- Faster releases (weeks → days, same-day across all platforms)
- All platforms released simultaneously
- Reduced human error
- Easier long-term maintenance

### Part 2 Work Items

- [ ] GitHub Actions workflows for each platform
- [ ] Automated version bumping
- [ ] Automated changelog generation
- [ ] Release coordination across platforms
- [ ] Binary caching for faster builds

---

---

## Roadmap

```
Q2 2026                    Q3 2026                    Q4 2026
───────────────────────────────────────────────────────────────
PART 1                     PARTS 1 & 2                PART 2

AI Enablement Files        UniFFI Modernisation       Build Automation
• llms.txt (all libs)      • Update binding approach  • CI/CD pipelines
• AGENTS.md                • Standardise generation   • Auto-publish
• Claude Skills            • Document process         • Release coordination
• Cursor rules
• JSON schemas             MCP Servers                Content & Outreach
                           • LDK Node MCP             • Tutorials
                           • BDK MCP                  • Workshop updates
                                                      • Community engagement
```

---

*Proposal by Bitcoin Zavior*
*Extension to Spiral BDK/LDK Node Bindings Grant*
