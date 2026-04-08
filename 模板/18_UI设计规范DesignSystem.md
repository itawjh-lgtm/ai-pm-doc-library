# UI设计规范(Design System) — 通用提示词模板

> 使用方法：复制以下全部内容 → 粘贴到任意大模型 → 替换所有 [占位符] → 即可生成完整文档

---

# Role
你是一位拥有12年经验的资深UI设计系统架构师，曾在字节跳动/腾讯等头部互联网公司主导Design System搭建。精通Apple HIG、Material Design 3规范和WCAG 2.1无障碍标准，擅长构建基于Design Token的可扩展设计系统。熟练运用Atomic Design（原子设计）方法论，从Token → 原子 → 分子 → 组织 → 模板 → 页面逐层构建组件库，确保设计一致性、开发效率和多端适配能力。

# Step-back Prompt
在构建设计系统之前，先思考以下高层问题：
1. 该产品的品牌差异化体现在哪里？设计系统如何承载品牌识别度？
2. 设计系统需要支持多少个端（iOS/Android/Web/小程序）？跨端一致性和平台特性如何平衡？
3. 团队规模和协作方式如何？设计系统的维护和迭代机制是什么？

# Task
请为 [产品名称] 构建一套完整的UI设计规范文档，包含Design Token体系、色彩/字体/间距/投影规范、组件状态矩阵、响应式断点和深色模式完整规范。

# Context
- 平台：[iOS/Android/Web/多端]
- 品牌调性：[关键词：如科技感/温暖/专业/年轻活力]
- 目标用户审美偏好：[用户群体特征]
- 参考产品/风格：[参考1、参考2]
- 设计工具：[Figma/Sketch]
- 前端技术栈：[React/Flutter/SwiftUI/原生]

# Few-shot Example

以下为"AI写作助手App"的Design Token片段示例：

```
## Design Token — 色彩
| Token名称 | Light值 | Dark值 | 使用场景 |
|-----------|---------|--------|---------|
| color.primary.default | #2563EB | #60A5FA | 主按钮/链接/激活态 |
| color.primary.hover | #1D4ED8 | #93C5FD | 主按钮悬停 |
| color.primary.pressed | #1E40AF | #3B82F6 | 主按钮按下 |
| color.bg.primary | #FFFFFF | #1A1A2E | 页面主背景 |
| color.bg.secondary | #F8FAFC | #252540 | 卡片/模块背景 |
| color.text.primary | #0F172A | #F1F5F9 | 主文字 |

## 组件状态矩阵 — Button
| 状态 | 背景色Token | 文字色Token | 边框 | 投影 | 光标 |
|------|-----------|-----------|------|------|------|
| Default | color.primary.default | color.text.inverse | none | elevation.sm | pointer |
| Hover | color.primary.hover | color.text.inverse | none | elevation.md | pointer |
| Active/Pressed | color.primary.pressed | color.text.inverse | none | none | pointer |
| Disabled | color.bg.disabled | color.text.disabled | none | none | not-allowed |
| Loading | color.primary.default(50%opacity) | - | none | none | wait |
| Error | color.error.default | color.text.inverse | none | elevation.sm | pointer |
```

# Output Format

## 一、设计原则（3-5条）
每条原则须包含：原则名称、一句话定义、正面示例、反面示例。

## 二、Design Token体系

### Token命名规范
| 层级 | 命名规则 | 示例 |
|------|---------|------|
| 全局Token(Global) | color.[色彩角色].[色阶] | color.blue.500 |
| 语义Token(Alias) | color.[用途].[状态] | color.primary.default |
| 组件Token(Component) | [组件].[属性].[状态] | button.bg.hover |

### 色彩Token
| Token名称 | Light值 | Dark值 | 使用场景 | WCAG对比度 |
|-----------|---------|--------|---------|-----------|

### 字体Token
| Token名称 | 字族 | 字号 | 行高 | 字重 | 字间距 | 使用场景 |
|-----------|------|------|------|------|--------|---------|

### 间距Token
| Token名称 | 数值 | 使用场景 |
|-----------|------|---------|
| spacing.xs | 4pt | 图标与文字间距 |
| spacing.sm | 8pt | 紧凑元素间距 |
| spacing.md | 12pt | 标准内间距 |
| spacing.lg | 16pt | 标准元素间距 |
| spacing.xl | 24pt | 模块间距 |
| spacing.2xl | 32pt | 大区块间距 |
| spacing.3xl | 48pt | 页面级间距 |

### 投影/高度Token(Elevation)
| Token名称 | Light值(box-shadow) | Dark值(边框/叠加) | 使用场景 |
|-----------|-------------------|------------------|---------|
| elevation.none | none | none | 平面元素 |
| elevation.sm | 0 1px 2px rgba(0,0,0,0.05) | 1px border rgba(255,255,255,0.05) | 卡片 |
| elevation.md | 0 4px 6px rgba(0,0,0,0.1) | 1px border rgba(255,255,255,0.08) | 浮层/下拉菜单 |
| elevation.lg | 0 10px 15px rgba(0,0,0,0.1) | 2px border rgba(255,255,255,0.1) | 弹窗/Modal |
| elevation.xl | 0 20px 25px rgba(0,0,0,0.15) | 2px border rgba(255,255,255,0.12) | 全屏浮层 |

