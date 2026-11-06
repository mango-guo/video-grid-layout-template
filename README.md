# 1920×1080 视频文字排版模板 · Video Grid Layout Template

基于 Josef Müller-Brockmann《平面设计中的网格系统》的视频画面排版参考：12 栏网格、字号层级、间距节奏、内容分区与红线标注，随时可作为 16:9 画面的排版底稿。

A 16:9 (1920×1080) text-layout reference for video frames, built on the grid principles in Müller-Brockmann's *Grid Systems in Graphic Design*: 12-column grid, type scale, 12-px spacing rhythm, content zones and redline annotations.

![Annotated layout](previews/layout-annotated.zh.png)

| 带标注 · Annotated | 纯文字 · Clean |
|---|---|
| ![](previews/layout-annotated.en.png) | ![](previews/layout-clean.zh.png) |

## 使用 · Usage

1. 用浏览器打开 `index.html`（中文）或 `index.en.html`（English）。
2. 载入画面：点击“载入画面 / Load frame”，或把图片拖到画面上，或将图片命名为 `frame.jpg` 放在同一目录（已在 `.gitignore` 中忽略，不会被提交）。
3. 顶部按钮可分别开关：网格、内容分区、排版标注、文字；“切换文案”轮换示例文案。
4. 导出 1920×1080 PNG（无界面）：

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars --window-size=1920,1080 --virtual-time-budget=6000 --screenshot=out.png "file://$PWD/index.html?export=1&copy=0"
```

URL 参数 · Params: `export=1` 仅输出画布 · `copy=0–3` 选择文案 · `hide=grid,zones,notes,copy` 隐藏图层。

## 网格规格 · Grid spec

| 项目 | 数值 |
|---|---|
| 左右边距 · side margins | 120 px |
| 上下边距 · top/bottom | 96 px |
| 栏数 · columns | 12 |
| 栏宽 · column | 118 px |
| 栏距 · gutter | 24 px |
| 间距单位 · spacing unit | 12 px → 24 / 36 / 48 / 72 |
| 引题 · eyebrow | 24 px |
| 主标题 · headline | 72 / 84 |
| 正文 · body | 32 / 48 |
| 标注 · data label | 28 + 24 |
| 字幕 · subtitles | 中文 40 / 英文 28，第 3–10 栏居中 |

栏宽计算：`(1920 − 120×2 − 24×11) ÷ 12 = 118`

## 套用到新画面 · Adapting to a new frame

内容分区（A–D）与文字坐标是按示例画面设定的。换画面时：

1. 先找出画面中的**安静区**（暗、平、无运动）放标题，标出**主体动作区**和**高亮区**避开文字。
2. 在 `#zones` 中改分区矩形，在 CSS 中把 `#eyebrow / #headline / #body / #tag` 移到对应栏位。
3. 保持字号层级、12 px 间距和共用左边线不变——这才是跨镜头的一致性。

The A–D zones and text positions are set for the sample frame. For a new shot, find the quiet area for type, mark the hero action and bright areas as no-text, then move the zone rectangles in `#zones` and the text blocks in CSS onto the matching columns. Keep the type scale, spacing unit and shared left edge unchanged.

## 说明 · Notes

- 示例文案与品牌名 “HEARTH” 均为虚构占位。Sample copy and the “HEARTH” brand are placeholders.
- 仓库不含原始参考画面；未载入画面时显示场景示意图。No source footage is included; a schematic stand-in renders until you load a frame.
- 尺寸为 1920×1080 设计像素，需在真实素材和目标设备上检查对比度与可读性。
