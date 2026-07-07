# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研、内容聚合与外部资源管理的轻量级导航站点系统，定位于帮助开发者、技术研究员与内容运营人员高效管理、分类展示和快速检索大量外部文章链接。系统以静态站点生成方式运行，支持按来源域名、文章编号、分类标签进行多维度检索，适用于构建技术周刊、资源清单、外链档案馆或内部知识库入口。

项目目标用户包括技术社区运营者、开源项目维护者、个人知识管理实践者以及需要定期整理大量阅读列表的研究人员。WebIndex 不提供内容抓取或存储服务，仅作为 URL 元数据管理与展示层，严格遵循外部资源引用规范，所有链接均保留原始出处域名与完整路径。

## 功能概览

批量导入与结构化存储：支持通过命令行工具将大量 URL 记录批量导入系统，自动解析域名、路径参数与扩展名，生成标准化索引记录。

多源域名分组展示：系统自动识别 URL 所属一级域名，按域名分组生成独立导航页面，便于用户按来源站点筛选内容。

文章编号快速定位：每条记录保留原始文章编号或路径末尾数字标识，支持通过编号前缀模糊检索，适配编号体系化的外部站点。

响应式移动端适配：前端模板基于移动优先原则设计，针对手机浏览器优化排版与触控操作，确保在移动设备上获得流畅阅读体验。

静态站点生成输出：构建过程输出纯静态 HTML 文件，无需后端服务或数据库支持，可部署于任何支持 HTTP 服务的托管平台。

分类标签扩展机制：支持为每条 URL 手动添加自定义标签（如「技术深度」「案例研究」「数据报告」），标签数据存储于独立配置文件中。

检索过滤命令行界面：提供 CLI 工具支持按域名、编号范围、导入批次等条件筛选记录，便于运维人员执行数据清洗与导出操作。

## 应用场景

技术周刊素材整理：技术编辑每周从多个行业站点收集数十篇值得推荐的文章，通过 WebIndex 批量导入后生成带分组导航的周刊页面，替代手工维护散乱的书签列表。

开源项目外部链接归档：开源项目维护者将项目文档中引用的所有外部资源（设计参考、技术规范、依赖文档）统一收录至 WebIndex，作为项目附属的外链索引库，方便贡献者查阅。

行业报告与白皮书清单管理：研究机构分析师定期收集行业报告 PDF 链接与摘要页面，使用 WebIndex 按年份、机构、主题创建多维导航目录，提升内部协作效率。

个人知识库入口构建：知识管理实践者将长期积累的阅读清单、课程链接、工具官网等资源导入系统，生成个人专属的导航起始页，替代浏览器混乱的书签栏。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex-starter.git
cd webindex-starter

# 安装依赖（基于 Node.js 18+ 与 npm）
npm install

# 执行批量导入（示例：导入批次 34/60 的 URL 数据）
npm run import -- --batch=34 --source=./data/urls-batch34.txt

# 构建静态站点
npm run build

# 启动本地预览服务（默认端口 8080）
npm run serve
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或更高 | 运行时环境，用于执行构建脚本与 CLI 工具 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与提交更新 |
| 磁盘空间 | 至少 50 MB | 用于存储源码、构建产物及索引数据文件 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows 下建议使用 WSL 或 Git Bash |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何导入 URL、如何生成站点、如何自定义分类标签 |
| 配置参考 | /docs/config-reference.md | 站点标题、分组规则、输出路径等配置项说明 |
| 开发者指南 | /docs/developer-guide.md | 插件扩展机制、模板变量、CLI 命令开发规范 |
| 部署指南 | /docs/deployment.md | 支持 GitHub Pages、Netlify、Vercel 等平台的部署步骤 |

## 资源列表

