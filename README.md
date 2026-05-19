<div id="top"></div>

<!-- PROJECT SHIELDS -->

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![GNU License][license-shield]][license-shield-url]
[![Python Version][python-shield]][python-url]
[![Blender Versions][blender-shield]][blender-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <h1 align="center">🎹 MIDIAnimator</h1>
  <p align="center">
    Procedurally animate 3D instruments using MIDI files in Blender.
    <br>
    <strong>Works with Blender 3.0, 4.0, and 5.0</strong>
  </p>
  <h3><a href="#future-of-midianimator">⚠️ Read Updates About Rust Rewrite 🚧</a></h3>
  <br>
  <a href="https://midianimatordocs.readthedocs.io/"><strong>📖 Explore the Docs</strong></a>
  ·
  <a href="https://github.com/imacj/MIDIAnimator/issues">🐛 Report Bug</a>
  ·
  <a href="https://github.com/imacj/MIDIAnimator/issues">✨ Request Feature</a>
</div>

---

## 📋 Table of Contents

1. [About The Project](#about-the-project)
2. [Features](#features)
3. [Quick Start](#quick-start)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Project Structure](#project-structure)
7. [Tech Stack](#tech-stack)
8. [Roadmap](#roadmap)
9. [Contributing](#contributing)
10. [License](#license)
11. [Contact](#contact)
12. [Acknowledgments](#acknowledgments)

---

## 🎯 About The Project

**MIDIAnimator** is an open-source Blender addon that transforms MIDI files into professional 3D instrument animations. Whether you're creating music videos, game assets, or interactive experiences, MIDIAnimator automates the tedious process of keyframe animation.

### What It Does

- **Parses MIDI files** and extracts note data, timing, velocity, and instrument information
- **Automates keyframe creation** in Blender based on musical events
- **Supports multiple animation types** including keyframe, procedural, and physics-based animations
- **Works with any 3D instrument model** - pianos, guitars, drums, synthesizers, and more

### Demo

Watch the technical demo to see MIDIAnimator in action:

[![Radiant Ensemble Demo](https://img.youtube.com/vi/hW_21_5kVK8/maxresdefault.jpg)](https://www.youtube.com/watch?v=hW_21_5kVK8 "Radiant Ensemble - MIDIAnimator Demo")

---

## ✨ Features

### Core Features

| Feature | Description |
|---------|-------------|
| **MIDI Import** | Load any standard MIDI file (.mid, .midi) |
| **Automatic Keyframing** | Generate keyframes for note on/off events |
| **Velocity Mapping** | Map note velocity to animation intensity/scale |
| **Multi-track Support** | Handle multiple MIDI tracks and channels |
| **Instrument Detection** | Auto-detect GM instruments from MIDI program changes |
| **Note Sorting** | Sort notes by pitch, time, or channel |
| **Anchor Points** | Configurable animation anchor points per object |

### Animation Types

- **Keyframe Animation** - Traditional keyframe-based animation
- **Procedural Animation** - Math-driven continuous animation
- **Breakdown Animation** - Simplified keyframe style
- **Custom Shaping** - User-defined animation curves

### Advanced Features

- **Custom Properties Panel** - Fine-tune animation parameters per object
- **Batch Processing** - Animate multiple objects from single track
- **Preview Playback** - Real-time animation preview in Blender
- **Export Options** - Export animations as keyframes or action strips
- **Python API** - Programmatic access for automation scripts

---

## 🚀 Quick Start

### Prerequisites

- Blender 3.0, 4.0, or 5.0
- Python 3.10+
- MIDI file to animate

### Five-Minute Setup

1. **Download** the latest release from the [Releases](https://github.com/imacj/MIDIAnimator/releases) page
2. **Open** Blender and go to `Edit → Preferences → Add-ons`
3. **Click** "Install" and select the `.zip` file
4. **Enable** the addon by checking the box
5. **Done!** Access MIDIAnimator from the `N` panel in the 3D viewport

---

## 📦 Installation

### Method 1: Official Release (Recommended)

1. Navigate to [Releases](https://github.com/imacj/MIDIAnimator/releases)
2. Download the latest `MIDIAnimator-vX.X.X.zip`
3. In Blender: `Edit → Preferences → Add-ons → Install`
4. Select the downloaded zip file

### Method 2: Development Version

```bash
# Clone the repository
git clone https://github.com/imacj/MIDIAnimator.git

# Navigate to the project
cd MIDIAnimator

# Create a symlink to Blender addons (Linux/Mac)
ln -s $(pwd)/MIDIAnimator ~/.config/blender/3.0/scripts/addons/

# On Windows, copy the folder to:
# %APPDATA%\Blender Foundation\Blender\3.0\scripts\addons\
```

### Method 3: Install Specific Version for Blender

| Blender Version | Branch/Tag |
|-----------------|------------|
| Blender 3.0 | `v1.x.x-blender3` |
| Blender 4.0 | `v1.x.x-blender4` |
| Blender 5.0 | `main` |

---

## 🎮 Usage

### Basic Workflow

1. **Prepare your scene** - Set up your 3D instrument model
2. **Import MIDI** - Use the MIDIAnimator panel to load your MIDI file
3. **Configure settings** - Set animation type, timing, and mapping options
4. **Generate animation** - Click "Animate" to create keyframes
5. **Refine** - Adjust timing curves and add effects as needed

### Panel Options

```
┌─────────────────────────────────┐
│  MIDIAnimator                   │
├─────────────────────────────────┤
│  MIDI File: [Browse...]         │
│  Track: [Dropdown]              │
│  Animation Type: [Keyframe  ▼] │
│                                 │
│  Note On Frame: 1              │
│  Frame Duration: 30             │
│  Velocity Scale: 1.0            │
│                                 │
│  [Animate Notes] [Clear Anim]  │
└─────────────────────────────────┘
```

### Common Use Cases

#### Piano Animation
```python
# Import piano MIDI and animate white/black keys
# Settings: Animation Type = Keyframe
# Note On Frame = 1, Frame Duration = 15
```

#### Synthesizer LED Animation
```python
# Map velocity to emission strength
# Settings: Animation Type = Procedural
# Use "Scale" property mapped to velocity
```

#### Drum Kit Animation
```python
# Animate multiple objects from different tracks
# Settings: Track = Drums, Frame Duration = 5
```

---

## 📂 Project Structure

```
MIDIAnimator/
├── MIDIAnimator/                 # Main Python package
│   ├── __init__.py              # Addon entry point
│   ├── src/                    # Core animation logic
│   │   ├── animation.py        # Animation generation
│   │   ├── algorithms.py       # Note sorting/processing
│   │   └── instruments.py      # Instrument mappings
│   ├── data_structures/        # MIDI data handling
│   │   └── midi.py            # MIDI parsing
│   ├── ui/                    # Blender UI components
│   │   ├── panels.py         # Addon panels
│   │   └── operators.py      # Blender operators
│   └── utils/                 # Utilities
│       ├── blender.py        # Blender helpers
│       ├── logger.py         # Logging
│       └── gmInstrumentMap.py  # GM instrument data
│
├── rust-impl/                  # Rust/Tauri rewrite (experimental)
│   └── midianimator/          # New desktop application
│       ├── src/              # React frontend
│       ├── src-tauri/        # Rust backend
│       └── package.json     # Dependencies
│
├── docs/                      # Documentation (Sphinx)
│   ├── tutorials/           # User tutorials
│   ├── general/            # General documentation
│   └── images/             # Documentation images
│
├── .github/                  # GitHub workflows
├── LICENSE.txt              # GPLv3 license
├── README.md               # This file
└── pyproject.toml          # Python project config
```

---

## 🛠 Tech Stack

### Original Python Version

| Component | Technology |
|-----------|-------------|
| Language | Python 3.10 |
| Target App | Blender 3.0, 4.0, 5.0 |
| MIDI Library | [mido](https://mido.readthedocs.io/) |
| Documentation | Sphinx + MyST |

### New Rust/Tauri Version (Experimental)

| Component | Technology |
|-----------|-------------|
| Backend | Rust |
| MIDI Library | [midly](https://github.com/p万千 instructions/midly) |
| Frontend | React.js + TypeScript |
| UI Framework | React Flow, Framer Motion |
| Styling | TailwindCSS |
| Packaging | Tauri |

---

## 🗺️ Roadmap

### Phase 1: Current (Python/Blender)
- ✅ MIDI file parsing
- ✅ Basic keyframe animation
- ✅ Multiple animation types
- ✅ Velocity mapping
- ⏳ Enhanced documentation

### Phase 2: Rust Rewrite
- [ ] Standalone desktop application
- [ ] Node-based UI (React Flow)
- [ ] Plugin system for 3D apps
- [ ] Multi-software support (Blender, Maya, C4D)

### Phase 3: Future
- [ ] Real-time sync with DAWs
- [ ] Cloud rendering integration
- [ ] Motion capture import
- [ ] AI-assisted animation enhancement

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### Development Setup

```bash
# Clone and setup
git clone https://github.com/imacj/MIDIAnimator.git
cd MIDIAnimator

# Install dev dependencies
pip install -r requirements-dev.txt

# Run tests (if available)
pytest tests/
```

### Pull Request Process

1. **Fork** the Project
2. **Create** your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your Changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the Branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Coding Standards

- Follow [PEP 8](https://peps.python.org/pep-0008/) for Python code
- Use type hints where possible
- Add docstrings to new functions
- Test your changes with Blender 3.0, 4.0, and 5.0

---

## 📜 License

Distributed under the **GNU General Public License v3.0**.

- You may freely use, modify, and distribute this software
- **You may NOT publish this as closed source**
- Derivative works must also be open source

See [`LICENSE.txt`](LICENSE.txt) for the full license text.

---

## 📧 Contact

**James Alt** - [jalt@capital.edu](mailto:jalt@capital.edu)

**Project Link**: [https://github.com/imacj/MIDIAnimator](https://github.com/imacj/MIDIAnimator)

**Documentation**: [https://midianimatordocs.readthedocs.io/](https://midianimatordocs.readthedocs.io/)

---

## 🙏 Acknowledgments

### Development Tools

- [Visual Studio Code](https://code.visualstudio.com) - Primary IDE
- [Blender Development Addon](https://marketplace.visualstudio.com/items?itemName=JacquesLucke.blender-development) - Blender debugging
- [Fake Blender Python API Module](https://github.com/nutti/fake-bpy-module) - Code completion
- [Blender Python API Documentation](https://docs.blender.org/api/current/) - API reference

### Inspiration & Resources

- [Blender Guru](https://www.youtube.com/blenderguru) - Animation tutorials
- [MIDI Manufacturers Association](https://www.midi.org) - MIDI specifications
- [mido library](https://mido.readthedocs.io/) - Python MIDI handling
- Open source community contributors

---

# 🔄 Future of MIDIAnimator

> ⚠️ **Important**: MIDIAnimator is being rewritten in Rust for better performance and flexibility.

## Why Rust?

The original Python/Blender implementation has served well, but has limitations:

- **Performance**: Python cannot match Rust's speed for large MIDI files
- **Flexibility**: Tied closely to Blender's API
- **Portability**: Requires Blender to run

## New Implementation

### Architecture

```
┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│   React.js UI   │ ←──→ │   Rust Backend  │ ←──→ │  3D Application │
│   (TypeScript)  │      │   (midly)       │      │  (Blender/Maya) │
└─────────────────┘      └─────────────────┘      └─────────────────┘
         │                        │                        │
         └────────────────────────┴────────────────────────┘
                                  │
                          ┌───────┴───────┐
                          │  Tauri App    │
                          │  (Executable) │
                          └───────────────┘
```

### Features Planned

- **Standalone desktop application** (no Blender required for MIDI processing)
- **Plugin system** for supporting multiple 3D applications
- **Node-based visual programming** (React Flow)
- **Real-time DAW sync** for live animation
- **Cross-platform** (Windows, macOS, Linux)

### Technology Stack

| Component | Technology |
|-----------|------------|
| Backend | Rust |
| Frontend | React.js + TypeScript |
| Desktop Framework | Tauri |
| MIDI Library | midly |
| UI Components | React Flow, Framer Motion |
| Styling | TailwindCSS |

### Will My Projects Transfer?

Probably not. The new architecture is fundamentally different. You'll need to re-create your projects in the new interface, but we'll provide migration guides.

### Timeline

- **Alpha**: Q2 2024 - Basic MIDI parsing + React UI
- **Beta**: Q3 2024 - Blender plugin integration
- **1.0**: Q4 2024 - Full release with documentation

---

## ⭐ Show Your Support

If MIDIAnimator helps you create amazing animations, give us a star!

```bash
# Star the repository
git star
```

Or simply click the ⭐ button on the repository page.

---

<div align="center">

**Made with 🎵 and 🧊 for the animation community**

*Last updated: May 2026*

</div>

---

<!-- MARKDOWN LINKS & IMAGES -->

[contributors-shield]: https://img.shields.io/github/contributors/imacj/MIDIAnimator.svg?style=flat
[contributors-url]: https://github.com/imacj/MIDIAnimator/graphs/contributors

[forks-shield]: https://img.shields.io/github/forks/imacj/MIDIAnimator.svg?style=flat
[forks-url]: https://github.com/imacj/MIDIAnimator/network/members

[stars-shield]: https://img.shields.io/github/stars/imacj/MIDIAnimator.svg?style=flat
[stars-url]: https://github.com/imacj/MIDIAnimator/stargazers

[issues-shield]: https://img.shields.io/github/issues/imacj/MIDIAnimator.svg?style=flat
[issues-url]: https://github.com/imacj/MIDIAnimator/issues

[license-shield]: https://img.shields.io/github/license/imacj/MIDIAnimator.svg?style=flat
[license-shield-url]: https://github.com/imacj/MIDIAnimator/blob/master/LICENSE.txt

[python-shield]: https://img.shields.io/pypi/pyversions/mido?label=Python%203.10%2B
[python-url]: https://python.org/downloads

[blender-shield]: https://img.shields.io/badge/Blender-3.0%20%7C%204.0%20%7C%205.0-blue
[blender-url]: https://blender.org/download