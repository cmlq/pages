# 课件类 HTML 视觉规范

## 1. 适用范围

本规范作为当前工作区的全局前端视觉规范，用于后续生成“课件”类 HTML 页面时统一视觉语言、主题变量、布局组件、讲解态交互和响应式行为。

适用对象包括但不限于：

- 课件展示页
- 分页讲解页
- Swiper 轮播式内容页
- 目录页、章节页、结构化知识页
- 对话式、流程式、时间线式、指标式内容页

若具体项目目录下存在更近的页面设计规范、组件规范或任务说明，则以更近文档为准；本规范作为默认全局基线使用。

## 2. 设计目标

- 支持深色模式与浅色模式自动切换
- 所有页面围绕可配置主题色构建
- 视觉风格采用 Apple 风格的半透明卡片、柔和阴影、圆角和层次化留白
- 适配桌面端与移动端
- 适合“可翻页、可讲解、可目录导航”的课件型 HTML

## 3. 核心视觉原则

### 3.1 主题与氛围

- 默认主色为蓝色系，可按项目替换 `--theme-primary`
- 成功、警告、危险、紫色作为辅助语义色
- 浅色模式强调干净、通透、轻量
- 深色模式强调对比、聚焦、沉浸

### 3.2 版式语言

- 页面以全屏视口为基础：`height: 100vh`
- 单页内容推荐包裹在 `.apple-page` 与 `.apple-card` 中
- 内容层级通过标题、子标题、卡片、分栏、强调块建立
- 优先采用高留白、大字号、低噪声布局

### 3.3 交互风格

- Hover 动效以轻微上浮、背景增强、阴影增强为主
- 讲解场景优先使用“当前高亮、同级弱化”的讲解态悬停
- 翻页场景可使用 `swiper-container` / `swiper-slide`
- 导航控件采用半透明圆形按钮与底部分页点
- 交互反馈尽量克制，不使用过重动效

## 4. 主题变量规范

### 4.1 可配置主题色

- `--theme-primary`：主色
- `--theme-success`：成功色
- `--theme-warning`：警告色
- `--theme-danger`：危险色
- `--theme-purple`：辅助紫色

### 4.2 浅色模式基础变量

- `--bg-primary`
- `--bg-secondary`
- `--surface-primary`
- `--surface-secondary`
- `--separator`
- `--label-primary`
- `--label-secondary`
- `--label-tertiary`
- `--shadow-sm`
- `--shadow-md`

### 4.3 深色模式基础变量

通过 `@media (prefers-color-scheme: dark)` 覆盖主题色、背景色、分隔线、文本色和阴影配置。

## 5. 页面骨架与全局基础

### 5.1 全局基础约束

- 统一 `box-sizing: border-box`
- `body` 使用 Apple 风格字体栈
- 页面默认禁止横向滚动，整体基于全视口展示
- 幻灯页内容区允许纵向滚动

### 5.2 课件页面基础容器

- `.swiper-container`：整套课件容器
- `.swiper-slide`：单页课件
- `.apple-page`：单页居中容器
- `.apple-card`：核心内容卡片容器

推荐结构：

```html
<div class="swiper-container">
  <div class="swiper-slide">
    <section class="apple-page">
      <div class="apple-card">
        <!-- page content -->
      </div>
    </section>
  </div>
</div>
```

## 6. 页面类型与组件索引

本规范中的 CSS 实际覆盖了“页面类型 + 内容布局 + 导航控件 + 讲解态交互”四类能力。后续生成课件类 HTML 时，优先从以下结构中组合，而不是重新发明样式体系。

### 6.1 页面类型

- `cover`：封面页
- `directory-grid` / `dir-item`：目录页
- `chapter-cover`：章节封面页

### 6.2 通用内容布局