- http://www.mobile.cvsifc.cn/Article/8336.shtml
- http://www.mobile.cvsifc.cn/Article/74109.shtml
- http://www.mobile.hcbezg.cn/Article/6053.shtml
- http://www.mobile.hcbezg.cn/Article/5602.shtml
- http://www.mobile.hcbezg.cn/Article/0937.shtml
- http://www.mobile.cvsifc.cn/Article/3025723.shtml
- http://www.mobile.fuvxie.cn/Article/4582812.shtml
- http://www.mobile.cvsifc.cn/Article/067789.shtml
- http://www.mobile.hcbezg.cn/Article/1589979.shtml
- http://www.mobile.hcbezg.cn/Article/7160908.shtml
- http://www.mobile.fuvxie.cn/Article/6903.shtml
- http://www.mobile.hcbezg.cn/Article/9927.shtml
- http://www.mobile.fuvxie.cn/Article/1016359.shtml
- http://www.mobile.hcbezg.cn/Article/06335.shtml
- http://www.mobile.hcbezg.cn/Article/7426.shtml
- http://www.mobile.fuvxie.cn/Article/9386692.shtml
- http://www.mobile.hcbezg.cn/Article/429501.shtml
- http://www.mobile.hcbezg.cn/Article/1247085.shtml
- http://www.mobile.hcbezg.cn/Article/491066.shtml
- http://www.mobile.cvsifc.cn/Article/564986.shtml
- http://www.mobile.fuvxie.cn/Article/2711.shtml
- http://www.mobile.hcbezg.cn/Article/595155.shtml
- http://www.mobile.cvsifc.cn/Article/55215.shtml
- http://www.mobile.hcbezg.cn/Article/9831211.shtml
- http://www.mobile.cvsifc.cn/Article/4117.shtml
- http://www.mobile.hcbezg.cn/Article/703554.shtml
- http://www.mobile.hcbezg.cn/Article/0980792.shtml
- http://www.mobile.fuvxie.cn/Article/0367.shtml
- http://www.mobile.fuvxie.cn/Article/77795.shtml
- http://www.mobile.cvsifc.cn/Article/2326.shtml
- http://www.mobile.cvsifc.cn/Article/2236849.shtml
- http://www.mobile.fuvxie.cn/Article/44080.shtml
- http://www.mobile.hcbezg.cn/Article/5547.shtml
- http://www.mobile.hcbezg.cn/Article/579248.shtml
- http://www.mobile.hcbezg.cn/Article/6328.shtml
- http://www.mobile.cvsifc.cn/Article/383660.shtml
- http://www.mobile.cvsifc.cn/Article/4059.shtml
- http://www.mobile.hcbezg.cn/Article/2436.shtml
- http://www.mobile.fuvxie.cn/Article/09754.shtml
- http://www.mobile.hcbezg.cn/Article/7541528.shtml
- http://www.mobile.fuvxie.cn/Article/9130041.shtml
- http://www.mobile.hcbezg.cn/Article/4106.shtml
- http://www.mobile.fuvxie.cn/Article/4949299.shtml
- http://www.mobile.fuvxie.cn/Article/963899.shtml
- http://www.mobile.cvsifc.cn/Article/262392.shtml
- http://www.mobile.cvsifc.cn/Article/9226172.shtml
- http://www.mobile.hcbezg.cn/Article/6443.shtml
- http://www.mobile.cvsifc.cn/Article/8370.shtml
- http://www.mobile.hcbezg.cn/Article/0069.shtml
- http://www.mobile.fuvxie.cn/Article/01809.shtml
- http://www.mobile.fuvxie.cn/Article/024786.shtml
- http://www.mobile.hcbezg.cn/Article/74541.shtml
- http://www.mobile.cvsifc.cn/Article/813010.shtml
- http://www.mobile.fuvxie.cn/Article/3172.shtml
- http://www.mobile.hcbezg.cn/Article/11771.shtml
- http://www.mobile.fuvxie.cn/Article/2046046.shtml
- http://www.mobile.fuvxie.cn/Article/722656.shtml
- http://www.mobile.hcbezg.cn/Article/2785.shtml
- http://www.mobile.hcbezg.cn/Article/143625.shtml
- http://www.mobile.fuvxie.cn/Article/473204.shtml
- http://www.mobile.fuvxie.cn/Article/57692.shtml
- http://www.mobile.fuvxie.cn/Article/038743.shtml
- http://www.mobile.cvsifc.cn/Article/19150.shtml
- http://www.mobile.cvsifc.cn/Article/1606997.shtml
- http://www.mobile.hcbezg.cn/Article/1112.shtml
- http://www.mobile.hcbezg.cn/Article/9527766.shtml
- http://www.mobile.fuvxie.cn/Article/72600.shtml
- http://www.mobile.fuvxie.cn/Article/6335.shtml
- http://www.mobile.hcbezg.cn/Article/30529.shtml
- http://www.mobile.fuvxie.cn/Article/7409968.shtml
- http://www.mobile.hcbezg.cn/Article/41391.shtml
- http://www.mobile.hcbezg.cn/Article/8241.shtml
- http://www.mobile.hcbezg.cn/Article/9705.shtml
- http://www.mobile.cvsifc.cn/Article/7403.shtml
- http://www.mobile.hcbezg.cn/Article/8151.shtml
- http://www.mobile.cvsifc.cn/Article/786136.shtml
- http://www.mobile.fuvxie.cn/Article/0485.shtml
- http://www.mobile.fuvxie.cn/Article/700970.shtml
- http://www.mobile.hcbezg.cn/Article/194676.shtml
- http://www.mobile.hcbezg.cn/Article/7337.shtml
- http://www.mobile.fuvxie.cn/Article/6689.shtml
- http://www.mobile.fuvxie.cn/Article/288852.shtml
- http://www.mobile.cvsifc.cn/Article/9375134.shtml
- http://www.mobile.cvsifc.cn/Article/1025182.shtml
- http://www.mobile.fuvxie.cn/Article/9470334.shtml
- http://www.mobile.hcbezg.cn/Article/28088.shtml
- http://www.mobile.hcbezg.cn/Article/8280.shtml
- http://www.mobile.hcbezg.cn/Article/474337.shtml
- http://www.mobile.fuvxie.cn/Article/5489.shtml
- http://www.mobile.cvsifc.cn/Article/00985.shtml
- http://www.mobile.hcbezg.cn/Article/4576.shtml
- http://www.mobile.fuvxie.cn/Article/6490325.shtml
- http://www.mobile.hcbezg.cn/Article/6724.shtml
- http://www.mobile.fuvxie.cn/Article/4626134.shtml
- http://www.mobile.hcbezg.cn/Article/9452.shtml
- http://www.mobile.fuvxie.cn/Article/5403890.shtml
- http://www.mobile.cvsifc.cn/Article/468952.shtml
- http://www.mobile.fuvxie.cn/Article/6583.shtml
- http://www.mobile.hcbezg.cn/Article/29817.shtml
- http://www.mobile.cvsifc.cn/Article/5525755.shtml
- http://www.mobile.cvsifc.cn/Article/4404605.shtml
- http://www.mobile.fuvxie.cn/Article/2598.shtml
- http://www.mobile.hcbezg.cn/Article/9097795.shtml
- http://www.mobile.cvsifc.cn/Article/6067.shtml
- http://www.mobile.fuvxie.cn/Article/3690042.shtml
- http://www.mobile.fuvxie.cn/Article/33953.shtml
- http://www.mobile.cvsifc.cn/Article/1892.shtml
- http://www.mobile.cvsifc.cn/Article/537349.shtml
- http://www.mobile.fuvxie.cn/Article/40821.shtml
- http://www.mobile.fuvxie.cn/Article/88575.shtml
- http://www.mobile.cvsifc.cn/Article/207569.shtml
- http://www.mobile.hcbezg.cn/Article/1331056.shtml
- http://www.mobile.fuvxie.cn/Article/5618.shtml
- http://www.mobile.cvsifc.cn/Article/0838933.shtml
- http://www.mobile.cvsifc.cn/Article/6293939.shtml
- http://www.mobile.cvsifc.cn/Article/7639.shtml
- http://www.mobile.hcbezg.cn/Article/06179.shtml
- http://www.mobile.cvsifc.cn/Article/4673.shtml
- http://www.mobile.fuvxie.cn/Article/918698.shtml
- http://www.mobile.hcbezg.cn/Article/5339.shtml
- http://www.mobile.hcbezg.cn/Article/52262.shtml
- http://www.mobile.hcbezg.cn/Article/7041.shtml
- http://www.mobile.cvsifc.cn/Article/22713.shtml
- http://www.mobile.fuvxie.cn/Article/701214.shtml
- http://www.mobile.cvsifc.cn/Article/6566045.shtml
- http://www.mobile.hcbezg.cn/Article/71555.shtml
- http://www.mobile.fuvxie.cn/Article/579070.shtml
- http://www.mobile.cvsifc.cn/Article/5478.shtml
- http://www.mobile.fuvxie.cn/Article/96358.shtml
- http://www.mobile.fuvxie.cn/Article/06934.shtml
- http://www.mobile.hcbezg.cn/Article/785976.shtml
- http://www.mobile.cvsifc.cn/Article/210274.shtml
- http://www.mobile.hcbezg.cn/Article/9820544.shtml
- http://www.mobile.hcbezg.cn/Article/620298.shtml
- http://www.mobile.fuvxie.cn/Article/051020.shtml
- http://www.mobile.hcbezg.cn/Article/958768.shtml
- http://www.mobile.cvsifc.cn/Article/8387669.shtml
- http://www.mobile.fuvxie.cn/Article/4917.shtml
- http://www.mobile.cvsifc.cn/Article/943752.shtml
- http://www.mobile.hcbezg.cn/Article/46415.shtml
- http://www.mobile.hcbezg.cn/Article/0146718.shtml
- http://www.mobile.fuvxie.cn/Article/85554.shtml
- http://www.mobile.fuvxie.cn/Article/9541025.shtml
- http://www.mobile.fuvxie.cn/Article/817549.shtml
- http://www.mobile.cvsifc.cn/Article/97395.shtml
- http://www.mobile.fuvxie.cn/Article/039460.shtml
- http://www.mobile.cvsifc.cn/Article/268382.shtml
- http://www.mobile.hcbezg.cn/Article/7772185.shtml
- http://www.mobile.fuvxie.cn/Article/187477.shtml
- http://www.mobile.cvsifc.cn/Article/37800.shtml
- http://www.mobile.hcbezg.cn/Article/5400.shtml
- http://www.mobile.hcbezg.cn/Article/0839.shtml
- http://www.mobile.cvsifc.cn/Article/8134281.shtml
- http://www.mobile.fuvxie.cn/Article/914632.shtml
- http://www.mobile.cvsifc.cn/Article/264648.shtml
- http://www.mobile.hcbezg.cn/Article/16485.shtml
- http://www.mobile.cvsifc.cn/Article/95067.shtml
- http://www.mobile.hcbezg.cn/Article/05760.shtml
- http://www.mobile.cvsifc.cn/Article/765978.shtml
- http://www.mobile.hcbezg.cn/Article/3011.shtml
- http://www.mobile.fuvxie.cn/Article/02315.shtml
- http://www.mobile.fuvxie.cn/Article/3324564.shtml
- http://www.mobile.cvsifc.cn/Article/0617090.shtml
- http://www.mobile.cvsifc.cn/Article/1454.shtml
- http://www.mobile.hcbezg.cn/Article/310956.shtml
- http://www.mobile.cvsifc.cn/Article/1414.shtml
- http://www.mobile.fuvxie.cn/Article/886001.shtml
- http://www.mobile.cvsifc.cn/Article/8272.shtml
- http://www.mobile.fuvxie.cn/Article/74867.shtml
- http://www.mobile.hcbezg.cn/Article/0020.shtml
- http://www.mobile.cvsifc.cn/Article/70725.shtml
- http://www.mobile.fuvxie.cn/Article/351182.shtml
- http://www.mobile.fuvxie.cn/Article/6104134.shtml
- http://www.mobile.cvsifc.cn/Article/6343.shtml
- http://www.mobile.hcbezg.cn/Article/5286266.shtml
- http://www.mobile.hcbezg.cn/Article/85693.shtml
- http://www.mobile.hcbezg.cn/Article/1721661.shtml
- http://www.mobile.fuvxie.cn/Article/16491.shtml
- http://www.mobile.cvsifc.cn/Article/922512.shtml
- http://www.mobile.cvsifc.cn/Article/687852.shtml
- http://www.mobile.fuvxie.cn/Article/193348.shtml
- http://www.mobile.cvsifc.cn/Article/06725.shtml
- http://www.mobile.fuvxie.cn/Article/428039.shtml
- http://www.mobile.hcbezg.cn/Article/572195.shtml
- http://www.mobile.fuvxie.cn/Article/36181.shtml
- http://www.mobile.hcbezg.cn/Article/2069.shtml
- http://www.mobile.cvsifc.cn/Article/568485.shtml
- http://www.mobile.fuvxie.cn/Article/033867.shtml
- http://www.mobile.fuvxie.cn/Article/2650.shtml
- http://www.mobile.fuvxie.cn/Article/39832.shtml
- http://www.mobile.fuvxie.cn/Article/879563.shtml
- http://www.mobile.hcbezg.cn/Article/6586.shtml
- http://www.mobile.cvsifc.cn/Article/5864.shtml
- http://www.mobile.cvsifc.cn/Article/9421711.shtml
- http://www.mobile.cvsifc.cn/Article/3732.shtml
- http://www.mobile.cvsifc.cn/Article/232303.shtml
- http://www.mobile.hcbezg.cn/Article/4681499.shtml
- http://www.mobile.hcbezg.cn/Article/7261885.shtml
- http://www.mobile.hcbezg.cn/Article/57574.shtml
- http://www.mobile.hcbezg.cn/Article/33941.shtml
- http://www.mobile.hcbezg.cn/Article/972263.shtml
- http://www.mobile.cvsifc.cn/Article/416177.shtml
- http://www.mobile.fuvxie.cn/Article/3820136.shtml
- http://www.mobile.hcbezg.cn/Article/7310.shtml
- http://www.mobile.hcbezg.cn/Article/1715.shtml
- http://www.mobile.fuvxie.cn/Article/42679.shtml
- http://www.mobile.cvsifc.cn/Article/2131567.shtml
- http://www.mobile.cvsifc.cn/Article/47677.shtml
- http://www.mobile.fuvxie.cn/Article/8025.shtml
- http://www.mobile.cvsifc.cn/Article/722886.shtml
- http://www.mobile.fuvxie.cn/Article/091946.shtml
- http://www.mobile.fuvxie.cn/Article/31511.shtml
- http://www.mobile.hcbezg.cn/Article/6645070.shtml
- http://www.mobile.cvsifc.cn/Article/09107.shtml
- http://www.mobile.fuvxie.cn/Article/1919.shtml
- http://www.mobile.fuvxie.cn/Article/184606.shtml
- http://www.mobile.fuvxie.cn/Article/1573694.shtml
- http://www.mobile.hcbezg.cn/Article/7539775.shtml
- http://www.mobile.cvsifc.cn/Article/9958849.shtml
- http://www.mobile.hcbezg.cn/Article/5253.shtml
- http://www.mobile.fuvxie.cn/Article/4895.shtml
- http://www.mobile.cvsifc.cn/Article/3909.shtml
- http://www.mobile.cvsifc.cn/Article/06582.shtml
- http://www.mobile.hcbezg.cn/Article/6989.shtml
- http://www.mobile.cvsifc.cn/Article/833229.shtml
- http://www.mobile.cvsifc.cn/Article/848865.shtml
- http://www.mobile.fuvxie.cn/Article/3973.shtml
- http://www.mobile.hcbezg.cn/Article/43981.shtml
- http://www.mobile.hcbezg.cn/Article/0458174.shtml
- http://www.mobile.cvsifc.cn/Article/058359.shtml
- http://www.mobile.fuvxie.cn/Article/59897.shtml
- http://www.mobile.cvsifc.cn/Article/9420.shtml
- http://www.mobile.hcbezg.cn/Article/2314493.shtml
- http://www.mobile.fuvxie.cn/Article/38368.shtml
- http://www.mobile.hcbezg.cn/Article/9626947.shtml
- http://www.mobile.fuvxie.cn/Article/1520138.shtml
- http://www.mobile.fuvxie.cn/Article/040127.shtml
- http://www.mobile.hcbezg.cn/Article/132085.shtml
- http://www.mobile.cvsifc.cn/Article/741243.shtml
- http://www.mobile.hcbezg.cn/Article/776526.shtml
- http://www.mobile.hcbezg.cn/Article/2020.shtml
- http://www.mobile.fuvxie.cn/Article/8279031.shtml
- http://www.mobile.fuvxie.cn/Article/8568169.shtml
- http://www.mobile.cvsifc.cn/Article/66182.shtml
- http://www.mobile.hcbezg.cn/Article/1314930.shtml
- http://www.mobile.cvsifc.cn/Article/667330.shtml
- http://www.mobile.cvsifc.cn/Article/790560.shtml
- http://www.mobile.fuvxie.cn/Article/661558.shtml
- http://www.mobile.fuvxie.cn/Article/6328765.shtml
- http://www.mobile.fuvxie.cn/Article/6964577.shtml

