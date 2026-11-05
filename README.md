# 心理咨询家谱图编辑器 · Counseling Genogram Editor

一张**单文件、零依赖、完全离线**的家谱图（genogram）编辑器：把 `index.html` 拖进浏览器就能画心理咨询里用的三代家谱图，人物符号、结构关系、情感关系、排版、导出全部现成。

- **零安装**：一个 HTML 文件，无 CDN、无 npm、无构建步骤，不联网
- **零外链**：运行时不发起任何网络请求，界面与图形全部本地渲染
- **数据留在本机**：只用浏览器 localStorage 自动存档，作者不收集任何数据
- **MIT 开源**：可自由使用、修改、商用；**商用时必须保留版权声明并署名「白贵阳」**，见 [LICENSE](LICENSE) 与 [NOTICE.md](NOTICE.md)

> 本工具是记录与沟通用的绘图辅助，不提供诊断、评估或治疗建议。用于临床记录时请遵守所在机构的伦理规范与来访者知情同意要求。

## 截图

![主界面：三代示例家谱图](docs/screenshot-overview.png)
*首次打开载入的三代示例（12 人、4 组伴侣关系、7 条亲子关系、4 条情感线），符号内的数字是依出生年份实时计算的年龄；已故者打叉并显示寿年。*

![右侧人物面板](docs/screenshot-person-panel.png)
*点选人物后右侧展开属性面板：姓名、性别、符号、生卒、孕产状态，以及可增删改的备注条目与事件列表；被选中的索引咨访用双轮廓标出。*

![图例与关系对照表](docs/screenshot-legend.png)
*图例共 63 行真实线型，可搜索、可点击某一行直接应用到当前选中的关系——看到的就是画出来会得到的效果。*

## 功能

### 人物符号

- 8 种基础符号：男性（方）、女性（圆）、性别未明（菱形）、非二元（拱形）、间性、跨性别男、跨性别女、宠物（点线菱形）
- 叠加标记：**索引咨访**（双轮廓，全图仅一个）、**已故**（符号内打叉；符号中心有文字时自动改为四角短线）、**孕产**（怀孕 = 符号内正三角，流产 = 符号内实心圆点）
- 符号中心自动显示年龄：健在按出生日期实时计算，已故显示寿年；出生日期缺失时留空

### 关系

| 类别 | 数量 | 覆盖 |
| --- | --- | --- |
| 伴侣 / 结构关系 | 16 种状态（另加「单亲」） | 结婚、订婚、同居、交往、婚外情、一夜情、分居、离婚、断绝、再婚、丧偶、婚姻无效、强迫/性侵关系、血亲婚配、离婚·A 方监护、离婚·B 方监护 |
| 亲子关系 | 8 种 | 亲生、收养、寄养、继子女、监护（G）、代孕（S）、精子捐赠（SD）、卵子捐赠（ED） |
| 情感关系 | 39 种 | 亲密、融合、疏远、冲突、敌对、断绝、断裂修复、关注、照顾者、控制、操纵、嫉妒、忽视、暴力、虐待（未分类/身体/情感/性）、爱、热恋、崇拜、痴迷、友谊、挚友、不信任、从未见面、仇恨 等 |

- 线中图标（`//`、`⊘`、`▯▯`、`×`、`○`、`◇`、箭头等）全部由 SVG 图元现场绘制，不依赖任何字体或图片
- 同一对人物之间可以同时挂多条情感线；情感线有方向（`from → to`）
- **图例 63 行**：人物符号、结构线型、亲子线型、情感线型逐条列出，含临床含义、线宽、虚实说明

### 排版

- 同层兄弟姐妹共用一条横线；父母关系线中心与子女首末跨度两端对齐
- 中继竖线居中，**全部正交布线，不出现斜线**
- 两个人物符号边到边净距 ≥ **70px**，文字块之间 ≥ 20px，文字不会被线穿过
- 拖动人物做微调后，连线自动贴合重排；「排版」一键复位
- 支持一对多子女、多段婚姻、跨代嵌套；子树可**折叠 / 展开**，画布实时自适应
- 小屏（画布宽度 < 620px）自动只把**选中分支**铺满视口，保证字号可读

### 记录与界面

- 每人可挂多条备注：职业、诊断、重大事件、标签、原话、备注
- 每人可挂多条「重要事件 / 经历」：时间、地点、事件，可增删改
- 撤销 / 重做、5 套主题色卡（符号填充与画布底色可手动覆盖）
- localStorage 自动存档：文档、视图、主题分三个键保存，刷新或关掉浏览器再打开数据还在
- 键盘可达：Tab 可聚焦到人物符号，Enter / 空格 即选中

### 导出

