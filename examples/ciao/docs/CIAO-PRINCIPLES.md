# CIAO Defensive Programming Principles (v2.8)

**Original Author**: Cloudgen Wong (`cloudgen.wong@gmail.com`)  
**Widely adopted and extended by**: Wilgat Wong in projects such as `pix-client`, `poe-client`, `SyncPrjs`, `pomo`, `ChronicleLogger`, `certbot-nginx`, `mariadb-galera`, etc.

**CIAO** = **C**aution • **I**ntentional • **A**nti-fragile • **O**ver-engineered

---

## Purpose

CIAO is a defensive programming philosophy designed as the **best practice when working with AI**.  
It forces both AI and human developers to think beyond the immediate task — toward long-term robustness, security, auditability, traceability, and maximum compatibility across environments and user scenarios.

---

## Core Principles

### 1. Caution (Defensive by Default)
- Assume nothing about the runtime environment, inputs, memory, permissions, or system state.
- Always add explicit checks for NULL, bounds, allocation failures, permission issues, etc.
- Provide safe, graceful fallbacks instead of crashes or silent failures.

### 2. Intentional Verbosity & Transparency
- Code must be deliberately verbose with clear section headers and comments.
- Every major function and component must include a **General Purpose** section explaining its objective.

### 3. Anti-fragile & Resilient Design
- Code should survive minimal environments, unexpected inputs, and edge cases.

### 4. Single Source of Output
- All program output (info, warnings, errors, debug) **must** go through centralized logging functions only.

### 5. Single Point of Entry
- Every major module or component should have a clear **Single Point of Entry** for initialization.

### 6. General Purpose Requirement
- Every public or reusable function must clearly state its **General Purpose**.

### 7. Reusable Function Protection
- Reusable functions must include this exact warning:

  ```text
  # !!! DO NOT MODIFY OR SIMPLIFY THIS FUNCTION !!!
  # Designed to be reusable in other projects.
  ```

### 8. Cross-Platform, Multi-Build & Execution Environment Awareness
- Design with multiple operating systems and multiple build systems in mind.

### 9. Safe Temporary File Handling
- Always choose the correct temporary storage and prefer atomic write patterns.

### 10. Right Backup & Restore Strategy
- Before any destructive or state-changing operation, always create a dated/versioned backup.

### 11. Independent Three-Digit Versioning per Component
- Every class, module, or major component maintains its own independent `MAJOR.MINOR.PATCH` version.

### 12. Security & Traceability Reasons
- Strictly separate `stdout` (user-facing) and `stderr` (diagnostics).
- Support multiple log levels: ERROR, WARNING, INFO, DEBUG.
- Debug mode must be switchable via environment variable (e.g. `DEBUG=1`).

### 13. Support for Multiple Version Management Systems & Shells
- Be compatible with `sdkman`, `pyenv`, `conda`, `nvm`, `rbenv`, etc.
- Support multiple shells: `sh`, `dash`, `ash`, `bash`, `zsh`, `fish`, `Git Bash`, etc.

### 14. Interactive vs Non-Interactive Mode Awareness (New in v2.8)
- Always be aware of whether the program is running in **interactive** or **non-interactive** mode.
- Detect non-interactive environments (e.g., scripts, CI/CD, `curl | sh`, Docker builds, Ansible, etc.).
- When performing actions that normally require user input (e.g., package installation, database setup, confirmation prompts):
  - Provide safe defaults or automatic behavior in non-interactive mode.
  - Example: When installing MariaDB, use `--no-interactive`, `--yes`, or appropriate flags (`DEBIAN_FRONTEND=noninteractive apt-get install -y mariadb-server`).
  - Never hang waiting for user input in non-interactive contexts.
- Support common non-interactive installation patterns such as `curl | sh` pipelines.
- Clearly document how the program behaves in both interactive and non-interactive modes.

### 15. Encouraging User Help Functions
- Provide clear, comprehensive help / usage information (`--help`, `-h`, or `help` command).
- Make help output useful even for non-interactive usage (e.g., include examples, environment variables, and non-interactive flags).
- Encourage users to discover safe usage patterns through helpful messages.
- In error cases, suggest the appropriate help command or relevant documentation.

### 16. Input Pattern Checking
- Always validate user input and command-line arguments before use.
- Reject or sanitize dangerous patterns (e.g., overly long strings, unexpected characters, malicious paths).
- Provide clear error messages when input validation fails.
- Log rejected inputs at appropriate log levels for traceability.

### 17. Protect Against AI & Human Modification
- Use large, visible CIAO headers at the top of every file.
- Make security-critical, backup, versioning, logging, environment-awareness, and interactive-mode sections highly visible for AI audit.

---

## How to Apply CIAO in Your Project

1. Add this file (`CIAO-PRINCIPLES.md`) to your repository root or `docs/` folder.
2. Include the full CIAO header at the top of every source file.
3. Follow the principles of Single Point of Entry, centralized logging, independent versioning, proper backup strategy, and interactive/non-interactive awareness.
4. When AI assists in writing or refactoring code, always cross-check against these principles.

---

**Last updated**: April 2026
