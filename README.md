# Nucleus Investment — Hugo 站点骨架

一个面向核相关投资公司的 Hugo 静态站点基础骨架。设计目标：简洁、专业、金融友好、易扩展。

## 功能概览
- 标准 Hugo 结构与可扩展配置（菜单、分类、Sitemap、Robots、Privacy）。
- 轻量自定义主题 `atomic-core`：模块化 partials（head、header/nav、footer）、基础布局（base/list/single）、最小样式。
- 核心页面：Home（Hero）、About、Strategy、Team、News/Insights、Contact。
- Archetypes：`default`、`post`、`person`；Shortcodes：`button`（后续可扩展）。
- Data 目录：公司与合规元数据（地址、隐私提示、独立/中立声明）。

## 目录结构
```
nuclear-invest-hugo/
  archetypes/             # 内容模板
  config/_default/        # 站点配置（hugo.toml）
  content/                # 内容页（About/Strategy/Team/News/Contact）
  data/                   # 公司与合规数据（company.yaml / compliance.yaml）
  static/                 # 静态资源（robots.txt 等）
  themes/atomic-core/     # 轻量主题
    layouts/_default/     # base/list/single 基础模板
    layouts/partials/     # head/header/footer partials
    layouts/shortcodes/   # button 等短代码
    static/css/           # 主题样式（main.css）
    static/img/           # 主题图片（logo.svg）
```

## 本地开发
前置：安装 Hugo（建议 extended 版）。
- macOS（Homebrew）：`brew install hugo`
- Ubuntu/Debian：`apt install hugo`
- 或从官方 Releases 下载二进制（extended）。

开发与预览：
- 在项目根目录运行：`hugo server -D`
- 浏览器访问：`http://localhost:1313`

构建静态文件：
- 在项目根目录运行：`hugo`
- 生成目录：`public/`

## 内容与主题扩展
- 新增文章：`hugo new news/my-post.md`（使用 `archetypes/post.md`）
- 新增团队成员：`hugo new team/john-doe.md`（可切换为 `data/team.yaml` 方式）
- 页面描述与 SEO：在内容 Front Matter 中添加 `description` 字段。
- 菜单：`config/_default/hugo.toml` 的 `[menu.main]` 可增改；或在页面 Front Matter 中声明 `menu.main`。
- 配色与品牌：`config/_default/hugo.toml` 的 `[params]`；主题样式在 `themes/atomic-core/static/css/main.css`。
- 短代码：示例 `{{< button href="/contact/" >}}请求咨询{{< /button >}}`；可在 `layouts/shortcodes/` 目录新增 `note`、`quote` 等。

## 合规与隐私
- 站点默认启用 `enableRobotsTXT = true` 与 Sitemap；`privacy` 配置尽量关闭外部追踪与嵌入。
- 页脚展示中立索引与独立声明：内容源自 `data/compliance.yaml`。
- 表单与数据上传不在本期范围；后续若需要，建议采用静态表单服务或最小后端，严格遵循数据最小化原则。

## 命名与国际化
- 默认语言：`zh-cn`；如需 EN/FR，可采用 Hugo 多语言配置（`config/_default/` 下新增语言段）。
- 微文案与 CTA 可参考既有规划（独立与安全优先；中立索引不构成背书）。

## 维护与后续路线
- 按需新增 Section（如 Knowledge Hub、Publications、Services），保持模块化与简洁。
- 补充 Open Graph 与 JSON-LD（已在 `head.html` 基础支持组织结构）。
- 引入自定义字体时建议自托管，避免第三方隐私问题；目前采用系统字体优先级。

## 许可证
本仓库为项目骨架与示例内容，后续请结合公司实际信息替换占位文本与数据。
