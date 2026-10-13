# 个人传记 biography-skill 🖊️

![version](https://img.shields.io/badge/version-1.2.0-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![platform](https://img.shields.io/badge/platform-WorkBuddy-orange)

> 帮助普通人写个人传记的 Agent Skill：访谈式采集回忆、自动整理时间线、章节化成稿。
> 用户只需要聊天式地回忆人生，剩下的交给 AI。
>
> An Agent Skill that helps ordinary people write their own biography through natural conversation — interview-style memory collection, automatic timeline organization, and chapter-based drafting. [English README](#english-readme)

每个人都值得被记录，但传记写作对普通人来说门槛太高——不知道怎么开头、记不住具体时间、一写就变成流水账。这个 Skill 把「写传记」变成一场自然的对话：AI 扮演专业传记访谈者，像聊天一样引导你回忆人生中的关键时刻、重要人物与转折点，自动把零散回忆整理成时间线，最后组织成连贯、有温度的章节成稿。

## 功能特性

- **访谈式采集**：像专业传记作者一样，用有温度的一连串提问引导回忆，一次只问一个问题，从细节切入而非问卷式盘问
- **结构化整理**：自动把零散回忆按时间线归档，识别人物关系与主题线索，补全时间、地点；前后说法冲突时主动与你确认，绝不自行编补
- **章节化成稿**：按八章结构把素材组织成连贯章节，保留你自己的语言风格和情感色彩，拒绝干巴巴的流水账
- **渐进式写作**：支持随时中断、随时续写。人生很长，传记可以慢慢写
- **照片与插图**：访谈中在合适时机自然引导你提供老照片，照片按年份和章节登记归档；全程没有照片时，成稿后会询问是否配 AI 生成示意插图（明确标注「AI 生成示意图」，绝不冒充真实照片）
- **隐私本地优先**：所有素材都存在本地工作目录，不上传任何远程服务，敏感内容由你自己决定保留还是删除

## 快速开始

**WorkBuddy 用户：**

1. 下载本仓库的 [`biography-skill.skill`](./biography-skill.skill) 文件
2. 在 WorkBuddy 中加载该 `.skill` 文件
3. 说出触发词，例如：
   - 「启动个人传记」
   - 「帮我写传记」
   - 「帮我爸写一本传记」
4. 跟随 AI 的提问聊天式回忆；随时说「今天就到这里」，下次接着说「续写传记」即可继续
5. 说「整理成稿」开始章节化写作，每章写完会给你确认后再定稿

**其他 AI 助手：** 直接让助手读取 [`skill/biography-skill/SKILL.md`](./skill/biography-skill/SKILL.md) 并按其中的指令工作即可。

## 演示示例

想看看实际效果？[`examples/`](./examples/) 目录里有一段完整的虚构演示：

- [`examples/demo-interview.md`](./examples/demo-interview.md)：访谈对话片段 → 素材落库记录 → 章节成稿开头，展示从聊天到成稿的完整链路

## 它是怎么工作的

```
聊天回忆 → 访谈式采集（问题库引导，保留原话）
        → 结构化整理（时间线 + 人物表 + 冲突确认）
        → 传记蓝图（章节划分，与你确认）
        → 章节化成稿（每章确认后定稿，支持无限续写）
```

写作过程中 AI 会在工作目录维护一份结构化的素材库：

```
biography-data/
├── profile.md        # 传主档案：姓名、出生年月、籍贯
├── timeline.md       # 时间线：按年份归档的回忆条目
├── characters.md     # 人物表：重要人物及其关系
├── open-questions.md # 待确认事项：前后矛盾、缺失信息
├── photos.md        # 照片登记簿：文件名、内容、年份、关联章节
├── photos/          # 照片原件（你自行放入）
└── materials/        # 原始素材：按主题分文件，保留原话
```

## 质量保证

Skill 内置「质检四查」机制（[`skill/biography-skill/references/quality-checklist.md`](./skill/biography-skill/references/quality-checklist.md)），每章定稿前必须逐项通过：

1. **事实可溯**：人名、年代、事件都能指回素材记录，发现一处无出处即不交付
2. **文风一致**：全书人称、称谓、腔调统一，对话保留传主原话
3. **文字清晰**：通读无错字病句，清除 AI 套话（「时光荏苒」出现一个删一个）
4. **节奏**：各章密度均衡，章首连读能讲清一生脉络

## 目录结构

```
biography-skill/
├── README.md                     # 本文件
├── LICENSE                       # MIT License
├── SKILL.md                      # 根级 Skill 说明（WorkBuddy 规范 frontmatter）
├── biography-skill.skill         # 打包文件（WorkBuddy 直接加载）
├── examples/
│   └── demo-interview.md         # 虚构演示：访谈 → 素材 → 成稿
└── skill/
    └── biography-skill/
        ├── SKILL.md              # 核心执行指令（AI 的工作流）
        └── references/
            ├── interview-questions.md  # 访谈问题库（七大主题 + 追问技巧）
            ├── chapter-templates.md    # 章节结构模板（八章结构 + 文风规范）
            └── quality-checklist.md    # 质检四查（事实可溯/文风一致/文字清晰/节奏）
```

## 常见问题

**Q：素材会泄露吗？**
不会。所有素材保存在你本地工作目录的 `biography-data/` 下，Skill 不包含任何网络上传行为。你可以随时删除整个目录。

**Q：可以给已故的长辈写吗？**
可以。由直系亲属发起，访谈对象从「传主本人」变成「记得他的人」——Skill 的访谈与成稿流程同样适用。

**Q：写到一半能停吗？**
随时停。素材和进度都落盘保存，下次说「续写传记」即可接着聊。

## License

[MIT](LICENSE) © 2026 Zhongqiang Wang

---

## English README

**biography-skill** helps ordinary people write their own biography — no writing skills required. You chat; the AI does the interviewing, organizing, and drafting.

### How it works

1. Load `biography-skill.skill` in WorkBuddy (or point any AI assistant at `skill/biography-skill/SKILL.md`)
2. Say a trigger phrase, e.g. "启动个人传记" / "帮我写传记"
3. The AI interviews you one question at a time, records your memories verbatim into a local structured archive (`biography-data/`: profile, timeline, characters, raw materials)
4. When you're ready, say "整理成稿" — it proposes a chapter blueprint for your approval, then drafts chapter by chapter (2,000–4,000 chars each), preserving your voice and wording
5. Every chapter passes a four-point quality check before delivery: traceable facts, consistent voice, clean prose, balanced pacing

### Key properties

- **Interview, not questionnaire**: one question at a time, detail-driven follow-ups
- **Nothing fabricated**: missing memories are marked as open questions, never invented
- **Privacy-first**: all materials stay in your local workspace; nothing is uploaded
- **Photos & illustrations**: the AI asks for old photos at natural moments and files them by year and chapter; if none are available, it offers clearly-labeled AI-generated illustrations after the text is delivered
- **Resumable forever**: stop anytime, continue anytime

See `examples/demo-interview.md` for a full (fictional) demo of the interview-to-chapter pipeline.

License: [MIT](LICENSE) © 2026 Zhongqiang Wang
