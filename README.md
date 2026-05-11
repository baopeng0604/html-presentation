# html-presentation

Apple 风 / Notion 风 HTML 演示文稿生成器 —— 一个 Claude Code Skill，用于快速生成可用于视频分镜、内容展示、技术分享的专业 HTML 幻灯片。

## 特性

- **Apple/Notion 风格**: 黑底白字，紫色标题 + 黄色强调，极简专业
- **16:9 响应式布局**: 使用 `clamp()` 弹性字号，CSS Grid/Flexbox 布局
- **完整 Slide Engine**: 翻页切换、进度条、导航点、键盘/触摸操作
- **丰富的内置组件**: 卡片、徽章、对比栏、步骤流、引用框、IPO 流程图、提示词展示等
- **淡入动画**: 逐元素延迟动画，增强演示节奏感
- **纯静态 HTML**: 零依赖，浏览器直接打开即可演示

## 安装

### 前置条件

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 已安装

### 安装 Skill

```bash
# 克隆仓库到本地
git clone https://github.com/baopeng0604/html-presentation.git

# 软链接到 Claude Code skills 目录，即可自动加载
ln -s $(pwd)/html-presentation ~/.claude/skills/html-presentation

Note:
clause 对话中，需要 /reload-plugins
```

Claude Code 会自动发现 `~/.claude/skills/` 下的 Skill，无需额外配置。

## 使用方法

在 Claude Code 对话中使用 `/html-presentation` 显式调用 Skill，例如：

> /html-presentation 帮我生成一个 10 页的 HTML 演示文稿，介绍大模型的工作原理，风格用苹果风黑底

> /html-presentation 做一个关于 React 19 新特性的技术分享 slides，需要有对比展示和流程图

Claude 会自动：
1. 规划内容结构（封面 → 痛点 → 核心内容 → 总结）
2. 生成包含翻页、进度条、导航点的完整 HTML 文件
3. 根据主题匹配合适的组件（卡片、步骤流、对比栏等）

生成后直接用浏览器打开 `.html` 文件即可演示。

### 键盘快捷键

| 按键 | 功能 |
|------|------|
| `→` / `↓` / `Space` | 下一页 |
| `←` / `↑` | 上一页 |
| `Home` | 跳到首页 |
| `End` | 跳到末页 |
| `T` | 切换逐字稿栏 显示/隐藏 |
| `J` | 逐字稿向下滚动一行 |
| `K` | 逐字稿向上滚动一行 |
| 点击右侧圆点 | 跳转到指定页 |

### 逐字稿 / 照读脚本

每页幻灯片支持通过 `data-notes` 属性添加完整照读脚本，覆盖当前页所有信息点：

```html
<section class="slide" data-notes="大家好，欢迎来到今天的分享。我是...">
```

- AI 生成 PPT 时会自动为每页编写完整演讲稿
- 演示时底部显示当前页逐字稿，**按 `T` 键切换显示/隐藏**
- 无 `data-notes` 的页面自动隐藏栏位
- 翻页时逐字稿自动跟随切换

## 设计规范

| 用途 | 颜色值 | 说明 |
|------|--------|------|
| 主背景色 | `#000000` | 纯黑色 |
| 主文字色 | `#ffffff` | 纯白色 |
| 标题文字色 | `#b98eff` | 紫色 |
| 强调文字色 | `#ffc402` | 黄色 |
| 次要文字色 | `#888888` | 浅灰色 |

字体: Inter (英文/数字) + Noto Sans SC (中文)，通过 Google Fonts 加载。

## 可用组件

| 组件 | 类名 | 用途 |
|------|------|------|
| 卡片 | `.card` / `.card-grid` | 内容块，支持 2/3 栏 |
| 徽章 | `.badge` | 标签/分类 |
| 高亮条 | `.highlight-bar` | 强调内容 |
| 对比栏 | `.vs-col` | 对比展示 |
| 步骤流 | `.steps` / `.step` | 流程展示 |
| 引用框 | `.quote-block` | 引言/金句 |
| IPO 圆 | `.ipo-circle` | I-P-O 流程图 |
| 提示框 | `.prompt-box` | 提示词展示 |
| 逐字稿栏 | `.transcript-bar` | 底部演讲稿/备注显示，按 T 切换 |
| 发光效果 | `.glow` | 装饰背景光晕 |
| 封面标签 | `.cover-tag` | 封面元数据 |

## TODO

- [ ] **亮色主题**: 新增 Apple Keynote 白底风格，当前仅支持黑底
- [ ] **更多视觉风格**: 终端风、杂志风、渐变弥散风、赛博朋克风
- [ ] **PPTX 导出**: 将 HTML 幻灯片导出为 .pptx 文件
- [ ] **演讲者模式**: 独立窗口显示逐字稿 + 计时器 + 下一页预览
- [ ] **自动播放**: 定时翻页，适合展厅/展台循环播放
- [ ] **全屏 API**: 浏览器全屏模式，隐藏浏览器 UI
- [ ] **幻灯片总览**: 类似 Keynote 的灯箱视图，一览所有页面
- [ ] **图片/图表组件**: 支持插图、数据图表的专用布局组件
- [ ] **更多动画预设**: 除 fade-up 外，增加 slide-in、scale-in 等入场效果
- [ ] **打印样式**: 适合打印/导出 PDF 的样式表
- [ ] **嵌入视频/iframe**: 在幻灯片中嵌入视频或网页

## 项目结构

```
html-presentation/
├── SKILL.md                      # Skill 定义文件（样式规范 + 使用说明）
├── templates/
│   └── presentation.html         # HTML 模板（含完整 Slide Engine）
└── README.md
```

## 参考来源

- 原始仓库: https://github.com/baopeng0604/html-presentation
- 视频教程: [手把手教你打造专属HTML SKILL！让AI完全懂你的设计风格](https://www.bilibili.com/video/BV1HToiBCEwg/?share_source=copy_web&vd_source=712f0e9d936cbf0122fb49cc19ca5abb)

## License

MIT
