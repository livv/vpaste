# CLAUDE.md

本文档为 Claude Code (claude.ai/code) 在 vPaste_pages 代码库中工作提供指导。

## 项目概览

vPaste_pages 是 vPaste（一款 macOS 剪贴板管理应用）的静态营销网站。项目使用纯 HTML5、CSS3 和原生 JavaScript ES6+ 构建，无需构建系统或包依赖。

## 技术栈

- **前端**：原生 HTML5、CSS3、ES6+ JavaScript
- **无框架**：不使用 React、Vue、Angular 或其他前端框架
- **CSS**：自定义属性（变量）、Flexbox、Grid 布局
- **无包管理器**：所有资源均为本地自包含文件

## 项目结构

```
vPaste_pages/
├── index.html          # 主落地页
├── privacy.html        # 隐私政策页面
├── terms.html          # 服务条款页面
├── assets/
│   ├── css/
│   │   └── styles.css  # 主样式表
│   └── img/
│       ├── icon.png    # 应用图标
│       └── screenshot.png  # 应用截图
├── js/
│   └── i18n.js         # 国际化模块
└── CLAUDE.md          # 本文档
```

## 开发命令

由于这是静态网站且无构建系统，标准开发命令不适用。使用系统内置 HTTP 服务器或任何静态文件服务器进行测试：

```bash
# Python 3
python -m http.server 8000

# 或使用 Node.js（如果可用）
npx http-server -p 8000
```

## 核心特性

### 国际化 (i18n)
- 中英双语支持
- 通过 `js/i18n.js` 中的 `toggleLanguage()` 函数实现语言切换
- 语言状态保存在 localStorage 中
- 所有文本内容使用 data 属性进行翻译

### 响应式设计
- 移动端优先方法
- 断点：768px（平板）、1024px（桌面）
- 使用 CSS 自定义属性实现流体排版和间距

### 无障碍访问
- 语义化 HTML5 元素
- 屏幕阅读器 ARIA 属性
- 键盘导航支持
- 高对比度和焦点指示器

## 代码规范

### HTML
- 使用 `<header>`、`<main>`、`<nav>`、`<footer>` 等语义化结构
- 国际化使用 data 属性：`data-i18n="key"` 和 `data-i18n-placeholder`
- SEO 和响应式视口的 Meta 标签

### CSS
- BEM 风格的类命名约定
- CSS 自定义属性用于主题
- 移动端优先的媒体查询
- 平滑过渡和动画效果

### JavaScript
- ES6+ 模块 (`type="module"`)
- 事件委托模式处理导航
- 使用 `const`/`let` 声明变量
- 箭头函数和现代语法

## 常见任务

### 添加新内容
1. 直接编辑 HTML 文件 - 无需编译
2. 在 `js/i18n.js` 的相应语言对象中添加翻译
3. 遵循现有的语义结构和类命名模式

### 修改样式
1. 更新 `:root` 中的 CSS 自定义属性进行全局更改
2. 直接编辑 `assets/css/styles.css`
3. 保持移动端优先的渐进增强方法

### 语言切换
- 语言状态由 `js/i18n.js` 管理
- 使用 `data-i18n` 属性标记可翻译元素
- 更改后测试两种语言版本

## 测试

需要手动测试：
- 在多设备测试（移动端、平板、桌面）
- 验证中文和英文布局
- 使用屏幕阅读器检查无障碍访问
- 使用 W3C 验证器验证 HTML/CSS

## 近期开发背景

项目近期专注于优化语言切换按钮设计：
- 从分段式双按钮改为简洁的单按钮设计
- 当前状态指示：显示目标语言（例如中文模式下显示"English"）
- 统一在三个页面实现（index.html、privacy.html、terms.html）