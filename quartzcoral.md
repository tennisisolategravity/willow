# Mobile Article Aggregator Service (MAAS)

Mobile Article Aggregator Service 是一个面向移动端内容聚合与分发场景的轻量化外链资源管理与导航系统。该项目定位于技术内容运营团队、个人站长以及移动端信息流开发者，用于将分散在多个移动端子域名下的结构化工单文章进行统一索引、分类展示与快速检索。MAAS 不提供数据库存储，仅通过静态资源映射与外部链接重定向机制，实现高效的资源导航能力，适用于日均千级到十万级 URL 的导航站点部署。

当前批次为第五批次，共收录 250 条有效文章链接，覆盖三个主要移动端子域名内容源。本项目为纯前端资源整合层，不对链接内容进行修改、转码或代理，仅作为结构化索引表对外提供服务。

## 功能概览

- 多源链接统一索引: 将 hcbezg.cn、cvsifc.cn、fuvxie.cn 三个移动子域名下的文章链接按原始路径进行收录与分类展示。
- 按批次与目录分页导航: 支持按批次编号（第 5/60 批）及文章 ID 区间进行筛选与定位。
- 静态站点生成输出: 项目构建后输出纯静态 HTML 与 Markdown 索引文件，可直接部署于 Nginx、Apache 或 CDN。
- 免数据库零配置运行: 无需任何后端服务或数据库，所有链接数据以 JSON 配置文件形式存储于仓库。
- 链接状态健康检查集成: 内置基于 Headless 浏览器的外链可用性检测脚本，可定期检查链接返回状态。
- 移动端自适应索引页: 索引页采用响应式设计，适配手机与平板设备浏览。
- 自定义分类标签系统: 管理员可通过编辑分类映射文件，为每个文章 ID 打上最多三个层级标签。
- 全文检索接口: 提供基于 JavaScript 的前端模糊搜索函数，支持按文章 ID 关键字快速匹配。

## 应用场景

技术博客与资讯站点的外部引用整理: 内容编辑团队可将大量分散在移动端子域名下的引用链接通过 MAAS 进行集中管理，并在站点侧边栏或相关文章底部嵌入索引页链接，提升读者获取扩展阅读材料的效率。

移动端信息流应用的资源位配置: 移动 App 或 H5 信息流产品可在后台管理系统中嵌入 MAAS 生成的 JSON 数据接口，用于动态加载推荐阅读文章列表，无需单独维护文章数据库。

个人站长对采集内容的二次导航: 独立站长可将系统采集或手动提交的移动端文章链接通过 MAAS 生成清晰的导航目录页，并按批次发布到站点特定栏目，作为站内资源地图。

团队内部知识库的外链备份: 技术团队在编写内部 Wiki 或项目文档时，可将引用的外部移动文章链接通过 MAAS 统一归档并记录批次号，防止后续链接失效导致文档引用断裂。

## 快速开始

以下命令适用于 Linux / macOS 及 Windows WSL 环境。

```bash
# 克隆项目仓库
git clone https://github.com/maas-project/mobile-article-aggregator.git
cd mobile-article-aggregator

# 安装依赖（仅需 Node.js 与 npm）
npm install

# 执行构建，生成静态索引文件
npm run build

# 启动本地预览服务（默认监听 8080 端口）
npm run serve
```

访问 http://localhost:8080 即可查看当前批次的链接索引页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.x 或更高 | 用于执行构建脚本与本地服务 |
| npm | 8.x 或更高 | 依赖管理工具 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ | 用于预览索引页，支持 ES6 语法 |
| Git | 2.25+ | 版本控制与仓库克隆 |
| curl / wget | 任意版本 | 可选，用于远程拉取更新配置 |
| make | 3.81+ | 可选，用于自动化任务执行 |
| shellcheck | 0.7+ | 可选，用于脚本静态检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide.md | 如何使用索引页进行链接检索与筛选 |
| 管理员手册 | /docs/admin-guide.md | 如何新增批次、修改分类映射与重新构建 |
| 开发者指南 | /docs/developer-guide.md | 项目目录结构、配置文件格式与扩展开发 |
| 部署参考 | /docs/deployment.md | Nginx / Apache / CDN 部署示例与性能调优 |
| 数据格式说明 | /docs/data-format.md | 链接 JSON 结构、字段含义与校验规则 |
| 健康检查说明 | /docs/health-check.md | 链接可用性检测脚本的使用与定时任务配置 |

## 资源列表

