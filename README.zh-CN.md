# netnewswire-guide

[English →](README.md)

**线上站点 →** [https://nnw.elonwoo.com/](https://nnw.elonwoo.com/)

Unofficial visual guide to the NetNewsWire codebase — a capability map plus source-cited flow diagrams showing how its features are built and how data moves through them.

## 这是什么

这是对一个 NetNewsWire fork（`https://github.com/elonwoo/NetNewsWire`）的源码解读图集，基线提交 `512e461782a2d283d71a07f08e38201bf38da310`。

图集包含一张能力地图和五条工作流。每张图上的每个节点都标注了对应的源码文件与行号，在图的交互界面里可以直接点回 GitHub 上的原始位置。所有图都由 `ir/` 下的 JSON IR 生成，并通过结构校验。

站点是纯静态的：打开 `index.html` 即可，也可以直接部署到 Cloudflare Pages，不需要构建步骤。

## 目录结构

| 路径 | 说明 |
| --- | --- |
| `index.html` | 站点入口：总览、指标与六张图的卡片列表 |
| `diagrams/` | 六张自包含的可探索图表 HTML，每张一个文件，无外部依赖 |
| `ir/` | 生成上述图表所用的 JSON IR，一一对应 |

## 六张图

| 标题 | 类型 | 节点 | 文件 |
| --- | --- | --- | --- |
| NetNewsWire 能力地图 | 能力地图 | 81 | `diagrams/netnewswire-capabilities.html` |
| NetNewsWire 刷新管线 | 工作流 | 11 | `diagrams/netnewswire-refresh.html` |
| NetNewsWire 添加订阅 | 工作流 | 17 | `diagrams/netnewswire-subscribe.html` |
| NetNewsWire 已读与星标的状态回写 | 工作流 | 13 | `diagrams/netnewswire-status-sync.html` |
| NetNewsWire 搜索索引 | 工作流 | 16 | `diagrams/netnewswire-search-index.html` |
| NetNewsWire AI 翻译与改写 | 工作流 | 13 | `diagrams/netnewswire-ai-pipeline.html` |

合计 151 个节点、74 条连线。

## 生成方式

每张图由 archify 从 `ir/*.json` 生成，并依次通过四道闸门：

1. `validate` — IR 结构校验
2. `deliver` — 产物落盘与自包含性检查
3. `check` — 图表结构与连线规则检查
4. `browser-check` — 浏览器内的渲染与交互实测

六张图四道闸门全部通过（6 × 4 = 24 次）。

## 许可与非官方声明

本项目不是 NetNewsWire 官方项目。源项目 NetNewsWire 采用 MIT 许可，本图集内容同样以 MIT 许可发布。
