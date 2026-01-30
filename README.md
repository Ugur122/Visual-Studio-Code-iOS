# Code — Extensible Code Editor with Plugin System

**Code** is a lightweight, modern code editor built with Swift and SwiftUI, designed to be fully extensible through a custom plugin system.

The main goal of this project is to provide a flexible editor architecture where new features, languages, UI behaviors, and even application localizations can be added via external plugins — without rebuilding the core app.

---

## ✨ Features

- 🔌 Custom Plugin System (`.cex` packages)
- 🎨 Syntax Highlighting via Extensions
- ⌨️ Toolbar Shortcuts powered by Plugins
- 🧩 Language Support (Swift, C, C++, C#, JSON, HTML, CSS, JS via extensions)
- 🧠 Regex-based Highlighting Engine
- 📦 Zip-like Extension Package Format
- 🛠 Cursor control & smart insertion via plugins
- 📑 Line Numbers
- 🧩 Modular Editor Architecture
- 🍎 Built for iPhones with SwiftUI

---

## 📸 Screenshots

> Add your screenshots to the repository and update the paths below.

### Editor Overview
![Editor Overview](screenshots/editor.png)

### Plugin Manager
![Plugin Manager](screenshots/plugins.png)

### Toolbar Shortcuts
![Toolbar Shortcuts](screenshots/toolbar.png)

### Extension Info View
![Extension Info](screenshots/extension-info.png)

---

## Plugin System Overview

Plugins are distributed as `.cex` packages (zip-compatible) with the following structure:

MyExtension.cex
├─ extension.json
├─ icon.png
├─ description.md
├─ shortcuts.json
└─ highlight.json

Plugins can provide:

- Syntax highlighting rules
- Toolbar shortcut buttons
- Cursor movement & smart insertion
- Language definitions
- Metadata & documentation

---

## Plugin Developer Guide

### 1. extension.json

```json
{
  "schemaVersion": 1,
  "name": "My Language Support",
  "developer": "Your Name",
  "description": "Adds syntax highlighting and shortcuts",
  "price": 0,
  "type": "Highlighter",
  "canRemove": true,
  "permissions": ["Editor Access"],
  "icon": "icon.png",
  "readme": "description.md",
  "shortcuts": "shortcuts.json"
}
```

⸻

2. shortcuts.json
```json
[
  {
    "title": "()",
    "insertText": "()",
    "fileTypes": ["swift"],
    "cursorOffset": -1
  },
  {
    "title": "{}",
    "insertText": "{}",
    "fileTypes": ["swift"],
    "cursorOffset": -1
  }
]
```

⸻

3. highlight.json
```json
[
  {
    "pattern": "\\b(func|class|struct|enum|let|var)\\b",
    "colorHex": "systemBlue",
    "fileTypes": ["swift"]
  },
  {
    "pattern": "\"[^\"]*\"",
    "colorHex": "systemRed",
    "fileTypes": ["swift"]
  }
]
```

⸻

Plugin API Concepts

Cursor Control

Plugins can control cursor placement:
	•	cursorOffset = -1 → move cursor left
	•	cursorOffset = 0 → keep cursor at end
	•	cursorOffset = -N → move cursor N characters left

⸻

Permissions

Plugins declare required permissions:
	•	Editor Access
	•	File Access
	•	Network Access

Users must approve permissions before installation.

Why this project?

This editor is designed as a platform — not just an app.

The architecture allows developers to:
	•	Create new language support without touching the core
	•	Add syntax highlighting dynamically
	•	Extend the editor UI via plugins
	•	Provide full application localization via extensions
	•	Experiment with IDE features in a modular way

⸻

Roadmap
	•	Tree-sitter based highlighting
	•	Code completion plugins
	•	Debugger plugins
	•	Theme engine
	•	Plugin marketplace
	•	Multi-cursor support
	•	Snippet system

⸻

Status

This project is actively developed and experimental.
Breaking changes may occur as the plugin API evolves.

⸻

Contributing

Contributions are not allowed. If you havee any suggestions, contact me:
boramirakyurek21@icloud.com