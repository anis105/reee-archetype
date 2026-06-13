# reee-archetype — CBA · CUBAL 2025-26 球员画像

双联赛球员画像站点。顶部一个标签在 **CBA** 与 **CUBAL** 两个 2025-26 赛季画像页之间切换。

线上地址：<https://anis105.github.io/reee-archetype/>

## 结构

```
index.html                     2 标签 iframe 壳页（CBA | CUBAL），公开无密码
cba_archetype_2025-26.html     CBA 2025-26 球员画像（内部含 CUBA→CBA 升学内容）
cubal_archetype_2025-26.html   CUBAL 2025-26 球员画像
.nojekyll                      关闭 Jekyll，保证带下划线文件名原样发布
```

- 壳页默认显示 CBA，点标签切到 CUBAL；URL 带 `#cba` / `#cubal` 锚点，可直链。
- 当前标签即时加载，另一标签延迟预取，切换无白屏。
- CBA 页为固定宽桌面版，移动端可横向滚动查看；CUBAL 页为响应式。

## 两页来源（溯源）

| 页面 | 来源文件 | 上游 |
|---|---|---|
| CBA | `升学点亮视图.html` 的去密码门快照 | 升学点亮视图生成流程 |
| CUBAL | `cubal_court_archetype_2025-26_no_password.html` 原样复制 | `cubal-archetype` 仓库 `tools/build_court_archetype_viz.py` |

> **重新导入 CBA 页时需重做去密码门**：原 `升学点亮视图.html` 带 PBKDF2 密码门，
> 以 `<!-- AGV1_CSS_START/END -->`、`<!-- AGV1_HTML_START/END -->`、
> `<!-- AGV1_JS_START/END -->` 三段标记包裹，整段删除即得公开版（`<body>` 默认不加锁）。

## 部署

GitHub Pages：Settings → Pages → Deploy from branch **`main` / (root)**。
纯静态，无构建步骤，HTML 文件本身即交付物。