- http://m.mobile.hcbezg.cn/Article/4668.shtml
- http://m.mobile.cvsifc.cn/Article/131496.shtml
- http://m.mobile.fuvxie.cn/Article/015208.shtml
- http://m.mobile.hcbezg.cn/Article/86831.shtml
- http://m.mobile.hcbezg.cn/Article/85909.shtml
- http://m.mobile.fuvxie.cn/Article/6800401.shtml
- http://m.mobile.fuvxie.cn/Article/04335.shtml
- http://m.mobile.hcbezg.cn/Article/4205.shtml
- http://m.mobile.hcbezg.cn/Article/424175.shtml
- http://m.mobile.fuvxie.cn/Article/85718.shtml
- http://m.mobile.cvsifc.cn/Article/2935573.shtml
- http://m.mobile.hcbezg.cn/Article/6858.shtml
- http://m.mobile.fuvxie.cn/Article/8488080.shtml
- http://m.mobile.hcbezg.cn/Article/54354.shtml
- http://m.mobile.fuvxie.cn/Article/19243.shtml
- http://m.mobile.hcbezg.cn/Article/6397.shtml
- http://m.mobile.hcbezg.cn/Article/891957.shtml
- http://m.mobile.fuvxie.cn/Article/68064.shtml
- http://m.mobile.hcbezg.cn/Article/4440031.shtml
- http://m.mobile.hcbezg.cn/Article/2933274.shtml
- http://m.mobile.hcbezg.cn/Article/01772.shtml
- http://m.mobile.fuvxie.cn/Article/3876.shtml
- http://m.mobile.cvsifc.cn/Article/4399.shtml
- http://m.mobile.fuvxie.cn/Article/34374.shtml
- http://m.mobile.fuvxie.cn/Article/99230.shtml
- http://m.mobile.cvsifc.cn/Article/1524.shtml
- http://m.mobile.cvsifc.cn/Article/0626180.shtml
- http://m.mobile.fuvxie.cn/Article/3186276.shtml
- http://m.mobile.cvsifc.cn/Article/663059.shtml
- http://m.mobile.hcbezg.cn/Article/2372.shtml
- http://m.mobile.fuvxie.cn/Article/1272.shtml
- http://m.mobile.hcbezg.cn/Article/5771.shtml
- http://m.mobile.fuvxie.cn/Article/390687.shtml
- http://m.mobile.cvsifc.cn/Article/7670.shtml
- http://m.mobile.cvsifc.cn/Article/21064.shtml
- http://m.mobile.hcbezg.cn/Article/872636.shtml
- http://m.mobile.hcbezg.cn/Article/493485.shtml
- http://m.mobile.fuvxie.cn/Article/1392.shtml
- http://m.mobile.fuvxie.cn/Article/9561860.shtml
- http://m.mobile.fuvxie.cn/Article/117065.shtml
- http://m.mobile.fuvxie.cn/Article/9590.shtml
- http://m.mobile.cvsifc.cn/Article/6476.shtml
- http://m.mobile.hcbezg.cn/Article/7072430.shtml
- http://m.mobile.fuvxie.cn/Article/5090071.shtml
- http://m.mobile.fuvxie.cn/Article/194168.shtml
- http://m.mobile.hcbezg.cn/Article/885674.shtml
- http://m.mobile.hcbezg.cn/Article/927979.shtml
- http://m.mobile.fuvxie.cn/Article/6282510.shtml
- http://m.mobile.cvsifc.cn/Article/11927.shtml
- http://m.mobile.hcbezg.cn/Article/81768.shtml
- http://m.mobile.cvsifc.cn/Article/55559.shtml
- http://m.mobile.fuvxie.cn/Article/9469.shtml
- http://m.mobile.fuvxie.cn/Article/5579916.shtml
- http://m.mobile.hcbezg.cn/Article/219729.shtml
- http://m.mobile.hcbezg.cn/Article/038307.shtml
- http://m.mobile.cvsifc.cn/Article/136488.shtml
- http://m.mobile.cvsifc.cn/Article/986994.shtml
- http://m.mobile.fuvxie.cn/Article/497357.shtml
- http://m.mobile.fuvxie.cn/Article/892842.shtml
- http://m.mobile.hcbezg.cn/Article/513618.shtml
- http://m.mobile.cvsifc.cn/Article/9272.shtml
- http://m.mobile.fuvxie.cn/Article/782164.shtml
- http://m.mobile.hcbezg.cn/Article/14816.shtml
- http://m.mobile.hcbezg.cn/Article/728790.shtml
- http://m.mobile.cvsifc.cn/Article/3565.shtml
- http://m.mobile.hcbezg.cn/Article/929876.shtml
- http://m.mobile.hcbezg.cn/Article/9205.shtml
- http://m.mobile.fuvxie.cn/Article/3441.shtml
- http://m.mobile.hcbezg.cn/Article/35212.shtml
- http://m.mobile.cvsifc.cn/Article/8611.shtml
- http://m.mobile.cvsifc.cn/Article/37028.shtml
- http://m.mobile.cvsifc.cn/Article/160705.shtml
- http://m.mobile.fuvxie.cn/Article/1820927.shtml
- http://m.mobile.fuvxie.cn/Article/1138071.shtml
- http://m.mobile.cvsifc.cn/Article/19537.shtml
- http://m.mobile.fuvxie.cn/Article/136520.shtml
- http://m.mobile.hcbezg.cn/Article/391864.shtml
- http://m.mobile.hcbezg.cn/Article/0052622.shtml
- http://m.mobile.fuvxie.cn/Article/6403311.shtml
- http://m.mobile.hcbezg.cn/Article/5932.shtml
- http://m.mobile.cvsifc.cn/Article/58689.shtml
- http://m.mobile.cvsifc.cn/Article/6018011.shtml
- http://m.mobile.hcbezg.cn/Article/9821.shtml
- http://m.mobile.fuvxie.cn/Article/85533.shtml
- http://m.mobile.fuvxie.cn/Article/998943.shtml
- http://m.mobile.fuvxie.cn/Article/8224.shtml
- http://m.mobile.cvsifc.cn/Article/873030.shtml
- http://m.mobile.cvsifc.cn/Article/309248.shtml
- http://m.mobile.fuvxie.cn/Article/36495.shtml
- http://m.mobile.hcbezg.cn/Article/5910712.shtml
- http://m.mobile.cvsifc.cn/Article/8618114.shtml
- http://m.mobile.hcbezg.cn/Article/10478.shtml
- http://m.mobile.hcbezg.cn/Article/69156.shtml
- http://m.mobile.hcbezg.cn/Article/508891.shtml
- http://m.mobile.cvsifc.cn/Article/1798236.shtml
- http://m.mobile.cvsifc.cn/Article/9439254.shtml
- http://m.mobile.hcbezg.cn/Article/1477.shtml
- http://m.mobile.cvsifc.cn/Article/6821.shtml
- http://m.mobile.fuvxie.cn/Article/2025.shtml
- http://m.mobile.cvsifc.cn/Article/94925.shtml
- http://m.mobile.fuvxie.cn/Article/8601.shtml
- http://m.mobile.hcbezg.cn/Article/639442.shtml
- http://m.mobile.fuvxie.cn/Article/1197.shtml
- http://m.mobile.cvsifc.cn/Article/1452974.shtml
- http://m.mobile.cvsifc.cn/Article/372460.shtml
- http://m.mobile.cvsifc.cn/Article/795424.shtml
- http://m.mobile.fuvxie.cn/Article/4200652.shtml
- http://m.mobile.fuvxie.cn/Article/087044.shtml
- http://m.mobile.hcbezg.cn/Article/380500.shtml
- http://m.mobile.cvsifc.cn/Article/9527.shtml
- http://m.mobile.fuvxie.cn/Article/532999.shtml
- http://m.mobile.hcbezg.cn/Article/2000.shtml
- http://m.mobile.cvsifc.cn/Article/178414.shtml
- http://m.mobile.hcbezg.cn/Article/7518.shtml
- http://m.mobile.fuvxie.cn/Article/60161.shtml
- http://m.mobile.fuvxie.cn/Article/50200.shtml
- http://m.mobile.cvsifc.cn/Article/29280.shtml
- http://m.mobile.cvsifc.cn/Article/7325.shtml
- http://m.mobile.hcbezg.cn/Article/4938063.shtml
- http://m.mobile.fuvxie.cn/Article/8389513.shtml
- http://m.mobile.fuvxie.cn/Article/77362.shtml
- http://m.mobile.cvsifc.cn/Article/90553.shtml
- http://m.mobile.cvsifc.cn/Article/1374304.shtml
- http://m.mobile.fuvxie.cn/Article/0981241.shtml
- http://m.mobile.fuvxie.cn/Article/533206.shtml
- http://m.mobile.cvsifc.cn/Article/97025.shtml
- http://m.mobile.fuvxie.cn/Article/5359066.shtml
- http://m.mobile.fuvxie.cn/Article/56757.shtml
- http://m.mobile.hcbezg.cn/Article/5756.shtml
- http://m.mobile.fuvxie.cn/Article/243519.shtml
- http://m.mobile.hcbezg.cn/Article/252097.shtml
- http://m.mobile.cvsifc.cn/Article/2109.shtml
- http://m.mobile.fuvxie.cn/Article/0176.shtml
- http://m.mobile.cvsifc.cn/Article/1019.shtml
- http://m.mobile.fuvxie.cn/Article/9592451.shtml
- http://m.mobile.hcbezg.cn/Article/315597.shtml
- http://m.mobile.hcbezg.cn/Article/33144.shtml
- http://m.mobile.hcbezg.cn/Article/018101.shtml
- http://m.mobile.fuvxie.cn/Article/3233534.shtml
- http://m.mobile.cvsifc.cn/Article/552566.shtml
- http://m.mobile.cvsifc.cn/Article/524231.shtml
- http://m.mobile.fuvxie.cn/Article/77665.shtml
- http://m.mobile.hcbezg.cn/Article/5746.shtml
- http://m.mobile.fuvxie.cn/Article/5426977.shtml
- http://m.mobile.hcbezg.cn/Article/6164.shtml
- http://m.mobile.hcbezg.cn/Article/19364.shtml
- http://m.mobile.hcbezg.cn/Article/1487.shtml
- http://m.mobile.fuvxie.cn/Article/0019.shtml
- http://m.mobile.hcbezg.cn/Article/8468203.shtml
- http://m.mobile.cvsifc.cn/Article/26108.shtml
- http://m.mobile.cvsifc.cn/Article/7162.shtml
- http://m.mobile.hcbezg.cn/Article/035661.shtml
- http://m.mobile.fuvxie.cn/Article/0220467.shtml
- http://m.mobile.hcbezg.cn/Article/0379506.shtml
- http://m.mobile.fuvxie.cn/Article/8927.shtml
- http://m.mobile.hcbezg.cn/Article/0190.shtml
- http://m.mobile.fuvxie.cn/Article/3110862.shtml
- http://m.mobile.cvsifc.cn/Article/7363404.shtml
- http://m.mobile.cvsifc.cn/Article/0748.shtml
- http://m.mobile.hcbezg.cn/Article/41663.shtml
- http://m.mobile.fuvxie.cn/Article/6807.shtml
- http://m.mobile.hcbezg.cn/Article/14625.shtml
- http://m.mobile.fuvxie.cn/Article/792681.shtml
- http://m.mobile.cvsifc.cn/Article/89490.shtml
- http://m.mobile.hcbezg.cn/Article/837849.shtml
- http://m.mobile.fuvxie.cn/Article/0342.shtml
- http://m.mobile.hcbezg.cn/Article/3182.shtml
- http://m.mobile.hcbezg.cn/Article/408857.shtml
- http://m.mobile.hcbezg.cn/Article/1517.shtml
- http://m.mobile.hcbezg.cn/Article/602424.shtml
- http://m.mobile.fuvxie.cn/Article/65836.shtml
- http://m.mobile.hcbezg.cn/Article/12598.shtml
- http://m.mobile.hcbezg.cn/Article/99853.shtml
- http://m.mobile.cvsifc.cn/Article/626734.shtml
- http://m.mobile.fuvxie.cn/Article/013318.shtml
- http://m.mobile.cvsifc.cn/Article/0285.shtml
- http://m.mobile.cvsifc.cn/Article/8929.shtml
- http://m.mobile.fuvxie.cn/Article/2221.shtml
- http://m.mobile.fuvxie.cn/Article/893173.shtml
- http://m.mobile.hcbezg.cn/Article/50129.shtml
- http://m.mobile.fuvxie.cn/Article/6769088.shtml
- http://m.mobile.hcbezg.cn/Article/6760234.shtml
- http://m.mobile.fuvxie.cn/Article/68259.shtml
- http://m.mobile.fuvxie.cn/Article/6368862.shtml
- http://m.mobile.hcbezg.cn/Article/4499.shtml
- http://m.mobile.cvsifc.cn/Article/2605.shtml
- http://m.mobile.fuvxie.cn/Article/237445.shtml
- http://m.mobile.cvsifc.cn/Article/1284731.shtml
- http://m.mobile.hcbezg.cn/Article/0231.shtml
- http://m.mobile.hcbezg.cn/Article/0337209.shtml
- http://m.mobile.fuvxie.cn/Article/589980.shtml
- http://m.mobile.hcbezg.cn/Article/5613.shtml
- http://m.mobile.fuvxie.cn/Article/3344.shtml
- http://m.mobile.cvsifc.cn/Article/7641.shtml
- http://m.mobile.cvsifc.cn/Article/033487.shtml
- http://m.mobile.fuvxie.cn/Article/913004.shtml
- http://m.mobile.cvsifc.cn/Article/344765.shtml
- http://m.mobile.cvsifc.cn/Article/3780367.shtml
- http://m.mobile.hcbezg.cn/Article/093249.shtml
- http://m.mobile.fuvxie.cn/Article/5661.shtml
- http://m.mobile.hcbezg.cn/Article/762141.shtml
- http://m.mobile.fuvxie.cn/Article/9711959.shtml
- http://m.mobile.hcbezg.cn/Article/9745159.shtml
- http://m.mobile.fuvxie.cn/Article/2010.shtml
- http://m.mobile.hcbezg.cn/Article/97997.shtml
- http://m.mobile.cvsifc.cn/Article/6861.shtml
- http://m.mobile.fuvxie.cn/Article/754388.shtml
- http://m.mobile.fuvxie.cn/Article/181774.shtml
- http://m.mobile.hcbezg.cn/Article/0044.shtml
- http://m.mobile.hcbezg.cn/Article/2802.shtml
- http://m.mobile.fuvxie.cn/Article/8688871.shtml
- http://m.mobile.cvsifc.cn/Article/2325680.shtml
- http://m.mobile.hcbezg.cn/Article/1057504.shtml
- http://m.mobile.fuvxie.cn/Article/3231417.shtml
- http://m.mobile.cvsifc.cn/Article/7444.shtml
- http://m.mobile.hcbezg.cn/Article/39616.shtml
- http://m.mobile.fuvxie.cn/Article/863185.shtml
- http://m.mobile.cvsifc.cn/Article/8274978.shtml
- http://m.mobile.cvsifc.cn/Article/3110.shtml
- http://m.mobile.cvsifc.cn/Article/9827.shtml
- http://m.mobile.fuvxie.cn/Article/3887127.shtml
- http://m.mobile.fuvxie.cn/Article/9114.shtml
- http://m.mobile.fuvxie.cn/Article/774695.shtml
- http://m.mobile.fuvxie.cn/Article/1993.shtml
- http://m.mobile.hcbezg.cn/Article/9515.shtml
- http://m.mobile.cvsifc.cn/Article/691955.shtml
- http://m.mobile.hcbezg.cn/Article/2728.shtml
- http://m.mobile.fuvxie.cn/Article/4713.shtml
- http://m.mobile.fuvxie.cn/Article/41551.shtml
- http://m.mobile.cvsifc.cn/Article/5296367.shtml
- http://m.mobile.hcbezg.cn/Article/8766381.shtml
- http://m.mobile.fuvxie.cn/Article/8286530.shtml
- http://m.mobile.cvsifc.cn/Article/702535.shtml
- http://m.mobile.fuvxie.cn/Article/392733.shtml
- http://m.mobile.hcbezg.cn/Article/64909.shtml
- http://m.mobile.cvsifc.cn/Article/559577.shtml
- http://m.mobile.fuvxie.cn/Article/6050.shtml
- http://m.mobile.cvsifc.cn/Article/951876.shtml
- http://m.mobile.cvsifc.cn/Article/02663.shtml
- http://m.mobile.cvsifc.cn/Article/151251.shtml
- http://m.mobile.hcbezg.cn/Article/7616191.shtml
- http://m.mobile.hcbezg.cn/Article/7739201.shtml
- http://m.mobile.fuvxie.cn/Article/6774125.shtml
- http://m.mobile.hcbezg.cn/Article/4014.shtml
- http://m.mobile.fuvxie.cn/Article/11514.shtml
- http://m.mobile.fuvxie.cn/Article/934015.shtml
- http://m.mobile.cvsifc.cn/Article/860886.shtml
- http://m.mobile.hcbezg.cn/Article/4938.shtml
- http://m.mobile.cvsifc.cn/Article/5834.shtml
- http://m.mobile.fuvxie.cn/Article/8144477.shtml