## 项目结构

```
webindex-starter/
├── src/                           # 源代码主目录
│   ├── core/                      # 核心处理模块
│   │   ├── parser.js              # URL 解析与域名提取逻辑
│   │   ├── indexer.js             # 索引构建与记录管理
│   │   └── validator.js           # URL 格式校验与去重
│   ├── cli/                       # 命令行工具实现
│   │   ├── import.js              # 批量导入命令
│   │   ├── build.js               # 构建命令
│   │   └── serve.js               # 本地预览服务命令
│   ├── template/                  # 前端模板引擎
│   │   ├── layout.ejs             # 主布局模板
│   │   ├── index.ejs              # 首页模板
│   │   └── domain.ejs             # 域名分组详情页模板
│   ├── assets/                    # 静态资源
│   │   ├── css/                   # 样式表文件
│   │   ├── js/                    # 前端交互脚本
│   │   └── fonts/                 # 字体文件
│   └── utils/                     # 通用工具函数
│       ├── logger.js              # 日志输出
│       ├── config.js              # 配置加载
│       └── file.js                # 文件读写辅助
├── data/                          # 数据存储目录
│   ├── urls/                      # 原始 URL 导入文件存放处
│   ├── index.db.json              # 索引数据库（JSON 格式）
│   └── tags.json                  # 分类标签配置
├── dist/                          # 构建输出目录（生成站点）
│   ├── index.html                 # 首页
│   ├── domains/                   # 域名分组页面
│   └── assets/                    # 构建后的静态资源
├── tests/                         # 单元测试与集成测试
│   ├── parser.test.js             # 解析器测试
│   └── indexer.test.js            # 索引器测试
├── docs/                          # 项目文档
│   ├── user-guide.md              # 用户手册
│   ├── config-reference.md        # 配置参考
│   └── developer-guide.md         # 开发者指南
├── .github/                       # GitHub 工作流配置
│   └── workflows/                 # CI 持续集成配置
├── package.json                   # 项目依赖与脚本定义
├── README.md                      # 项目说明文档（本文件）
└── LICENSE                        # MIT 许可证
```

