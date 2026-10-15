<div align="center">

#  macOS Golden Gate

**A High-Fidelity, Production-Grade Web Desktop Operating System Built with React 18, TypeScript & Web APIs**

[![Live Demo](https://img.shields.io/badge/Live_Demo-Cloudflare_Pages-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://github.com/naishal988)
[![React](https://img.shields.io/badge/React_18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript_5-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite_Bundler-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![SCSS](https://img.shields.io/badge/Sass_Modules-CC6699?style=for-the-badge&logo=sass&logoColor=white)](https://sass-lang.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

<br />

<p align="center">
  macOS Golden Gate is an architecture-grade web recreation of Apple's desktop operating system running directly inside modern web browsers. Engineered beyond traditional static web portfolios, it features authentic system lifecycle daemons, true window state machines, hardware Web Battery synchronization, an intelligent aerial video wallpaper engine, and an interactive Apple Intelligence Siri controller.
</p>

</div>

---

## 📑 Table of Contents

- [Architectural Overview](#-architectural-overview)
- [System Highlights & Features](#-system-highlights--features)
  - [Hardware & System Subsystems](#1-hardware--system-subsystems)
  - [Dynamic Aerial Wallpaper & Lock Screen](#2-dynamic-aerial-wallpaper--lock-screen)
  - [Desktop, Dock & Multitasking (Levels 1–3)](#3-desktop-dock--multitasking-levels-13)
  - [Advanced Finder Architecture (Level 4)](#4-advanced-finder-architecture-level-4)
  - [Apple Intelligence & Spotlight Universal Search (Level 5)](#5-apple-intelligence--spotlight-universal-search-level-5)
  - [Media & Vision Subsystems (Apple Music & FaceTime)](#6-media--vision-subsystems)
- [Core Application Suite](#-core-application-suite)
- [Tech Stack & Architecture](#-tech-stack--architecture)
- [Performance & Cloudflare Optimizations](#-performance--cloudflare-optimizations)
- [Author & Credits](#-author--credits)

---

## 🏛️ Architectural Overview

Most web-based desktop clones operate as shallow presentation layers consisting of a few draggable `div` wrappers. **macOS Golden Gate** is architected as an in-browser operating system shell driven by centralized reactive state machines:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        macOS Shell Layer                               │
│  Top Menu Bar  │  Dynamic Island / Notifications  │  Control Center   │
├────────────────────────────────────────────────────────────────────────┤
│                     Window Management Subsystem                        │
│  Process Lifecycle (PID)  │  Z-Index Stacking  │  Stage Manager Mesh   │
├────────────────────────────────────────────────────────────────────────┤
│                       Hardware & Web API Layer                         │
│  Web Battery API  │  Hardware Fallback Plug  │  MediaPipe Vision Pipe  │
│  Audio Singleton  │  Time-Phased Aerial Engine  │  CORS-Resilient CDN  │
└────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ System Highlights & Features

### 1. Hardware & System Subsystems
- **Native Web Battery API Integration**: Reads client battery capacity, charging states, and discharging time in real time via `navigator.getBattery()`.
- **Privacy Shield / AC Power Fallback**: Gracefully detects privacy browsers (such as Brave with fingerprint protection enabled) or AC-powered desktops without throwing unhandled exceptions, rendering the authentic Apple Power Adapter (🔌) glyph.
- **Permanent Finder Process Daemon**: Emulates the native macOS Unix shell lifecycle. Finder can never be killed—`Cmd + Q` is protected, the Dock running dot is permanently active, and the Force Quit modal provides a native **"Relaunch"** mechanism rather than killing the process.
- **Cinematic Boot & Physical Shutdown Sequence**:
  - Fullscreen edge-to-edge hardware cable insertion sequence (`mac_boot.mp4`) transitioning into the Apple progress bar.
  - Deep-ambient shutdown screen featuring a realistic dark Mac Mini hardware view with an interactive, breathing LED power button (⏻) that reloads and boots the machine fresh upon click.

---

### 2. Dynamic Aerial Wallpaper & Lock Screen
- **macOS Sonoma / Tahoe Aerial Engine**:
  - While on the Lock Screen, smooth 1080p aerial video loops continuously in the background via dedicated high-speed CDN assets.
  - Upon unlocking, the video engine smoothly settles and cross-fades over 2.2 seconds into a matching 4K static photograph, dropping GPU and CPU consumption to 0% during active desktop work.
- **Time-of-Day 4-Phase Chronometer**:
  - **Day (06:00 – 16:30)**: Golden Gate Day aerial stream & static backdrop.
  - **Sunset (16:30 – 18:30)**: Warm amber golden-hour lighting.
  - **Evening (18:30 – 20:30)**: Twilight dusk with illuminated bridge cables.
  - **Night (20:30 – 06:00)**: Deep night skyline with illuminated architectural lighting.
- **Liquid Glassmorphism Lock Screen**:
  - Authentic 12-hour rounded frosted typography with ambient background refraction.
  - Translucent password pill container with interactive Touch ID / Enter prompt.
  - Full window containment guard ensuring running background application windows never leak through the transparent lock screen.

---

### 3. Desktop, Dock & Multitasking (Levels 1–3)
- **Fluid Dock Animation**: Cosine-wave magnification physics with customizable sizing (40px–70px) and smooth auto-hide behaviors.
- **Stage Manager**: Side-docking inactive application sets into live reactive thumbnail piles while isolating the focused active window.
- **Mission Control (`F3`)**: Exposes all running application windows across an unoccluded spatial grid.
- **Native Keyboard Shortcuts**:
  - `Cmd + Tab`: macOS App Switcher HUD.
  - `Cmd + Q`: Force-terminates focused application process.
  - `Cmd + W`: Closes window DOM while maintaining running state in memory.
  - `Cmd + M`: Minimizes active window directly into the Dock.
  - `Cmd + H`: Hides application windows without quitting.

---

### 4. Advanced Finder Architecture (Level 4)
- **4 Segmented View Modes**:
  1. **Icon View**: Free-grid macOS squircle file arrangements with label wrapping.
  2. **List View**: Sortable tabular view featuring Name, Date Modified, Size, and Kind with ascending/descending toggles.
  3. **Miller Columns View**: Classic Apple cascading column layout with horizontal auto-scroll and detailed Inspector preview metadata for selected files.
  4. **Gallery View**: Large centered preview canvas with an interactive bottom filmstrip.
- **Multi-Tab Browsing (`Cmd + T`)**: Native tab bar supporting tab creation, drag-and-drop between tabs, and single-tab closure (`Cmd + W`).
- **Interactive Path Bar (Breadcrumbs)**: Bottom-mounted interactive breadcrumb hierarchy (`Macintosh HD › Users › naishal › Documents`) allowing one-click upward navigation.

---

### 5. Apple Intelligence & Spotlight Universal Search (Level 5)
- **Spotlight Universal Search (`Cmd + Space`)**:
  - Opens as a compact 52px floating frosted glass pill; dynamically expands downward only when user query input begins.
  - Instant App launcher, document locator, and built-in math calculation & unit conversion evaluator.
- **Apple Intelligence (Type to Siri)**:
  - Anchored in the top-right menu bar as a minimalist liquid glass pill with an animated glowing multi-color gradient border.
  - Natural Language Intent Parser: Typing commands like *"open calculator"*, *"launch safari"*, or *"start music"* immediately executes window dispatch actions.
  - Integrated LLM Assistant capable of answering portfolio, cybersecurity, and general technology queries.

---

### 6. Media & Vision Subsystems
- **Apple Music Engine**:
  - Singleton HTML5 Audio controller managing synchronized playback across the standalone app and the Control Center Now Playing card.
  - Integrated multi-tier search engine supporting both local assets and online streaming queries.
  - Floating Picture-in-Picture (PiP) mini-player supporting window closure without terminating audio sessions.
- **FaceTime with Computer Vision Gestures**:
  - Real-time gesture recognition (Hearts, Fireworks, Rain, Thumbs-up/down) powered by MediaPipe.
  - Performance-throttled at 30 FPS with complete camera and worker shutdown on minimize to prevent frame drops.

---

## 📦 Core Application Suite

| Icon | Application | Highlights |
| :---: | :--- | :--- |
|  | **Finder** | 4 view modes (Miller Columns, Gallery, List, Icons), tabs, path bar |
| 🧭 | **Safari** | Functional browser shell with bookmarks, security sandbox, and tabs |
| 💻 | **Terminal** | Interactive zsh-style shell with portfolio commands (`whoami`, `projects`) |
| 🎵 | **Apple Music** | Full playback engine, audio scrubbers, and live online search |
| 📹 | **FaceTime** | Camera integration with AI hand-gesture reactions (30 FPS capped) |
| 🖼️ | **Photos** | Portfolio certificates, image inspector, favorites, and metadata |
| 🔑 | **Passwords** | macOS Sequoia style 2FA authenticator with live 30s circular timers |
| ⚙️ | **System Settings** | Displays, Wallpapers, Network, Bluetooth, Battery, and Appearance |
| 🧮 | **Calculator** | Responsive, symmetric Apple keypad with operator tracking |
| 📝 | **Notes** | Persistent desktop sticky notes and architectural scratchpads |

---

## 🛠️ Tech Stack & Architecture

- **Core Framework**: React 18 / Preact (High-performance virtual DOM rendering)
- **Language**: TypeScript 5 (Strict type safety, custom interfaces)
- **State Architecture**: Jotai (Atomic state, decoupled reactive process stores)
- **Styling**: SCSS Modules (Liquid glassmorphism, GPU-accelerated backdrop filters)
- **Vision AI**: MediaPipe Vision Tasks (Throttled WebAssembly worker)
- **Build System**: Vite (ESM-based HMR, Rollup manual chunking)
- **Hosting & Edge Delivery**: Cloudflare Pages + GitHub Releases CDN for large binary assets

---

## 🚀 Performance & Cloudflare Optimizations

1. **Asset Offloading**:
   - High-bitrate 1080p MP4 aerial video streams are served through direct CDN binary releases, preserving a zero-cost, ultra-fast initial site load on Cloudflare Pages free tier.
2. **Heavy Engine Quarantine**:
   - Computer Vision (`@mediapipe/tasks-vision`) and complex sub-modules are strictly lazy-loaded via dynamic `import()`, ensuring initial JavaScript execution time remains under 250ms.
3. **GPU Compositing & Interaction Smoothing**:
   - Heavy CSS `backdrop-filter: blur(40px)` layers dynamically step down during rapid window dragging and resizing gestures to guarantee smooth 60 FPS performance on integrated graphics hardware.

---

## 👤 Author & Credits

**Naishal Nadiya**  
*Cybersecurity Researcher & Full-Stack Software Engineer*

- **GitHub**: [@naishal988](https://github.com/naishal988)
- **LinkedIn**: [Naishal Nadiya](https://www.linkedin.com/in/naishal-nadiya-791333333/)
- **Project Repository**: `naishal988/macos-assets` / `Macos-Based-portfolio`

---

<div align="center">
  <sub>Engineered with precision to recreate the authentic feel of macOS in the modern browser.</sub>
</div>