## 项目结构

```
mobile-article-aggregator/
├── build/                                   # 构建输出目录，存放生成的静态页面
│   ├── index.html                           # 批次总览页，含全部链接索引
│   └── assets/                              # 静态资源子目录
│       ├── css/                             # 样式表文件
│       │   └── main.min.css                 # 压缩后的主样式
│       └── js/                              # 前端脚本
│           └── search.min.js                # 搜索与筛选功能脚本
├── src/                                     # 源代码目录
│   ├── data/                                # 数据配置
│   │   ├── batch-5.json                     # 第五批次链接数据（核心数据文件）
│   │   ├── batch-meta.json                  # 所有批次的元信息描述
│   │   └── categories.yaml                  # 分类标签映射定义
│   ├── templates/                           # 页面模板
│   │   ├── layout.ejs                       # 基础 HTML 布局模板
│   │   └── partials/                        # 模板局部组件
│   │       ├── header.ejs                   # 顶部导航区域
│   │       └── footer.ejs                   # 页脚信息区域
│   ├── scripts/                             # 构建与工具脚本
│   │   ├── build.js                         # 主构建脚本，负责生成静态页
│   │   ├── health-check.js                  # 外链可用性检测脚本
│   │   └── validate-data.js                 # 数据格式校验脚本
│   └── styles/                              # 样式源码
│       ├── main.scss                        # 主样式入口
│       └── components/                      # 样式组件模块
│           ├── _table.scss                  # 索引表格样式
│           └── _nav.scss                    # 导航栏样式
├── tests/                                   # 单元测试目录
│   ├── data-validate.test.js                # 数据校验测试用例
│   └── search.test.js                       # 搜索函数测试用例
├── docs/                                    # 项目文档，对应文档导航章节
│   ├── user-guide.md                       
│   ├── admin-guide.md                      
│   ├── developer-guide.md                  
│   ├── deployment.md                       
│   ├── data-format.md                      
│   └── health-check.md                     
├── config/                                  # 环境与工具配置
│   ├── eslint.config.js                     # ESLint 代码检查配置
│   └── prettier.config.js                   # Prettier 格式化配置
├── .gitignore                               # Git 忽略文件列表
├── package.json                             # npm 项目清单与依赖
├── README.md                                # 项目说明文档（即本文档）
├── LICENSE                                  # MIT 许可证文件
└── Makefile                                 # 自动化构建任务定义
```

