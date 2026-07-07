# Mobile Article Index Collector

Mobile Article Index Collector 是一个面向移动端技术内容聚合与导航的开源工具，旨在解决移动开发、移动安全、移动端运维及跨平台应用场景中，技术文档碎片化分布、检索效率低下的问题。本项目通过结构化的资源索引机制，将分散在多个移动端技术站点中的高质量文章按主题、场景和用途进行归集与分类，为移动端工程师、技术决策者及研究人员提供一套可快速部署、可扩展的外部资源导航框架。

项目本身不存储或缓存任何文章内容，仅提供基于 URL 的元数据索引与分类体系。用户可通过本项目提供的分类规则、标签系统及检索接口，快速定位所需技术资料。项目设计遵循最小依赖原则，可在任意支持 HTTP 请求的轻量级环境中运行，适用于个人开发者的技术笔记管理、团队内部知识库建设，以及开源社区的技术资源共建共享。

## 功能概览

- **多维度资源分类**：支持按移动平台（Android、iOS、HarmonyOS）、技术领域（UI 渲染、网络通信、数据存储、安全加固）及文档类型（教程、API 参考、案例分析、故障排查）对文章链接进行标记与分组。

- **自定义标签系统**：允许用户为每个 URL 附加一个或多个自定义标签，实现精细化筛选。标签支持导入导出，便于团队同步分类标准。

- **批量链接导入与校验**：提供命令行工具，支持从纯文本文件、CSV 或 JSON 中批量导入 URL，并自动执行可达性校验与响应状态码记录，标记失效链接。

- **静态站点生成模式**：内置模板引擎，可将索引数据渲染为静态 HTML 导航页面，支持响应式设计，适配移动端和桌面端浏览，无需后端服务即可部署至任何静态托管平台。

- **查询过滤器与正则匹配**：提供基于 Python 正则表达式的 URL 模式过滤功能，支持按域名、路径关键词、文件扩展名等条件快速筛选链接子集，便于做专项分析。

- **元数据扩展字段**：每条索引记录支持存储标题推测、来源站点、收录时间、最后校验时间等元数据，所有字段均可作为排序与过滤条件。

## 应用场景

**移动开发团队内部知识库建设**  
技术团队可使用本项目搭建私有化资源导航站，将团队积累的踩坑记录、性能优化案例、第三方 SDK 文档等散落链接统一收录，新成员入职时可快速获取经过筛选的学习资料集合。

**开源技术文档聚合站点**  
开源社区维护者可将本项目作为文档聚合底座，将散布在各处的教程、视频、博客文章按模块整理，通过静态生成功能输出为结构清晰的文档门户，降低社区用户的信息获取门槛。

**移动安全研究参考资料库**  
移动安全研究人员可利用本项目的标签与过滤系统，收集各类漏洞分析报告、加固方案、逆向工程教程，并按漏洞类型（如注入、越权、组件暴露）或操作系统版本进行分类，形成专项参考资料库。

**个人技术博客外链管理**  
技术博主或独立开发者可使用本项目管理个人博客中的外部引用链接，定时校验链接有效性，避免文章中出现死链，同时生成外链清单供读者直接访问推荐资源。

## 快速开始

以下命令演示了从克隆仓库到启动基础索引服务的完整流程。

```bash
# 克隆项目仓库
git clone https://github.com/mobile-index-collector/mic-core.git
cd mic-core

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化索引数据库（SQLite）
python mic_cli.py init --db-path ./data/index.db

# 从文本文件批量导入 URL（每行一个 URL）
python mic_cli.py import --input ./sources/url_list.txt --tags "mobile,reference"

# 启动本地静态预览服务（默认端口 8080）
python mic_cli.py serve --port 8080 --output ./public
```

访问 `http://127.0.0.1:8080` 即可查看生成的导航页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，用于 CLI 工具与模板渲染 |
| SQLite | 3.28 及以上 | 默认索引数据库引擎，支持并发读 |
| requests | 2.25.1 及以上 | 用于 URL 可达性校验与响应分析 |
| jinja2 | 3.0.0 及以上 | 静态页面模板渲染引擎 |
| click | 8.0.0 及以上 | 命令行交互框架，用于 CLI 子命令解析 |
| pytest | 7.0.0 及以上（可选） | 单元测试框架，仅开发环境需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何安装、配置、导入链接、生成静态站点？标签系统如何使用？ |
| 开发指南 | /docs/developer-guide/ | 项目模块划分是什么？如何扩展新的分类器？如何提交代码？ |
| API 参考 | /docs/api-reference/ | CLI 命令的完整参数列表是什么？索引数据库的 Schema 定义？ |
| 设计文档 | /docs/design/ | 索引数据结构为何这样设计？标签系统的匹配策略是什么？ |