### 圆角Token
| Token名称 | 数值 | 使用场景 |
|-----------|------|---------|
| radius.none | 0 | 无圆角 |
| radius.sm | 4pt | 标签/小按钮 |
| radius.md | 8pt | 输入框/卡片 |
| radius.lg | 12pt | 大卡片/图片 |
| radius.xl | 16pt | 弹窗/底部Sheet |
| radius.full | 9999pt | 圆形头像/药丸按钮 |

## 三、色彩体系

### 品牌色
| 色彩角色 | 色阶 | Light色值 | Dark色值 | 使用场景 | WCAG AA(在白底/黑底上) |
|---------|------|----------|---------|---------|---------------------|

### 功能色
| 色彩角色 | Light色值 | Dark色值 | 使用场景 |
|---------|----------|---------|---------|
| Success | #______ | #______ | 成功状态/正向操作 |
| Warning | #______ | #______ | 警告状态/需注意 |
| Error | #______ | #______ | 错误状态/危险操作 |
| Info | #______ | #______ | 信息提示/中性引导 |

### 中性色(灰度)
| 层级 | Light色值 | Dark色值 | 使用场景 |
|------|----------|---------|---------|
| Gray-50 | | | 页面背景 |
| Gray-100 | | | 卡片背景/分割线 |
| Gray-200 | | | 边框/禁用背景 |
| Gray-300 | | | 占位符文字 |
| Gray-500 | | | 次要文字 |
| Gray-700 | | | 主要文字(Light) |
| Gray-900 | | | 标题文字(Light) |

## 四、字体规范

### 字体选择
| 平台 | 中文 | 英文/数字 | 等宽(代码) |
|------|------|----------|-----------|
| iOS | PingFang SC | SF Pro | SF Mono |
| Android | [自定义/系统默认] | Roboto | Roboto Mono |
| Web | [自定义/系统默认] | [自定义/系统默认] | [自定义/系统默认] |

### 字号层级（≤6级）
| 层级名称 | Token | 字号 | 行高 | 字重 | 使用场景 |
|---------|-------|------|------|------|---------|
| Display | font.display | 28pt | 36pt | Bold(700) | 页面大标题(极少使用) |
| Heading1 | font.h1 | 22pt | 30pt | Semibold(600) | 页面标题 |
| Heading2 | font.h2 | 18pt | 26pt | Semibold(600) | 模块标题 |
| Body | font.body | 16pt | 24pt | Regular(400) | 正文内容 |
| Caption | font.caption | 14pt | 20pt | Regular(400) | 辅助说明 |
| Small | font.small | 12pt | 16pt | Regular(400) | 标签/时间戳 |

## 五、核心组件规范

### 组件状态矩阵

每个组件须覆盖以下状态：

| 状态 | 说明 | 视觉变化 |
|------|------|---------|
| Default | 默认静止态 | 基础样式 |
| Hover | 鼠标悬停(Web/桌面端) | 背景色加深/投影增加 |
| Active/Pressed | 按下态 | 背景色更深/缩放0.95 |
| Focused | 键盘聚焦 | 添加焦点环(2px品牌色) |
| Disabled | 不可操作 | 降低透明度(40%)/灰色 |
| Loading | 加载中 | Spinner/骨架态 |
| Error | 错误态 | 红色边框/提示文字 |

### 按钮(Button)
| 类型 | 尺寸(高度) | 内间距 | 圆角 | 字号 | 状态覆盖 |
|------|----------|--------|------|------|---------|
| Primary | L:48pt M:40pt S:32pt | 水平16pt | radius.md | body/caption | Default/Hover/Active/Disabled/Loading |
| Secondary | 同上 | 同上 | 同上 | 同上 | 同上 |
| Text/Ghost | 同上 | 水平8pt | 同上 | 同上 | Default/Hover/Active/Disabled |

### 输入框(Input)
| 属性 | 规范 | 状态覆盖 |
|------|------|---------|
| 高度 | 48pt(标准)/40pt(紧凑) | Default/Focused/Error/Disabled |
| 圆角 | radius.md | |
| 内间距 | 水平12pt | |
| 标签 | 浮动标签(Material风格)/固定标签(上方) | |

### 卡片(Card)
### 导航栏(Navigation)
### 弹窗(Dialog/Sheet)
### Toast/Snackbar
### 列表项(List Item)
### 标签页(Tabs)

（每个组件按照上述Button格式输出完整规范）

## 六、图标规范
| 属性 | 规范 |
|------|------|
| 风格 | [线性/面性/双色] |
| 网格 | 24×24pt画布，20×20pt安全区域 |
| 尺寸系列 | 16pt(密集) / 20pt(紧凑) / 24pt(标准) / 32pt(大) |
| 线宽 | 1.5pt(标准) / 2pt(加粗) |
| 圆角 | 内角1pt，外角按比例 |
| 颜色 | 使用语义Token(color.icon.primary / secondary / disabled) |

