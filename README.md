# 论文阅读工作流

一个面向 Codex 的中文论文阅读 Skill，用于把单篇技术论文整理成有来源依据的结构化笔记，并继续处理公式、图表、指标和术语追问。用户明确要求时，它也可以从 Zotero 获取论文、更新既有 Notion 数据库条目，并在写入后回读验收。

## 主要能力

- 完整笔记默认严格使用 `TL;DR + Background + Motivation + Method + Experiments + Drawbacks` 六个顶层部分，不自行增加论文信息表、目录或参考资料等模块。
- 除章节标题外，笔记正文默认不使用加粗。
- 区分论文定义、实验直接证据、阅读者推断和尚未验证内容。
- 详细解释核心公式的直觉、作用、计算顺序、关键符号、假设和适用边界。
- 将图表证据自然融入它所支持的现有章节，不另设图表解读模块或逐图卡片；除非用户明确要求，否则不截图、不上传、不嵌入图片。
- 安全更新既有 Notion 条目，保留数据库属性，并在异步写入后重新获取页面验收。

## 安装

### 推荐：直接克隆到 Codex Skills 目录

```bash
git clone https://github.com/COK-ZhangZiliang/paper-reading-workflow.git \
  ~/.codex/skills/paper-reading-workflow
```

仓库根目录就是完整 Skill，克隆后无需再复制子目录。

若目标目录本身就是通过上述命令创建的 Git 克隆，可更新到最新版本：

```bash
git -C ~/.codex/skills/paper-reading-workflow pull --ff-only
```

若目标目录存在但不是该仓库的 Git 克隆，不要直接执行更新命令或覆盖其中内容；请先备份原目录，再选择新的安装目录或重新克隆。

论文阅读和本地笔记生成不依赖在线连接器。从 Zotero 取文或写入 Notion 时，目标机器还需要相应连接器、本地服务与访问权限。

安装后，在新的 Codex 对话中调用：

```text
使用 $paper-reading-workflow 精读这篇论文，并把中文笔记写入数据库对应项。
```

## 目录结构

```text
paper-reading-workflow/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── full-note-and-evidence.md
    ├── live-publication.md
    └── technical-explanations.md
```

Skill 标识必须使用 ASCII kebab-case，因此内部名称为 `paper-reading-workflow`；界面名称、使用说明和工作流内容均为中文。
