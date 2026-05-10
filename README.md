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

将此仓库克隆到本地，然后在 Claude Code 中注册 Skill:

```bash
# 克隆仓库
git clone https://github.com/juanjuanjie/html-presentation.git
```

在 Claude Code 的配置中添加此 Skill 路径（CLAUDE.md 或 settings.json），Claude 即可在对话中自动识别并使用。

## 使用方法

在 Claude Code 对话中直接描述需求，例如：

> 帮我生成一个 10 页的 HTML 演示文稿，介绍大模型的工作原理，风格用苹果风黑底

> 做一个关于 React 19 新特性的技术分享 slides，需要有对比展示和流程图

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
| 点击右侧圆点 | 跳转到指定页 |

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
| 发光效果 | `.glow` | 装饰背景光晕 |
| 封面标签 | `.cover-tag` | 封面元数据 |

## 项目结构

```
html-presentation/
├── SKILL.md                      # Skill 定义文件（样式规范 + 使用说明）
├── templates/
│   └── presentation.html         # HTML 模板（含完整 Slide Engine）
└── README.md
```

## 参考来源

- 原始仓库: https://github.com/juanjuanjie/html-presentation
- 视频教程: [手把手教你打造专属HTML SKILL！让AI完全懂你的设计风格](https://www.bilibili.com/video/BV1HToiBCEwg/?share_source=copy_web&vd_source=712f0e9d936cbf0122fb49cc19ca5abb)

## License

MIT
