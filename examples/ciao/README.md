# ciao

[![Version](https://img.shields.io/badge/Version-1.3.3-blue?style=flat-square)](https://github.com/Cloudgen/ciao)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**The friendliest terminal greeting tool.**
A simple, cheerful way to say hello to yourself every time you open a terminal.

using [CIAO](docs/CIAO-PRINCIPLES.md) Defensive Programming Principles
---

## ✨ Features

- Beautiful, friendly greeting with your username and emoji
- One-liner install via `curl | sh`
- Supports both user (`~/.local/bin`) and system-wide (`/usr/local/bin`) installation
- Built-in self-update, version check, and diagnostics (`about`)
- Full **JSON output support** for scripting and automation
- Extremely robust — works reliably on minimal shells and harsh environments
- Quiet and JSON modes for scripting

---

## 🚀 Quick Installation

**User installation (recommended):**

```sh
curl -fsSL https://raw.githubusercontent.com/cloudgen/ciao/main/examples/ciao/src/ciao | sh
```

**System-wide (requires root):**

```sh
curl -fsSL https://raw.githubusercontent.com/cloudgen/ciao/main/examples/ciao/src/ciao | sudo sh
```

After installation, **restart your terminal** or run:

```sh
source ~/.bashrc    # for bash
# or
source ~/.zshrc     # for zsh
```

Then try it:

```sh
ciao
```

---

## 📖 Usage

### Basic Commands

```sh
ciao                    # Show friendly greeting (default)
ciao --version          # Show version
ciao --version-check    # Compare with latest version on GitHub
ciao --self-update      # Update to the latest version
ciao --help             # Show help
```

### Options

- `--quiet, -q`     — Suppress the greeting message
- `--json`          — Output in machine-readable JSON format (implies `--quiet`)
- `--version, -v`   — Show version information
- `--version-check` — Check against latest GitHub version
- `--self-update`   — Update to latest version
- `--force`         — Force reinstall/update
- `--help, -h`      — Show this help

---

### Examples

```sh
# Normal greeting
ciao

# Quiet mode (no output unless error)
ciao --quiet

# JSON output (great for scripts)
ciao --json

# Check for updates
ciao --version-check

# Update ciao
ciao --self-update
```

**JSON Output Example:**

```json
{
  "type": "success",
  "message": "Ciao, Cloudgen 👋",
  "greeting": "Ciao, Cloudgen 👋",
  "user": "Cloudgen"
}
```

---

## Why the Defensive Style?

This script is **intentionally verbose** and heavily commented.

The repetition and safety checks protect against real-world edge cases:
- `curl | sh` in non-interactive shells
- Minimal environments (`dash`, BusyBox `ash`)
- Missing `$HOME`
- Git Bash on Windows

The many `!!! DO NOT MODIFY OR SIMPLIFY !!!` warnings exist to prevent well-meaning "cleanups" that often break subtle behaviors. The same philosophy powers `countdown` and `timer`.

It may look over-engineered for such a simple tool, but this approach makes it extremely reliable across diverse systems.

---

## Platform Compatibility

| Platform              | Shell                | Status     | Notes                              |
|-----------------------|----------------------|------------|------------------------------------|
| Alpine Linux          | BusyBox ash          | Excellent  | Primary minimal target             |
| Git Bash (Windows)    | Bash                 | Excellent  | Full support                       |
| Rocky Linux / RHEL    | Bash                 | Excellent  | Enterprise environments            |
| macOS                 | Bash / zsh           | Excellent  | Fully supported                    |
| Most Linux distros    | dash / bash          | Excellent  | Broad compatibility                |

---
## Contributing

Contributions are welcome!

Please **preserve the defensive style** and existing comments — especially around installation, output handling, and Quiet/JSON logic.

---

## License

MIT License — see the [LICENSE](LICENSE) file for details.

---

**Made with care and a healthy dose of friendliness.** 👋

*Last updated for version 1.3.3*

