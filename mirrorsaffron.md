# WebArchive Bridge

WebArchive Bridge 是一个面向技术研究人员、数据归档工作者和内容分析师的轻量级移动端网页资源聚合与导航系统。项目定位于对分散在多个移动端域名下的历史文章页面进行集中索引、分类标注和快速检索，解决技术文档、教程笔记和行业资讯在移动端碎片化发布后难以统一管理和追溯的问题。项目本身不存储任何页面内容，仅提供基于 URL 元数据的索引服务，适用于个人知识库扩充、竞品内容监控、移动端 SEO 效果跟踪以及历史页面变更检测等场景。

## 功能概览

**多源异构 URL 聚合管理**：支持从多个移动端子域名批量导入文章链接，自动识别来源站点并归类，提供统一的列表视图和筛选入口。

**基础元数据自动提取**：对每个收录的 URL 进行请求头分析，自动补全内容类型、响应状态码、最后修改时间等基础字段，降低人工整理成本。

**关键词标签系统**：允许用户为每条记录添加自定义标签，支持多标签组合筛选，便于按技术领域、作者、时间周期等维度快速定位相关文章。

**变更检测与状态监控**：定期对已收录链接进行可用性探测，标记失效、跳转或内容变更的条目，输出变更报告供用户审阅。

**批量导入与导出**：支持通过文本文件或表格批量添加 URL 列表，同时支持将索引数据导出为 CSV 或 JSON 格式，便于二次加工或迁移至其他知识管理工具。

**快速全文检索**：基于 URL 路径关键词和自定义标签构建轻量级倒排索引，支持模糊搜索和精确匹配两种模式，结果按相关度排序。

**移动端适配界面**：采用响应式设计，在手机和平板设备上提供良好的浏览和操作体验，满足移动办公和碎片化阅读需求。

## 应用场景

技术博客与教程归档：技术人员在日常浏览移动端技术社区时，可将有价值的教程文章链接统一收录至 WebArchive Bridge，配合标签记录技术栈分类，后续复习或查阅时无需回忆原始发布站点，直接在本地索引中检索即可。

竞品内容更新监控：产品经理或市场分析师可录入竞品官方移动站点的文章列表，系统定期检测页面变更状态，当竞品发布新内容或修改旧文时，用户能第一时间获得通知，辅助决策分析。

历史页面迁移与重定向追踪：网站迁移或改版过程中，大量旧 URL 需要验证是否有效跳转。运维人员可将待迁移的 URL 列表导入系统，通过变更检测功能逐条确认跳转目标，确保迁移完整性。

学术文献与参考资料管理：研究人员收集移动端发布的会议论文链接、技术报告或数据公报时，利用批量导入功能和标签体系，按项目、课题或时间线组织参考资料，避免链接丢失或遗忘。

## 快速开始

以下命令演示了从代码仓库克隆、安装依赖到启动开发服务器的完整流程。

```bash
git clone https://github.com/webarchive-bridge/webarchive-bridge.git
cd webarchive-bridge
npm install
npm run dev
```

执行完成后，访问控制台输出的本地地址即可进入系统主界面。生产环境部署请参考文档导航中的部署指南。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.17.0 或更高 | 运行时环境，用于执行后端服务和构建前端资源 |
| npm | 9.0.0 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.39.0 或更高 | 嵌入式数据库，存储索引元数据和用户配置 |
| Redis | 7.0.0 或更高 | 缓存与任务队列后端，用于调度变更检测任务 |
| Nginx | 1.24.0 或更高 | 生产环境反向代理服务器，推荐用于静态资源分发 |
| PM2 | 5.3.0 或更高 | 进程守护工具，用于生产环境服务持久化运行 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速搭建开发环境？首次使用需要配置哪些参数？ |
| 操作手册 | docs/user-guide.md | 如何批量导入 URL？标签系统如何工作？检测报告在哪里查看？ |
| 部署运维 | docs/deployment.md | 生产环境如何配置 Nginx 和 PM2？如何备份 SQLite 数据库？ |
| 开发参考 | docs/api-reference.md | 后端 API 有哪些端点？请求与响应格式是什么？如何扩展自定义检测规则？ |

## 资源列表