## 贡献指南

1. 提交 Issue 讨论: 在 GitHub Issues 中描述您希望增加的新功能、发现的 Bug 或对现有链接分类的调整建议，等待维护者确认后再进行开发。
2. 克隆仓库并创建分支: 从 main 分支切出新的功能分支，分支命名遵循 feature/描述 或 fix/描述 格式。
3. 更新数据文件与文档: 若涉及批次链接新增或修改，请同步编辑 src/data/ 下的对应 JSON 文件，并运行 npm run validate 确保数据格式正确。若涉及功能变更，需同步更新 docs/ 下相关文档。
4. 运行测试与构建: 执行 npm test 检查所有单元测试通过，然后执行 npm run build 确认构建无误。若构建失败，请排查模板或数据问题。
5. 发起 Pull Request: 提交 PR 至 main 分支，并在描述中关联相关 Issue 编号。维护者将在 3 个工作日内进行 Review。合并后您的贡献将列入项目贡献者列表。

## 常见问题

Q: 为什么资源列表中每个链接都包含 /Article/ 路径和 .shtml 后缀？我可以更改这些链接格式吗？

A: 这些链接是用户提供的原始数据，项目作为外链汇总站严格保留原始 URL 格式，不进行任何改写或重定向处理。如果您需要修改链接结构，请直接在数据源文件中调整，但需确保最终生成的索引页中每个链接与原始数据完全一致。

Q: 项目是否支持 HTTPS 自动升级？

A: 本项目不强制升级 HTTP 到 HTTPS，也不改变任何 URL 的协议前缀。所有链接严格按照用户输入原样输出，包括协议类型和域名格式。如果您希望使用 HTTPS 访问目标链接，请自行在数据源中替换为 HTTPS 协议的原始链接。

Q: 如何更新到下一批次（第 6/60 批）？

A: 在 src/data/ 目录下创建 batch-6.json 文件，按照 batch-5.json 的格式填入新链接数据。然后更新 batch-meta.json 中的批次总数和描述信息，重新运行 npm run build 即可生成包含新批次的索引页。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
