# LinkMap 移动端技术资源导航站

LinkMap 是一个面向移动端开发工程师、运维工程师与技术决策者的结构化外链资源汇总系统。该项目并非传统的内容管理系统，而是一个高度规范化的技术资源导航枢纽，专注于聚合、分类与呈现来自多个移动端信息源的技术文章、接口文档与运维案例。LinkMap 的核心价值在于将散落于不同移动端域名下的碎片化技术内容，通过统一的索引机制与分类体系进行重组，使得开发者能够在同一入口下快速检索并定位到特定技术问题的参考实现。

本项目采用静态站点生成方案，资源清单以纯文本格式维护，支持自动化校验与批量更新。LinkMap 适用于需要长期跟踪多个技术输出源、但又希望避免被单一平台绑定的团队或个人研究者。通过本导航站，用户无需记忆多个子域名的文章编号与路径规则，即可通过分类索引或关键词联想获取目标资源。

## 功能概览

多源资源统一索引：系统将来自不同移动端域名的技术文章、解决方案文档与配置案例进行统一编号与分类，屏蔽底层域名差异，提供单一入口访问体验。

分类标签与全文检索：每一条收录资源均附带技术领域标签，支持按标签筛选和基于标题片段的快速检索，提升资源查找效率。

资源状态监控与失效检测：后台定期对收录的 URL 进行可达性检查，标记异常链接并生成报告，保证导航库的可用性。

批量导入与增量更新：支持通过文本列表批量追加新资源，自动去重并合并分类标签，适用于资源库的持续扩展。

结构化元数据导出：支持将资源列表导出为 JSON、CSV 或 Markdown 表格格式，便于嵌入技术文档或进行二次数据分析。

访问统计与热度排序：记录用户对各类资源的点击频次，提供按热度排序的视图，帮助识别高频使用的参考资料。

多端适配的响应式界面：前端界面针对桌面端与移动端浏览器进行适配，确保在各类屏幕尺寸下均可流畅浏览与操作。

## 应用场景

移动端 SDK 集成问题排查：开发团队在集成第三方移动端 SDK 时遇到编译错误或运行时异常，可通过 LinkMap 检索同类问题的历史解决案例，快速定位到对应的技术文章或补丁说明。

多团队技术文档交叉引用：大型项目中的不同团队分别维护各自的移动端文档站点，LinkMap 作为统一导航层，帮助团队成员跨项目查找接口定义、配置参数与示例代码。

技术选型与方案评估：架构师在进行移动端技术选型时，通过 LinkMap 查阅不同来源的实践案例与性能对比数据，辅助决策过程。

运维故障处理知识库积累：运维人员将日常遇到的移动端服务异常及处理步骤记录为外部文章，通过 LinkMap 集中管理，形成可检索的故障知识库。

新人培训与学习路径指引：新入职的移动端开发工程师通过 LinkMap 的标签分类，系统性地学习项目所涉及的技术栈与常见问题处理方案。

## 快速开始

以下步骤指导用户在本地环境中快速部署 LinkMap 导航站服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkmap-nav.git
cd linkmap-nav

# 安装依赖（基于 Node.js 22 LTS 与 pnpm）
pnpm install

