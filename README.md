# Zed Next

<p align="center">
  <strong>A new interface for the Zed editor.</strong>
  <br />
  <sub>Native performance. Modern UX. Extensible by design.</sub>
</p>

<p align="center">
  <a href="https://github.com/zed-industries/zed">
    <img src="https://img.shields.io/badge/based%20on-Zed-111111?style=flat-square" alt="Based on Zed" />
  </a>
  <img src="https://img.shields.io/badge/status-experimental-orange?style=flat-square" alt="Experimental" />
  <img src="https://img.shields.io/badge/UI-GPUI-blue?style=flat-square" alt="GPUI" />
  <img src="https://img.shields.io/badge/language-Rust-dea584?style=flat-square" alt="Rust" />
</p>

<p align="center">
  <a href="#vision">Vision</a>
  ·
  <a href="#architecture">Architecture</a>
  ·
  <a href="#webview">WebView</a>
  ·
  <a href="#roadmap">Roadmap</a>
  ·
  <a href="#development">Development</a>
</p>

---

## Overview

**Zed Next** is an experimental fork of [Zed](https://github.com/zed-industries/zed) focused on rethinking the editor interface from the ground up.

The project preserves Zed's high-performance native editor foundation while exploring a new UI/UX architecture designed around composability, customization, and extensibility.

> **Keep the engine. Reimagine the experience.**

Zed Next is not an attempt to replace Zed's editor engine. It is an exploration of what the Zed experience could become with a fundamentally different interface.

---

## Vision

Modern development environments are becoming more than text editors.

They are increasingly composed of:

* editors
* terminals
* previews
* documentation
* AI interfaces
* dashboards
* browser-based tools
* development servers
* interactive extensions

Zed Next explores an architecture where these experiences can coexist naturally inside a single workspace.

```text
┌────────────────────────────────────────────────────────────┐
│                        Zed Next                             │
├──────────────────────┬─────────────────────────────────────┤
│                      │                                     │
│       Sidebar        │            Workspace                │
│                      │                                     │
│   Explorer           │   ┌─────────┬─────────┬─────────┐   │
│   Search             │   │ Editor  │ Preview │ WebView │   │
│   Git                │   └─────────┴─────────┴─────────┘   │
│   Extensions         │                                     │
│                      │                                     │
├──────────────────────┴─────────────────────────────────────┤
│ Terminal                 Problems              AI          │
└────────────────────────────────────────────────────────────┘
```

The goal is a workspace that feels native while remaining flexible enough to host richer interactive experiences.

---

## What We're Building

### Native UI

The primary interface is built with **GPUI**, keeping the application fast, responsive, and deeply integrated with the native editor.

The new UI architecture focuses on:

* Workspace composition
* Flexible layouts
* Panels and docks
* Tabs
* Command-driven navigation
* Keyboard-first interaction
* Consistent design tokens
* Customizable themes
* Reusable UI components

### Web Experiences

Zed Next also explores a first-class WebView layer for interfaces that benefit from HTML, CSS, and JavaScript.

Potential applications include:

* Web previews
* Browser panels
* HTML/CSS previews
* React, Vue, and Svelte applications
* DevTools
* OAuth and authentication flows
* AI interfaces
* Interactive documentation
* Web-based extensions
* Local development previews

The long-term goal is to make native and web interfaces feel like parts of the same application rather than separate worlds.

---

## Architecture

Zed Next is designed around three complementary layers:

```text
                         Zed Next
                            │
             ┌──────────────┼──────────────┐
             │              │              │
          Native UI       Core           Web UI
             │              │              │
            GPUI       Zed Services       WebView
             │              │              │
       ┌─────┼─────┐   ┌────┼─────┐   ┌───┴────┐
       │     │     │   │    │     │   │        │
    Panels  Tabs  UX  Editor LSP  Git React   HTML
                       Terminal     AI   Vue    CSS
```

### Core

The existing Zed foundation remains responsible for the heavy lifting:

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

### Native UI

The new UI layer provides:

* Workspace
* Sidebar
* Tabs
* Panels
* Toolbars
* Command palette
* Status bar
* Themes
* Navigation
* UI components

### Web UI

The WebView layer provides a foundation for:

* HTML/CSS/JavaScript interfaces
* Application previews
* Rich AI experiences
* Web-based extensions
* Interactive tools

---

## WebView

One of the long-term goals is a platform-independent WebView abstraction that can become a first-class workspace item.

The intended API is conceptually simple:

```rust
let webview = WebView::new("https://example.com");

workspace.open(webview);
```

A WebView could eventually expose capabilities such as:

```rust
webview.load_url("http://localhost:3000");

webview.reload();

webview.execute_script(
    "window.zed.refresh()"
);
```

And provide communication between JavaScript and the native application:

```text
        Web Application
               │
          JavaScript
               │
               ▼
        ┌─────────────┐
        │   WebView   │
        │    Bridge   │
        └──────┬──────┘
               │
          Rust / Zed
               │
       ┌───────┼────────┐
       │       │        │
    Editor   Project   Workspace
```

The WebView implementation is intentionally designed as an abstraction so that the underlying browser technology can evolve independently.

---

## Design Principles

### Native First

Use GPUI and native rendering where performance, interaction, and editor integration matter most.

### Composable

UI should be built from reusable primitives rather than tightly coupled screens.

### Keyboard First

Every important workflow should remain accessible without reaching for the mouse.

### Extensible

The architecture should make it possible to add new panels, views, tools, and web-powered experiences without rewriting the workspace.

### Performance Conscious

New UI capabilities should preserve the responsiveness and performance characteristics expected from Zed.

### Progressive Architecture

Large architectural changes should be introduced incrementally rather than through a single destructive rewrite.

---

## Roadmap

### Phase 1 · UI Foundation

* [ ] Design system
* [ ] UI component library
* [ ] New workspace shell
* [ ] Sidebar
* [ ] Tabs
* [ ] Panels
* [ ] Layout system
* [ ] Theme system

### Phase 2 · Core Integration

* [ ] Editor integration
* [ ] File explorer
* [ ] Search
* [ ] Git
* [ ] Terminal
* [ ] Command palette
* [ ] Keymap integration
* [ ] Workspace state

### Phase 3 · WebView

* [ ] WebView abstraction
* [ ] Native surface integration
* [ ] Pane integration
* [ ] Navigation
* [ ] JavaScript execution
* [ ] Native ↔ JavaScript bridge
* [ ] DevTools

### Phase 4 · Web Experiences

* [ ] Local development previews
* [ ] React/Vue/Svelte previews
* [ ] AI interfaces
* [ ] Web-based extensions
* [ ] Interactive documentation

### Phase 5 · Extensibility

* [ ] Custom workspace layouts
* [ ] UI extensions
* [ ] Web/native hybrid extensions
* [ ] UI scripting
* [ ] Advanced customization

---

## Development

Zed Next is built with Rust and currently follows the upstream Zed development environment.

### Prerequisites

Install the dependencies required by your platform and Rust toolchain.

See the upstream development documentation:

* [macOS development](https://github.com/zed-industries/zed/blob/main/docs/src/development/macos.md)
* [Linux development](https://github.com/zed-industries/zed/blob/main/docs/src/development/linux.md)
* [Windows development](https://github.com/zed-industries/zed/blob/main/docs/src/development/windows.md)

### Build

```bash
cargo check
```

For development builds, follow the platform-specific instructions in the upstream documentation.

---

## Contributing

Zed Next is an experimental project.

Architecture and APIs may change substantially while the project evolves.

Before submitting a large architectural change, please open an issue or discussion to establish the direction first.

Small improvements, bug fixes, documentation, experiments, and design proposals are welcome.

---

## Relationship to Zed

Zed Next is derived from the open-source [Zed](https://github.com/zed-industries/zed) project.

Zed provides the foundation for the editor, rendering infrastructure, language tooling, collaboration, and other core functionality.

Zed Next focuses primarily on exploring a different interface and extensibility model on top of that foundation.

---

## License

Zed Next is derived from Zed and remains subject to the applicable upstream licensing terms.

Zed source code is licensed primarily under **GPL-3.0-or-later**, with Apache-2.0 components where indicated.

Third-party dependency licenses must also be preserved in accordance with the requirements of the respective projects.

See the repository license files and upstream Zed project for complete licensing information.

---

## Acknowledgements

Zed Next would not exist without the work of the Zed team and the open-source community.

Special thanks to the creators and contributors of:

* [Zed](https://github.com/zed-industries/zed)
* [GPUI](https://github.com/zed-industries/zed/tree/main/crates/gpui)
* [Tree-sitter](https://github.com/tree-sitter/tree-sitter)
* [Atom](https://github.com/atom/atom)

---

<p align="center">
  <sub>Built on Zed. Reimagined for what's next.</sub>
</p>
