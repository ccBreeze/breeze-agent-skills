# DrawIO 图形规范指南

> drawio 文件基于 mxGraph 的 XML 结构。本规范覆盖 XML 生成所需的全部格式约束。

## 输出规范

所有生成代码必须符合 DrawIO XML 语法，并输出完整文件结构：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<mxfile>
  <diagram id="GeneratedDiagram" name="自动生成的图表">
    <mxGraphModel>
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        <!-- 生成的节点/连接线 -->
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

- `vertex="1"` 代表节点，必须包含 `mxGeometry` 坐标信息
- `edge="1"` 代表连接线，需指定 `source` 和 `target`
- style 必须严格匹配 DrawIO 规则：`rounded=1`、`edgeStyle=orthogonalEdgeStyle`、`jumpStyle=arc;jumpSize=6`、`endArrow=classic` 等
- 弱化元素禁止使用 `opacity`，必须使用配色方案"弱化元素"颜色，配合更细边框/虚线实现

完整模板见 `assets/template.drawio`。

## 基础要求

- 展示在 A4 纸上（`pageWidth="1300" pageHeight="1000"` 或按需调整），选择合适的字体大小
- 字体必须全部加粗（`fontStyle=1`），标题等关键元素字号加大（`fontSize=20`），正文 `fontSize=12-14`
- 线段统一使用 3pt 宽度（`strokeWidth=3`），核心流程线 4pt，保证在论文打印后依然清晰可见
- 所有文本格式（加粗、下标上标、公式代码）必须正确实现
- 使用标准 drawio 文件格式，保证兼容性
- 组件必须完全容纳文字，避免文字溢出
- 所有线条必须设置 `jumpStyle=arc` 和 `jumpSize=6`，确保交叉处清晰可辨
- 所有连接线拐点必须设置 `rounded=1` 保证美观
- 统一箭头样式 `endArrow=classic`

## 布局规范

- **画布边距**：所有图形内容距离画布边缘左右间距至少 100px，上下间距至少 50px；当画布尺寸远大于内容区域时，内容必须在画布中水平居中和垂直居中
- 组件间垂直和水平间距保持统一（30-50px 为宜）
- 将相关的组件放入容器或组中，以提高图表的可读性和组织性
- 对齐方式使用 center，保持一致性
- 使用网格对齐（`gridSize=10`）辅助布局
- 容器内子元素与边界保持 30-40px 内边距
- 避免组件和连接线重叠，特别是避免线条穿过文字

## 连接线规范

- 连接线默认使用 `edgeStyle=orthogonalEdgeStyle`
- 所有箭头样式必须统一（`endArrow=classic`）
- 多条连接线汇入同一组件时，应从不同方向进入（如左、中、右）
- 同一起点的多条连接线应适当分散起点位置
- 为所有交叉的连接线添加跳跃样式（`jumpStyle=arc`）
- 长距离连接线应适当设置航点（`waypoints`）引导路径
- 使用 `exitX/exitY` 和 `entryX/entryY` 精确控制出入点
- **绝对禁止连接线遮挡文字和组件标签**
- 同一水平层、相邻泳道之间的单跳链路（如 A → Event → B）优先使用直线，不要弯折；推荐 `edgeStyle=none;rounded=0`，并确保两端节点垂直中心对齐（`exitY=0.5` / `entryY=0.5`）
- 当用户明确要求"线体不要弯曲"时，禁止引入 waypoints 和正交拐点，直接改为同轴直线连接

> 线条交叉/遮挡问题的实战处理方案见 `references/line-avoidance.md`。

## 组件连接设计

- 组件使用浮动连接点，而非固定连接点
- 相关组件应放置在合理的相对位置，减少连线复杂度
- 复杂流程应分层次展示，避免连线交叉过多

## 文本与组件规范

- 所有组件内文本必须加粗（`fontStyle=1`）
- 数学公式使用 HTML 格式：`h<sup>v</sup>` 和 `h<sub>inter</sub>`，不要使用 LaTeX 格式
- 公式可以根据条件更换字体
- 数学符号如点乘必须使用正确格式：◎ 应写为 `&odot;`
- 合理使用 `waypoints`：在需要精确控制连接路径时，可以使用固定的 `waypoints` 来避免线条交叉和文字遮挡
- 组件大小应根据内容自适应，保持适当留白
- 流程图中的**方法节点**（函数/调用点）必须写"方法名 + 作用说明"两行，不可只写调用名；作用说明建议使用"动词 + 业务结果"（例如"广播关闭事件，通知子应用清缓存"）
- **事件节点**建议写"事件名 + 含义/触发时机"两行，避免只保留事件常量导致语义不完整

## 视觉层次（核心流程突出）

颜色值从 `references/color-schemes.md` 中所选配色方案的表格取值。

**核心流程节点与连线**：

```
节点: fillColor=<核心节点填充>;strokeColor=<核心节点边框>;strokeWidth=3;shadow=1
连线: strokeWidth=4;strokeColor=<核心节点边框>
枢纽节点: fillColor=<枢纽节点填充>;strokeColor=<枢纽节点边框>;shadow=1（用于关键函数/入口）
```

**辅助/配置元素（弱化处理）**：

```
节点: fillColor=<弱化元素填充>;strokeColor=<弱化元素边框>;strokeWidth=2
连线: strokeColor=<弱化元素边框>;strokeWidth=2
详情展开线: dashed=1;dashPattern=8 4;strokeColor=<弱化元素边框>;strokeWidth=2
```

**功能模块内部节点**（如增强器、中间件等同级组件）：

```
容器: fillColor=<容器背景填充>;strokeColor=<容器背景边框>;strokeWidth=3
子节点: fillColor=<功能节点填充>;strokeColor=<功能节点边框>;strokeWidth=3
```

## 命名与结构规范

- `diagram name` 必须命名为有意义的名称（如"多模态特征融合流程"）
- 组件 ID 必须反映其功能（如 `with-cache`、`request-interceptor`）
- 连接线 ID 应反映实际连接关系，使用 `edge-` 前缀（如 `edge-compose-to-chain`）
- 相关元素应放在一起，提高代码可读性

## 特殊场景处理

- 复杂图表应考虑分层或分区域展示
- 多条平行连接线应保持一致的间距和样式
- 长路径连接应使用中间节点或分段处理
- 双向连接使用两条独立的连接线而非双向箭头
