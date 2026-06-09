# Xcode 27 Skills

A collection of [Agent Skills](https://docs.claude.com/en/docs/claude-code/skills) exported from **Xcode 27**. These skills give AI coding agents (Claude Code, etc.) authoritative, up-to-date guidance for building Apple platform apps — covering SwiftUI, UIKit modernization, Swift Testing, C bounds-safety, Xcode security hardening, and on-device verification.

> **Attribution**
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

The [`skills`](https://www.npmjs.com/package/skills) CLI auto-detects your agent (Claude Code, Codex, etc.) and installs into it. Point it at this repo with the `owner/repo` shorthand:

```sh
# Pick interactively from the list of skills:
npx skills add superagents-lab/xcode27-skills

# Install one specific skill:
npx skills add superagents-lab/xcode27-skills --skill swiftui-specialist

# Install all seven:
npx skills add superagents-lab/xcode27-skills --skill '*'
```

Useful flags: `--list` to preview the skills without installing, `-g`/`--global` to install at the user level instead of the current project, and `--copy` to copy files instead of symlinking. Swap in any skill name from the [table above](#skills).

> Requires Node. If `npx` is missing, install it first: `brew install node`.

### Option 2 — Manual install (any agent)

A skill is just a directory containing a `SKILL.md`, so any agent that supports the Agent Skills format can use it — clone the repo and copy the skill directories into wherever your agent looks for skills.

```sh
git clone https://github.com/superagents-lab/xcode27-skills.git

# Copy all seven skills, or just the ones you want, into your agent's skills directory:
cp -R xcode27-skills/*/ <your-skills-directory>/
cp -R xcode27-skills/swiftui-specialist <your-skills-directory>/
```

The agent auto-discovers any directory containing a `SKILL.md` and surfaces it when a task matches the skill's `description`.

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
