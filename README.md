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

## Structure

Each skill is a directory containing a `SKILL.md` (with YAML frontmatter — `name`, `description`, etc.) and optional `references/` and `scripts/` subdirectories that the agent loads on demand.

```
<skill-name>/
├── SKILL.md          # entry point + metadata
├── references/       # detailed docs loaded as needed
└── scripts/          # helper scripts (where present)
```

## Usage

These skills are designed to be discovered by coding agents that support the Agent Skills format. To use them with Claude Code, place a skill directory under your skills path (for example `~/.claude/skills/`) or a project's `.claude/skills/`, and the agent will surface it when the task matches the skill's `description`.