## 资源列表

- http://www.mobile.fuvxie.cn/Article/8314.shtml
- http://www.mobile.cvsifc.cn/Article/3693969.shtml
- http://www.mobile.hcbezg.cn/Article/9412.shtml
- http://www.mobile.hcbezg.cn/Article/0016.shtml
- http://www.mobile.fuvxie.cn/Article/3968.shtml
- http://www.mobile.fuvxie.cn/Article/4186.shtml
- http://www.mobile.cvsifc.cn/Article/212069.shtml
- http://www.mobile.cvsifc.cn/Article/2078.shtml
- http://www.mobile.fuvxie.cn/Article/5541997.shtml
- http://www.mobile.hcbezg.cn/Article/1573.shtml
- http://www.mobile.cvsifc.cn/Article/8396.shtml
- http://www.mobile.hcbezg.cn/Article/3245637.shtml
- http://www.mobile.hcbezg.cn/Article/93753.shtml
- http://www.mobile.fuvxie.cn/Article/16416.shtml
- http://www.mobile.cvsifc.cn/Article/6360195.shtml
- http://www.mobile.cvsifc.cn/Article/204877.shtml
- http://www.mobile.fuvxie.cn/Article/6201.shtml
- http://www.mobile.fuvxie.cn/Article/3385150.shtml
- http://www.mobile.fuvxie.cn/Article/092547.shtml
- http://www.mobile.fuvxie.cn/Article/70092.shtml
- http://www.mobile.fuvxie.cn/Article/915232.shtml
- http://www.mobile.hcbezg.cn/Article/3089.shtml
- http://www.mobile.hcbezg.cn/Article/0835953.shtml
- http://www.mobile.hcbezg.cn/Article/77419.shtml
- http://www.mobile.hcbezg.cn/Article/640170.shtml
- http://www.mobile.cvsifc.cn/Article/1009.shtml
- http://www.mobile.fuvxie.cn/Article/7246.shtml
- http://www.mobile.hcbezg.cn/Article/5008.shtml
- http://www.mobile.hcbezg.cn/Article/984345.shtml
- http://www.mobile.cvsifc.cn/Article/6509266.shtml
- http://www.mobile.cvsifc.cn/Article/7210.shtml
- http://www.mobile.hcbezg.cn/Article/957172.shtml
- http://www.mobile.fuvxie.cn/Article/64771.shtml
- http://www.mobile.hcbezg.cn/Article/15214.shtml
- http://www.mobile.cvsifc.cn/Article/9740.shtml
- http://www.mobile.fuvxie.cn/Article/6627209.shtml
- http://www.mobile.cvsifc.cn/Article/63671.shtml
- http://www.mobile.hcbezg.cn/Article/13632.shtml
- http://www.mobile.hcbezg.cn/Article/409574.shtml
- http://www.mobile.cvsifc.cn/Article/9444016.shtml
- http://www.mobile.cvsifc.cn/Article/3925161.shtml
- http://www.mobile.hcbezg.cn/Article/2499370.shtml
- http://www.mobile.cvsifc.cn/Article/8220.shtml
- http://www.mobile.fuvxie.cn/Article/9896.shtml
- http://www.mobile.fuvxie.cn/Article/3372776.shtml
- http://www.mobile.hcbezg.cn/Article/3973231.shtml
- http://www.mobile.cvsifc.cn/Article/2700390.shtml
- http://www.mobile.cvsifc.cn/Article/1394820.shtml
- http://www.mobile.hcbezg.cn/Article/74248.shtml
- http://www.mobile.hcbezg.cn/Article/529161.shtml
- http://www.mobile.cvsifc.cn/Article/168851.shtml
- http://www.mobile.fuvxie.cn/Article/34882.shtml
- http://www.mobile.fuvxie.cn/Article/3321139.shtml
- http://www.mobile.fuvxie.cn/Article/512467.shtml
- http://www.mobile.hcbezg.cn/Article/43116.shtml
- http://www.mobile.cvsifc.cn/Article/3148.shtml
- http://www.mobile.hcbezg.cn/Article/9237072.shtml
- http://www.mobile.cvsifc.cn/Article/8582296.shtml
- http://www.mobile.hcbezg.cn/Article/3174910.shtml
- http://www.mobile.hcbezg.cn/Article/6254054.shtml
- http://www.mobile.cvsifc.cn/Article/6322.shtml
- http://www.mobile.cvsifc.cn/Article/4908119.shtml
- http://www.mobile.fuvxie.cn/Article/35331.shtml
- http://www.mobile.cvsifc.cn/Article/07680.shtml
- http://www.mobile.cvsifc.cn/Article/42098.shtml
- http://www.mobile.fuvxie.cn/Article/8318.shtml
- http://www.mobile.fuvxie.cn/Article/78693.shtml
- http://www.mobile.fuvxie.cn/Article/66000.shtml
- http://www.mobile.cvsifc.cn/Article/897401.shtml
- http://www.mobile.fuvxie.cn/Article/9875933.shtml
- http://www.mobile.fuvxie.cn/Article/5929186.shtml
- http://www.mobile.fuvxie.cn/Article/44305.shtml
- http://www.mobile.cvsifc.cn/Article/076510.shtml
- http://www.mobile.cvsifc.cn/Article/4260408.shtml
- http://www.mobile.cvsifc.cn/Article/924408.shtml
- http://www.mobile.hcbezg.cn/Article/7260.shtml
- http://www.mobile.fuvxie.cn/Article/3954.shtml
- http://www.mobile.cvsifc.cn/Article/2893.shtml
- http://www.mobile.cvsifc.cn/Article/0101636.shtml
- http://www.mobile.fuvxie.cn/Article/214310.shtml
- http://www.mobile.hcbezg.cn/Article/46096.shtml
- http://www.mobile.hcbezg.cn/Article/79726.shtml
- http://www.mobile.cvsifc.cn/Article/45920.shtml
- http://www.mobile.fuvxie.cn/Article/136081.shtml
- http://www.mobile.hcbezg.cn/Article/1836.shtml
- http://www.mobile.fuvxie.cn/Article/2045657.shtml
- http://www.mobile.cvsifc.cn/Article/9856.shtml
- http://www.mobile.hcbezg.cn/Article/71542.shtml
- http://www.mobile.hcbezg.cn/Article/14827.shtml
- http://www.mobile.cvsifc.cn/Article/16989.shtml
- http://www.mobile.fuvxie.cn/Article/4984.shtml
- http://www.mobile.fuvxie.cn/Article/9752282.shtml
- http://www.mobile.cvsifc.cn/Article/267744.shtml
- http://www.mobile.fuvxie.cn/Article/269406.shtml
- http://www.mobile.cvsifc.cn/Article/472791.shtml
- http://www.mobile.cvsifc.cn/Article/9670713.shtml
- http://www.mobile.hcbezg.cn/Article/147764.shtml
- http://www.mobile.cvsifc.cn/Article/7788.shtml
- http://www.mobile.fuvxie.cn/Article/840332.shtml
- http://www.mobile.hcbezg.cn/Article/06964.shtml
- http://www.mobile.fuvxie.cn/Article/7447.shtml
- http://www.mobile.hcbezg.cn/Article/9289890.shtml
- http://www.mobile.fuvxie.cn/Article/128690.shtml
- http://www.mobile.cvsifc.cn/Article/82917.shtml
- http://www.mobile.cvsifc.cn/Article/44043.shtml
- http://www.mobile.fuvxie.cn/Article/965413.shtml
- http://www.mobile.cvsifc.cn/Article/9928.shtml
- http://www.mobile.cvsifc.cn/Article/86937.shtml
- http://www.mobile.cvsifc.cn/Article/6131679.shtml
- http://www.mobile.cvsifc.cn/Article/716968.shtml
- http://www.mobile.fuvxie.cn/Article/48681.shtml
- http://www.mobile.hcbezg.cn/Article/5740844.shtml
- http://www.mobile.fuvxie.cn/Article/975830.shtml
- http://www.mobile.cvsifc.cn/Article/40795.shtml
- http://www.mobile.hcbezg.cn/Article/320483.shtml
- http://www.mobile.cvsifc.cn/Article/892531.shtml
- http://www.mobile.hcbezg.cn/Article/5888874.shtml
- http://www.mobile.fuvxie.cn/Article/21526.shtml
- http://www.mobile.fuvxie.cn/Article/3704205.shtml
- http://www.mobile.hcbezg.cn/Article/2138326.shtml
- http://www.mobile.fuvxie.cn/Article/670172.shtml
- http://www.mobile.hcbezg.cn/Article/2298391.shtml
- http://www.mobile.hcbezg.cn/Article/583077.shtml
- http://www.mobile.fuvxie.cn/Article/8176.shtml
- http://www.mobile.cvsifc.cn/Article/71606.shtml
- http://www.mobile.cvsifc.cn/Article/663090.shtml
- http://www.mobile.hcbezg.cn/Article/408643.shtml
- http://www.mobile.hcbezg.cn/Article/5337306.shtml
- http://www.mobile.hcbezg.cn/Article/5824.shtml
- http://www.mobile.hcbezg.cn/Article/0535.shtml
- http://www.mobile.hcbezg.cn/Article/23412.shtml
- http://www.mobile.hcbezg.cn/Article/97553.shtml
- http://www.mobile.cvsifc.cn/Article/6676929.shtml
- http://www.mobile.fuvxie.cn/Article/78493.shtml
- http://www.mobile.cvsifc.cn/Article/348721.shtml
- http://www.mobile.fuvxie.cn/Article/0330079.shtml
- http://www.mobile.hcbezg.cn/Article/748565.shtml
- http://www.mobile.hcbezg.cn/Article/5402613.shtml
- http://www.mobile.cvsifc.cn/Article/20106.shtml
- http://www.mobile.hcbezg.cn/Article/39452.shtml
- http://www.mobile.hcbezg.cn/Article/6288275.shtml
- http://www.mobile.fuvxie.cn/Article/048620.shtml
- http://www.mobile.fuvxie.cn/Article/5454.shtml
- http://www.mobile.fuvxie.cn/Article/325155.shtml
- http://www.mobile.cvsifc.cn/Article/6699.shtml
- http://www.mobile.cvsifc.cn/Article/749401.shtml
- http://www.mobile.fuvxie.cn/Article/30555.shtml
- http://www.mobile.hcbezg.cn/Article/34960.shtml
- http://www.mobile.hcbezg.cn/Article/3251697.shtml
- http://www.mobile.fuvxie.cn/Article/8854.shtml
- http://www.mobile.fuvxie.cn/Article/3674997.shtml
- http://www.mobile.hcbezg.cn/Article/64137.shtml
- http://www.mobile.hcbezg.cn/Article/5510.shtml
- http://www.mobile.cvsifc.cn/Article/8555813.shtml
- http://www.mobile.cvsifc.cn/Article/5462446.shtml
- http://www.mobile.hcbezg.cn/Article/08332.shtml
- http://www.mobile.hcbezg.cn/Article/6984.shtml
- http://www.mobile.cvsifc.cn/Article/96709.shtml
- http://www.mobile.hcbezg.cn/Article/35553.shtml
- http://www.mobile.hcbezg.cn/Article/39114.shtml
- http://www.mobile.fuvxie.cn/Article/610951.shtml
- http://www.mobile.hcbezg.cn/Article/117967.shtml
- http://www.mobile.fuvxie.cn/Article/85298.shtml
- http://www.mobile.hcbezg.cn/Article/4111.shtml
- http://www.mobile.fuvxie.cn/Article/37428.shtml
- http://www.mobile.cvsifc.cn/Article/8300.shtml
- http://www.mobile.cvsifc.cn/Article/32322.shtml
- http://www.mobile.fuvxie.cn/Article/055126.shtml
- http://www.mobile.hcbezg.cn/Article/6052769.shtml
- http://www.mobile.cvsifc.cn/Article/3119234.shtml
- http://www.mobile.cvsifc.cn/Article/0544133.shtml
- http://www.mobile.hcbezg.cn/Article/98101.shtml
- http://www.mobile.hcbezg.cn/Article/4878.shtml
- http://www.mobile.fuvxie.cn/Article/14973.shtml
- http://www.mobile.cvsifc.cn/Article/41341.shtml
- http://www.mobile.hcbezg.cn/Article/42878.shtml
- http://www.mobile.cvsifc.cn/Article/6855688.shtml
- http://www.mobile.fuvxie.cn/Article/36794.shtml
- http://www.mobile.hcbezg.cn/Article/860615.shtml
- http://www.mobile.hcbezg.cn/Article/328564.shtml
- http://www.mobile.fuvxie.cn/Article/1386432.shtml
- http://www.mobile.cvsifc.cn/Article/9085.shtml
- http://www.mobile.hcbezg.cn/Article/5046.shtml
- http://www.mobile.cvsifc.cn/Article/148718.shtml
- http://www.mobile.fuvxie.cn/Article/8392281.shtml
- http://www.mobile.fuvxie.cn/Article/8582.shtml
- http://www.mobile.fuvxie.cn/Article/95260.shtml
- http://www.mobile.fuvxie.cn/Article/1716.shtml
- http://www.mobile.fuvxie.cn/Article/25583.shtml
- http://www.mobile.fuvxie.cn/Article/566047.shtml
- http://www.mobile.fuvxie.cn/Article/781840.shtml
- http://www.mobile.cvsifc.cn/Article/1117.shtml
- http://www.mobile.cvsifc.cn/Article/4260.shtml
- http://www.mobile.hcbezg.cn/Article/5123.shtml
- http://www.mobile.fuvxie.cn/Article/8530.shtml
- http://www.mobile.cvsifc.cn/Article/5093132.shtml
- http://www.mobile.fuvxie.cn/Article/796457.shtml
- http://www.mobile.fuvxie.cn/Article/432308.shtml
- http://www.mobile.hcbezg.cn/Article/097829.shtml
- http://www.mobile.fuvxie.cn/Article/7778.shtml
- http://www.mobile.cvsifc.cn/Article/570386.shtml
- http://www.mobile.cvsifc.cn/Article/2761.shtml
- http://www.mobile.fuvxie.cn/Article/313482.shtml
- http://www.mobile.cvsifc.cn/Article/0883.shtml
- http://www.mobile.cvsifc.cn/Article/7277.shtml
- http://www.mobile.cvsifc.cn/Article/5116960.shtml
- http://www.mobile.hcbezg.cn/Article/8104408.shtml
- http://www.mobile.hcbezg.cn/Article/27826.shtml
- http://www.mobile.fuvxie.cn/Article/01490.shtml
- http://www.mobile.hcbezg.cn/Article/054195.shtml
- http://www.mobile.hcbezg.cn/Article/7986.shtml
- http://www.mobile.fuvxie.cn/Article/69024.shtml
- http://www.mobile.cvsifc.cn/Article/59246.shtml
- http://www.mobile.hcbezg.cn/Article/27927.shtml
- http://www.mobile.fuvxie.cn/Article/9069437.shtml
- http://www.mobile.hcbezg.cn/Article/095063.shtml
- http://www.mobile.fuvxie.cn/Article/303443.shtml
- http://www.mobile.hcbezg.cn/Article/991856.shtml
- http://www.mobile.cvsifc.cn/Article/4582699.shtml
- http://www.mobile.fuvxie.cn/Article/9413607.shtml
- http://www.mobile.fuvxie.cn/Article/57611.shtml
- http://www.mobile.fuvxie.cn/Article/3029003.shtml
- http://www.mobile.cvsifc.cn/Article/829553.shtml
- http://www.mobile.hcbezg.cn/Article/094797.shtml
- http://www.mobile.fuvxie.cn/Article/68645.shtml
- http://www.mobile.fuvxie.cn/Article/9987.shtml
- http://www.mobile.fuvxie.cn/Article/5299.shtml
- http://www.mobile.hcbezg.cn/Article/8709586.shtml
- http://www.mobile.hcbezg.cn/Article/5689.shtml
- http://www.mobile.fuvxie.cn/Article/594587.shtml
- http://www.mobile.cvsifc.cn/Article/7625494.shtml
- http://www.mobile.cvsifc.cn/Article/21370.shtml
- http://www.mobile.cvsifc.cn/Article/7764690.shtml
- http://www.mobile.cvsifc.cn/Article/8204162.shtml
- http://www.mobile.hcbezg.cn/Article/61830.shtml
- http://www.mobile.cvsifc.cn/Article/3139.shtml
- http://www.mobile.hcbezg.cn/Article/419315.shtml
- http://www.mobile.cvsifc.cn/Article/06801.shtml
- http://www.mobile.hcbezg.cn/Article/13521.shtml
- http://www.mobile.cvsifc.cn/Article/92341.shtml
- http://www.mobile.cvsifc.cn/Article/10310.shtml
- http://www.mobile.hcbezg.cn/Article/9403.shtml
- http://www.mobile.fuvxie.cn/Article/05975.shtml
- http://www.mobile.hcbezg.cn/Article/28653.shtml
- http://www.mobile.fuvxie.cn/Article/780998.shtml
- http://www.mobile.fuvxie.cn/Article/284896.shtml
- http://www.mobile.cvsifc.cn/Article/0200.shtml
- http://www.mobile.hcbezg.cn/Article/6188.shtml
- http://www.mobile.hcbezg.cn/Article/010100.shtml
- http://www.mobile.cvsifc.cn/Article/1102.shtml

