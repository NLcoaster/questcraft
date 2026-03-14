# ⛏ QuestCraft

> A visual NPC dialog tree editor for Minecraft — build branching conversations with a flowchart interface and export directly to Bedrock or Java Edition.

![Version](https://img.shields.io/badge/version-0.0.1-green)
![Platform](https://img.shields.io/badge/platform-Browser-blue)
![License](https://img.shields.io/badge/license-GPL--3.0-blue)

---

## ✨ Features

### 🗺 Visual Flowchart Editor
- Drag nodes from the sidebar onto the canvas, or click to place them at the center
- Connect nodes by dragging from an output port to an input port
- Pan the canvas by clicking and dragging on empty space
- Zoom with the scroll wheel or the zoom controls
- Snap-to-grid positioning (10px grid)
- Fit all nodes into view with one click

### 📦 Node Types

| Node | Description |
|------|-------------|
| 💬 **Dialog** | An NPC says something. Assign an NPC and write text per language. |
| 🔀 **Choice** | The player picks from multiple options. Each option has its own output port. |
| ⚡ **Condition** | Checks a variable. Green port = true, red port = false. |
| ⚙ **Action** | Runs something in the background: give/take items (with amount), play sounds, set variables, or run commands. |
| ↗ **Jump** | Jumps directly to another node — useful for avoiding repetition. |
| ⏹ **End** | Closes the conversation. |

### 🌐 Multilingual Dialog
- Add any number of languages to your project (NL, EN, DE, FR, and 40+ more)
- Language tabs on every node — switch between languages with one click
- Translation status indicator per language (green = filled, red = missing)
- **Auto-translate** button per node or per language using:
  - [LibreTranslate](https://libretranslate.com) (free, default)
  - Google Translate API (requires API key)
  - Anthropic Claude API (best quality, requires API key)

### 🧑 NPC Management
- Add, rename and delete NPCs with custom colors
- Click an NPC in the sidebar to **filter the canvas** — nodes from other NPCs are dimmed
- Each dialog and choice node can be assigned to a specific NPC

### 💾 Save & Load
- Save as `.npcproj` (recommended), `.json`, or `.yaml`
- Load any previously saved file
- **Auto-save** option (1, 5, or 10 minute intervals)
- Keyboard shortcut: `Ctrl+S`

### ⬇ Export to Minecraft

#### Bedrock Edition (.mcaddon)
- Generates a `scenes.json` with NPC dialogue scenes
- Generates `.lang` files for every project language (e.g. `nl_NL.lang`, `en_US.lang`)
- Generates a `manifest.json` for the behavior pack
- Minecraft automatically picks the player's language — no extra setup needed
- Double-click the `.mcaddon` file to import into Minecraft

#### Java Edition (BetonQuest YAML)
- Generates a `.yml` conversation file compatible with [BetonQuest](https://betonquest.org)
- Multi-language keys (`text_nl`, `text_en`, etc.) — BetonQuest picks the player's language automatically
- Copy to `plugins/BetonQuest/conversations/` and run `/bq reload`

### 🔍 Preview Mode
- Simulate the conversation as a player
- Click through dialog and choice nodes
- Switch between languages in real time
- Shows which nodes are not yet connected

### { } JSON Viewer
- Live preview of your project data with node statistics and translation status
- Switch to raw JSON editor — edit and apply changes directly
- Copy the full JSON to clipboard

### ♾ Loop Detection
- Automatically detects when a new connection would create an infinite loop
- Shows a warning toast with the option to connect anyway (useful for "return to menu" patterns)

### ✂ Delete Connections
- Hover over any connection line to reveal a scissors button
- Click to remove the connection
- Undo with `Ctrl+Z`

---

## ⚙ Settings

Open with the `⚙` button in the top bar.

| Setting | Options |
|---------|---------|
| **Theme** | Dark (default) / Light |
| **Canvas background** | Dots (default) / Grid / None |
| **UI language** | NL, EN, DE, FR, SV, NB, DA, FI, IS |
| **Translation provider** | LibreTranslate (default), Google Translate, Anthropic Claude |
| **API key** | For Google or Anthropic translation |
| **Default export format** | Bedrock / Java |
| **Auto-save interval** | Off / 1 min / 5 min / 10 min |

All settings are saved in your browser's `localStorage`.

---

## ⌨ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Ctrl+S` | Save |
| `Delete` | Delete selected node |
| `F1` | Open help menu |
| `Scroll` | Zoom in / out |

---

## 🚀 Getting Started

QuestCraft is a **single HTML file** — no installation, no dependencies, no server needed.

1. Download `questcraft.html`
2. Open it in any modern browser (Chrome, Firefox, Edge)
3. Drag elements from the sidebar onto the canvas
4. Connect nodes by dragging from output ports to input ports
5. Fill in dialog text per language in the right panel
6. Click **⬇ Exporteer** to export to Minecraft

---

## 🎮 Supported Minecraft Versions

| Version | Support |
|---------|---------|
| **Bedrock Edition** | ✅ Native `.mcaddon` export |
| **Java Edition** | ✅ BetonQuest YAML export |
| **Both (via Geyser)** | ✅ Use Java export with Geyser bridge |

---

## 🌍 Supported Languages (UI)

🇳🇱 Nederlands · 🇬🇧 English · 🇩🇪 Deutsch · 🇫🇷 Français · 🇸🇪 Svenska · 🇳🇴 Norsk · 🇩🇰 Dansk · 🇫🇮 Suomi · 🇮🇸 Íslenska

---

## 🔧 Translation Providers

### LibreTranslate (Default — Free)
No API key needed. Uses the public LibreTranslate endpoint. You can also [self-host](https://github.com/LibreTranslate/LibreTranslate) it.

### Google Translate
Requires a [Google Cloud API key](https://cloud.google.com/translate). Works directly from the browser (no CORS issues). Pay-per-use pricing.

### Anthropic Claude
Requires an [Anthropic API key](https://console.anthropic.com). Best translation quality for natural NPC dialog. Enter your key in ⚙ Settings — it is stored locally in your browser and never shared.

> ⚠ **Note:** When using an API key, do not share your `questcraft.html` file or the browser's localStorage publicly.

---

## 📁 Bedrock Export Structure

After exporting, put the files into this folder structure and zip it as `.mcaddon`:

```
YourProject.mcaddon
└── behavior_pack/
    ├── manifest.json
    ├── dialogue/
    │   └── yourproject_scenes.json
    └── texts/
        ├── nl_NL.lang
        ├── en_US.lang
        └── ...
```

---

## 🗺 Roadmap

- [ ] Multiple canvases per project (one per NPC or quest line)
- [ ] Real `.mcaddon` zip download (JSZip)
- [ ] More action types (XP, effects, teleport)
- [ ] Citizens plugin export (Java)
- [ ] Denizen script export (Java)
- [ ] Import from existing BetonQuest YAML

---

## 📄 License

[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html) — you are free to use, modify and distribute QuestCraft, but any modified versions must also be released under GPL 3.0 and remain open source.

---

*Made with help of Claude.ai*
