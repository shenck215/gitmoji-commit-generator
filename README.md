# Gitmoji Commit Generator

一个用于 Codex 的 Gitmoji Commit Message 生成 skill。它会读取当前仓库的 Git diff，根据改动意图选择合适的 Gitmoji 标识符，并生成中文提交标题与正文。

## 功能

- 优先基于 staged changes 生成提交信息。
- 当没有 staged changes 时，自动回退到 unstaged changes。
- 根据 `references/gitmoji_map.md` 匹配最合适的 Gitmoji 类型。
- 输出中文 subject，并在正文中说明改动动机。
- 对 Supabase、Taro、Umi、Next 等特定技术栈变更做显著标注。

## 安装

将本仓库放入 Codex skills 目录：

```bash
git clone <repo-url> ~/.codex/skills/gitmoji-commit-generator
```

然后在 Codex 中使用：

```text
Use $gitmoji-commit-generator to generate a Gitmoji commit message from the current staged changes.
```

## 目录结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── gitmoji_map.md
```

## 输出格式

标题：

```text
:<type>: <中文提交标题>
```

正文：

```text
- **[改动点]** [业务背景/技术动机]
```

