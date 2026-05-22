---
name: notion-skill
description: Interact with Notion to manage pages, databases, and blocks. Use when the user wants to read from or write to their Notion workspace, search for content, or automate Notion workflows.
---

# Notion Skill

## Overview

This skill allows the agent to interact with Notion via the Model Context Protocol (MCP). It supports listing databases and pages, retrieving content, searching, and making updates to properties or page blocks.

> **Workflow Relacionado**: Para instrucciones específicas sobre cómo sincronizar archivos locales con Notion (usando H1 para títulos o Slugs para nombres de archivo), utiliza siempre el workflow definido en `.agent/workflows/notion-sync.md`.

## Task-Based Guidelines

### 1. Information Retrieval
- **List Databases/Pages**: Use `list_databases` or `list_pages` to see what is available.
- **Get Content**: Use `get_page` or `get_database` to retrieve metadata. To read the actual content of a page, use `get_block_children` recursively if necessary.
- **Search**: Use `search` to find items across the workspace by title.

### 2. Content Updates & Creation
- **Create Items**: Use `create_page` to add new entries to a database or as a standalone page. Use `create_database` to define new structured data collections.
- **Modify Items**: Use `update_page` or `update_database` to change titles, properties, or icons.
- **Manage Blocks**: Use `append_block_children` to add content (text, images, headings) to an existing page or block.
- **Archive**: Use `archive_page` to delete/archive items.

### 3. Best Practices
- **Authentication (CRITICAL):** The Notion MCP integration strictly requires the API key to be retrieved from the `mcp.json` file in the root directory under the path `mcpServers.notion.env.NOTION_TOKEN`. Do not look for system-wide environment variables like `NOTION_KEY`, `NOTION_API_KEY`, or `NOTION_TOKEN`.
- **MCP Tool Bugs (update_block):** The official `mcp_notion_API-update-a-block` tool currently suffers from a schema validation error (400 Bad Request) because it wraps the block JSON in a `type` property. If you need to update a block's content, **DO NOT** use the MCP tool. Instead, write a temporary Node.js script using `fetch`. The script must read the `NOTION_TOKEN` directly from the `mcp.json` file to authenticate the `PATCH` request to `https://api.notion.com/v1/blocks/{block_id}`.
- **Permissions**: Remind the user that the integration must be added to the specific page/database via the "Connections" menu in Notion.
- **Data Structure:** Notion pages must live inside a Database or Wiki to support custom properties (like Frontmatter metadata). Standalone pages cannot have custom properties.
- **Recursion**: When reading deeply nested pages, be mindful of the number of API calls.
- **Formatting**: When appending blocks, ensure the block objects match the Notion API schema (e.g., `paragraph`, `heading_1`, etc.).

## Examples

- "List my Notion databases"
- "Search for 'Project Alpha' in Notion"
- "Add a new task to the 'Work' database with status 'Done'"
- "Read the content of my 'Meeting Notes' page"

## Resources

### references/
- **api_reference.md**: (Optional) Detailed Notion API object types and property definitions.

### scripts/
Executable code that can be run directly to perform specific operations.

**Examples from other skills:**
- PDF skill: fill_fillable_fields.cjs, extract_form_field_info.cjs - utilities for PDF manipulation
- CSV skill: normalize_schema.cjs, merge_datasets.cjs - utilities for tabular data manipulation

**Appropriate for:** Node.cjs scripts (cjs), shell scripts, or any executable code that performs automation, data processing, or specific operations.

**Note:** Scripts may be executed sin necesidad de cargarse en el contexto, pero aún pueden ser leídos por **Google Antigravity** para realizar ajustes en el entorno o parcheos.

### assets/
Files not intended to be loaded into context, but rather used within the output **Google Antigravity** produces.

**Examples from other skills:**
- Brand styling: PowerPoint template files (.pptx), logo files
- Frontend builder: HTML/React boilerplate project directories
- Typography: Font files (.ttf, .woff2)

**Appropriate for:** Templates, boilerplate code, document templates, images, icons, fonts, o cualquier archivo destinado a copiarse o usarse en el resultado final.

---

**Any unneeded directories can be deleted.** Not every skill requires all three types of resources.