- http://wap.mobile.hcbezg.cn/Article/20920.shtml
- http://wap.mobile.fuvxie.cn/Article/470595.shtml
- http://wap.mobile.hcbezg.cn/Article/216047.shtml
- http://wap.mobile.cvsifc.cn/Article/1477842.shtml
- http://wap.mobile.cvsifc.cn/Article/9762.shtml
- http://wap.mobile.cvsifc.cn/Article/492188.shtml
- http://wap.mobile.fuvxie.cn/Article/67167.shtml
- http://wap.mobile.fuvxie.cn/Article/5816.shtml
- http://wap.mobile.cvsifc.cn/Article/774795.shtml
- http://wap.mobile.fuvxie.cn/Article/028945.shtml
- http://wap.mobile.fuvxie.cn/Article/636253.shtml
- http://wap.mobile.fuvxie.cn/Article/904838.shtml
- http://wap.mobile.hcbezg.cn/Article/742873.shtml
- http://wap.mobile.fuvxie.cn/Article/2668.shtml
- http://wap.mobile.fuvxie.cn/Article/6179391.shtml
- http://wap.mobile.fuvxie.cn/Article/0061588.shtml
- http://wap.mobile.cvsifc.cn/Article/8285393.shtml
- http://wap.mobile.hcbezg.cn/Article/459914.shtml
- http://wap.mobile.fuvxie.cn/Article/21899.shtml
- http://wap.mobile.hcbezg.cn/Article/0955.shtml
- http://wap.mobile.hcbezg.cn/Article/650208.shtml
- http://wap.mobile.fuvxie.cn/Article/07566.shtml
- http://wap.mobile.cvsifc.cn/Article/79657.shtml
- http://wap.mobile.cvsifc.cn/Article/0752467.shtml
- http://wap.mobile.cvsifc.cn/Article/8122.shtml
- http://wap.mobile.hcbezg.cn/Article/882242.shtml
- http://wap.mobile.cvsifc.cn/Article/0407.shtml
- http://wap.mobile.fuvxie.cn/Article/13849.shtml
- http://wap.mobile.cvsifc.cn/Article/04201.shtml
- http://wap.mobile.cvsifc.cn/Article/0787.shtml
- http://wap.mobile.fuvxie.cn/Article/9676206.shtml
- http://wap.mobile.hcbezg.cn/Article/564552.shtml
- http://wap.mobile.hcbezg.cn/Article/6302160.shtml
- http://wap.mobile.cvsifc.cn/Article/86067.shtml
- http://wap.mobile.cvsifc.cn/Article/2927448.shtml
- http://wap.mobile.cvsifc.cn/Article/906234.shtml
- http://wap.mobile.fuvxie.cn/Article/776123.shtml
- http://wap.mobile.fuvxie.cn/Article/927591.shtml
- http://wap.mobile.cvsifc.cn/Article/7230.shtml
- http://wap.mobile.cvsifc.cn/Article/1875972.shtml
- http://wap.mobile.cvsifc.cn/Article/706336.shtml
- http://wap.mobile.hcbezg.cn/Article/922995.shtml
- http://wap.mobile.hcbezg.cn/Article/1537326.shtml
- http://wap.mobile.hcbezg.cn/Article/316906.shtml
- http://wap.mobile.hcbezg.cn/Article/4562.shtml
- http://wap.mobile.cvsifc.cn/Article/69032.shtml
- http://wap.mobile.fuvxie.cn/Article/397298.shtml
- http://wap.mobile.hcbezg.cn/Article/6421.shtml
- http://wap.mobile.cvsifc.cn/Article/4104936.shtml
- http://wap.mobile.cvsifc.cn/Article/1383.shtml
- http://wap.mobile.hcbezg.cn/Article/39605.shtml
- http://wap.mobile.cvsifc.cn/Article/1458.shtml
- http://wap.mobile.fuvxie.cn/Article/23608.shtml
- http://wap.mobile.cvsifc.cn/Article/1987.shtml
- http://wap.mobile.hcbezg.cn/Article/78022.shtml
- http://wap.mobile.cvsifc.cn/Article/2794.shtml
- http://wap.mobile.hcbezg.cn/Article/0035.shtml
- http://wap.mobile.hcbezg.cn/Article/38866.shtml
- http://wap.mobile.hcbezg.cn/Article/3069.shtml
- http://wap.mobile.fuvxie.cn/Article/492113.shtml
- http://wap.mobile.fuvxie.cn/Article/4541.shtml
- http://wap.mobile.fuvxie.cn/Article/5147965.shtml
- http://wap.mobile.hcbezg.cn/Article/7281.shtml
- http://wap.mobile.cvsifc.cn/Article/3524.shtml
- http://wap.mobile.cvsifc.cn/Article/4163439.shtml
- http://wap.mobile.hcbezg.cn/Article/2967.shtml
- http://wap.mobile.cvsifc.cn/Article/37108.shtml
- http://wap.mobile.fuvxie.cn/Article/5896.shtml
- http://wap.mobile.hcbezg.cn/Article/23483.shtml
- http://wap.mobile.cvsifc.cn/Article/7471.shtml
- http://wap.mobile.hcbezg.cn/Article/43695.shtml
- http://wap.mobile.fuvxie.cn/Article/0371.shtml
- http://wap.mobile.fuvxie.cn/Article/022412.shtml
- http://wap.mobile.fuvxie.cn/Article/7773708.shtml
- http://wap.mobile.fuvxie.cn/Article/64380.shtml
- http://wap.mobile.fuvxie.cn/Article/402024.shtml
- http://wap.mobile.cvsifc.cn/Article/2448.shtml
- http://wap.mobile.hcbezg.cn/Article/7632245.shtml
- http://wap.mobile.hcbezg.cn/Article/120507.shtml
- http://wap.mobile.fuvxie.cn/Article/408845.shtml
- http://wap.mobile.hcbezg.cn/Article/75510.shtml
- http://wap.mobile.cvsifc.cn/Article/602311.shtml
- http://wap.mobile.hcbezg.cn/Article/40456.shtml
- http://wap.mobile.cvsifc.cn/Article/5286477.shtml
- http://wap.mobile.hcbezg.cn/Article/34590.shtml
- http://wap.mobile.fuvxie.cn/Article/5310.shtml
- http://wap.mobile.hcbezg.cn/Article/9781916.shtml
- http://wap.mobile.hcbezg.cn/Article/4131339.shtml
- http://wap.mobile.cvsifc.cn/Article/2229.shtml
- http://wap.mobile.fuvxie.cn/Article/869281.shtml
- http://wap.mobile.cvsifc.cn/Article/3831129.shtml
- http://wap.mobile.cvsifc.cn/Article/04855.shtml
- http://wap.mobile.fuvxie.cn/Article/5419.shtml
- http://wap.mobile.fuvxie.cn/Article/63616.shtml
- http://wap.mobile.fuvxie.cn/Article/2699.shtml
- http://wap.mobile.hcbezg.cn/Article/13274.shtml
- http://wap.mobile.hcbezg.cn/Article/5638.shtml
- http://wap.mobile.cvsifc.cn/Article/9409.shtml
- http://wap.mobile.cvsifc.cn/Article/7879080.shtml
- http://wap.mobile.fuvxie.cn/Article/6867.shtml
- http://wap.mobile.fuvxie.cn/Article/358760.shtml
- http://wap.mobile.fuvxie.cn/Article/7923.shtml
- http://wap.mobile.fuvxie.cn/Article/2422.shtml
- http://wap.mobile.fuvxie.cn/Article/734777.shtml
- http://wap.mobile.fuvxie.cn/Article/1872609.shtml
- http://wap.mobile.fuvxie.cn/Article/049077.shtml
- http://wap.mobile.hcbezg.cn/Article/73759.shtml
- http://wap.mobile.hcbezg.cn/Article/9944306.shtml
- http://wap.mobile.hcbezg.cn/Article/1341666.shtml
- http://wap.mobile.cvsifc.cn/Article/051407.shtml
- http://wap.mobile.fuvxie.cn/Article/49693.shtml
- http://wap.mobile.cvsifc.cn/Article/6118.shtml
- http://wap.mobile.hcbezg.cn/Article/4365304.shtml
- http://wap.mobile.hcbezg.cn/Article/455872.shtml
- http://wap.mobile.cvsifc.cn/Article/636613.shtml
- http://wap.mobile.hcbezg.cn/Article/425925.shtml
- http://wap.mobile.hcbezg.cn/Article/60701.shtml
- http://wap.mobile.cvsifc.cn/Article/113663.shtml
- http://wap.mobile.hcbezg.cn/Article/1426.shtml
- http://wap.mobile.cvsifc.cn/Article/52138.shtml
- http://wap.mobile.fuvxie.cn/Article/777864.shtml
- http://wap.mobile.cvsifc.cn/Article/8760.shtml
- http://wap.mobile.hcbezg.cn/Article/31075.shtml
- http://wap.mobile.fuvxie.cn/Article/562209.shtml
- http://wap.mobile.cvsifc.cn/Article/85548.shtml
- http://wap.mobile.fuvxie.cn/Article/22061.shtml
- http://wap.mobile.hcbezg.cn/Article/38526.shtml
- http://wap.mobile.fuvxie.cn/Article/507812.shtml
- http://wap.mobile.cvsifc.cn/Article/3658.shtml
- http://wap.mobile.fuvxie.cn/Article/4451940.shtml
- http://wap.mobile.fuvxie.cn/Article/1437.shtml
- http://wap.mobile.cvsifc.cn/Article/1663357.shtml
- http://wap.mobile.hcbezg.cn/Article/2638429.shtml
- http://wap.mobile.cvsifc.cn/Article/2061.shtml
- http://wap.mobile.cvsifc.cn/Article/8137739.shtml
- http://wap.mobile.fuvxie.cn/Article/2979805.shtml
- http://wap.mobile.hcbezg.cn/Article/2962289.shtml
- http://wap.mobile.fuvxie.cn/Article/797682.shtml
- http://wap.mobile.hcbezg.cn/Article/6685192.shtml
- http://wap.mobile.cvsifc.cn/Article/096797.shtml
- http://wap.mobile.hcbezg.cn/Article/55147.shtml
- http://wap.mobile.cvsifc.cn/Article/11807.shtml
- http://wap.mobile.hcbezg.cn/Article/6203796.shtml
- http://wap.mobile.cvsifc.cn/Article/5999005.shtml
- http://wap.mobile.fuvxie.cn/Article/0755.shtml
- http://wap.mobile.fuvxie.cn/Article/6611.shtml
- http://wap.mobile.fuvxie.cn/Article/3907.shtml
- http://wap.mobile.hcbezg.cn/Article/14977.shtml
- http://wap.mobile.cvsifc.cn/Article/44323.shtml
- http://wap.mobile.cvsifc.cn/Article/2902.shtml
- http://wap.mobile.cvsifc.cn/Article/611003.shtml
- http://wap.mobile.fuvxie.cn/Article/12253.shtml
- http://wap.mobile.hcbezg.cn/Article/861287.shtml
- http://wap.mobile.cvsifc.cn/Article/85746.shtml
- http://wap.mobile.cvsifc.cn/Article/3603.shtml
- http://wap.mobile.hcbezg.cn/Article/6428686.shtml
- http://wap.mobile.cvsifc.cn/Article/0675.shtml
- http://wap.mobile.fuvxie.cn/Article/0737.shtml
- http://wap.mobile.hcbezg.cn/Article/370311.shtml
- http://wap.mobile.fuvxie.cn/Article/25563.shtml
- http://wap.mobile.fuvxie.cn/Article/64175.shtml
- http://wap.mobile.cvsifc.cn/Article/485799.shtml
- http://wap.mobile.cvsifc.cn/Article/8070.shtml
- http://wap.mobile.cvsifc.cn/Article/6265.shtml
- http://wap.mobile.fuvxie.cn/Article/28037.shtml
- http://wap.mobile.hcbezg.cn/Article/487177.shtml
- http://wap.mobile.hcbezg.cn/Article/60568.shtml
- http://wap.mobile.cvsifc.cn/Article/12195.shtml
- http://wap.mobile.fuvxie.cn/Article/1914.shtml
- http://wap.mobile.cvsifc.cn/Article/6217.shtml
- http://wap.mobile.cvsifc.cn/Article/8673960.shtml
- http://wap.mobile.hcbezg.cn/Article/5686332.shtml
- http://wap.mobile.hcbezg.cn/Article/9519999.shtml
- http://wap.mobile.cvsifc.cn/Article/739643.shtml
- http://wap.mobile.fuvxie.cn/Article/3099795.shtml
- http://wap.mobile.hcbezg.cn/Article/64928.shtml
- http://wap.mobile.fuvxie.cn/Article/092522.shtml
- http://wap.mobile.hcbezg.cn/Article/6154313.shtml
- http://wap.mobile.hcbezg.cn/Article/1816281.shtml
- http://wap.mobile.cvsifc.cn/Article/857350.shtml
- http://wap.mobile.fuvxie.cn/Article/18237.shtml
- http://wap.mobile.fuvxie.cn/Article/3453.shtml
- http://wap.mobile.fuvxie.cn/Article/54524.shtml
- http://wap.mobile.hcbezg.cn/Article/5749.shtml
- http://wap.mobile.cvsifc.cn/Article/96979.shtml
- http://wap.mobile.cvsifc.cn/Article/493068.shtml
- http://wap.mobile.cvsifc.cn/Article/61387.shtml
- http://wap.mobile.hcbezg.cn/Article/5577821.shtml
- http://wap.mobile.fuvxie.cn/Article/6703117.shtml
- http://wap.mobile.hcbezg.cn/Article/457979.shtml
- http://wap.mobile.cvsifc.cn/Article/4859.shtml
- http://wap.mobile.cvsifc.cn/Article/6374.shtml
- http://wap.mobile.hcbezg.cn/Article/9726940.shtml
- http://wap.mobile.cvsifc.cn/Article/68808.shtml
- http://wap.mobile.fuvxie.cn/Article/464615.shtml
- http://wap.mobile.hcbezg.cn/Article/8075.shtml
- http://wap.mobile.hcbezg.cn/Article/6494.shtml
- http://wap.mobile.fuvxie.cn/Article/961223.shtml
- http://wap.mobile.hcbezg.cn/Article/2653129.shtml
- http://wap.mobile.hcbezg.cn/Article/3784.shtml
- http://wap.mobile.fuvxie.cn/Article/0501.shtml
- http://wap.mobile.fuvxie.cn/Article/303829.shtml
- http://wap.mobile.fuvxie.cn/Article/7652631.shtml
- http://wap.mobile.hcbezg.cn/Article/3358.shtml
- http://wap.mobile.fuvxie.cn/Article/78767.shtml
- http://wap.mobile.fuvxie.cn/Article/23629.shtml
- http://wap.mobile.cvsifc.cn/Article/1042374.shtml
- http://wap.mobile.hcbezg.cn/Article/73504.shtml
- http://wap.mobile.hcbezg.cn/Article/400717.shtml
- http://wap.mobile.hcbezg.cn/Article/7625.shtml
- http://wap.mobile.cvsifc.cn/Article/170311.shtml
- http://wap.mobile.fuvxie.cn/Article/2975.shtml
- http://wap.mobile.hcbezg.cn/Article/84556.shtml
- http://wap.mobile.fuvxie.cn/Article/1315900.shtml
- http://wap.mobile.hcbezg.cn/Article/8446.shtml
- http://wap.mobile.hcbezg.cn/Article/47467.shtml
- http://wap.mobile.cvsifc.cn/Article/349221.shtml
- http://wap.mobile.hcbezg.cn/Article/43531.shtml
- http://wap.mobile.hcbezg.cn/Article/8276349.shtml
- http://wap.mobile.fuvxie.cn/Article/044213.shtml
- http://wap.mobile.fuvxie.cn/Article/044064.shtml
- http://wap.mobile.fuvxie.cn/Article/67667.shtml
- http://wap.mobile.cvsifc.cn/Article/967238.shtml
- http://wap.mobile.cvsifc.cn/Article/70597.shtml
- http://wap.mobile.cvsifc.cn/Article/7126.shtml
- http://wap.mobile.fuvxie.cn/Article/6904337.shtml
- http://wap.mobile.fuvxie.cn/Article/23431.shtml
- http://wap.mobile.cvsifc.cn/Article/7102.shtml
- http://wap.mobile.hcbezg.cn/Article/3407178.shtml
- http://wap.mobile.cvsifc.cn/Article/45669.shtml
- http://wap.mobile.fuvxie.cn/Article/2840343.shtml
- http://wap.mobile.fuvxie.cn/Article/7061.shtml
- http://wap.mobile.fuvxie.cn/Article/1166321.shtml
- http://wap.mobile.cvsifc.cn/Article/99703.shtml
- http://wap.mobile.cvsifc.cn/Article/9786.shtml
- http://wap.mobile.fuvxie.cn/Article/51180.shtml
- http://wap.mobile.fuvxie.cn/Article/9197126.shtml
- http://wap.mobile.cvsifc.cn/Article/9645.shtml
- http://wap.mobile.hcbezg.cn/Article/86726.shtml
- http://wap.mobile.hcbezg.cn/Article/72914.shtml
- http://wap.mobile.fuvxie.cn/Article/82284.shtml
- http://wap.mobile.cvsifc.cn/Article/146471.shtml
- http://wap.mobile.hcbezg.cn/Article/8739051.shtml
- http://wap.mobile.cvsifc.cn/Article/8819.shtml
- http://wap.mobile.cvsifc.cn/Article/332276.shtml
- http://wap.mobile.fuvxie.cn/Article/3750050.shtml
- http://wap.mobile.fuvxie.cn/Article/2628938.shtml
- http://wap.mobile.fuvxie.cn/Article/06379.shtml
- http://wap.mobile.cvsifc.cn/Article/00126.shtml
- http://wap.mobile.cvsifc.cn/Article/5022301.shtml