- `content-title` / `content-sub`：通用标题区
- `two-columns`：双栏布局
- `three-columns`：三栏或自适应多栏布局
- `card`：卡片式内容块
- `apple-list`：列表式内容块
- `structure`：结构图式内容块
- `dialogue`：对话式内容块
- `timeline`：时间线内容块
- `comparison`：对比表内容块
- `step-flow`：步骤流程块
- `callout`：引用块
- `highlight`：高亮块
- `metrics-grid`：指标卡片组
- `accordion`：折叠面板
- `gallery-grid`：图库网格

### 6.3 导航与翻页控件

- `nav-button`
- `nav-prev`
- `nav-next`
- `pagination`
- `pagination .dot`

### 6.4 讲解态悬停工具类

- `presentation-hover-page`：一整页或一个悬停作用域
- `presentation-hover-target`：可被讲解态聚焦的内容块
- `presentation-hover-current`：当前悬停主目标
- `presentation-hover-related`：与当前目标联动高亮的关联块
- `presentation-hover-row`：适用于表格行等行级高亮场景

## 7. 各组件使用说明

### 7.1 封面页 `cover`

适用于整套课件首页。

包含元素：

- 主标题 `h1`
- 副标题 `.subtitle`
- 描述 `.description`
- 翻页提示 `.swipe-hint`

视觉特征：

- 标题采用渐变文字
- 文案居中
- 强调第一屏识别度与开场感

### 7.2 目录页 `directory-grid`

适用于展示章节、模块或页面入口。

特点：

- 使用响应式网格
- 每项由图标、标题、说明组成
- Hover 时轻微上浮

### 7.3 章节封面页 `chapter-cover`

适用于章节切换页。

包含元素：

- 章节编号 `.chapter-number`
- 章节标题 `.chapter-title`
- 章节说明 `.chapter-desc`

### 7.4 通用卡片 `card`

适用于知识点、说明块、总结块、术语块。

特点：

- 半透明背景
- 圆角边框
- 轻微悬浮反馈

### 7.4.1 讲解态悬停 `presentation-hover-*`

适用于讲师现场讲解时，需要用鼠标把观众注意力稳定拉到某个卡片、面板、节点或一组联动元素上的页面。

视觉目标：

- 当前目标明确提亮
- 同页同级元素适度弱化
- 需要联动的元素同步高亮
- 弱化后仍保持可读，不直接消失

推荐粒度：

- 卡片级：适用于知识点卡片、术语卡片、三栏卡片组
- 面板级：适用于左右对比、大区块结构图
- 节点级：适用于流程图、链路图、层级图
- 联动级：适用于“卡片 + 时间节点”“角色节点 + 职责卡”“主节点 + 子节点”这类成组结构

默认排除页面：

- 封面页 `cover`
- 章节封面页 `chapter-cover`

使用约束：

- 同一页优先只保留一种主粒度，不同时混用过多层级
- 如果页面已经以“左右大面板”为主结构，优先做面板级悬停，不要再让面板内部每个小块都单独抢焦点
- 如果页面主题是流程讲解，优先做节点级或联动级悬停
- 如果页面主题是知识分类，优先做卡片级悬停
- 讲解态建议由脚本切换类名，不依赖纯 CSS 猜测页面结构

### 7.5 列表 `apple-list`

适用于要点罗列、结论列举、注意事项说明。

特点：

- 每项自带底部分隔线
- 使用主题色圆点作为视觉引导

### 7.6 结构图 `structure`

适用于层级关系、概念拆解、流程树状说明。

特点：

- 父节点使用左侧主题色强调线
- 子节点使用虚线层级关系

### 7.7 对话式 `dialogue`

适用于角色对话、问答演示、师生互动模拟。

特点：

- 左右对话气泡分离
- 右侧发言可使用主题主色反白

### 7.8 时间线 `timeline`

适用于发展过程、事件序列、教学步骤进程。

特点：

- 左侧竖线串联节点
- 主题色圆点标记时间节点

### 7.9 对比表 `comparison`

适用于方案对比、前后差异、优劣分析。

特点：

- 左右两列对称布局
- 标题区域使用主题色底边强调

### 7.10 步骤流程 `step-flow`

