<div align="center">

#  macOS Golden Gate

### A macOS-inspired desktop experience, running in your browser.

A high-fidelity web desktop simulation built with **React 18, TypeScript, Vite, and modern Web APIs**. Explore a familiar desktop environment with interactive windows, a responsive Dock, a multi-view Finder, system-style controls, media tools, and time-aware aerial wallpapers.

<p>
  <a href="https://macos.naishalpnadiya988.workers.dev/">
    <img src="https://img.shields.io/badge/LIVE_DEMO-Open_Desktop-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Open live demo" />
  </a>
  <img src="https://img.shields.io/badge/React-18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React 18" />
  <img src="https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript 5" />
  <img src="https://img.shields.io/badge/Vite-Build_Tool-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/SCSS-Modules-CC6699?style=for-the-badge&logo=sass&logoColor=white" alt="SCSS Modules" />
</p>

<p>
  <a href="https://macos.naishalpnadiya988.workers.dev/"><strong>Explore the live desktop →</strong></a>
</p>

<p><em>Recommended: use an up-to-date Chromium-based browser on a desktop for the fullest experience. Some features depend on browser support, permissions, and available hardware.</em></p>

</div>

---

## ✨ Overview

**macOS Golden Gate** reimagines the desktop operating-system experience as an interactive web environment. Instead of being a static landing page, it brings together window management, desktop utilities, app-style interfaces, keyboard shortcuts, media playback, and selected browser APIs in one cohesive UI.

The project focuses on three things:

- **A familiar desktop feel:** a menu bar, Dock, windows, app switcher, Mission Control, and Stage Manager-style multitasking.
- **Interactive applications:** Finder, Safari-style browsing UI, Terminal, Music, Photos, Notes, Calculator, System Settings, and more.
- **A polished visual system:** glass-like surfaces, animated transitions, aerial wallpapers, and responsive window interactions.

> **Note:** This is an independent browser-based simulation inspired by desktop UI patterns. It is not an actual macOS installation and is not affiliated with or endorsed by Apple Inc.

## 🚀 Quick Links

