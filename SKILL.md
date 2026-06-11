---
name: inspur-ppt-skill
description: 生成浪潮/海岳公司风格的汇报、方案、产品介绍、转正汇报、AI 产品发布和内部分享 PPT。优先基于本 skill 的 templates/*.pptx 制作原生 PowerPoint, 也可在用户需要网页演示、横向翻页 deck、单文件 HTML PPT 时使用 assets/template-inspur.html 生成公司风格网页 PPT。适用于用户提到"浪潮风格"、"海岳大模型"、"公司 PPT"、"汇报模板"、"方案 PPT"、"转正汇报"、"产品介绍"、"网页 PPT"等场景。
---

# Inspur PPT Skill

用于制作浪潮/海岳公司风格 PPT。风格依据当前 skill 内的 `templates/` 和 `examples/` 归纳:

- 主色: 深蓝 `#0D48CE/#0E48CE`, 亮蓝 `#1D78FA/#006EFF`, 青绿 `#00A0A0`, 白底和深蓝底交替。
- 字体: 中文优先 `Microsoft YaHei`/`微软雅黑`, 英文和数字优先 `Arial`/`Inter`。
- 气质: 企业科技、可信、清爽、信息密度中高, 避免花哨装饰。
- 常见版式: 封面、目录、章节页、指标卡、流程图、三/四列能力卡、左右图文、案例页、对比表、收束页。

## 工作流

### 1. 判断交付形态

默认选择 **原生 PPTX**:

- 用户要"公司 PPT"、"汇报"、"方案"、"转正汇报"、"产品介绍"、"可以编辑的 PPT"。
- 先读 `references/native-pptx-workflow.md`。
- 优先复制并改造 `templates/汇报模板.pptx`; 新员工转正场景使用 `templates/新员工转正汇报模板.pptx`。

只有在用户明确需要网页、HTML、横向翻页、单文件演示、浏览器打开时, 选择 **网页 PPT**:

- 先读 `references/html-layouts.md`。
- 复制 `assets/template-inspur.html` 到目标项目的 `index.html`。
- 生成后运行 `node <SKILL_ROOT>/scripts/validate-inspur-deck.mjs <index.html>`。

### 2. 需求对齐

如果用户只给了主题, 最多问 1-3 个关键问题。优先问:

1. 受众和场景: 内部汇报、客户方案、产品发布、述职/转正、技术分享?
2. 页数或演讲时长: 10 分钟约 8-10 页, 20 分钟约 12-16 页, 30 分钟约 18-24 页。
3. 是否有旧 PPT、文档、数据、截图、必须使用的模板?

如果信息足以开工, 直接做合理假设并继续。

### 3. 先定结构再写页面

用公司汇报的默认叙事:

1. 封面: 标题、部门/作者、日期、英文副标或口号。
2. 目录: 3-5 个部分, 编号用 `01/02/03/04`。
3. 背景/问题: 现状、痛点、趋势或客户需求。
4. 方案/产品: 架构、能力、流程、核心优势。
5. 实践/案例: 场景、落地路径、效果数据。
6. 总结/计划: 价值、下一步、资源诉求或 Q&A。

详细视觉规则读 `references/style-guide.md`。

### 4. 使用素材

资源导览:

```
inspur_ppt_skill/
├── SKILL.md
├── templates/
│   ├── 汇报模板.pptx
│   └── 新员工转正汇报模板.pptx
├── examples/
│   └── *.pptx
├── assets/
│   └── template-inspur.html
├── references/
│   ├── style-guide.md
│   ├── native-pptx-workflow.md
│   ├── html-layouts.md
│   └── checklist.md
└── scripts/
    └── validate-inspur-deck.mjs
```

不要把 `examples/浪潮海岳商业AI产品方案V2.pptx` 整体复制到新项目里, 它体积很大。只把它作为风格和内容参考。

### 5. 质量检查

交付前必须读 `references/checklist.md` 并自检。重点:

- 标题、正文、图表不进入页脚/页码区域。
- 一页只表达一个中心观点, 不把长文档硬塞进单页。
- 颜色不跑偏: 蓝白科技主调, 少量青绿或橙色只做强调。
- 中文大标题不超过两行; 客户方案页避免口号化空话。
- PPTX 必须可编辑; HTML 必须本地打开可翻页。

## 参考来源

本 skill 的组织方式参考 `guizang-ppt-skill` 的分层方法: `SKILL.md` 放核心流程, `references/` 放可按需加载的细则, `assets/` 放模板, `scripts/` 放校验脚本。不要把参考项目的品牌、赞助信息或视觉风格写进浪潮/海岳输出物。
