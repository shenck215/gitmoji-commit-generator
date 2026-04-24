---
name: gitmoji-commit-generator
description: 为 Git 变更生成符合 Gitmoji 规范的提交信息（Commit Message）。当用户完成代码修改，需要根据 git diff 总结改动、撰写提交日志、为 staged changes 生成提交标题或按 Gitmoji 风格提交时触发。支持深度 Diff 分析、多维意图匹配以及中英文混合格式。
---

# Gitmoji Commit Generator

按照以下流程生成高质量的 Git Commit Message：

## 核心流程

1.  **扫描变更**：
    - 优先读取暂存区（Staged Changes）的代码差异。
    - 仅当不存在暂存区变更时，才读取未暂存（Unstaged Changes）的代码差异。
    - 总结核心改动逻辑。
2.  **确定意图类型**：
    - 读取 `references/gitmoji_map.md`。
    - 将改动内容与映射表中的意图进行匹配，选择**最准确**的一个作为标题开头。
3.  **撰写信息**：
    - **标题格式**：`:<type>: <subject>`（注意：subject 必须使用中文简要描述）。
    - **正文 (Body) 格式**：
        - 使用无序列表。
        - 格式：`- **[改动点]** [业务背景/技术动机]`。
        - 特殊关注：若涉及 Supabase 变更、跨端适配 (Taro) 或框架特定逻辑 (Umi/Next)，必须在正文中显著标注。

## 约束条件
- 若存在 staged changes，只基于 staged changes 生成提交信息，不混入 unstaged changes。
- 只有在 staged changes 为空时，才基于 unstaged changes 生成提交信息。
- 标题行字数控制在 50 字符以内。
- 正文应侧重于解释“为什么”这样做，而不仅仅是“做了什么”。