## 贡献指南

1. 阅读项目文档中的开发者指南（/docs/developer-guide.md），了解代码规范、测试要求与提交流程。
2. 在 GitHub 仓库的 Issue 列表中查找未被分配的待办任务，或提交新 Issue 描述你希望解决的问题或新增功能。
3. Fork 项目仓库，在本地开发分支上完成代码修改，确保所有单元测试通过且新增代码覆盖率达到 80% 以上。
4. 提交 Pull Request 时附带清晰的变更说明，引用相关 Issue 编号，并确保 commit 信息遵循 Conventional Commits 规范。
5. 等待项目维护者进行 Code Review，根据反馈意见进行修订，合并后你的贡献将出现在下一版本发布说明中。

## 常见问题

Q: 系统是否支持导入 HTTPS 协议的 URL？导入后是否会强制转换协议？

A: 系统不对 URL 协议做任何强制转换，完全保留用户导入时的原始协议字符串。无论是 http 还是 https，系统均原样存储并在前端页面中直接输出。用户应确保导入的 URL 协议与实际可访问性一致。

Q: 导入的 URL 数量是否有限制？单次最大导入记录数是多少？

A: 系统本身不设硬性数量上限，但单批次导入建议不超过 2000 条记录，以确保构建性能与内存占用处于合理范围。对于超过 5000 条的数据集，建议拆分为多个批次依次导入，系统支持按批次号进行增量合并与去重。

Q: 构建后的静态站点是否支持搜索功能？

A: 基础版本支持前端模糊检索，检索范围覆盖 URL 原文、域名、文章编号。对于更复杂的全文检索需求（如按标题或摘要搜索），需要自行接入第三方搜索引擎服务（如 Algolia 或 Meilisearch），系统预留了搜索结果页面的模板扩展接口。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