## 项目结构

```
mic-core/
├── cli/                                 # 命令行接口模块
│   ├── __init__.py                      # 模块初始化，导出主命令组
│   ├── commands.py                      # 定义 import、serve、init 等子命令实现
│   └── validators.py                    # 输入校验与参数格式化
├── core/                                # 核心索引引擎
│   ├── indexer.py                       # 索引构建、更新、查询的主逻辑
│   ├── models.py                        # SQLAlchemy ORM 模型定义（IndexRecord, Tag）
│   └── filters.py                       # 正则过滤、标签匹配、多条件组合查询
├── data/                                # 数据存储目录（运行时生成）
│   ├── index.db                         # SQLite 默认数据库文件
│   └── imports/                         # 存放外部导入的原始 URL 列表备份
├── templates/                           # 静态站点渲染模板
│   ├── base.html                        # 基础 HTML 骨架
│   ├── index.html                       # 首页导航列表渲染模板
│   └── detail.html                      # 单条链接元数据详情页模板
├── tests/                               # 单元测试与集成测试
│   ├── test_indexer.py                  # 索引核心功能测试
│   ├── test_filters.py                  # 过滤表达式解析与匹配测试
│   └── fixtures/                        # 测试用固定数据集
├── docs/                                # 完整文档源文件
│   ├── user-guide/                      # 用户手册章节
│   ├── developer-guide/                 # 开发指南与贡献规范
│   └── design/                          # 架构设计决策记录
├── requirements.txt                     # 生产环境 Python 依赖列表
├── requirements-dev.txt                 # 开发环境额外依赖（测试、代码检查）
├── setup.py                             # 项目打包与安装配置
├── README.md                            # 项目入口说明文档（本文件）
└── LICENSE                              # MIT 许可证文本
```

