---
name: find-skills
description: 搜索并安装 Claude Code / Agent Skills 生态中的海量实用技能（基于 skills.sh 与 GitHub 全球开源技能库），支持按关键词精准检索、展示安装热度与用途，并支持一键下载安装至全局或当前项目。
argument-hint: "<关键词或技能名> [--install <owner/repo@skill>] [--global]"
user-invocable: true
disable-model-invocation: false
allowed-tools: Bash, Read, Write, Edit, Glob, Grep
---

# find-skills - 技能发现与一键安装助手

用户需要寻找、评估或安装适合的 Agent Skills 技能：`$ARGUMENTS`

## 执行流程

### 1. 技能检索 (Search)
当用户提供搜索关键词或表达某种技能需求时：
- 执行官方生态查找命令：
  ```bash
  npx -y skills find $ARGUMENTS
  ```
- 从返回列表中提炼最匹配、安装量高（如 10K+ / 100K+ Installs）、口碑好的前 3~5 个优质技能推荐给用户，包含：
  * **技能全名**：`<owner/repo@skill-name>`
  * **热度指数**：安装量与来源
  * **核心功能**：一句话说明这个技能能解决什么痛点
  * **安装命令**：
    - Claude Code: `npx -y skills add <owner/repo@skill-name> -a claude-code`
    - Cursor / 通用 Agent: `npx -y skills add <owner/repo@skill-name>`

### 2. 技能安装 (Install)
当用户要求“帮我安装”或指定了具体技能名时：
- **安装到当前项目**（默认）：
  ```bash
  # Claude Code
  npx -y skills add <target-skill> -a claude-code

  # 通用 Agent / Cursor
  npx -y skills add <target-skill>
  ```
- **安装到全局**（跨所有项目通用，若用户指定 `--global` 或表示想全局使用）：
  ```bash
  # Claude Code 全局
  npx -y skills add <target-skill> -a claude-code -g

  # 通用 Agent 全局
  npx -y skills add <target-skill> -g
  ```
- 如果是 GitHub 单独的 `SKILL.md` 链接或代码片段，直接抓取并规范化保存至 `.claude/skills/<skill-name>/SKILL.md`。

### 3. 安装后验证与汇报
- 安装完成后执行 `npx -y skills list -a claude-code` 验证是否成功挂载；
- 告诉用户触发方式：可以直接在输入框输入 `/<skill-name>` 即可调用，如果当前会话未立即索引，可输入 `/reload-skills` 快速刷新。