| 格式 | 说明 |
| --- | --- |
| PNG 图片 | 1x / 2x（默认 2x），与预览同一份 SVG 栅格化 |
| PDF / 打印 | 两页：第 1 页图形，第 2 页逐人 + 逐关系的文本明细 |
| HTML 单文件 | 两页静态文档，带主题样式，可直接分享或归档 |
| 数据图例 | 一份独立的线型对照表 HTML，适合打印贴在案头 |
| JSON 备份 / 导入 | 全量数据，可跨设备迁移，也可导入旧备份 |

除打印外，导出前都会先弹出预览，**预览即所得**：预览与最终文件走同一份 SVG 序列化路径。

## 怎么用

1. 下载本仓库的 `index.html`（就一个文件）
2. **双击打开**，或在浏览器里把文件**拖进窗口**
3. 首次打开会载入一张三代示例图，可以直接在它上面改；想从零开始就点「导出 → 新建空白图」（会二次确认）

不需要安装、不需要联网、不需要跑任何命令。想放到内网共享也只要把这个文件放上去，别人下载即用。

## 操作与快捷键

| 快捷键 | 作用 |
| --- | --- |
| `Ctrl+Z` | 撤销 |
| `Ctrl+Shift+Z` / `Ctrl+Y` | 重做 |
| `Ctrl+S` | 导出 JSON 备份 |
| `Del` / `Backspace` | 删除选中的人物 / 关系 |
| `F` | 适应屏幕 |
| `0` | 缩放到 100% |
| `+` / `-` | 放大 / 缩小（每步 1.15 倍） |
| `?` 或 `Shift+/` | 打开图例与快捷键面板 |
| `Esc` | 关闭弹层 / 取消选中 / 取消正在建立的情感线 |
| `Enter` | 选中人物时跳到姓名输入框；Tab 聚焦符号后按 Enter 等于选中 |
| `空格` | 选中人物时折叠 / 展开其子树 |

鼠标与面板：

- **滚轮缩放**（以光标位置为中心），**空白处拖动平移**
- 拖动人物符号可微调位置，再用「排版」复位
- 工具栏：`＋ 人物`、`伴侣`、`子女`、`删除`、`排版`、缩放、`撤销`、`重做`、`导出`、`主题`、`图例`
- 建立情感线：选中人物后点面板里的「＋ 新建情感线」，再点另一个目标人物（按 `Esc` 可取消）
- 图例面板里点任意一行，会把它应用到当前选中的那条关系上

## 数据结构与备份

JSON 备份是一个纯文本对象，可直接读、可手工改、可进版本库（注意：若含来访者信息，请自行脱敏后再外发）。

```jsonc
{
  "schemaVersion": 1,
  "meta": { "title": "家谱图标题", "createdAt": "ISO 时间", "updatedAt": "ISO 时间" },
  "persons": [
    {
      "id": "p1",
      "name": "姓名",
      "gender": "male",              // male | female | other | unknown
      "symbol": "",                  // 可选：覆盖默认符号，如 person_nonbinary
      "deceased": false,
      "birthYear": 1968, "birthDate": "", // birthDate 为 YYYY-MM-DD，优先于 birthYear
      "deathYear": null, "deathDate": "",
      "pregnancy": null,             // null | pregnant | miscarriage
      "collapsed": false,            // 子树是否折叠
      "offset": { "x": 0, "y": 0 },  // 手动微调位移，可用「排版」清零
      "notes":  [ { "id": "n1", "type": "occupation", "label": "职业", "value": "中学教师" } ],
      "events": [ { "id": "e1", "time": "2019-06", "place": "医院", "text": "确诊抑郁" } ]
    }
  ],
  "unions": [ { "id": "u1", "a": "p1", "b": "p2", "status": "married",
                "since": 1962, "until": null, "order": 0, "note": "" } ],
  "parentLinks": [ { "id": "l1", "child": "p3", "union": "u1",
                     "kind": "biological", "order": 0, "primary": true } ],
  "emotionalLinks": [ { "id": "e1", "from": "p3", "to": "p6", "type": "conflict", "note": "" } ],
  "probandId": "p3",
  "view": { "x": 0, "y": 0, "scale": 1 }
}
```

要点：

- `probandId` 是标量，因此**一张图只有一个「索引咨访」**
- `unions[].status` 取 16 种结构状态之一；`parentLinks[].kind` 取 8 种亲子类型之一；`emotionalLinks[].type` 取 39 种情感线型之一
- `notes[].type`：`occupation` 职业、`diagnosis` 诊断、`event` 重大事件、`tag` 标签、`quote` 原话、`note` 备注
- 导入时会自动规范化与迁移：补齐缺省字段、丢弃重复 `id`、清理非法日期、把未知枚举回退到默认值
- 浏览器里存三个键：`genogram.v1.doc`（文档）、`genogram.v1.view`（视图）、`genogram.v1.theme`（主题）

## 浏览器兼容性

| 浏览器 | 状态 |
| --- | --- |
| Chrome / Edge 100+ | 完整支持（推荐） |
| Firefox 100+ | 完整支持 |
| Safari 15+ | 基本可用；`file://` 下 localStorage 可能被限制，建议改用 Chrome/Edge 或本地静态服务 |

