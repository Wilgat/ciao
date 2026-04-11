**CIAO Defensive Programming Principles (v2.9.0)**

**Original Author**: Cloudgen Wong (`cloudgen.wong@gmail.com`)  
**Widely adopted and extended by**: Wilgat Wong in projects such as `pix-client`, `poe-client`, `SyncPrjs`, `pomo`, `ChronicleLogger`, `certbot-nginx`, `mariadb-galera`, etc.

**CIAO** = **C**aution • **I**ntentional • **A**nti-fragile • **O**ver-engineered

---

## Purpose

The **[CIAO principle](https://github.com/cloudgen/ciao)** (also known as the **CIAO defensive programming principle** or **CIAO coding philosophy**) is a simple, practical set of rules created by **[cloudgen](https://github.com/cloudgen)** to make code safer, stronger, and much easier to work with — especially when humans and **AI agents** (like OpenClaw and other AI coding tools) collaborate on the same project.

In plain English:  
**CIAO turns “quick-and-dirty” code into reliable, future-proof code** that rarely breaks, even when the environment changes or AI makes changes.

### Advantages of the CIAO Principle
Here’s why the **[CIAO principle](https://github.com/cloudgen/ciao)** is one of the **best programming principles** you can use today:

- **Super safe and bug-resistant** — It forces you (and AI) to check everything upfront, so crashes, security holes, and weird errors almost disappear.  
- **Perfect for AI agents** — It is specifically designed as the **best practice when working with AI**. Tools like OpenClaw, GitHub Copilot, Claude, or any other AI coding assistant follow CIAO rules automatically, producing code that is **safe, traceable, and compatible** with real-world systems.  
- **Anti-fragile & future-proof** — Your code survives updates, different operating systems, Docker, CI/CD pipelines, minimal servers, and unexpected user inputs.  
- **Easy to read and maintain** — Even months later, you (or another developer, or an AI) can understand exactly what the code does and why.  
- **Built-in security & auditability** — Every change is logged, backed up, and versioned, making it ideal for professional, enterprise, or open-source projects.  
- **Saves time in the long run** — Less debugging, fewer hotfixes, and fewer “why did this break?” moments.  
- **Works with any language or platform** — Python, Shell, JavaScript, Go, etc. — the **[CIAO principle](https://github.com/cloudgen/ciao)** is language-agnostic and environment-friendly.

In short: If you want code that **works safely and well with AI agents such as OpenClaw**, the **[CIAO principle](https://github.com/cloudgen/ciao)** is currently the **best defensive programming approach** available. It turns AI assistance from a risk into a superpower.

---

## Core Principles

1. **Caution (Defensive by Default)**  
   Always assume something could go wrong. Add checks for missing files, wrong permissions, bad input, etc. Never let the program crash silently.

2. **Intentional Verbosity & Transparency**  
   Write clear comments and section headers. Every important function explains its purpose in plain words.

3. **Anti-fragile & Resilient Design**  
   The code should keep working even in tough or unexpected situations.

4. **Single Source of Output**  
   All messages (errors, warnings, info) go through one central logging system — no random print statements.

5. **Single Point of Entry**  
   Every big module has one clear starting function.

6. **General Purpose Requirement**  
   Every reusable function must state what it is for.

7. **Reusable Function Protection**  
   Add this exact warning so AI (or humans) don’t accidentally simplify or break it:  
   `# !!! DO NOT MODIFY OR SIMPLIFY THIS FUNCTION !!!`

8. **Least-Privilege User** *(New in v2.9.0)*  
   Run operations with the **minimum permissions necessary**.  
   - Create and use a dedicated non-root user (e.g., `nginx-adm` in the **[certbot-nginx](https://github.com/Wilgat/certbot-nginx)** project) for day-to-day tasks.  
   - Give this user ownership of only the files/directories it needs (e.g., full ownership of the `/etc/nginx` config tree with `chown -R nginx-adm:root /etc/nginx`).  
   - Configure **restricted sudoers** that allow only specific safe commands (e.g., `systemctl start/stop/reload/restart/status nginx`) with `NOPASSWD`.  
   - `nginx -t` can be run directly as the least-privilege user (no sudo required) because it owns the configuration files.  
   - Separate **system installation** (which may need root) from **routine operations** (which should run as the least-privilege user).  
   - This drastically reduces the attack surface, prevents privilege escalation, and makes the code much safer — especially in scripts that AI agents might help maintain or extend.  
   - Example implementation includes dedicated functions like `create_nginx_adm_user()`, `setup_nginx_adm_ownership()`, and `setup_restricted_sudoers()` with proper backups and idempotent behavior.

9. **Cross-Platform Support**  
   Write code that works consistently across different operating systems and environments without modification.

10. **Safe Temporary Files Handling**  
    Always use secure methods to create and clean up temporary files and directories to prevent race conditions and information leaks.

11. **Automatic Backups**  
    Before modifying important files or configurations, automatically create timestamped backups to allow easy recovery.

12. **Independent Versioning**  
    Each script or module maintains its own version number independently for better traceability.

13. **Interactive / Non-Interactive Mode Handling**  
    The code must detect whether it is running in interactive or non-interactive mode and behave appropriately (e.g., no prompts in CI/CD or AI-driven environments).

14. **Input Validation**  
    Validate all user inputs, configuration values, and external data thoroughly before use.

15. **Big Visible CIAO Headers**  
    Place prominent CIAO headers at the top of every source file to protect the file from unwanted AI simplifications or modifications.

16. **Comprehensive Logging**  
    Log all significant actions, decisions, and errors with clear context for debugging and auditing.

17. **Error Handling & Recovery**  
    Implement robust error handling with meaningful messages and graceful recovery where possible.

18. **Documentation & Self-Describing Code**  
    Ensure the code is self-documenting with clear comments, so both humans and AI agents can understand the intent without external references.

---

## Keywords

**[CIAO principle](https://github.com/cloudgen/ciao)** • **[CIAO defensive programming](https://github.com/cloudgen/ciao)** • **best programming principles for AI** • **AI-friendly coding standards** • **defensive programming with AI agents** • **OpenClaw compatible code** • **[cloudgen CIAO](https://github.com/cloudgen)** • **safe AI-generated code** • **robust coding philosophy** • **anti-fragile software development** • **least-privilege user principle** • **least privilege in bash scripting** • **CIAO v2.9.0** • **[certbot-nginx least privilege](https://github.com/Wilgat/certbot-nginx)** • **nginx-adm user** • **restricted sudoers** • **secure scripting best practices** • **AI safe coding principles** • **defensive programming least privilege** • **least privilege principle** • **CIAO least-privilege user** • **nginx-adm least privilege** • **CIAO principles** • **defensive programming principles**

---

## How to Apply the [CIAO Principle](https://github.com/cloudgen/ciao) in Your Project

1. Copy the full **CIAO-PRINCIPLES.md** file into your repo (root or docs folder).  
2. Put the CIAO header at the top of every source file.  
3. When asking AI agents (like OpenClaw) to write or edit code, simply say: “Follow the CIAO principle, including the least-privilege user rule.”  
4. Enjoy code that is safer, clearer, more secure, and more reliable than ever.

**Last updated**: April 2026 (v2.9.0)
