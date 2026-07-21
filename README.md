# AI Coding Agents on Android

> Run Claude Code, Codex, PI CLI, Antigravity, and more on your Android phone via Termux + proot-distro Ubuntu.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform: Android](https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white)](https://developer.android.com/)
[![Environment: Termux](https://img.shields.io/badge/Environment-Termux-000000?logo=linux&logoColor=white)](https://termux.dev/)

---

## Table of Contents

- [Overview](#overview)
- [Supported Agents](#supported-agents)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Usage](#usage)
- [Architecture](#architecture)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This repository provides step-by-step guides and automated install scripts to run modern AI coding agents directly on Android devices. By combining **Termux** with **proot-distro Ubuntu**, you get a full Linux userland — no root access, no unlocked bootloader, no cloud sandbox required.

Your phone is a Linux box you already own. These guides help you use it like one.

## Supported Agents

| Agent | Command | Status |
|-------|---------|--------|
| **Claude Code** | `claude` | ✅ Guide available |
| **Codex** | `codex` | ✅ Guide available |
| **PI CLI** | `pi` | ✅ Guide available |
| **Antigravity** | `antigravity` | ✅ Guide available |
| **More agents** | — | 🚧 In progress |

Each agent has its own dedicated README with a one-line `setup.sh` and a manual step-by-step installation path.

## Prerequisites

- An Android device (mid-range or flagship recommended for best performance)
- [Termux](https://f-droid.org/packages/com.termux/) installed from **F-Droid** (not Google Play)
- ~500 MB free storage for the Ubuntu rootfs, overall 2GB requires for first one.
- Internet connection

> ⚠️ **Important:** Install Termux from F-Droid, not the Google Play Store. The Play Store version is deprecated and no longer maintained.

## Quick Start

```bash
# 1. Update Termux packages
apt update -y && apt install proot-distro -y

# 2. Install Ubuntu
proot-distro install ubuntu

# 3. Enter Ubuntu shell
proot-distro login ubuntu

# 4. Install Node.js (required by most agents)
apt install nodejs -y

# 5. Install your agent of choice (example: PI CLI)
npm install -g @earendil-works/pi-coding-agent

# 6. Run it
pi
```

## Installation

### 1. Termux — The Foundation

Termux provides a real package manager and shell environment on Android. Install it from F-Droid, then update packages:

```bash
apt update && apt upgrade -y
```

### 2. proot-distro — Ubuntu on Android

`proot-distro` gives you a full, isolated Ubuntu userland:

```bash
apt install proot-distro -y
proot-distro install ubuntu
proot-distro login ubuntu
```

### 3. Agent Installation

Once inside Ubuntu, follow the individual guide for your chosen agent:

- [Claude Code Setup](https://github.com/fiozxr/claude-agent-android)
- [Codex Setup](https://github.com/fiozxr/codex-agent-android)
- [PI CLI Setup](https://github.com/fiozxr/pi-agent-android)
- [Antigravity Setup](https://github.com/fiozxr/antigravity-agent-android)

## Usage

After installation, all agents run from the same Ubuntu shell:

```bash
# Start Ubuntu
proot-distro login ubuntu

# Run any installed agent
claude      # Anthropic Claude Code
codex       # OpenAI Codex
pi          # PI CLI
antigravity # Antigravity runtime
```

You can install and run multiple agents side-by-side in the same environment.

## Architecture

```
┌─────────────────────────────────────┐
│           Android OS                │
│  (No root required — user space)    │
├─────────────────────────────────────┤
│            Termux                   │
│    (Package manager + shell)        │
├─────────────────────────────────────┤
│         proot-distro                │
│    (Isolated Ubuntu userland)       │
├─────────────────────────────────────┤
│      Node.js + AI Agents            │
│  (Claude, Codex, PI, Antigravity)   │
└─────────────────────────────────────┘
```

- **Layer 1:** Termux provides the terminal and package manager.
- **Layer 2:** proot-distro creates an isolated Ubuntu environment.
- **Layer 3:** Node.js enables npm-based agent installs.
- **Result:** Agents run exactly as they would on a standard Linux laptop.

## FAQ

**Do I need a rooted phone?**  
No. Termux and proot-distro both run without root access.

**Will this work on any Android phone?**  
Yes, though performance scales with RAM and CPU. Mid-range and flagship devices handle these agents comfortably.

**Is this safe to run alongside normal apps?**  
Yes. The Ubuntu environment is fully isolated in its own directory. Removing it is a single command.

**Can I run multiple agents at once?**  
Yes. All agents coexist in the same Ubuntu environment.

**How do I uninstall everything?**  
```bash
proot-distro remove ubuntu
```

## Contributing

Contributions are welcome. If you've got a new agent working on Android, or improvements to existing guides, open a pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-agent`)
3. Commit your changes (`git commit -am 'Add guide for X agent'`)
4. Push to the branch (`git push origin feature/new-agent`)
5. Open a Pull Request

## License

Distributed under the MIT License. See [LICENSE](./LICENSE) for more information.

---
