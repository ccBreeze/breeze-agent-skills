# Installing breeze-agent-skills for Codex

Enable breeze-agent-skills in Codex via native skill discovery. Just clone and symlink.

## Prerequisites

- Git

## Installation

1. **Clone the breeze-agent-skills repository:**

   ```bash
   git clone https://github.com/ccBreeze/breeze-agent-skills.git ~/.codex/breeze-agent-skills
   ```

2. **Create the skills symlink:**

   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/breeze-agent-skills/.agents/skills ~/.agents/skills/breeze-agent-skills
   ```

   **Windows (PowerShell):**

   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\breeze-agent-skills" "$env:USERPROFILE\.codex\breeze-agent-skills\.agents\skills"
   ```

3. **Restart Codex** (quit and relaunch the CLI) to discover the skills.

## Verify

```bash
ls -la ~/.agents/skills/breeze-agent-skills
```

You should see a symlink (or junction on Windows) pointing to your breeze-agent-skills `.agents/skills` directory.

## Updating

```bash
cd ~/.codex/breeze-agent-skills && git pull
```

Skills update instantly through the symlink.

## Uninstalling

```bash
rm ~/.agents/skills/breeze-agent-skills
```

Optionally delete the clone: `rm -rf ~/.codex/breeze-agent-skills`.
