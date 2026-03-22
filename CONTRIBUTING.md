# Contributing to Qanot Plugins Registry

## Adding a Plugin

1. Create your plugin repo with this structure:
   ```
   qanot-plugin-<name>/
     plugin.json     # Required: name, version, description, author, dependencies
     plugin.py       # Required: QanotPlugin class extending Plugin
     README.md       # Recommended: usage docs
   ```

2. Fork this repo and add your entry to `index.json`:
   ```json
   {
     "name": "your_plugin",
     "version": "1.0.0",
     "description": "What it does",
     "author": "Your Name",
     "git_url": "https://github.com/you/qanot-plugin-your-plugin.git",
     "tags": ["relevant", "tags"],
     "min_qanot_version": "2.0.0"
   }
   ```

3. Open a PR. We will review for:
   - No malicious code (os.system, eval, exec, subprocess)
   - No install scripts (install.sh, setup.sh)
   - No compiled binaries (.exe, .so, .dll)
   - No embedded secrets (.env files)
   - Dependencies on the approved allowlist

## Security Requirements

- HTTPS git URLs only
- No shell scripts in plugin directory
- No `eval()`, `exec()`, `os.system()` unless justified
- Dependencies must be from the approved list
- All plugins are scanned automatically on install

## Plugin Quality Guidelines

- Clear `plugin.json` with accurate description
- Tools should have descriptive names and parameters
- Error messages should be helpful (Uzbek or English)
- Include teardown() cleanup for connections
- Test your plugin with `qanot plugin scan <name>`