| Resource | Link |
| --- | --- |
| Live demo | [macOS Golden Gate](https://macos.naishalpnadiya988.workers.dev/) |
| Author's GitHub | [@naishal988](https://github.com/naishal988) |
| TypeScript | [Official documentation](https://www.typescriptlang.org/) |
| React | [Official documentation](https://react.dev/) |

## 📑 Table of Contents

- [Architecture at a Glance](#-architecture-at-a-glance)
- [Feature Highlights](#-feature-highlights)
  - [System and Power](#1-system-and-power)
  - [Aerial Wallpaper and Lock Screen](#2-aerial-wallpaper-and-lock-screen)
  - [Desktop, Dock, and Multitasking](#3-desktop-dock-and-multitasking)
  - [Finder](#4-finder)
  - [Spotlight and AI Assistant](#5-spotlight-and-ai-assistant)
  - [Media and Vision](#6-media-and-vision)
- [Built-in Applications](#-built-in-applications)
- [Technology Stack](#-technology-stack)
- [Performance Approach](#-performance-approach)
- [Browser Support and Permissions](#-browser-support-and-permissions)
- [Keyboard Shortcuts](#-keyboard-shortcuts)
- [Author](#-author)

---

## 🏛️ Architecture at a Glance

The desktop is organized as coordinated UI and application subsystems, with shared state helping windows and system controls respond consistently.

```text
┌──────────────────────────────────────────────────────────────────┐
│                         DESKTOP SHELL                            │
│        Menu Bar  ·  Notifications  ·  Control Center              │
├──────────────────────────────────────────────────────────────────┤
│                     WINDOW MANAGEMENT                            │
│      Focus & Z-Index  ·  Minimize / Maximize  ·  App Switching    │
├──────────────────────────────────────────────────────────────────┤
│                     DESKTOP APPLICATIONS                         │
│      Finder  ·  Browser  ·  Terminal  ·  Music  ·  Utilities      │
├──────────────────────────────────────────────────────────────────┤
│                    WEB API / MEDIA LAYER                          │
│       Battery API  ·  Audio  ·  Camera  ·  MediaPipe Vision       │
├──────────────────────────────────────────────────────────────────┤
│                   ASSETS & EDGE DELIVERY                          │
│          Static Assets  ·  Video Wallpapers  ·  CDN               │
└──────────────────────────────────────────────────────────────────┘
```

## ⚡ Feature Highlights

### 1. System and Power

- **Battery status integration:** reads battery level and charging information through the Web Battery API where the browser supports it.
- **Graceful fallback states:** handles unavailable or blocked battery information without making the desktop depend on that API.
- **Persistent Finder behavior:** Finder is treated as a core desktop process. Its relaunch flow is designed to feel closer to a system utility than an ordinary app window.
- **Boot and shutdown sequences:** includes an edge-to-edge startup animation and a dedicated shutdown screen with an interactive power control.

### 2. Aerial Wallpaper and Lock Screen

- **Aerial video backgrounds:** the lock screen can display looping 1080p aerial video assets.
- **Unlock transition:** transitions from video to a matching static wallpaper to reduce ongoing background media work during desktop use.
- **Time-aware atmosphere:** wallpaper variants are selected for different parts of the day.

  | Period | Time range | Visual mood |
  | --- | --- | --- |
  | Day | 06:00–16:30 | Bright aerial views |
  | Sunset | 16:30–18:30 | Warm golden-hour tones |
  | Evening | 18:30–20:30 | Twilight and illuminated structures |
  | Night | 20:30–06:00 | Dark skyline and night lighting |

- **Liquid-glass styling:** frosted typography, translucent controls, and layered backgrounds create a glass-like lock-screen design.
- **Window containment:** application windows are kept behind the lock-screen layer while the desktop is locked.

### 3. Desktop, Dock, and Multitasking

- **Responsive Dock magnification:** cursor proximity drives smooth icon scaling, with configurable icon sizing and auto-hide behavior.
- **Stage Manager-style layout:** inactive app windows can be grouped into side thumbnails while the focused app remains prominent.
- **Mission Control:** opens a spatial overview of running application windows.
- **Window states:** supports common minimize, maximize, hide, close, and focus transitions.
- **App switcher:** a keyboard shortcut brings up a visual switcher for running applications.

### 4. Finder

Finder includes four ways to browse its virtual file interface:

- **Icon View:** a free-grid layout with rounded icons and wrapped labels.
- **List View:** sortable columns for name, modified date, size, and file type.
- **Column View:** cascading folder columns with a selected-item inspector.
- **Gallery View:** a large preview area with a filmstrip for browsing items.

Additional Finder interactions include:

- Multi-tab browsing, including creating and closing tabs.
- A clickable breadcrumb path bar for navigating to parent folders.
- Selected-file previews and metadata where available.
- Sorting controls in List View.

### 5. Spotlight and AI Assistant

- **Spotlight-style search:** opens as a compact floating panel and expands as the user types.
- **Quick actions:** supports app launching, document lookup, and built-in calculations or unit conversions where implemented.
- **Type-to-assistant interface:** a menu-bar assistant UI with an animated gradient accent.
- **Natural-language app commands:** prompts such as `open calculator`, `launch safari`, or `start music` can trigger matching app actions.
- **Integrated assistant:** can answer portfolio, cybersecurity, and general technology questions when the configured assistant service is available.

### 6. Media and Vision

- **Music playback:** a shared HTML5 Audio controller keeps playback state synchronized between the Music app and the Control Center's Now Playing area.
- **Media search:** combines local assets with online search integrations, including YouTube Data API v3 and iTunes search where configured.
- **Picture-in-Picture-style mini-player:** the mini-player can remain available while the main Music window is closed.
- **Camera-based gesture effects:** MediaPipe Vision Tasks can recognize supported hand gestures and trigger visual reactions such as hearts, fireworks, rain, or thumbs-up/down.
- **Resource-aware camera lifecycle:** camera and vision processing can be paused when the relevant window is minimized to reduce unnecessary work.

## 📦 Built-in Applications

| Icon | Application | Highlights |
| --- | --- | --- |
|  | **Finder** | Icon, List, Column, and Gallery views; tabs; breadcrumb path bar |
| 🧭 | **Safari-style Browser** | Browser-inspired shell, bookmarks, and tabs |
| 💻 | **Terminal** | Interactive zsh-style interface with commands such as `whoami` and `projects` |
| 🎵 | **Music** | Playback controls, scrubbing, and supported online search integrations |
| 📹 | **FaceTime-style Camera** | Camera integration and supported AI gesture reactions |
| 🖼️ | **Photos** | Portfolio images, certificates, favorites, and metadata views |
| 🔑 | **Passwords** | Authenticator-style interface with 30-second timer visuals |
| ⚙️ | **System Settings** | Appearance, wallpaper, display, network, Bluetooth, and battery panels |
| 🧮 | **Calculator** | Responsive keypad and arithmetic operations |
| 📝 | **Notes** | Persistent notes and workspace scratchpads |

## 🧰 Technology Stack

| Layer | Technology | Role |
| --- | --- | --- |
| UI framework | React 18 | Component-based interface |
| Language | TypeScript 5 | Typed application logic and interfaces |
| State management | Jotai | Shared, atomic reactive state |
| Styling | SCSS Modules | Component-scoped styling and visual effects |
| Build tooling | Vite | Development server and production builds |
| Computer vision | MediaPipe Vision Tasks | Browser-based hand-gesture recognition |
| Media | HTML5 Audio and browser media APIs | Playback and media controls |
| Deployment | Cloudflare | Hosting and edge delivery for the live demo |

## 🚀 Performance Approach

The project uses a few strategies to keep the desktop responsive:

- **Load heavy features only when needed:** computer-vision modules can be dynamically imported rather than included in the initial application path.
- **Offload large media assets:** aerial videos and other large files can be served from dedicated CDN locations rather than bundled with application code.
- **Reduce background work:** the wallpaper can switch to a static image after unlock, and camera/vision processing can pause when not in use.
- **Tune visual effects during interaction:** expensive blur effects can be reduced during window dragging or resizing to help maintain smooth motion on integrated graphics.

Actual startup time, frame rate, and API availability vary by browser, device, network, and asset delivery conditions.

## 🌐 Browser Support and Permissions

For the best experience, use a modern desktop browser with hardware acceleration enabled. Depending on your browser and device, some capabilities may be unavailable or behave differently.

- **Camera features:** require camera permission and a secure context such as HTTPS or localhost.
- **Battery information:** the Web Battery API is not supported in every browser and may be restricted for privacy reasons.
- **Online media search:** may depend on external APIs, network access, API configuration, and CORS behavior.
- **Keyboard shortcuts:** browser or operating-system shortcuts may take priority over in-page shortcuts.

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| --- | --- |
| `Cmd + Tab` | Open the app switcher |
| `Cmd + Q` | Quit or close the focused app through the desktop's app lifecycle |
| `Cmd + W` | Close the active window while keeping the app's running state where supported |
| `Cmd + M` | Minimize the active window to the Dock |
| `Cmd + H` | Hide the application's windows |
| `Cmd + T` | Open a new Finder tab |
| `Cmd + Space` | Open Spotlight-style search |
| `F3` | Open Mission Control |

Shortcut handling may vary across browsers and operating systems. Some combinations may be reserved by the browser or host OS.

## 👤 Author

**Naishal Nadiya**  
Cybersecurity student and software developer

- **GitHub:** [@naishal988](https://github.com/naishal988)
- **Live project:** [macOS Golden Gate](https://macos.naishalpnadiya988.workers.dev/)

---

<div align="center">

**Built with curiosity, code, and a love for desktop UI.**

<sub>macOS Golden Gate is an independent fan-made project for learning and demonstration purposes.</sub>

</div>