## 项目结构

```
webarchive-bridge/
├── backend/                         # 后端服务核心代码
│   ├── src/
│   │   ├── controllers/             # 请求控制器，处理路由逻辑
│   │   ├── models/                  # 数据模型定义，包含 URL 记录和标签实体
│   │   ├── services/                # 业务服务层，含检测、索引、导入导出服务
│   │   ├── workers/                 # 后台任务进程，执行定时检测和队列消费
│   │   └── utils/                   # 通用工具函数，含请求头解析和字符串处理
│   ├── config/                      # 配置文件目录，包含数据库连接和缓存配置
│   └── tests/                       # 后端单元测试与集成测试用例
├── frontend/                        # 前端应用源码
│   ├── src/
│   │   ├── pages/                   # 页面组件，包含列表页、详情页、导入页
│   │   ├── components/              # 可复用 UI 组件，含表格、标签选择器、搜索栏
│   │   ├── stores/                  # 状态管理，基于 Pinia 的全局数据仓库
│   │   └── api/                     # 与后端交互的接口封装层
│   ├── public/                      # 静态资源，含 favicon 和基础样式
│   └── tests/                       # 前端组件测试和 E2E 测试
├── docs/                            # 项目文档，含入门指南、操作手册和 API 参考
├── scripts/                         # 运维脚本，包含数据库迁移和初始化数据填充
├── data/                            # 数据存储目录，存放 SQLite 数据库文件和备份
├── logs/                            # 日志输出目录，按日期分割的服务运行日志
├── docker-compose.yml               # Docker 编排文件，用于快速搭建完整运行环境
├── Dockerfile                       # 后端服务容器构建定义
├── nginx.conf                       # 生产环境 Nginx 反向代理配置模板
├── package.json                     # 项目依赖清单和脚本命令定义
└── README.md                        # 项目说明文档
```