## 贡献指南

1. 阅读项目设计文档与开发指南，了解索引数据结构、标签系统及 CLI 命令的扩展方式。设计文档位于 `/docs/design/` 目录下。

2. 在 GitHub 上 fork 本仓库，创建以 `feature/` 或 `fix/` 为前缀的分支，遵循语义化命名规范，例如 `feature/add-json-export`。

3. 编写代码时请遵循 PEP 8 编码规范，并为新增函数或类添加完整的 docstring 注释。所有对外 CLI 参数变更需同步更新用户手册。

4. 在提交 Pull Request 之前，确保所有单元测试通过（执行 `pytest tests/`），并且新增功能有对应的测试用例覆盖。

5. 提交 PR 时请清晰描述改动动机、实现方式及影响范围，若涉及索引数据库 Schema 变更，需附带迁移脚本或说明兼容性处理方案。

## 常见问题

**Q：导入大量 URL 时出现超时或连接错误，如何处理？**

A：CLI 工具默认使用 5 秒连接超时和 10 秒读取超时。对于大规模导入，建议使用 `--timeout` 参数调大超时阈值，或使用 `--skip-check` 选项跳过实时可达性校验，后续再通过 `verify` 子命令单独校验。同时检查网络环境是否稳定，部分站点可能限制频繁访问，可适当增加 `--delay` 参数设置请求间隔。

**Q：如何迁移索引数据到另一台机器？**

A：默认 SQLite 数据库文件位于 `data/index.db`，直接复制该文件即可迁移所有索引记录与标签数据。若需跨数据库类型（如迁移至 PostgreSQL），可使用 `export` 命令导出为 JSON 格式，再在目标环境使用 `import` 命令导入。注意迁移后需重新执行可达性校验以确保链接状态准确。

**Q：静态生成的导航页面能否支持搜索功能？**

A：内置模板生成的页面为纯静态 HTML，不支持服务端搜索。如需搜索功能，建议将生成的页面部署至支持静态站点搜索的托管平台（如 Cloudflare Pages 或 Vercel 的搜索插件），或使用 `--output-json` 选项生成索引数据的 JSON 文件，配合前端搜索库（如 Lunr.js 或 FlexSearch）自行集成。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
