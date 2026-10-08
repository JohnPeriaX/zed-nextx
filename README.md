# Zed Next

> A reimagined Zed experience with a new UI/UX architecture, native performance, and an extensible WebView foundation.

Zed Next is an experimental fork of [Zed](https://github.com/zed-industries/zed) focused on rethinking the editor experience from the ground up while preserving the high-performance editor core that makes Zed special.

The goal is simple:

**Keep the engine. Reimagine the experience.**

---

## ✨ Vision

Zed Next explores a new approach to the modern code editor:

* 🎨 A completely redesigned UI/UX
* ⚡ Native, GPU-accelerated interfaces powered by GPUI
* 🧩 A modular workspace and panel architecture
* ⌨️ Keyboard-first workflows
* 🎛️ Highly customizable layouts and themes
* 🌐 First-class WebView integration
* 🤖 Rich AI interfaces
* 👀 Built-in web and application previews
* 🔌 Extensible UI surfaces for future plugins and extensions

The long-term goal is to make native UI and web-based UI work together seamlessly inside the editor.

```text
                         Zed Next
                            │
              ┌─────────────┴─────────────┐
              │                           │
           Native UI                   Web UI
             GPUI                    WebView
              │                           │
       ┌──────┴──────┐              ┌─────┴─────┐
       │             │              │           │
    Editor        Workspace       React       HTML
    Terminal      Panels          Vue         CSS
    Sidebar       Commands        Svelte      JS
       │             │              │           │
       └─────────────┴──────────────┴───────────┘
                            │
                       Zed Core
```

---

## 🚧 Status

**Experimental / Early Development**

This project is actively exploring a new UI architecture on top of Zed's existing editor core.

Things will change.

APIs, layouts, components, and internal architecture may change significantly while the project evolves.

---

## 🏗️ Architecture

Zed Next aims to separate the editor's core functionality from its user interface.

### Zed Core

The existing Zed engine continues to provide the underlying functionality:

* Editor
* Buffers
* Projects
* LSP
* Git
* Terminal
* Search
* Diagnostics
* File system
* Language tooling
* Collaboration

### New UI Layer

The new UI layer is responsible for:

* Workspace layout
* Sidebar
* Tabs
* Panels
* Command palette
* Toolbars
* Status bar
* Themes
* Navigation
* UI components

The UI is built using **GPUI** and is designed to evolve independently from the editor core.

---

## 🌐 WebView

One of the long-term goals of Zed Next is to provide a first-class WebView abstraction.

For example:

```rust
let webview = WebView::new(
    "https://example.com"
);
```

A WebView could eventually live directly inside a Zed pane:

```text
┌─────────────────────────────────────────────┐
│ Editor │ Preview │ Browser │ AI              │
├─────────────────────────────────────────────┤
│                                             │
│              WebView                        │
│                                             │
│        https://example.com                  │
│                                             │
└─────────────────────────────────────────────┘
```

Potential use cases include:

* Browser panels
* Web previews
* HTML/CSS previews
* React/Vue/Svelte applications
* DevTools
* OAuth and authentication interfaces
* Web-based extension interfaces
* AI interfaces
* Interactive documentation
* Local development servers

The WebView layer is intended to remain backend-independent so that different native implementations can be explored in the future.

---

## 🎯 Project Goals

### UI/UX

Build a modern editor interface that is:

* Minimal
* Fast
* Keyboard-first
* Customizable
* Responsive
* Composable

### Performance

Preserve the performance characteristics of Zed and GPUI.

The new UI should not sacrifice native performance simply to make customization easier.

### Extensibility

Create clear boundaries between:

```text
Core
  │
  ├── Editor
  ├── Project
  ├── Terminal
  ├── Git
  └── LSP

UI
  │
  ├── Workspace
  ├── Panels
  ├── Components
  └── Themes

Web
  │
  ├── WebView
  ├── JavaScript
  └── Web UI
```

---

## 🛣️ Roadmap

### Phase 1 · New UI Foundation

* [ ] New design system
* [ ] New UI components
* [ ] New workspace shell
* [ ] New sidebar
* [ ] New tabs
* [ ] New panels
* [ ] New theme system

### Phase 2 · Core Integration

* [ ] Editor integration
* [ ] File explorer
* [ ] Search
* [ ] Git
* [ ] Terminal
* [ ] Command palette
* [ ] Keymap integration

### Phase 3 · WebView

* [ ] WebView abstraction
* [ ] Native surface integration
* [ ] Pane integration
* [ ] Navigation API
* [ ] JavaScript execution
* [ ] Rust ↔ JavaScript bridge
* [ ] DevTools integration

### Phase 4 · Web-powered Experiences

* [ ] React/Vue/Svelte previews
* [ ] AI UI
* [ ] Web-based extensions
* [ ] Interactive documentation
* [ ] Application previews

### Phase 5 · Long-term Exploration

* [ ] Advanced workspace layouts
* [ ] Custom UI plugins
* [ ] UI scripting
* [ ] Web/native hybrid extensions

---

## 💻 Development

Zed Next currently follows the development requirements and build process of upstream Zed.

### Building on macOS

See:

[Building Zed for macOS](./docs/src/development/macos.md)

### Building on Linux

See:

[Building Zed for Linux](./docs/src/development/linux.md)

### Building on Windows

See:

[Building Zed for Windows](./docs/src/development/windows.md)

---

## 🤝 Contributing

This project is experimental and welcomes exploration, experimentation, and architectural discussion.

Before making large changes, please consider opening an issue or discussion so that architectural decisions can be discussed before implementation.

---

## 🙏 Credits

Zed Next is based on [Zed](https://github.com/zed-industries/zed), created by Zed Industries and the creators of Atom and Tree-sitter.

This project would not exist without the work of the Zed team and the open-source community.

Upstream project:

https://github.com/zed-industries/zed

---

## 📜 Licensing

Zed Next is derived from Zed and remains subject to the licensing terms of the upstream project.

Zed source code is licensed primarily under **GPL-3.0-or-later**, with Apache-2.0 components where marked.

License information for third-party dependencies must be correctly maintained.

See the upstream project and repository license files for complete licensing information.

---

## 🌱 Why Zed Next?

Zed proved that a code editor can be fast, native, collaborative, and beautiful.

Zed Next explores a different question:

> **What happens if we keep that engine, but completely rethink the interface around it?**

That's what this project is about.