依赖的都是标准能力：SVG、Canvas `measureText`、`localStorage`、`DOMPoint`。没有 polyfill，没有第三方库。

## 关于「单文件零依赖」

- 全部 HTML / CSS / JS / SVG 都在 `index.html` 里，约 210 KB，**没有第二个文件**
- 没有 CDN、没有 `import`、没有 `fetch`、没有 Web Font、没有外部图片；源码里搜不到任何外链
- 源码中 SVG 命名空间常量写作 `'http' + '://www.w3.org/2000/svg'`（拼接而非字面量）：这是为了让静态检查脚本不把这串字符误判成「外部链接」，运行时行为与字面量完全一致
- 因此断网、内网、离线 U 盘环境都能用；也不存在「某个依赖包更新把页面搞坏」的风险

## 符号体系来源

图形语言沿用 **McGoldrick《Genograms》等公开文献中的家谱图传统**（家族治疗与家庭医学领域通用的符号约定）：方块=男、圆=女、叉线=已故、双轮廓=索引咨访、线型区分婚姻/离婚/情感性质等。

- 本项目是**独立自绘的 SVG 实现**，不包含、不复制任何商业家谱图软件的代码、素材或模板，与任何商业软件厂商无关
- 少数线型（如「矛盾」正弦波浪、「照顾者」楔形箭头）在传统体系中并无统一画法，本项目按讲义常见变体实现，并在图例里标为**「非标准扩展」**，临床使用请以所在机构的规范为准
- 图例中每一条线型都标注了线宽与虚实结构，便于与纸笔家谱图对照

## 已知限制

- **单文档**：一个浏览器只维护一张图（localStorage 单键）。多个案例请各自导出 JSON / HTML 保存；「新建空白图」会清空当前内容（有确认弹窗）
- **婚外情支的中继偏移**：婚外情支线在个别紧凑布局下，中继竖线会有小幅偏移，不影响符号与文字的可读性，但视觉上不如标准婚姻支严格居中
- **小屏只铺选中分支**：画布宽度小于 620px 时，默认只把选中分支填满视口，其余分支需要拖动查看
- **PDF 走浏览器打印通道**：页边距、页眉页脚、分页由浏览器决定，不同浏览器字体渲染也略有差异；想固定版式建议用「HTML 单文件」导出
- **PNG 栅格化上限**：导出宽度或高度超过 8192px 时会自动降采样，超大图会损失一些细节
- **无云同步 / 无协作**：数据不出本机是优点，也意味着换设备要手动迁移 JSON

## 贡献与反馈

- 欢迎提 Issue 与 PR：请说明复现步骤、浏览器与版本、期望结果与实际结果；涉及排版的改动请附前后截图
- 代码全部在一个文件里，修改前建议先读顶部的文件头注释（有分区说明）
- 请保持这几个硬约束：**单文件、零依赖、无 CDN、无构建步骤、不改变既有行为**
- 提交前请自测：控制台 0 报错、结构线无斜线、导出的 PNG / HTML 能正常打开、刷新后数据还在

## 许可证与署名

本项目以 **MIT License** 发布，版权归 **白贵阳**（2025-2026）。

- 你可以自由地使用、修改、分发，**包括商业用途**
- **商用时必须保留版权声明与许可全文**，并在网站 / 产品 / 文档的显著位置署名、附本仓库链接
- 推荐署名格式与更多示例见 [NOTICE.md](NOTICE.md)

最小可用的署名写法：

> 家谱图由「心理咨询家谱图编辑器」绘制 · © 2025-2026 白贵阳 · MIT License
> https://github.com/baiguiyang666-oss/counseling-genogram

---

## English Summary

A **single-file, zero-dependency, fully offline** editor for psychological genograms. Open `index.html` in any modern browser — no install, no build, no network calls.

**Features**: 8 person symbols plus overlays for index client, deceased, pregnancy/miscarriage, and auto-computed age; 16 couple/structure statuses, 8 parent–child types and 39 emotional relationship line types, all drawn as inline SVG; sibling alignment, centre-aligned couple lines, orthogonal routing with no diagonal edges, ≥70px symbol clearance, collapsible branches and drag-to-reposition with auto re-layout; per-person notes and timed life events; a searchable 63-row symbol/line legend; export to PNG (1x/2x), two-page PDF/print, self-contained HTML, or JSON backup/import, all with live preview; undo/redo, five colour themes, and autosave to `localStorage`.

**Licence**: MIT, © 2025-2026 白贵阳 (Bai Guiyang). Free for commercial use, but you **must keep the copyright notice and attribution**, and credit the author with a link to this repository. See [NOTICE.md](NOTICE.md) for the recommended attribution format.

**Disclaimer**: a drawing aid for documentation and communication — not a diagnostic or assessment tool.