# 构建资源索引并启动开发服务器
pnpm run build:index
pnpm run dev
```

执行上述命令后，开发服务器默认运行于 http://localhost:3000。访问该地址即可浏览资源导航界面。如需构建生产环境静态文件，请执行 `pnpm run build`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 22.x LTS 或更高 | 运行时环境，用于执行构建脚本与开发服务器 |
| pnpm | 8.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.40 或更高 | 版本控制工具，用于克隆仓库与提交更新 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，推荐使用 Linux 或 macOS 进行生产部署 |
| 浏览器 | 现代浏览器（Chrome 110+ / Firefox 110+ / Safari 16+）| 前端界面访问所需 |
| 磁盘空间 | 至少 500 MB | 用于存放源代码、依赖包及构建产物 |
| 网络访问 | 外网访问能力 | 用于资源状态检测与更新索引 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide.md | 如何使用 LinkMap 进行资源检索、分类浏览与收藏 |
| 维护指南 | /docs/maintainer-guide.md | 如何新增、更新或删除资源链接，如何执行批量导入 |
| 开发指南 | /docs/developer-guide.md | 如何二次开发、修改前端样式或扩展索引字段 |
| API 参考 | /docs/api-reference.md | 如何通过 RESTful API 查询资源、获取统计信息 |
| 部署指南 | /docs/deployment-guide.md | 如何将 LinkMap 部署到生产服务器或云平台 |
| 架构设计 | /docs/architecture.md | 项目的模块划分、数据流向与扩展点说明 |

## 资源列表

- http://map.mobile.fuvxie.cn/Article/8314.shtml
- http://map.mobile.cvsifc.cn/Article/3693969.shtml
- http://map.mobile.hcbezg.cn/Article/9412.shtml
- http://map.mobile.hcbezg.cn/Article/0016.shtml
- http://map.mobile.fuvxie.cn/Article/3968.shtml
- http://map.mobile.fuvxie.cn/Article/4186.shtml
- http://map.mobile.cvsifc.cn/Article/212069.shtml
- http://map.mobile.cvsifc.cn/Article/2078.shtml
- http://map.mobile.fuvxie.cn/Article/5541997.shtml
- http://map.mobile.hcbezg.cn/Article/1573.shtml
- http://map.mobile.cvsifc.cn/Article/8396.shtml
- http://map.mobile.hcbezg.cn/Article/3245637.shtml
- http://map.mobile.hcbezg.cn/Article/93753.shtml
- http://map.mobile.fuvxie.cn/Article/16416.shtml
- http://map.mobile.cvsifc.cn/Article/6360195.shtml
- http://map.mobile.cvsifc.cn/Article/204877.shtml
- http://map.mobile.fuvxie.cn/Article/6201.shtml
- http://map.mobile.fuvxie.cn/Article/3385150.shtml
- http://map.mobile.fuvxie.cn/Article/092547.shtml
- http://map.mobile.fuvxie.cn/Article/70092.shtml
- http://map.mobile.fuvxie.cn/Article/915232.shtml
- http://map.mobile.hcbezg.cn/Article/3089.shtml
- http://map.mobile.hcbezg.cn/Article/0835953.shtml
- http://map.mobile.hcbezg.cn/Article/77419.shtml
- http://map.mobile.hcbezg.cn/Article/640170.shtml
- http://map.mobile.cvsifc.cn/Article/1009.shtml
- http://map.mobile.fuvxie.cn/Article/7246.shtml
- http://map.mobile.hcbezg.cn/Article/5008.shtml
- http://map.mobile.hcbezg.cn/Article/984345.shtml
- http://map.mobile.cvsifc.cn/Article/6509266.shtml
- http://map.mobile.cvsifc.cn/Article/7210.shtml
- http://map.mobile.hcbezg.cn/Article/957172.shtml
- http://map.mobile.fuvxie.cn/Article/64771.shtml
- http://map.mobile.hcbezg.cn/Article/15214.shtml
- http://map.mobile.cvsifc.cn/Article/9740.shtml
- http://map.mobile.fuvxie.cn/Article/6627209.shtml
- http://map.mobile.cvsifc.cn/Article/63671.shtml
- http://map.mobile.hcbezg.cn/Article/13632.shtml
- http://map.mobile.hcbezg.cn/Article/409574.shtml
- http://map.mobile.cvsifc.cn/Article/9444016.shtml
- http://map.mobile.cvsifc.cn/Article/3925161.shtml
- http://map.mobile.hcbezg.cn/Article/2499370.shtml
- http://map.mobile.cvsifc.cn/Article/8220.shtml
- http://map.mobile.fuvxie.cn/Article/9896.shtml
- http://map.mobile.fuvxie.cn/Article/3372776.shtml
- http://map.mobile.hcbezg.cn/Article/3973231.shtml
- http://map.mobile.cvsifc.cn/Article/2700390.shtml
- http://map.mobile.cvsifc.cn/Article/1394820.shtml
- http://map.mobile.hcbezg.cn/Article/74248.shtml
- http://map.mobile.hcbezg.cn/Article/529161.shtml
- http://map.mobile.cvsifc.cn/Article/168851.shtml
- http://map.mobile.fuvxie.cn/Article/34882.shtml
- http://map.mobile.fuvxie.cn/Article/3321139.shtml
- http://map.mobile.fuvxie.cn/Article/512467.shtml
- http://map.mobile.hcbezg.cn/Article/43116.shtml
- http://map.mobile.cvsifc.cn/Article/3148.shtml
- http://map.mobile.hcbezg.cn/Article/9237072.shtml
- http://map.mobile.cvsifc.cn/Article/8582296.shtml
- http://map.mobile.hcbezg.cn/Article/3174910.shtml
- http://map.mobile.hcbezg.cn/Article/6254054.shtml
- http://map.mobile.cvsifc.cn/Article/6322.shtml
- http://map.mobile.cvsifc.cn/Article/4908119.shtml
- http://map.mobile.fuvxie.cn/Article/35331.shtml
- http://map.mobile.cvsifc.cn/Article/07680.shtml
- http://map.mobile.cvsifc.cn/Article/42098.shtml
- http://map.mobile.fuvxie.cn/Article/8318.shtml
- http://map.mobile.fuvxie.cn/Article/78693.shtml
- http://map.mobile.fuvxie.cn/Article/66000.shtml
- http://map.mobile.cvsifc.cn/Article/897401.shtml
- http://map.mobile.fuvxie.cn/Article/9875933.shtml
- http://map.mobile.fuvxie.cn/Article/5929186.shtml
- http://map.mobile.fuvxie.cn/Article/44305.shtml
- http://map.mobile.cvsifc.cn/Article/076510.shtml
- http://map.mobile.cvsifc.cn/Article/4260408.shtml
- http://map.mobile.cvsifc.cn/Article/924408.shtml
- http://map.mobile.hcbezg.cn/Article/7260.shtml
- http://map.mobile.fuvxie.cn/Article/3954.shtml
- http://map.mobile.cvsifc.cn/Article/2893.shtml
- http://map.mobile.cvsifc.cn/Article/0101636.shtml
- http://map.mobile.fuvxie.cn/Article/214310.shtml
- http://map.mobile.hcbezg.cn/Article/46096.shtml
- http://map.mobile.hcbezg.cn/Article/79726.shtml
- http://map.mobile.cvsifc.cn/Article/45920.shtml
- http://map.mobile.fuvxie.cn/Article/136081.shtml
- http://map.mobile.hcbezg.cn/Article/1836.shtml
- http://map.mobile.fuvxie.cn/Article/2045657.shtml
- http://map.mobile.cvsifc.cn/Article/9856.shtml
- http://map.mobile.hcbezg.cn/Article/71542.shtml
- http://map.mobile.hcbezg.cn/Article/14827.shtml
- http://map.mobile.cvsifc.cn/Article/16989.shtml
- http://map.mobile.fuvxie.cn/Article/4984.shtml
- http://map.mobile.fuvxie.cn/Article/9752282.shtml
- http://map.mobile.cvsifc.cn/Article/267744.shtml
- http://map.mobile.fuvxie.cn/Article/269406.shtml
- http://map.mobile.cvsifc.cn/Article/472791.shtml
- http://map.mobile.cvsifc.cn/Article/9670713.shtml
- http://map.mobile.hcbezg.cn/Article/147764.shtml
- http://map.mobile.cvsifc.cn/Article/7788.shtml
- http://map.mobile.fuvxie.cn/Article/840332.shtml
- http://map.mobile.hcbezg.cn/Article/06964.shtml
- http://map.mobile.fuvxie.cn/Article/7447.shtml
- http://map.mobile.hcbezg.cn/Article/9289890.shtml
- http://map.mobile.fuvxie.cn/Article/128690.shtml
- http://map.mobile.cvsifc.cn/Article/82917.shtml
- http://map.mobile.cvsifc.cn/Article/44043.shtml
- http://map.mobile.fuvxie.cn/Article/965413.shtml
- http://map.mobile.cvsifc.cn/Article/9928.shtml
- http://map.mobile.cvsifc.cn/Article/86937.shtml
- http://map.mobile.cvsifc.cn/Article/6131679.shtml
- http://map.mobile.cvsifc.cn/Article/716968.shtml
- http://map.mobile.fuvxie.cn/Article/48681.shtml
- http://map.mobile.hcbezg.cn/Article/5740844.shtml
- http://map.mobile.fuvxie.cn/Article/975830.shtml
- http://map.mobile.cvsifc.cn/Article/40795.shtml
- http://map.mobile.hcbezg.cn/Article/320483.shtml
- http://map.mobile.cvsifc.cn/Article/892531.shtml
- http://map.mobile.hcbezg.cn/Article/5888874.shtml
- http://map.mobile.fuvxie.cn/Article/21526.shtml
- http://map.mobile.fuvxie.cn/Article/3704205.shtml
- http://map.mobile.hcbezg.cn/Article/2138326.shtml
- http://map.mobile.fuvxie.cn/Article/670172.shtml
- http://map.mobile.hcbezg.cn/Article/2298391.shtml
- http://map.mobile.hcbezg.cn/Article/583077.shtml
- http://map.mobile.fuvxie.cn/Article/8176.shtml
- http://map.mobile.cvsifc.cn/Article/71606.shtml
- http://map.mobile.cvsifc.cn/Article/663090.shtml
- http://map.mobile.hcbezg.cn/Article/408643.shtml
- http://map.mobile.hcbezg.cn/Article/5337306.shtml
- http://map.mobile.hcbezg.cn/Article/5824.shtml
- http://map.mobile.hcbezg.cn/Article/0535.shtml
- http://map.mobile.hcbezg.cn/Article/23412.shtml
- http://map.mobile.hcbezg.cn/Article/97553.shtml
- http://map.mobile.cvsifc.cn/Article/6676929.shtml
- http://map.mobile.fuvxie.cn/Article/78493.shtml
- http://map.mobile.cvsifc.cn/Article/348721.shtml
- http://map.mobile.fuvxie.cn/Article/0330079.shtml
- http://map.mobile.hcbezg.cn/Article/748565.shtml
- http://map.mobile.hcbezg.cn/Article/5402613.shtml
- http://map.mobile.cvsifc.cn/Article/20106.shtml
- http://map.mobile.hcbezg.cn/Article/39452.shtml
- http://map.mobile.hcbezg.cn/Article/6288275.shtml
- http://map.mobile.fuvxie.cn/Article/048620.shtml
- http://map.mobile.fuvxie.cn/Article/5454.shtml
- http://map.mobile.fuvxie.cn/Article/325155.shtml
- http://map.mobile.cvsifc.cn/Article/6699.shtml
- http://map.mobile.cvsifc.cn/Article/749401.shtml
- http://map.mobile.fuvxie.cn/Article/30555.shtml
- http://map.mobile.hcbezg.cn/Article/34960.shtml
- http://map.mobile.hcbezg.cn/Article/3251697.shtml
- http://map.mobile.fuvxie.cn/Article/8854.shtml
- http://map.mobile.fuvxie.cn/Article/3674997.shtml
- http://map.mobile.hcbezg.cn/Article/64137.shtml
- http://map.mobile.hcbezg.cn/Article/5510.shtml
- http://map.mobile.cvsifc.cn/Article/8555813.shtml
- http://map.mobile.cvsifc.cn/Article/5462446.shtml
- http://map.mobile.hcbezg.cn/Article/08332.shtml
- http://map.mobile.hcbezg.cn/Article/6984.shtml
- http://map.mobile.cvsifc.cn/Article/96709.shtml
- http://map.mobile.hcbezg.cn/Article/35553.shtml
- http://map.mobile.hcbezg.cn/Article/39114.shtml
- http://map.mobile.fuvxie.cn/Article/610951.shtml
- http://map.mobile.hcbezg.cn/Article/117967.shtml
- http://map.mobile.fuvxie.cn/Article/85298.shtml
- http://map.mobile.hcbezg.cn/Article/4111.shtml
- http://map.mobile.fuvxie.cn/Article/37428.shtml
- http://map.mobile.cvsifc.cn/Article/8300.shtml
- http://map.mobile.cvsifc.cn/Article/32322.shtml
- http://map.mobile.fuvxie.cn/Article/055126.shtml
- http://map.mobile.hcbezg.cn/Article/6052769.shtml
- http://map.mobile.cvsifc.cn/Article/3119234.shtml
- http://map.mobile.cvsifc.cn/Article/0544133.shtml
- http://map.mobile.hcbezg.cn/Article/98101.shtml
- http://map.mobile.hcbezg.cn/Article/4878.shtml
- http://map.mobile.fuvxie.cn/Article/14973.shtml
- http://map.mobile.cvsifc.cn/Article/41341.shtml
- http://map.mobile.hcbezg.cn/Article/42878.shtml
- http://map.mobile.cvsifc.cn/Article/6855688.shtml
- http://map.mobile.fuvxie.cn/Article/36794.shtml
- http://map.mobile.hcbezg.cn/Article/860615.shtml
- http://map.mobile.hcbezg.cn/Article/328564.shtml
- http://map.mobile.fuvxie.cn/Article/1386432.shtml
- http://map.mobile.cvsifc.cn/Article/9085.shtml
- http://map.mobile.hcbezg.cn/Article/5046.shtml
- http://map.mobile.cvsifc.cn/Article/148718.shtml
- http://map.mobile.fuvxie.cn/Article/8392281.shtml
- http://map.mobile.fuvxie.cn/Article/8582.shtml
- http://map.mobile.fuvxie.cn/Article/95260.shtml
- http://map.mobile.fuvxie.cn/Article/1716.shtml
- http://map.mobile.fuvxie.cn/Article/25583.shtml
- http://map.mobile.fuvxie.cn/Article/566047.shtml
- http://map.mobile.fuvxie.cn/Article/781840.shtml
- http://map.mobile.cvsifc.cn/Article/1117.shtml
- http://map.mobile.cvsifc.cn/Article/4260.shtml
- http://map.mobile.hcbezg.cn/Article/5123.shtml
- http://map.mobile.fuvxie.cn/Article/8530.shtml
- http://map.mobile.cvsifc.cn/Article/5093132.shtml
- http://map.mobile.fuvxie.cn/Article/796457.shtml
- http://map.mobile.fuvxie.cn/Article/432308.shtml
- http://map.mobile.hcbezg.cn/Article/097829.shtml
- http://map.mobile.fuvxie.cn/Article/7778.shtml
- http://map.mobile.cvsifc.cn/Article/570386.shtml
- http://map.mobile.cvsifc.cn/Article/2761.shtml
- http://map.mobile.fuvxie.cn/Article/313482.shtml
- http://map.mobile.cvsifc.cn/Article/0883.shtml
- http://map.mobile.cvsifc.cn/Article/7277.shtml
- http://map.mobile.cvsifc.cn/Article/5116960.shtml
- http://map.mobile.hcbezg.cn/Article/8104408.shtml
- http://map.mobile.hcbezg.cn/Article/27826.shtml
- http://map.mobile.fuvxie.cn/Article/01490.shtml
- http://map.mobile.hcbezg.cn/Article/054195.shtml
- http://map.mobile.hcbezg.cn/Article/7986.shtml
- http://map.mobile.fuvxie.cn/Article/69024.shtml
- http://map.mobile.cvsifc.cn/Article/59246.shtml
- http://map.mobile.hcbezg.cn/Article/27927.shtml
- http://map.mobile.fuvxie.cn/Article/9069437.shtml
- http://map.mobile.hcbezg.cn/Article/095063.shtml
- http://map.mobile.fuvxie.cn/Article/303443.shtml
- http://map.mobile.hcbezg.cn/Article/991856.shtml
- http://map.mobile.cvsifc.cn/Article/4582699.shtml
- http://map.mobile.fuvxie.cn/Article/9413607.shtml
- http://map.mobile.fuvxie.cn/Article/57611.shtml
- http://map.mobile.fuvxie.cn/Article/3029003.shtml
- http://map.mobile.cvsifc.cn/Article/829553.shtml
- http://map.mobile.hcbezg.cn/Article/094797.shtml
- http://map.mobile.fuvxie.cn/Article/68645.shtml
- http://map.mobile.fuvxie.cn/Article/9987.shtml
- http://map.mobile.fuvxie.cn/Article/5299.shtml
- http://map.mobile.hcbezg.cn/Article/8709586.shtml
- http://map.mobile.hcbezg.cn/Article/5689.shtml
- http://map.mobile.fuvxie.cn/Article/594587.shtml
- http://map.mobile.cvsifc.cn/Article/7625494.shtml
- http://map.mobile.cvsifc.cn/Article/21370.shtml
- http://map.mobile.cvsifc.cn/Article/7764690.shtml
- http://map.mobile.cvsifc.cn/Article/8204162.shtml
- http://map.mobile.hcbezg.cn/Article/61830.shtml
- http://map.mobile.cvsifc.cn/Article/3139.shtml
- http://map.mobile.hcbezg.cn/Article/419315.shtml
- http://map.mobile.cvsifc.cn/Article/06801.shtml
- http://map.mobile.hcbezg.cn/Article/13521.shtml
- http://map.mobile.cvsifc.cn/Article/92341.shtml
- http://map.mobile.cvsifc.cn/Article/10310.shtml
- http://map.mobile.hcbezg.cn/Article/9403.shtml
- http://map.mobile.fuvxie.cn/Article/05975.shtml
- http://map.mobile.hcbezg.cn/Article/28653.shtml
- http://map.mobile.fuvxie.cn/Article/780998.shtml
- http://map.mobile.fuvxie.cn/Article/284896.shtml
- http://map.mobile.cvsifc.cn/Article/0200.shtml
- http://map.mobile.hcbezg.cn/Article/6188.shtml
- http://map.mobile.hcbezg.cn/Article/010100.shtml
- http://map.mobile.cvsifc.cn/Article/1102.shtml

## 项目结构

```
linkmap-nav/
├── src/                           # 源代码主目录
│   ├── indexer/                   # 资源索引引擎模块
│   │   ├── parser.ts              # 解析原始链接列表，提取域名与编号
│   │   ├── classifier.ts          # 基于路径规则与关键词进行自动分类
│   │   └── validator.ts           # 校验 URL 可达性与格式合规性
│   ├── web/                       # 前端界面模块
│   │   ├── pages/                 # 页面路由组件（首页、分类页、详情页）
│   │   ├── components/            # 可复用 UI 组件（导航栏、资源卡片、分页器）
│   │   └── assets/                # 静态资源（样式表、脚本、图标）
│   ├── api/                       # RESTful API 服务模块
│   │   ├── routes/                # 路由定义（资源查询、统计、状态）
│   │   ├── controllers/           # 请求处理逻辑
│   │   └── middleware/            # 认证、日志、错误处理中间件
│   ├── storage/                   # 数据持久化模块
│   │   ├── adapters/              # 存储适配器（本地 JSON、Redis、数据库）
│   │   ├── schemas/               # 资源数据模型定义
│   │   └── migrations/            # 数据结构迁移脚本
│   └── utils/                     # 通用工具函数
│       ├── logger.ts              # 结构化日志输出
│       ├── fetcher.ts             # HTTP 请求封装，用于状态检测
│       └── config.ts              # 环境变量与配置加载
├── data/                          # 数据目录
│   ├── raw/                       # 原始资源列表（按批次存放）
│   │   └── batch_14_60.txt        # 第 14/60 批次原始数据
│   ├── indexed/                   # 索引构建后的结构化数据
│   │   └── resources.json         # 合并后的资源元数据
│   └── cache/                     # 状态检测缓存
│       └── status_cache.json      # 链接可达性快照
├── tests/                         # 测试套件
│   ├── unit/                      # 单元测试（解析器、分类器）
│   └── integration/               # 集成测试（API 端点、存储层）
├── docs/                          # 文档目录
│   ├── user-guide.md              # 用户手册
│   ├── maintainer-guide.md        # 维护指南
│   └── api-reference.md           # API 参考文档
├── scripts/                       # 运维与辅助脚本
│   ├── import-batch.sh            # 批量导入新批次数据
│   ├── check-links.sh             # 手动触发链接状态检测
│   └── export-stats.sh            # 导出访问统计报告
├── .env.example                   # 环境变量模板
├── package.json                   # 项目依赖与脚本定义
├── tsconfig.json                  # TypeScript 编译配置
├── .eslintrc.js                   # 代码风格检查配置
└── README.md                      # 项目说明文档
```

## 贡献指南

欢迎社区开发者参与 LinkMap 项目的改进与扩展。请遵循以下流程提交贡献：

1. 查阅项目 Issue 列表，选择未被指派的 bug 修复或功能增强任务，或提交新的 Issue 描述您发现的问题或建议的新特性。

2. 派生项目仓库至个人账户，并在本地创建功能分支，分支名称格式为 `feature/功能简述` 或 `fix/问题编号`。

3. 在本地完成代码修改后，确保通过全部单元测试与集成测试，并更新相应的文档内容以保持同步。

4. 提交 Pull Request 至主仓库的 `main` 分支，在描述中清晰说明变更内容、测试覆盖情况以及是否涉及破坏性改动。

5. 项目维护者将在 3 个工作日内进行 Code Review，并根据反馈进行迭代修改。合并后您的贡献将纳入下一个发布版本。

## 常见问题

Q：如何添加一批新的资源链接到导航站？

A：将新的 URL 列表按行放入 `data/raw/` 目录下的文本文件中，命名格式为 `batch_批次号_60.txt`。然后执行 `pnpm run import:batch -- --file=文件名`，系统将自动进行去重、分类与索引更新。导入完成后需重新构建前端静态文件以生效。

Q：资源状态检测显示链接不可达，但实际浏览器中可以访问，如何解决？

A：LinkMap 的状态检测默认使用 HEAD 请求并设置 5 秒超时。部分服务器可能拒绝 HEAD 请求或响应较慢。您可以在 `.env` 文件中调整 `CHECK_TIMEOUT` 和 `CHECK_METHOD` 参数，或切换为 GET 请求模式。同时，检测结果会缓存 24 小时，您也可以手动执行 `pnpm run check:links -- --force` 强制刷新。

Q：是否支持自定义分类标签？

A：支持。分类逻辑位于 `src/indexer/classifier.ts`，您可以根据 URL 路径特征、域名或特定关键词添加新的分类规则。修改后需要重新构建索引。对于已有资源，您也可以在 `data/indexed/resources.json` 中手动编辑 `tags` 字段，然后执行 `pnpm run index:rebuild` 重新生成索引。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
