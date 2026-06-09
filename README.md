# Xcode 27 Skills

A collection of [Agent Skills](https://docs.claude.com/en/docs/claude-code/skills) exported from **Xcode 27**. These skills give AI coding agents (Claude Code, etc.) authoritative, up-to-date guidance for building Apple platform apps — covering SwiftUI, UIKit modernization, Swift Testing, C bounds-safety, Xcode security hardening, and on-device verification.

> **Attribution / 归属**
> The content of these skills was authored and published by **Apple** and exported from Xcode 27. This repository is a redistribution for convenience and reference only. All rights to the underlying guidance belong to Apple. No license is granted by this repository over Apple's content.

## Skills

| Skill | Purpose |
|-------|---------|
| [`swiftui-specialist`](swiftui-specialist/) | Best practices and idiomatic patterns for SwiftUI — structure, data flow, environment, modifiers, localization, animations, `ForEach`, and soft-deprecated APIs. |
| [`swiftui-whats-new-27`](swiftui-whats-new-27/) | New SwiftUI APIs, behaviors, and deprecations in the 2027 OS releases (iOS/macOS/watchOS/tvOS/visionOS 27) — `@State` macro, reorderable, swipe actions, toolbar overflow, `AsyncImage`, item bindings, document-based apps. |
| [`uikit-app-modernization`](uikit-app-modernization/) | Modernize UIKit apps for multi-window environments — replace legacy shared-state APIs, migrate to scene lifecycle, support dynamic scene sizing. |
| [`test-modernizer`](test-modernizer/) | Modernize test suites to use modern Swift Testing features or migrate from XCTest. |
| [`c-bounds-safety`](c-bounds-safety/) | Guide for the C `-fbounds-safety` language extension — language model, pointer annotations, adoption, build settings, and runtime debugging. |
| [`audit-xcode-security-settings`](audit-xcode-security-settings/) | Audit and progressively enable security-oriented Xcode build settings — compiler warnings, static analyzer checkers, and Enhanced Security hardening. |
| [`device-interaction`](device-interaction/) | Verify iOS app behavior on device or simulator via screenshots, UI hierarchy, and touch interactions. |

## Installation

Each top-level directory in this repo is a self-contained skill. Pick whichever method fits your agent.

### Option 1 — `npx skills` (universal, recommended)

The [`skills`](https://www.npmjs.com/package/skills) CLI installs a skill into any supported agent (Claude Code, Codex, etc.) and lets you choose project-local or global scope interactively. Install one skill at a time with `--skill`:

```sh
npx skills add https://github.com/fatwang2/xcode27-skills --skill swiftui-specialist
```

Swap in any skill name from the [table above](#skills) — e.g. `--skill swiftui-whats-new-27`, `--skill test-modernizer`. Omit `--skill` to pick from a list.

> Requires Node. If `npx` is missing, install it first: `brew install node`.

### Option 2 — Manual install (Claude Code)

Clone the repo and copy the skill directories into your skills path. Use `~/.claude/skills/` to make them available globally, or `<your-project>/.claude/skills/` to scope them to one project.

```sh
git clone https://github.com/fatwang2/xcode27-skills.git
mkdir -p ~/.claude/skills

# Install all seven skills globally…
cp -R xcode27-skills/*/ ~/.claude/skills/

# …or just the one you want:
cp -R xcode27-skills/swiftui-specialist ~/.claude/skills/
```

Claude Code auto-discovers any directory containing a `SKILL.md` and surfaces it when a task matches the skill's `description`.

### Option 3 — Xcode 27

These skills were exported *from* Xcode 27, so they can be loaded back into Xcode's coding intelligence. In Xcode, open the skills/agent settings and import (or point it at) a skill directory from this repo. Xcode reads the same `SKILL.md` format.

## Structure

Each skill is a directory containing a `SKILL.md` (with YAML frontmatter — `name`, `description`, etc.) and optional `references/` and `scripts/` subdirectories that the agent loads on demand.

```
<skill-name>/
├── SKILL.md          # entry point + metadata
├── references/       # detailed docs loaded as needed
└── scripts/          # helper scripts (where present)
```

## Usage

Once installed, the agent surfaces a skill automatically when your request matches its `description` — you don't need to invoke it explicitly. In Claude Code you can also trigger one directly by name, e.g. `/swiftui-specialist`, and add focus hints like "check for soft-deprecated APIs" or "modernize these XCTest cases".