适用于分步骤讲解、方法论说明、操作流程展示。

特点：

- 桌面端步骤横向排布
- 移动端自动转为纵向

### 7.11 引用块与高亮块

包含：

- `callout`
- `highlight`
- `highlight warning`
- `highlight success`

适用于：

- 金句引用
- 核心提示
- 风险提醒
- 正向结论

### 7.12 指标卡片 `metrics-grid`

适用于数字统计、关键指标、成果展示。

特点：

- 大数字主视觉
- 小标签辅助解释

### 7.13 折叠面板 `accordion`

适用于 FAQ、补充内容、展开式说明。

特点：

- 支持收起/展开
- 展开时通过类名 `.open` 控制

### 7.14 网格图库 `gallery-grid`

适用于案例展示、素材墙、图文卡片集。

特点：

- 图片区与说明区分离
- 支持占位图、插画、缩略图卡片

## 8. 响应式规范

### 8.1 移动端断点

- 断点：`max-width: 768px`

### 8.2 移动端适配策略

- `.apple-card` 减少内边距
- 封面主标题缩小
- 章节标题缩小
- 双栏、三栏、对比布局全部收敛为单栏
- 导航按钮尺寸缩小并贴边
- 对话气泡最大宽度放宽到 90%
- 步骤流程改为纵向

## 9. 使用约束

后续生成“课件”类 HTML 时，应默认遵循以下约束：

- 优先复用本规范提供的类名，不重复创建同义样式
- 优先通过修改主题变量换肤，而不是直接改写组件细节
- 页面应维持统一的圆角、阴影、边框透明度和文本层级
- 一页只保留一个主叙事重点，避免信息过载
- 对移动端必须保证单栏可读性和可点击性
- 需要翻页体验时，默认使用全屏页结构
- 需要目录、章节、内容页组合时，优先采用“封面 -> 目录 -> 章节页 -> 内容页”的稳定结构
- 需要讲解态 hover 时，优先复用 `presentation-hover-page` / `presentation-hover-target` / `presentation-hover-current` / `presentation-hover-related`
- 讲解态 hover 的默认原则是“当前高亮、同级弱化、关联联动、封面排除”
- 行级高亮场景优先使用 `presentation-hover-row`

## 10. 推荐生成模板

后续自动生成课件 HTML 时，推荐最小页面顺序如下：

1. 封面页
2. 目录页
3. 章节封面页
4. 1 到 3 页内容讲解页
5. 总结页或高亮结论页

常见内容组合建议：

- 知识讲解：`chapter-cover` + `two-columns` + `card`
- 流程说明：`step-flow` + `callout`
- 对比分析：`comparison` + `highlight`
- 历程说明：`timeline`
- 互动模拟：`dialogue`
- 数据结果：`metrics-grid`
- 讲解态聚焦：`presentation-hover-page` + `presentation-hover-target`
- 联动型讲解：`presentation-hover-page` + `presentation-hover-target` + `presentation-hover-related`

## 11. 可直接复用的原始 CSS

