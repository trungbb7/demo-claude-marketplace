# Demo Claude Code Marketplace

Kho mã nguồn mẫu dành cho **Claude Code Plugin Marketplace**. Repository này đóng vai trò làm chợ plugin (Marketplace catalog) chứa nhiều plugin tùy chỉnh cho Claude Code CLI.

---

## 📁 Cấu trúc Repository (Repository Structure)

```text
demo-claude-marketplace/
├── .claude-plugin/
│   └── marketplace.json            # File cấu hình chính của Marketplace Catalog
├── plugins/                        # Chứa tất cả các plugins
│   ├── cpp-code-review/            # Plugin 1: Review & Audit mã nguồn C++
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json         # Manifest của plugin cpp-code-review
│   │   ├── commands/               # Các Slash Commands tùy chỉnh (VD: /review-cpp)
│   │   │   └── review-cpp.md
│   │   ├── agents/                 # Các Sub-Agent tùy chỉnh (VD: cpp-auditor)
│   │   │   └── cpp-auditor.md
│   │   ├── skills/                 # Các Skill hướng dẫn cho Claude Code
│   │   │   └── cpp-best-practices/
│   │   │       └── SKILL.md
│   │   └── README.md
│   └── git-workflow/               # Plugin 2: Tự động hóa quy trình Git
│       ├── .claude-plugin/
│       │   └── plugin.json         # Manifest của plugin git-workflow
│       ├── commands/
│       │   └── conventional-commit.md
│       ├── skills/
│       │   └── git-standards/
│       │       └── SKILL.md
│       └── README.md
│   └── answer-formatter/           # Plugin 3: Định dạng phong cách trả lời & văn phong
│       ├── .claude-plugin/
│       │   └── plugin.json         # Manifest của plugin answer-formatter
│       ├── commands/
│       │   └── format-response.md
│       ├── skills/
│       │   └── response-formatting/
│       │       └── SKILL.md
│       └── README.md
└── README.md
```

---

## 🚀 Hướng dẫn sử dụng trong Claude Code CLI

### 1. Thêm Marketplace này vào Claude Code

Bạn có thể đăng ký Marketplace này trong Claude Code bằng cách chạy lệnh sau (chỉ định đường dẫn thư mục cục bộ hoặc URL GitHub):

- **Local Path (Cục bộ):**

  ```bash
  /plugin marketplace add d:/Workspace/test/demo-claude-marketplace
  ```

- **Khi đẩy repo lên GitHub:**
  ```bash
  /plugin marketplace add https://github.com/your-username/demo-claude-marketplace
  ```

### 2. Cài đặt Plugin từ Marketplace

Sau khi đã add marketplace, bạn cài đặt các plugin bằng tên marketplace:

```bash
/plugin install cpp-code-review@demo-claude-marketplace
/plugin install git-workflow@demo-claude-marketplace
/plugin install answer-formatter@demo-claude-marketplace
```

### 3. Sử dụng các tính năng đã cài đặt

- **Dùng Slash Command:**
  - `/review-cpp`: Yêu cầu Claude review code C++ theo chuẩn modern C++20.
  - `/conventional-commit`: Tự động đọc `git diff --staged` và gợi ý commit message chuẩn.
  - `/format-response`: Tùy chỉnh phong cách phản hồi (concise, executive, architect, tutor, code-first).

- **Dùng Sub-Agent:**
  - Thường được Claude Code kích hoạt hoặc gọi trực tiếp khi thực hiện kiểm thử / audit chuyên sâu.

---

## 📝 Hướng dẫn thêm Plugin mới vào Marketplace

1. **Tạo thư mục plugin mới trong `plugins/`:**
   ```bash
   mkdir -p plugins/my-new-plugin/.claude-plugin
   ```
2. **Tạo file `plugin.json` trong `plugins/my-new-plugin/.claude-plugin/plugin.json`:**
   ```json
   {
     "name": "my-new-plugin",
     "version": "1.0.0",
     "description": "Mô tả plugin của bạn",
     "author": { "name": "Tên Tác Giả" }
   }
   ```
3. **Thêm thành phần cho plugin (commands, skills, agents, hooks, v.v.):**
   - Commands: `plugins/my-new-plugin/commands/my-command.md`
   - Skills: `plugins/my-new-plugin/skills/my-skill/SKILL.md`
   - Agents: `plugins/my-new-plugin/agents/my-agent.md`
4. **Đăng ký plugin mới trong `.claude-plugin/marketplace.json`:**
   ```json
   {
     "name": "my-new-plugin",
     "source": "./plugins/my-new-plugin",
     "description": "Mô tả ngắn gọn về plugin",
     "version": "1.0.0"
   }
   ```

---

## 📌 Các quy tắc quan trọng (Best Practices)

- File `plugin.json` **bắt buộc** phải nằm trong thư mục `.claude-plugin/plugin.json` của từng plugin.
- File `marketplace.json` **bắt buộc** phải nằm trong thư mục `.claude-plugin/marketplace.json` tại gốc repository.
- Các tính năng như `commands/`, `skills/`, `agents/`, `hooks/` đặt tại gốc của thư mục plugin tương ứng (không đặt bên trong `.claude-plugin/`).
