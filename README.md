# Tianyu Skills (天宇团队共享 Agent Skills 技能库)

本仓库用于收集、维护和共享团队内部优质的 Agent Skills / Claude Code Skills。

## 📦 已收录技能

| 技能名称 | 目录 | 说明 |
| :--- | :--- | :--- |
| **find-skills** | `find-skills/` | 技能发现与一键安装助手，基于 skills.sh 与 GitHub 全球开源技能库检索、评估并安装高星优质技能 |

---

## 🚀 快速上手与安装

### 1. 使用 Skills CLI 安装（推荐）

可以通过官方 Skills CLI 快速将仓库中的技能安装到你的项目或全局环境中：

#### 安装 `find-skills` 技能：

- **安装至当前项目（Claude Code）**：
  ```bash
  npx -y skills add tianyuvsion/skills@find-skills -a claude-code
  ```

- **安装至全局（所有项目通用）**：
  ```bash
  npx -y skills add tianyuvsion/skills@find-skills -a claude-code -g
  ```

- **Cursor / 其他支持 Skills 的 Agent**：
  ```bash
  npx -y skills add tianyuvsion/skills@find-skills
  ```

### 2. 手动安装至 Claude Code

将 `find-skills` 目录复制到以下路径之一：
- **全局生效**：`~/.claude/skills/find-skills/`
- **项目生效**：`<项目根目录>/.claude/skills/find-skills/`

---

## 💡 使用指南

安装后，在 Claude Code 或对应 Agent 会话中：

1. **直接调用命令**：
   ```text
   /find-skills <关键词>
   ```
   例如：
   ```text
   /find-skills react performance
   /find-skills 微信小程序
   /find-skills testing playwright
   ```

2. **自然语言检索**：
   直接询问助手，例如：
   - “帮我找一个优化 React 性能的 skill”
   - “有推荐的 Git PR review 技能吗”

---

## 🛠️ 如何贡献新技能

欢迎将你在日常开发中沉淀的好用技能贡献到本仓库：

1. 在仓库根目录下创建技能目录：
   ```text
   <skill-name>/
   └── SKILL.md
   ```
2. 编写 `SKILL.md`，并在顶部添加规范的 YAML Frontmatter（包含 `name`、`description` 等元数据）。
3. 提交 PR 或直接 Push 至主分支。