```css
:root {
  /* 主题色 - 可修改任意色值 */
  --theme-primary: #007AFF;
  --theme-success: #34C759;
  --theme-warning: #FF9500;
  --theme-danger: #FF3B30;
  --theme-purple: #AF52DE;
  
  /* 浅色模式基础色 */
  --bg-primary: #FFFFFF;
  --bg-secondary: #F5F5F7;
  --surface-primary: rgba(255, 255, 255, 0.92);
  --surface-secondary: rgba(255, 255, 255, 0.68);
  --separator: rgba(60, 60, 67, 0.12);
  --label-primary: #000000;
  --label-secondary: #3A3A3C;
  --label-tertiary: #6C6C70;
  --shadow-sm: 0 2px 8px rgba(0,0,0,0.04), 0 2px 4px rgba(0,0,0,0.02);
  --shadow-md: 0 8px 20px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.02);
}

@media (prefers-color-scheme: dark) {
  :root {
    --theme-primary: #0A84FF;
    --theme-success: #30D158;
    --theme-warning: #FF9F0A;
    --theme-danger: #FF453A;
    --theme-purple: #BF5AF2;
    
    --bg-primary: #000000;
    --bg-secondary: #1C1C1E;
    --surface-primary: rgba(28,28,30,0.92);
    --surface-secondary: rgba(28,28,30,0.68);
    --separator: rgba(84,84,88,0.2);
    --label-primary: #FFFFFF;
    --label-secondary: #EBEBF5;
    --label-tertiary: #8E8E93;
    --shadow-sm: 0 2px 8px rgba(0,0,0,0.4);
    --shadow-md: 0 8px 20px rgba(0,0,0,0.6);
  }
}

* { margin: 0; padding: 0; box-sizing: border-box; }
body {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Text', 'SF Pro Display', system-ui;
  background: var(--bg-primary);
  color: var(--label-primary);
  overflow: hidden;
  height: 100vh;
}
.swiper-container { width: 100%; height: 100vh; }
.swiper-slide { overflow-y: auto; padding: 20px; }

/* 通用页面容器 */
.apple-page { min-height: 100%; display: flex; align-items: center; justify-content: center; padding: 40px 20px; }
.apple-card { max-width: 1280px; width: 100%; margin: 0 auto; background: var(--surface-primary); backdrop-filter: blur(20px); border-radius: 28px; padding: 48px 40px; box-shadow: var(--shadow-md); border: 0.5px solid var(--separator); }

/* 封面页 */
.cover { text-align: center; }
.cover h1 { font-size: 64px; font-weight: 700; letter-spacing: -0.02em; background: linear-gradient(135deg, var(--label-primary), var(--theme-primary)); background-clip: text; -webkit-background-clip: text; color: transparent; margin-bottom: 16px; }
.cover .subtitle { font-size: 28px; font-weight: 400; color: var(--label-secondary); margin-bottom: 24px; }
.cover .description { font-size: 17px; color: var(--label-tertiary); max-width: 600px; margin: 0 auto 40px; line-height: 1.5; }
.swipe-hint { display: inline-flex; align-items: center; gap: 8px; padding: 8px 20px; background: var(--surface-secondary); border-radius: 999px; font-size: 15px; color: var(--label-secondary); }

/* 目录页 */
.directory-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 24px; margin-top: 24px; }
.dir-item { background: var(--surface-secondary); backdrop-filter: blur(20px); border-radius: 24px; padding: 28px; border: 0.5px solid var(--separator); cursor: pointer; transition: all 0.3s ease; }
.dir-item:hover { transform: translateY(-4px); background: var(--surface-primary); box-shadow: var(--shadow-md); }
.dir-icon { font-size: 40px; margin-bottom: 16px; }
.dir-title { font-size: 24px; font-weight: 600; margin-bottom: 8px; }
.dir-desc { font-size: 15px; color: var(--label-tertiary); line-height: 1.4; }

/* 章节封面页 */
.chapter-cover { text-align: center; }
.chapter-number { font-size: 17px; font-weight: 600; text-transform: uppercase; letter-spacing: 1px; color: var(--theme-primary); margin-bottom: 16px; }
.chapter-title { font-size: 48px; font-weight: 700; letter-spacing: -0.01em; margin-bottom: 24px; }
.chapter-desc { font-size: 21px; font-weight: 400; color: var(--label-secondary); max-width: 700px; margin: 0 auto; line-height: 1.4; }

/* 通用内容样式 */
.content-title { font-size: 34px; font-weight: 700; letter-spacing: -0.01em; margin-bottom: 16px; }
.content-sub { font-size: 17px; color: var(--label-secondary); margin-bottom: 32px; }

/* 分栏布局 */
.two-columns { display: grid; grid-template-columns: 1fr 1fr; gap: 32px; }
.three-columns { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 28px; }

/* 卡片式 */
.card { background: var(--surface-secondary); border-radius: 24px; padding: 24px; border: 0.5px solid var(--separator); transition: all 0.2s; }
.card h3 { font-size: 22px; font-weight: 600; margin-bottom: 12px; }
.card p { font-size: 15px; color: var(--label-tertiary); line-height: 1.4; }
.card:hover { transform: translateY(-2px); background: var(--surface-primary); box-shadow: var(--shadow-sm); }

/* 讲解态悬停 */
.presentation-hover-page { isolation: isolate; }
.presentation-hover-target,
.presentation-hover-row td {
  transition:
    transform 0.22s ease,
    box-shadow 0.22s ease,
    border-color 0.22s ease,
    background 0.22s ease,
    opacity 0.22s ease,
    filter 0.22s ease,
    color 0.22s ease;
}
.presentation-hover-page.presentation-hover-active .presentation-hover-target {
  opacity: 0.42;
  filter: saturate(0.72) brightness(0.88);
  transform: scale(0.988);
}
.presentation-hover-page.presentation-hover-active .presentation-hover-target.presentation-hover-current {
  opacity: 1;
  filter: saturate(1.12) brightness(1.08);
  transform: translateY(-4px) scale(1.01);
  z-index: 6;
  border-color: color-mix(in srgb, var(--theme-primary) 42%, var(--separator));
  background: color-mix(in srgb, var(--theme-primary) 16%, var(--surface-primary));
  box-shadow:
    0 0 0 1px color-mix(in srgb, var(--theme-primary) 22%, transparent),
    0 18px 34px color-mix(in srgb, var(--theme-primary) 16%, transparent),
    var(--shadow-md);
}
.presentation-hover-page.presentation-hover-active .presentation-hover-target.presentation-hover-related {
  opacity: 0.92;
  filter: saturate(1.02) brightness(1.02);
  transform: translateY(-2px) scale(1.004);
  z-index: 5;
  border-color: color-mix(in srgb, var(--theme-primary) 30%, var(--separator));
  background: color-mix(in srgb, var(--theme-primary) 10%, var(--surface-primary));
  box-shadow:
    0 0 0 1px color-mix(in srgb, var(--theme-primary) 14%, transparent),
    0 12px 24px color-mix(in srgb, var(--theme-primary) 10%, transparent),
    var(--shadow-sm);
}
.presentation-hover-page:has(.presentation-hover-row:hover) .presentation-hover-row td {
  opacity: 0.42;
  filter: saturate(0.72) brightness(0.88);
  background: color-mix(in srgb, var(--surface-primary) 82%, transparent);
}
.presentation-hover-page:has(.presentation-hover-row:hover) .presentation-hover-row:hover td {
  opacity: 1;
  filter: none;
  color: var(--label-primary);
  background: color-mix(in srgb, var(--theme-primary) 18%, var(--surface-primary));
  box-shadow:
    inset 0 0 0 1px color-mix(in srgb, var(--theme-primary) 28%, transparent),
    0 12px 24px color-mix(in srgb, var(--theme-primary) 14%, transparent);
}

/* 列表式 */
.apple-list { list-style: none; }
.apple-list li { padding: 16px 0; border-bottom: 0.5px solid var(--separator); font-size: 17px; display: flex; gap: 12px; align-items: flex-start; }
.apple-list li:last-child { border-bottom: none; }
.list-bullet { width: 6px; height: 6px; border-radius: 999px; background: var(--theme-primary); margin-top: 8px; flex-shrink: 0; }

/* 结构图式 */
.structure { display: flex; flex-direction: column; gap: 24px; }
.structure-node { background: var(--surface-secondary); border-radius: 20px; padding: 20px; border-left: 4px solid var(--theme-primary); }
.structure-node h4 { font-size: 18px; font-weight: 600; margin-bottom: 8px; }
.structure-children { margin-top: 16px; padding-left: 24px; display: flex; flex-direction: column; gap: 12px; border-left: 1px dashed var(--separator); }
.structure-child { padding: 12px 16px; background: rgba(0,0,0,0.03); border-radius: 16px; font-size: 15px; }
@media (prefers-color-scheme: dark) { .structure-child { background: rgba(255,255,255,0.05); } }

/* 对话式 */
.dialogue { display: flex; flex-direction: column; gap: 24px; }
.dialogue-item { display: flex; gap: 16px; }
.dialogue-avatar { width: 48px; height: 48px; border-radius: 999px; background: var(--theme-primary); display: flex; align-items: center; justify-content: center; color: white; font-weight: 600; flex-shrink: 0; }
.dialogue-bubble { background: var(--surface-secondary); border-radius: 24px; padding: 16px 20px; max-width: 80%; border: 0.5px solid var(--separator); }
.dialogue-name { font-weight: 600; font-size: 15px; margin-bottom: 6px; color: var(--theme-primary); }
.dialogue-text { font-size: 16px; line-height: 1.4; }
.dialogue-item.right { flex-direction: row-reverse; }
.dialogue-item.right .dialogue-bubble { background: var(--theme-primary); color: white; }
.dialogue-item.right .dialogue-name { color: white; }

/* 时间线 */
.timeline { display: flex; flex-direction: column; gap: 24px; position: relative; padding-left: 30px; }
.timeline::before { content: ''; position: absolute; left: 9px; top: 12px; bottom: 12px; width: 2px; background: var(--separator); }
.timeline-item { position: relative; padding-left: 32px; }
.timeline-item::before { content: ''; position: absolute; left: -21px; top: 8px; width: 12px; height: 12px; border-radius: 999px; background: var(--theme-primary); border: 2px solid var(--bg-primary); box-shadow: 0 0 0 2px var(--theme-primary); }
.timeline-date { font-weight: 600; font-size: 17px; color: var(--theme-primary); margin-bottom: 6px; }
.timeline-title { font-size: 18px; font-weight: 600; margin-bottom: 8px; }
.timeline-desc { font-size: 15px; color: var(--label-tertiary); line-height: 1.4; }

/* 对比表 */
.comparison { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
.comparison-col { background: var(--surface-secondary); border-radius: 24px; padding: 24px; border: 0.5px solid var(--separator); }
.comparison-col h3 { font-size: 22px; font-weight: 600; text-align: center; padding-bottom: 16px; border-bottom: 2px solid var(--theme-primary); margin-bottom: 20px; }
.comparison-row { display: flex; justify-content: space-between; padding: 12px 0; border-bottom: 0.5px solid var(--separator); }
.comparison-label { font-weight: 500; }
.comparison-value { color: var(--label-tertiary); }

/* 步骤流程 */
.step-flow { display: flex; justify-content: space-between; gap: 16px; flex-wrap: wrap; }
.step { flex: 1; min-width: 180px; text-align: center; background: var(--surface-secondary); border-radius: 24px; padding: 24px 16px; position: relative; }
.step-number { width: 40px; height: 40px; background: var(--theme-primary); color: white; border-radius: 999px; display: flex; align-items: center; justify-content: center; font-weight: 700; font-size: 20px; margin: 0 auto 16px; }
.step-title { font-weight: 600; font-size: 18px; margin-bottom: 8px; }
.step-desc { font-size: 14px; color: var(--label-tertiary); }
.step:not(:last-child)::after { content: '→'; position: absolute; right: -20px; top: 50%; transform: translateY(-50%); font-size: 24px; color: var(--separator); }
@media (max-width: 768px) { .step:not(:last-child)::after { display: none; } }

/* 引用块/高亮块 */
.callout { background: var(--surface-secondary); border-radius: 20px; padding: 20px 24px; border-left: 4px solid var(--theme-primary); margin: 24px 0; }
.callout p { font-size: 17px; font-style: italic; color: var(--label-secondary); margin-bottom: 8px; }
.callout-author { font-size: 14px; color: var(--label-tertiary); text-align: right; }
.highlight { background: rgba(0, 122, 255, 0.12); border-radius: 20px; padding: 20px; border: 0.5px solid rgba(0, 122, 255, 0.3); }
.highlight.warning { background: rgba(255, 149, 0, 0.12); border-color: rgba(255, 149, 0, 0.3); }
.highlight.success { background: rgba(52, 199, 89, 0.12); border-color: rgba(52, 199, 89, 0.3); }

/* 指标卡片 */
.metrics-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 24px; }
.metric-card { background: var(--surface-secondary); border-radius: 24px; padding: 24px; text-align: center; border: 0.5px solid var(--separator); }
.metric-value { font-size: 48px; font-weight: 700; color: var(--theme-primary); line-height: 1; margin-bottom: 8px; }
.metric-label { font-size: 15px; color: var(--label-tertiary); }

/* 折叠面板 */
.accordion { border-radius: 20px; overflow: hidden; }
.accordion-item { border-bottom: 0.5px solid var(--separator); }
.accordion-header { padding: 18px 20px; font-weight: 600; font-size: 18px; cursor: pointer; display: flex; justify-content: space-between; align-items: center; background: var(--surface-secondary); transition: 0.2s; }
.accordion-header:hover { background: var(--surface-primary); }
.accordion-icon { font-size: 20px; transition: transform 0.3s; }
.accordion-item.open .accordion-icon { transform: rotate(180deg); }
.accordion-content { max-height: 0; overflow: hidden; transition: max-height 0.3s ease; background: var(--surface-primary); padding: 0 20px; }
.accordion-item.open .accordion-content { max-height: 500px; padding: 20px; }

/* 网格图库 */
.gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 24px; }
.gallery-item { background: var(--surface-secondary); border-radius: 24px; overflow: hidden; border: 0.5px solid var(--separator); transition: 0.2s; }
.gallery-item:hover { transform: translateY(-4px); box-shadow: var(--shadow-md); }
.gallery-image { width: 100%; height: 160px; background: linear-gradient(135deg, var(--surface-primary), var(--separator)); display: flex; align-items: center; justify-content: center; font-size: 48px; }
.gallery-caption { padding: 16px; }
.gallery-title { font-weight: 600; margin-bottom: 6px; }
.gallery-desc { font-size: 13px; color: var(--label-tertiary); }

/* 导航控件 */
.nav-button { position: absolute; top: 50%; transform: translateY(-50%); width: 48px; height: 48px; background: var(--surface-secondary); backdrop-filter: blur(20px); border-radius: 999px; display: flex; align-items: center; justify-content: center; cursor: pointer; border: 0.5px solid var(--separator); color: var(--theme-primary); transition: 0.2s; z-index: 10; }
.nav-button:hover { background: var(--theme-primary); color: white; }
.nav-prev { left: 20px; }
.nav-next { right: 20px; }
.pagination { position: absolute; bottom: 20px; left: 0; right: 0; display: flex; justify-content: center; gap: 8px; }
.pagination .dot { width: 8px; height: 8px; border-radius: 999px; background: var(--label-tertiary); transition: 0.2s; }
.pagination .dot.active { width: 24px; background: var(--theme-primary); }

/* 响应式 */
@media (max-width: 768px) {
  .apple-card { padding: 32px 24px; }
  .cover h1 { font-size: 44px; }
  .cover .subtitle { font-size: 22px; }
  .chapter-title { font-size: 34px; }
  .two-columns, .three-columns, .comparison { grid-template-columns: 1fr; }
  .nav-button { width: 40px; height: 40px; }
  .nav-prev { left: 10px; }
  .nav-next { right: 10px; }
  .dialogue-bubble { max-width: 90%; }
  .step-flow { flex-direction: column; }
  .step:not(:last-child)::after { display: none; }
}
```

## 12. 后续使用约定

从本规范创建新课件 HTML 时，默认先做以下三件事：

1. 先选主题色并决定是否保留自动深浅色模式
2. 先确定页面序列和所需组件组合
3. 再在此规范基础上填充业务内容，不另起一套视觉体系

如后续需要扩展组件，应优先在本文件追加，而不是在不同项目中各自分叉出不兼容版本。
