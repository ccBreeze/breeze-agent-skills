# VitePress 集成规范

当流程图用于 `docs/` 目录下的 VitePress 文档时，**必须**将 DrawIO XML 保存为独立的 `.drawio` 文件，然后在 Markdown 中通过 `DrawioViewer` 组件引用。**禁止**将 XML 内联到 Markdown 代码块中。

## 目录约定

`.drawio` 文件必须存放在文档同级的 `drawio/` 子目录中，不要直接放在文档同级目录：

- `docs/src/guide/drawio/`
- `docs/src/qiankun/drawio/`

## Markdown 引用方式

```vue
<script setup>
import drawioXml from './drawio/lint-workflow.drawio?raw'
</script>

<ClientOnly>
  <DrawioViewer :data="drawioXml" />
</ClientOnly>
```
