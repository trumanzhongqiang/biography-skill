---
name: biography-skill
description: "帮助普通人写个人传记：访谈式采集回忆、自动整理时间线、章节化成稿。触发词：'启动个人传记'、'个人传记'、'帮我写传记'、相关自然语言请求。"
version: 1.0.0
allowed-tools: Bash, Read, Write, Edit
compatibility: Windows/macOS/Linux. Requires WorkBuddy.
metadata:
  emoji: "🖊️"
---

# 个人传记（biography-skill）

帮普通人把自己的一生写成一本传记。用户只需要像聊天一样回忆人生，AI 负责访谈引导、素材整理和成稿写作。

## 使用方法

1. 在 WorkBuddy 中加载 `biography-skill.skill` 文件（或让助手读取本仓库 `skill/biography-skill/SKILL.md`）。
2. 说出触发词，例如「启动个人传记」或「帮我写传记」。
3. 跟随 AI 的提问聊天式回忆，素材自动归档到本地工作目录。
4. 任何时候都可以说「今天就到这里」，下次随时续写；说「整理成稿」即可开始章节化写作。

完整执行指令见 `skill/biography-skill/SKILL.md`，访谈问题库与章节模板见 `skill/biography-skill/references/`。
