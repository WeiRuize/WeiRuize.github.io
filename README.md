# 魏睿泽 · 学术主页

本地初版。双击 `打开主页.command` 可直接在默认浏览器打开页面；也可右键 `index.html`，选择“打开方式”中的浏览器。无需安装依赖或构建。这两种方式不依赖临时预览服务；若 `http://127.0.0.1:4173` 无法访问，请使用本地打开方式。也可运行 `python3 -m http.server 4173 --bind 127.0.0.1`，然后访问 `http://127.0.0.1:4173`。

页面参考 [minimal-academic-homepage](https://github.com/Xin-Jiaqi/minimal-academic-homepage) 的学术主页风格，使用独立编写的 HTML/CSS 实现浅灰背景、白色内容区、简洁标题与蓝色链接。没有复制该仓库的源码或资源。

## 内容结构

- 顶部：姓名、照片、研究方向、英语能力、邮箱和 GitHub 账号。
- **教育经历**：硕士研究生为哈尔滨工业大学（深圳）计算机技术，本科为西北工业大学软件工程；校名旁配有透明背景校徽。
- **项目经历**：5 个项目的概述、关键词与「查看项目」按钮。
- **获奖证书**：18 项竞赛及成果证明，包括竞赛获奖、软件著作权登记证书和项目结项证明。
- **个人荣誉**：11 项奖学金、个人荣誉与基地核心成员证明；使用与竞赛证书相同的图片展示组件。
- **项目详情**：项目概述、个人贡献、技术流程、成果和待补充材料。

研究生专业按本人补充标注为 **计算机技术**，研究方向为 **具身智能安全**。其余经历依据提供的简历，未推断入学年份、当前学籍、论文发表状态或实验数据。原简历中的“至今”改为起始时间；详情中的历史状态注明以简历为准。

## 维护方式

内容、CSS 和少量 JavaScript 都保存在 `index.html` 中，头像保存在 `assets/images/avatar.jpg`，校徽保存在 `assets/schools/`，证书和荣誉分别保存在 `assets/certificates/` 与 `assets/honors/`。复制或部署时请保留整个 `assets/` 目录；无需外部字体、图片服务、框架或接口。

1. **修改个人信息**：搜索 `<!-- HOME`，修改 `.profile` 内的姓名、简介与邮箱；搜索 `<!-- EDUCATION` 修改学校、学位、专业和研究方向。复制按钮自动读取 `#email-link` 的可见文字；页头和页脚的邮件链接也应同步更新。
2. **增加项目概述**：搜索 `<!-- PROJECTS`，复制一个 `<article class="project-card">`，修改标题、简介、日期与技术标签。
3. **增加项目详情**：搜索 `<!-- DETAIL VIEWS`，复制一个 `<main class="detail-view wrap" id="project-...">`，为详情及标题设置唯一 ID，修改对应的 `aria-labelledby`。将首页按钮的 `href` 指向该详情 ID。
4. **修改项目数量**：同步更新“项目经历”标题旁的 `.count`。
5. **修改证书目录**：证书目录与滑动展示共享 `certificateData` 数据，无需单独复制记录；添加数据后同步更新各栏标题旁的 `.count`。
6. **添加真实证书**：将图片保存到 `assets/certificates/` 或 `assets/honors/`；在 `index.html` 的 `certificateData` 中向 `competitions` 或 `honors` 添加 `{src: "./assets/certificates/example.jpg", title: "证书名称", description: "奖项、年份等已核实的信息"}`。可选字段 `thumbnail` 指向缩略图；省略时使用完整图片。多页材料使用 `pages: ["./assets/certificates/page-1.jpg", "./assets/certificates/page-2.jpg"]`，其中 `src` 为首页图片。为空的展示组件自动隐藏。图片支持滑动、鼠标拖动、左右按钮与方向键；居中图片最大，两侧依次缩小并淡化，点击后打开大图，图片下方显示标题和说明，按 Esc 或点击关闭按钮退出。不自动轮播。
7. **添加项目材料**：在项目详情的“展示材料”中加入截图、视频、仓库和演示链接。图片使用相对路径，例如 `./assets/projects/hdr/example.jpg`，并填写说明和 `alt`。
8. **调整样式**：CSS 开头 `:root` 定义颜色、最大宽度和圆角；其余样式按首页、项目、证书、详情与响应式分组。
9. **替换照片**：搜索 `class="portrait"`，将 `src` 改为自己的图片路径即可。

详情以 `#project-hdr` 等页内地址切换，仍是单个 HTML 文件。可直接打开详情地址、刷新，以及使用浏览器前进/后退；「返回项目经历」回到首页的项目列表。布局依靠现代浏览器的 `:target` 和 `:has()`，JavaScript 只增强页面标题、焦点、滚动位置和邮箱复制。

## GitHub Pages 部署

GitHub 账号为 [WeiRuize](https://github.com/WeiRuize)，仓库为 [WeiRuize.github.io](https://github.com/WeiRuize/WeiRuize.github.io)。GitHub Pages 从 `main` 分支根目录发布，部署地址为 [https://weiruize.github.io/](https://weiruize.github.io/)。更新页面或图片后提交并推送到 `main`，GitHub Pages 会重新发布。

网站无需构建依赖；保留 `index.html`、整个 `assets/` 目录与 `.nojekyll`。资源使用相对路径，项目详情使用页内地址。本地原始 ZIP/RAR 输入由 `.gitignore` 排除，不属于发布文件。

电话、微信、籍贯及原始简历 PDF 未放入网页；没有无效的仓库、论文或下载按钮。

## 校徽资源

使用透明背景的高清 PNG 原图，页面以 45–52 像素显示，保持原始比例与颜色。当前未使用 SVG，也未将位图封装为伪矢量。哈工大深圳条目使用哈尔滨工业大学通用校徽。

- `assets/schools/nwpu.png`：[西北工业大学校徽资源](https://www.urongda.com/logos/4161010699)，1024 × 1024。
- `assets/schools/hit.png`：[哈尔滨工业大学校徽资源](https://www.urongda.com/logos/4123010213)，1024 × 924。

校徽仅用于标识教育经历，权利归各学校所有；后续取得合适的透明 SVG 后可直接替换图片路径。

## 证书来源与整理

证书来自本人提供的 `竞赛证书.rar` 与 `个人荣誉.zip`，逐项查看图片或 PDF 后填写标题和说明。竞赛材料合并了重复的机器人锦标赛图片，个人荣誉合并了吴亚军奖学金的照片和扫描件，选用清晰的扫描件。PDF 渲染为网页图片；iCAN 使用 macOS PDFKit 渲染以保留完整字体。一张侧向拍摄的结项证明已转正。滑动区域使用缩略图，点击后加载完整图片；原始压缩包保留在本地。

软件著作权证书明确标注著作权人为西北工业大学，不将其表述为个人所有权。软件创新大赛材料是三页官方获奖公示，标注为公示材料；大图窗口支持翻页。个人荣誉中的基地核心成员材料为原始名单页。

已通过浏览器验证真实证书的缩放、按钮/方向键切换、拖动、点击大图、标题说明、Esc 关闭、目录入口、多页材料翻页和移动端页面宽度；同时检查所有图片加载及项目详情返回导航。
