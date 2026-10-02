# Demo Claude Code Marketplace

A sample repository for the **Claude Code Plugin Marketplace**. This repository serves as a plugin marketplace catalog containing custom plugins for the Claude Code CLI.

---

## 📁 Repository Structure

```text
demo-claude-marketplace/
├── .claude-plugin/
│   └── marketplace.json            # Main configuration file for the Marketplace Catalog
├── plugins/                        # Contains all plugins
│   ├── cpp-code-review/            # Plugin 1: C++ Code Review & Audit
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json         # Manifest for the cpp-code-review plugin
│   │   ├── commands/               # Custom Slash Commands (e.g. /review-cpp)
│   │   │   └── review-cpp.md
│   │   ├── agents/                 # Custom Sub-Agents (e.g. cpp-auditor)
│   │   │   └── cpp-auditor.md
│   │   ├── skills/                 # Skill guidelines for Claude Code
│   │   │   └── cpp-best-practices/
│   │   │       └── SKILL.md
│   │   └── README.md
│   └── git-workflow/               # Plugin 2: Git Workflow Automation
│       ├── .claude-plugin/
│       │   └── plugin.json         # Manifest for the git-workflow plugin
│       ├── commands/
│       │   └── conventional-commit.md
│       ├── skills/
│       │   └── git-standards/
│       │       └── SKILL.md
│       └── README.md
│   └── answer-formatter/           # Plugin 3: Response Formatting & Writing Style
│       ├── .claude-plugin/
│       │   └── plugin.json         # Manifest for the answer-formatter plugin
│       ├── commands/
│       │   └── format-response.md
│       ├── skills/
│       │   └── response-formatting/
│       │       └── SKILL.md
│       └── README.md
│   └── doc-review/                 # Plugin 4: Technical Document Review & Auditing (PRD, API Specs)
│       ├── .claude-plugin/
│       │   └── plugin.json         # Manifest for the doc-review plugin
│       ├── commands/
│       │   ├── review-doc.md
│       │   ├── audit-api-doc.md
│       │   └── doc-lint.md
│       ├── agents/
│       │   └── doc-auditor.md
│       ├── skills/
│       │   └── doc-review-standards/
│       │       └── SKILL.md
│       └── README.md
└── README.md
```

---

## 🚀 Usage Guide for Claude Code CLI

### 1. Add This Marketplace to Claude Code

Register this marketplace in Claude Code using the following command (specify the local directory path or GitHub URL):

- **Local Path:**

  ```bash
  /plugin marketplace add d:/Workspace/test/demo-claude-marketplace
  ```

- **When pushing the repo to GitHub:**
  ```bash
  /plugin marketplace add https://github.com/your-username/demo-claude-marketplace
  ```

### 2. Install Plugins from the Marketplace

Once the marketplace is added, install plugins by marketplace name:

```bash
/plugin install cpp-code-review@demo-claude-marketplace
/plugin install git-workflow@demo-claude-marketplace
/plugin install answer-formatter@demo-claude-marketplace
/plugin install doc-review@demo-claude-marketplace
```

### 3. Use Installed Features

- **Slash Commands:**
  - `/review-cpp`: Ask Claude to review C++ code against modern C++20 standards.
  - `/conventional-commit`: Auto-reads `git diff --staged` and suggests a standardized commit message.
  - `/format-response`: Customize response style (concise, executive, architect, tutor, code-first).
  - `/review-doc`: Comprehensive document quality audit (PRD, Tech Spec, Architecture, README) with a Quality Score.
  - `/audit-api-doc`: In-depth API documentation audit (OpenAPI, REST API reference, endpoints, schemas, status codes).
  - `/doc-lint`: Markdown format linter (heading hierarchy, broken links, image alt text, code blocks).

- **Sub-Agents:**
  - `cpp-auditor`: Memory safety and performance auditor for C++ codebases.
  - `doc-auditor`: Technical document auditor for detecting ambiguities and content gaps in product and technical specs.

---

## 📝 Adding a New Plugin to the Marketplace

1. **Create a new plugin directory inside `plugins/`:**
   ```bash
   mkdir -p plugins/my-new-plugin/.claude-plugin
   ```
2. **Create `plugin.json` at `plugins/my-new-plugin/.claude-plugin/plugin.json`:**
   ```json
   {
     "name": "my-new-plugin",
     "version": "1.0.0",
     "description": "Your plugin description",
     "author": { "name": "Your Name" }
   }
   ```
3. **Add plugin components (commands, skills, agents, hooks, etc.):**
   - Commands: `plugins/my-new-plugin/commands/my-command.md`
   - Skills: `plugins/my-new-plugin/skills/my-skill/SKILL.md`
   - Agents: `plugins/my-new-plugin/agents/my-agent.md`
4. **Register the new plugin in `.claude-plugin/marketplace.json`:**
   ```json
   {
     "name": "my-new-plugin",
     "source": "./plugins/my-new-plugin",
     "description": "Short description of your plugin",
     "version": "1.0.0"
   }
   ```

---

## 📌 Important Rules & Best Practices

- The `plugin.json` file **must** reside at `.claude-plugin/plugin.json` inside each plugin directory.
- The `marketplace.json` file **must** reside at `.claude-plugin/marketplace.json` at the repository root.
- Plugin components such as `commands/`, `skills/`, `agents/`, and `hooks/` must be placed at the root of the plugin directory (not inside `.claude-plugin/`).