## 七、动效规范
| 场景 | 动画类型 | 时长 | 缓动曲线 | 触发条件 | 性能要求 |
|------|---------|------|---------|---------|---------|
| 微交互(按钮/开关) | scale/color | 100-200ms | ease-out | 用户操作 | 60fps |
| 转场(页面切换) | slide/fade | 200-400ms | cubic-bezier(0.4,0,0.2,1) | 导航 | 60fps |
| 加载(骨架屏) | shimmer | 1500ms循环 | linear | 数据加载 | 60fps |
| 强调(成功/完成) | bounce/confetti | 300-600ms | spring(damping:0.6) | 关键节点 | 30fps可接受 |

## 八、响应式断点(Responsive Breakpoints)

| 断点名称 | 宽度范围 | 典型设备 | 栅格列数 | 边距 | 水槽(Gutter) |
|---------|---------|---------|---------|------|------------|
| Mobile S | <375px | iPhone SE | 4列 | 16px | 8px |
| Mobile | 375-428px | iPhone 14/15 | 4列 | 16px | 8px |
| Mobile L | 428-768px | iPhone Pro Max | 4列 | 20px | 12px |
| Tablet | 768-1024px | iPad Mini | 8列 | 24px | 16px |
| Desktop | 1024-1440px | 笔记本 | 12列 | 32px | 24px |
| Desktop L | >1440px | 大屏显示器 | 12列 | auto(最大内容宽度1200px) | 24px |

### 断点布局策略
| 场景 | Mobile | Tablet | Desktop |
|------|--------|--------|---------|
| 导航 | 底部Tab | 侧边栏(可折叠) | 侧边栏(固定) |
| 列表 | 单列 | 双列网格 | 三列网格 |
| 详情页 | 全屏 | 半屏弹窗 | 右侧面板 |
| 弹窗 | 底部Sheet | 居中Dialog | 居中Dialog |

## 九、深色模式完整规范

### 适配原则
| 原则 | 说明 |
|------|------|
| 背景层级 | 使用不同深度的暗色(#121212→#1E1E1E→#2C2C2C)区分层级 |
| 文字色 | 主文字使用87%白色透明度，次文字使用60%，禁用使用38% |
| 品牌色 | 使用品牌色的浅色变体(色阶300-400)以确保在深色背景上可读 |
| 投影替代 | 深色模式下投影不明显，使用边框(1px lighter border)替代 |
| 图片 | 添加scrim叠加层(rgba(0,0,0,0.1))降低图片亮度 |
| 插画 | 提供深色专用版本或降低饱和度 |

### 深色模式色值映射
| 语义Token | Light值 | Dark值 | 说明 |
|-----------|---------|--------|------|
| bg.primary | #FFFFFF | #121212 | 最底层背景 |
| bg.secondary | #F5F5F5 | #1E1E1E | 卡片/浮层背景 |
| bg.tertiary | #EEEEEE | #2C2C2C | 输入框/Tag背景 |
| surface.elevated | #FFFFFF + shadow | #2C2C2C + border | 抬升表面 |
| text.primary | rgba(0,0,0,0.87) | rgba(255,255,255,0.87) | 主文字 |
| text.secondary | rgba(0,0,0,0.60) | rgba(255,255,255,0.60) | 次文字 |
| divider | rgba(0,0,0,0.12) | rgba(255,255,255,0.12) | 分割线 |

### 深色模式切换机制
| 切换方式 | 说明 |
|---------|------|
| 跟随系统 | 默认选项，监听系统暗色模式设置 |
| 手动切换 | 设置页提供Light/Dark/Auto三档 |
| 过渡动画 | 全局色值渐变，时长300ms，ease-in-out |

# Constraints
- 色彩必须同时标注Light/Dark两套色值，并通过WCAG AA对比度验证
- 字号层级≤6级，全部基于统一的基数递增（建议4pt基数）
- 间距系统基于4pt基数的倍数关系
- 组件须覆盖全部7种状态：Default/Hover/Active/Focused/Disabled/Loading/Error
- 所有Token使用语义化命名（color.primary.default而非color.blue.500），支持主题切换
- 响应式断点至少覆盖Mobile/Tablet/Desktop三档，标注栅格/边距/水槽
- 深色模式为必填完整章节，包含色值映射表和适配原则
- 须考虑无障碍对比度（WCAG AA标准：正文≥4.5:1，大字≥3:1）
- 使用Mermaid语法输出: classDiagram用于Token层级关系

# Temperature Guidance
- Design Token和色值定义部分：Temperature 0.1（要求绝对精确）
- 组件状态矩阵和规范参数部分：Temperature 0.2（要求严谨一致）
- 设计原则和品牌调性部分：Temperature 0.5（允许创意表达）
- 整体建议Temperature：0.2
