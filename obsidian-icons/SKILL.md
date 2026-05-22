---
name: obsidian-icons
description: Guide for adding Lucide icons to files and directories in the Obsidian knowledge base using the obsidian-icon-folder plugin. Use when the user asks to add an icon to a file or directory.
---

# Obsidian Icons Skill

This skill allows you to help the user add or manage icons for their Obsidian knowledge base, leveraging the `obsidian-icon-folder` plugin which uses `lucide` icons.

## Icon List Location
The complete list of all supported Lucide icons has been generated in strict JSON format.
**Path:** `/mnt/c/Users/willycotes/Documents/Knowledge-base/.agent/skills/obsidian-icons/lucide-icons.json`

## How to use this skill:

1. **Browse Available Icons:**
   When the user asks you to assign an icon to a file or folder (e.g., "add a money icon to the Finance folder"), first search or read the JSON file at the path above to find a suitable Lucide icon name (e.g., `banknote`, `coins`, `dollar-sign`).
   You can use `grep_search` or script evaluation to find icons matching keywords.

2. **Applying the Icon (via obsidian-icon-folder data.json):**
   The `obsidian-icon-folder` plugin stores the file-to-icon mapping inside its `data.json` file.
   - **Path:** `/mnt/c/Users/willycotes/Documents/Knowledge-base/.obsidian/plugins/obsidian-icon-folder/data.json`
   - Look at the JSON structure. Typically, the root object has a property like `settings`, and the remaining keys are the relative file/folder paths mapped to the icon name.
   - **Important Naming Convention:** The plugin natively expects Lucide icons to be prefixed with `Li` followed by the **PascalCase** version of the icon name.
   - Example entry: `"Marketing/Facebook": "LiFacebook"` (for `facebook`), `"General": "LiLayoutDashboard"` (for `layout-dashboard`).
   - If you need to apply an icon, update the `data.json` file securely without breaking formatting. To ensure safety, use jq or Python scripts if the JSON is complex, or standard text replacements if simple.

3. **Applying the Icon (via Frontmatter):**
   If the user has `iconInFrontmatterEnabled: true` in their settings, you can alternatively add the icon directly to the Markdown frontmatter (e.g., `icon: lucide-facebook`).

Always maintain strict JSON format to prevent Obsidian parsing errors.