## 贡献指南

1. 阅读项目行为准则和贡献者公约，确保遵守社区规范。在 GitHub Issues 中查找标记为 help-wanted 或 good-first-issue 的任务，或提交新需求描述您希望解决的问题。

2. 克隆项目到本地，创建以 feature/ 或 fix/ 为前缀的分支，例如 feature/batch-import-csv。确保分支名称清晰反映变更内容。

3. 编写代码时遵循项目已配置的 ESLint 和 Prettier 规则。所有新增功能必须包含对应的单元测试，测试覆盖率不应低于 80%。对于后端变更，需提供 API 请求与响应的示例说明。

4. 提交前执行 npm run lint 和 npm run test 确保检查通过。提交信息采用 Conventional Commits 格式，即 type(scope): description，例如 feat(import): support CSV file with custom delimiter。

5. 推送分支后创建 Pull Request，在描述中关联相关 Issue 编号，并简要说明测试结果和变更影响范围。至少需要一名项目维护者审阅通过后方可合并。

## 常见问题

**问：系统是否存储原始文章内容或页面截图？**

答：不存储。WebArchive Bridge 仅保存 URL 地址、用户自定义标签、检测状态和基础元数据（如响应状态码、最后修改时间）。所有原始内容仍托管于原始站点，系统不涉及任何内容缓存或代理转发，确保无版权风险。

**问：变更检测功能如何处理需要登录或反爬机制的页面？**

答：检测模块默认仅发送标准 GET 请求头，不携带 Cookie 或会话信息，因此无法检测需要身份验证的页面。对于此类受限资源，系统会在状态栏中标记为 access-denied，用户可手动配置自定义请求头（如 Referer 或 User-Agent）以绕过基础限制，但登录态页面建议通过其他专用工具处理。

**问：批量导入支持哪些格式？最大条目数是多少？**

答：当前支持纯文本每行一个 URL 的 .txt 文件，以及包含 URL 列的 .csv 和 .xlsx 表格文件。单次导入上限为 5000 条，超过该数量建议分批操作。导入过程会实时校验 URL 格式合法性，并跳过重复记录，最终返回成功与失败条目的详细报告。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
