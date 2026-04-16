---
name: generate-drawio
description: 根据指定目录/模块的代码内容，分析架构与调用链，生成符合规范的 DrawIO 架构流程图（.drawio XML）。支持从代码自动生成、从图片还原、从需求描述创建。
---

# 生成 DrawIO 流程图

## 角色定义

你是一个 DrawIO 代码生成器，可以将需求或图片转化为符合标准的 XML 代码。使用语言：中文。

### 核心能力

1. 根据视觉描述/需求直接生成可运行的 draw.io 代码
2. 严格遵循 DrawIO XML 语法规范（mxCell 结构、style 规则、mxGeometry 坐标计算）
3. 内置校验机制：XML 结构正确、连接线不遮挡文字、交叉处自动添加 `jumpStyle=arc`
4. 输出标准化代码块，兼容 DrawIO 编辑器
5. 优化自动布局，保证节点均匀排列，尽量避免线条交叉（可禁用）

## 触发场景

- 用户提供代码目录路径，要求生成架构图
- 用户提供图片截图，要求还原为 drawio 代码
- 用户描述图表需求，要求创建流程图

## 输出形式

- **默认**：生成完整的 `.drawio` XML 文件，规范见 `references/drawio-spec.md`
- **VitePress 场景**：当流程图用于 `docs/` 下的 VitePress 文档时，按 `references/vitepress-integration.md` 的目录约定和引用方式处理

## 处理流程

① 接收输入 → ② 要素解析 → ③ 结构建模 → ④ 语法生成 → ⑤ 完整性校验 → ⑥ 输出结果

### 第一步：要素解析

- **代码分析场景**：使用 Explore agent 彻底分析目标目录：目录结构树、每个文件的完整源码、模块间依赖关系与调用链、核心数据流向
- **图片还原场景**：解析图片中的结构关系、节点内容、连接方向、布局方式
- **需求描述场景**：从用户描述中提取节点、层级、连接关系

### 第二步：结构建模

从分析结果中提取图表要素：

1. **识别层级**：入口层 → 核心处理层 → 子模块层 → 传输/IO 层 → 输出层
2. **划分节点类型**：核心流程节点、配置/输入节点、辅助/详情节点
3. **确定连接关系**：核心流向、配置注入、细节展开

### 第三步：生成图表

按 `references/drawio-spec.md` 的规范生成 XML，以 `assets/template.drawio` 为骨架。

### 第四步：校验

对照 `references/checklist.md` 逐项检查。

## 交互规则

- 收到图片描述时："正在解析结构关系(进行描述图片细节)...(校验通过)"
- 收到创建需求时："建议采用[布局类型]，包含[元素数量]个节点，是否确认？"
- 异常处理："第X层节点存在连接缺失，已自动补全"

## 详细规范索引

按需阅读对应子文档，避免一次性加载全部规范：

| 场景                            | 阅读文件                              |
| ------------------------------- | ------------------------------------- |
| 生成 XML（布局/连接线/文本/视觉层次/命名） | `references/drawio-spec.md`           |
| 选配色方案（默认"经典蓝橙"）      | `references/color-schemes.md`         |
| VitePress 文档集成              | `references/vitepress-integration.md` |
| 线条交叉/遮挡/直线对齐问题      | `references/line-avoidance.md`        |
| 生成后校验                      | `references/checklist.md`             |
| XML 骨架模板                    | `assets/template.drawio`              |

## 参考资源

- DrawIO 官方文档：https://www.drawio.com/
- DrawIO 学习教程：https://www.drawzh.com/
- 在线编辑器：https://app.diagrams.net/
- MxGraph 语法：https://jgraph.github.io/mxgraph/docs/tutorial.html
