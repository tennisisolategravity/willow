# WebIndex Hub

WebIndex Hub 是一个面向技术调研、信息聚合与外部资源治理场景的轻量级外链汇总与导航系统。项目定位于帮助开发者、技术运营人员与信息分析团队，以结构化方式管理分散于多个内容源的文章链接，降低跨平台信息检索与跟踪成本，同时提供稳定且可扩展的索引框架，便于对接自动化采集、URL 状态监控与分类标注流程。

本项目不提供内容抓取或存储服务，专注于链接资源的目录化组织、元数据描述与状态管理。其设计目标是成为各类技术团队内部知识体系中的“外链中台”，支持手工整理、脚本批量导入以及基于标签体系的快速筛选。项目默认以静态站点形态运行，兼容 GitHub Pages、Nginx 静态目录及 Cloudflare Pages 等多种部署方式，同时提供命令行工具用于校验链接可达性与响应时间，帮助维护资源列表的长期可用性。

## 功能概览

**多源链接统一入库**：支持从 CSV、JSON 及 Markdown 列表批量导入 URL，自动识别协议头与域名结构，保留原始链接完整性，不做任何自动补全或改写。

**分类标签与全文检索**：每条资源可关联多个分类标签，并基于 MiniSearch 或 Lunr 实现前端全文检索，支持按域名、关键词、批次号及导入时间过滤。

**链接状态健康检查**：内置基于 Node.js 或 Python 的异步 HTTP 检测模块，可定期对资源列表执行 HEAD 请求，标记异常状态码、超时或证书错误，并生成健康报告。

**批次管理与版本追溯**：支持按批次（如第 58/60 批）组织资源，记录每批导入时间、数量、来源说明，便于追踪资源更新节奏与增量变更。

**静态站点生成与主题切换**：提供默认文档风格主题与暗色模式，通过模板引擎将资源数据渲染为静态 HTML 页面，支持自定义页头、页脚与侧边栏信息。

**数据导出与 API 接口**：支持将资源列表导出为 JSON、CSV 或纯文本 URL 清单，同时提供只读 JSON API 供下游系统调用，接口路径为 `/api/links` 与 `/api/batches`。

## 应用场景

**技术团队内部知识库外链治理**：技术文档组或架构委员会可使用 WebIndex Hub 统一收纳各类技术博客、官方文档、RFC 草案与会议纪要链接，按项目或领域分类，替代零散的浏览器书签或团队文档中的散落链接。

**开源项目 README 与文档站资源附录管理**：开源项目维护者可将项目依赖的参考链接、社区教程、视频讲解等外链集中托管于 WebIndex Hub 生成的资源页面，并在 README 中嵌入该页面的访问地址，确保外部引用可追溯、可更新。

**信息采集与舆情监控的前置链接池**：舆情分析或市场调研团队可将每日新增的资讯链接、行业报告 URL 导入系统，借助批次管理区分不同采集任务，利用健康检查过滤失效链接后再交由后续分析流程处理。

**自动化巡检与链接老化检测**：运维或 SRE 团队可将 WebIndex Hub 部署为内部工具，用于定期扫描文档站、Wiki 或产品帮助中心中的所有外部引用链接，输出失效链接报表，辅助内容更新决策。

## 快速开始

以下步骤适用于 Node.js 18+ 环境，使用 pnpm 作为包管理器。若使用 npm 或 yarn，请相应替换命令。

```bash
# 克隆代码仓库
git clone https://github.com/webindex-hub/webindex-hub.git
cd webindex-hub

# 安装依赖
pnpm install

# 复制环境变量模板并配置数据目录
cp .env.example .env
mkdir -p data/batches

# 将资源列表放入数据目录（示例：批次 58）
# 假设资源文件为 batch-58.txt，每行一个 URL
cp /path/to/your/links.txt data/batches/batch-58.txt

# 执行导入脚本
pnpm run import --batch=58 --file=data/batches/batch-58.txt

# 生成静态站点
pnpm run build

# 启动开发服务器预览
pnpm run preview
```

生产环境部署建议执行 `pnpm run build` 后，将 `dist` 目录内容上传至 Web 服务器或对象存储服务。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用最新 LTS 版本 |
| pnpm | 8.x 或 9.x | 包管理器，用于依赖安装与脚本执行 |
| Python（可选） | 3.10+ | 仅在使用 Python 版健康检查工具时需要 |
| SQLite | 3.35+ | 内置数据存储引擎，用于资源元数据与批次记录 |
| Nginx / Apache（可选） | 任意稳定版 | 生产环境静态文件服务，非必须但推荐 |
| curl / wget（可选） | 任意版本 | 用于外部 HTTP 检测脚本的基础工具链 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户指南 | `/docs/guide/getting-started.md` | 如何首次启动、导入链接并生成站点？ |
| 管理员手册 | `/docs/admin/batch-management.md` | 如何管理多批次资源、清理旧数据、合并重复链接？ |
| 开发参考 | `/docs/dev/api-endpoints.md` | JSON API 的请求格式、返回字段与分页参数是什么？ |
| 运维部署 | `/docs/ops/deployment-options.md` | 支持哪些部署方式（静态托管、VPS、容器）？如何配置 SSL？ |

## 资源列表

- http://h5.mobile.cvsifc.cn/Article/8336.shtml
- http://h5.mobile.cvsifc.cn/Article/74109.shtml
- http://h5.mobile.hcbezg.cn/Article/6053.shtml
- http://h5.mobile.hcbezg.cn/Article/5602.shtml
- http://h5.mobile.hcbezg.cn/Article/0937.shtml
- http://h5.mobile.cvsifc.cn/Article/3025723.shtml
- http://h5.mobile.fuvxie.cn/Article/4582812.shtml
- http://h5.mobile.cvsifc.cn/Article/067789.shtml
- http://h5.mobile.hcbezg.cn/Article/1589979.shtml
- http://h5.mobile.hcbezg.cn/Article/7160908.shtml
- http://h5.mobile.fuvxie.cn/Article/6903.shtml
- http://h5.mobile.hcbezg.cn/Article/9927.shtml
- http://h5.mobile.fuvxie.cn/Article/1016359.shtml
- http://h5.mobile.hcbezg.cn/Article/06335.shtml
- http://h5.mobile.hcbezg.cn/Article/7426.shtml
- http://h5.mobile.fuvxie.cn/Article/9386692.shtml
- http://h5.mobile.hcbezg.cn/Article/429501.shtml
- http://h5.mobile.hcbezg.cn/Article/1247085.shtml
- http://h5.mobile.hcbezg.cn/Article/491066.shtml
- http://h5.mobile.cvsifc.cn/Article/564986.shtml
- http://h5.mobile.fuvxie.cn/Article/2711.shtml
- http://h5.mobile.hcbezg.cn/Article/595155.shtml
- http://h5.mobile.cvsifc.cn/Article/55215.shtml
- http://h5.mobile.hcbezg.cn/Article/9831211.shtml
- http://h5.mobile.cvsifc.cn/Article/4117.shtml
- http://h5.mobile.hcbezg.cn/Article/703554.shtml
- http://h5.mobile.hcbezg.cn/Article/0980792.shtml
- http://h5.mobile.fuvxie.cn/Article/0367.shtml
- http://h5.mobile.fuvxie.cn/Article/77795.shtml
- http://h5.mobile.cvsifc.cn/Article/2326.shtml
- http://h5.mobile.cvsifc.cn/Article/2236849.shtml
- http://h5.mobile.fuvxie.cn/Article/44080.shtml
- http://h5.mobile.hcbezg.cn/Article/5547.shtml
- http://h5.mobile.hcbezg.cn/Article/579248.shtml
- http://h5.mobile.hcbezg.cn/Article/6328.shtml
- http://h5.mobile.cvsifc.cn/Article/383660.shtml
- http://h5.mobile.cvsifc.cn/Article/4059.shtml
- http://h5.mobile.hcbezg.cn/Article/2436.shtml
- http://h5.mobile.fuvxie.cn/Article/09754.shtml
- http://h5.mobile.hcbezg.cn/Article/7541528.shtml
- http://h5.mobile.fuvxie.cn/Article/9130041.shtml
- http://h5.mobile.hcbezg.cn/Article/4106.shtml
- http://h5.mobile.fuvxie.cn/Article/4949299.shtml
- http://h5.mobile.fuvxie.cn/Article/963899.shtml
- http://h5.mobile.cvsifc.cn/Article/262392.shtml
- http://h5.mobile.cvsifc.cn/Article/9226172.shtml
- http://h5.mobile.hcbezg.cn/Article/6443.shtml
- http://h5.mobile.cvsifc.cn/Article/8370.shtml
- http://h5.mobile.hcbezg.cn/Article/0069.shtml
- http://h5.mobile.fuvxie.cn/Article/01809.shtml
- http://h5.mobile.fuvxie.cn/Article/024786.shtml
- http://h5.mobile.hcbezg.cn/Article/74541.shtml
- http://h5.mobile.cvsifc.cn/Article/813010.shtml
- http://h5.mobile.fuvxie.cn/Article/3172.shtml
- http://h5.mobile.hcbezg.cn/Article/11771.shtml
- http://h5.mobile.fuvxie.cn/Article/2046046.shtml
- http://h5.mobile.fuvxie.cn/Article/722656.shtml
- http://h5.mobile.hcbezg.cn/Article/2785.shtml
- http://h5.mobile.hcbezg.cn/Article/143625.shtml
- http://h5.mobile.fuvxie.cn/Article/473204.shtml
- http://h5.mobile.fuvxie.cn/Article/57692.shtml
- http://h5.mobile.fuvxie.cn/Article/038743.shtml
- http://h5.mobile.cvsifc.cn/Article/19150.shtml
- http://h5.mobile.cvsifc.cn/Article/1606997.shtml
- http://h5.mobile.hcbezg.cn/Article/1112.shtml
- http://h5.mobile.hcbezg.cn/Article/9527766.shtml
- http://h5.mobile.fuvxie.cn/Article/72600.shtml
- http://h5.mobile.fuvxie.cn/Article/6335.shtml
- http://h5.mobile.hcbezg.cn/Article/30529.shtml
- http://h5.mobile.fuvxie.cn/Article/7409968.shtml
- http://h5.mobile.hcbezg.cn/Article/41391.shtml
- http://h5.mobile.hcbezg.cn/Article/8241.shtml
- http://h5.mobile.hcbezg.cn/Article/9705.shtml
- http://h5.mobile.cvsifc.cn/Article/7403.shtml
- http://h5.mobile.hcbezg.cn/Article/8151.shtml
- http://h5.mobile.cvsifc.cn/Article/786136.shtml
- http://h5.mobile.fuvxie.cn/Article/0485.shtml
- http://h5.mobile.fuvxie.cn/Article/700970.shtml
- http://h5.mobile.hcbezg.cn/Article/194676.shtml
- http://h5.mobile.hcbezg.cn/Article/7337.shtml
- http://h5.mobile.fuvxie.cn/Article/6689.shtml
- http://h5.mobile.fuvxie.cn/Article/288852.shtml
- http://h5.mobile.cvsifc.cn/Article/9375134.shtml
- http://h5.mobile.cvsifc.cn/Article/1025182.shtml
- http://h5.mobile.fuvxie.cn/Article/9470334.shtml
- http://h5.mobile.hcbezg.cn/Article/28088.shtml
- http://h5.mobile.hcbezg.cn/Article/8280.shtml
- http://h5.mobile.hcbezg.cn/Article/474337.shtml
- http://h5.mobile.fuvxie.cn/Article/5489.shtml
- http://h5.mobile.cvsifc.cn/Article/00985.shtml
- http://h5.mobile.hcbezg.cn/Article/4576.shtml
- http://h5.mobile.fuvxie.cn/Article/6490325.shtml
- http://h5.mobile.hcbezg.cn/Article/6724.shtml
- http://h5.mobile.fuvxie.cn/Article/4626134.shtml
- http://h5.mobile.hcbezg.cn/Article/9452.shtml
- http://h5.mobile.fuvxie.cn/Article/5403890.shtml
- http://h5.mobile.cvsifc.cn/Article/468952.shtml
- http://h5.mobile.fuvxie.cn/Article/6583.shtml
- http://h5.mobile.hcbezg.cn/Article/29817.shtml
- http://h5.mobile.cvsifc.cn/Article/5525755.shtml
- http://h5.mobile.cvsifc.cn/Article/4404605.shtml
- http://h5.mobile.fuvxie.cn/Article/2598.shtml
- http://h5.mobile.hcbezg.cn/Article/9097795.shtml
- http://h5.mobile.cvsifc.cn/Article/6067.shtml
- http://h5.mobile.fuvxie.cn/Article/3690042.shtml
- http://h5.mobile.fuvxie.cn/Article/33953.shtml
- http://h5.mobile.cvsifc.cn/Article/1892.shtml
- http://h5.mobile.cvsifc.cn/Article/537349.shtml
- http://h5.mobile.fuvxie.cn/Article/40821.shtml
- http://h5.mobile.fuvxie.cn/Article/88575.shtml
- http://h5.mobile.cvsifc.cn/Article/207569.shtml
- http://h5.mobile.hcbezg.cn/Article/1331056.shtml
- http://h5.mobile.fuvxie.cn/Article/5618.shtml
- http://h5.mobile.cvsifc.cn/Article/0838933.shtml
- http://h5.mobile.cvsifc.cn/Article/6293939.shtml
- http://h5.mobile.cvsifc.cn/Article/7639.shtml
- http://h5.mobile.hcbezg.cn/Article/06179.shtml
- http://h5.mobile.cvsifc.cn/Article/4673.shtml
- http://h5.mobile.fuvxie.cn/Article/918698.shtml
- http://h5.mobile.hcbezg.cn/Article/5339.shtml
- http://h5.mobile.hcbezg.cn/Article/52262.shtml
- http://h5.mobile.hcbezg.cn/Article/7041.shtml
- http://h5.mobile.cvsifc.cn/Article/22713.shtml
- http://h5.mobile.fuvxie.cn/Article/701214.shtml
- http://h5.mobile.cvsifc.cn/Article/6566045.shtml
- http://h5.mobile.hcbezg.cn/Article/71555.shtml
- http://h5.mobile.fuvxie.cn/Article/579070.shtml
- http://h5.mobile.cvsifc.cn/Article/5478.shtml
- http://h5.mobile.fuvxie.cn/Article/96358.shtml
- http://h5.mobile.fuvxie.cn/Article/06934.shtml
- http://h5.mobile.hcbezg.cn/Article/785976.shtml
- http://h5.mobile.cvsifc.cn/Article/210274.shtml
- http://h5.mobile.hcbezg.cn/Article/9820544.shtml
- http://h5.mobile.hcbezg.cn/Article/620298.shtml
- http://h5.mobile.fuvxie.cn/Article/051020.shtml
- http://h5.mobile.hcbezg.cn/Article/958768.shtml
- http://h5.mobile.cvsifc.cn/Article/8387669.shtml
- http://h5.mobile.fuvxie.cn/Article/4917.shtml
- http://h5.mobile.cvsifc.cn/Article/943752.shtml
- http://h5.mobile.hcbezg.cn/Article/46415.shtml
- http://h5.mobile.hcbezg.cn/Article/0146718.shtml
- http://h5.mobile.fuvxie.cn/Article/85554.shtml
- http://h5.mobile.fuvxie.cn/Article/9541025.shtml
- http://h5.mobile.fuvxie.cn/Article/817549.shtml
- http://h5.mobile.cvsifc.cn/Article/97395.shtml
- http://h5.mobile.fuvxie.cn/Article/039460.shtml
- http://h5.mobile.cvsifc.cn/Article/268382.shtml
- http://h5.mobile.hcbezg.cn/Article/7772185.shtml
- http://h5.mobile.fuvxie.cn/Article/187477.shtml
- http://h5.mobile.cvsifc.cn/Article/37800.shtml
- http://h5.mobile.hcbezg.cn/Article/5400.shtml
- http://h5.mobile.hcbezg.cn/Article/0839.shtml
- http://h5.mobile.cvsifc.cn/Article/8134281.shtml
- http://h5.mobile.fuvxie.cn/Article/914632.shtml
- http://h5.mobile.cvsifc.cn/Article/264648.shtml
- http://h5.mobile.hcbezg.cn/Article/16485.shtml
- http://h5.mobile.cvsifc.cn/Article/95067.shtml
- http://h5.mobile.hcbezg.cn/Article/05760.shtml
- http://h5.mobile.cvsifc.cn/Article/765978.shtml
- http://h5.mobile.hcbezg.cn/Article/3011.shtml
- http://h5.mobile.fuvxie.cn/Article/02315.shtml
- http://h5.mobile.fuvxie.cn/Article/3324564.shtml
- http://h5.mobile.cvsifc.cn/Article/0617090.shtml
- http://h5.mobile.cvsifc.cn/Article/1454.shtml
- http://h5.mobile.hcbezg.cn/Article/310956.shtml
- http://h5.mobile.cvsifc.cn/Article/1414.shtml
- http://h5.mobile.fuvxie.cn/Article/886001.shtml
- http://h5.mobile.cvsifc.cn/Article/8272.shtml
- http://h5.mobile.fuvxie.cn/Article/74867.shtml
- http://h5.mobile.hcbezg.cn/Article/0020.shtml
- http://h5.mobile.cvsifc.cn/Article/70725.shtml
- http://h5.mobile.fuvxie.cn/Article/351182.shtml
- http://h5.mobile.fuvxie.cn/Article/6104134.shtml
- http://h5.mobile.cvsifc.cn/Article/6343.shtml
- http://h5.mobile.hcbezg.cn/Article/5286266.shtml
- http://h5.mobile.hcbezg.cn/Article/85693.shtml
- http://h5.mobile.hcbezg.cn/Article/1721661.shtml
- http://h5.mobile.fuvxie.cn/Article/16491.shtml
- http://h5.mobile.cvsifc.cn/Article/922512.shtml
- http://h5.mobile.cvsifc.cn/Article/687852.shtml
- http://h5.mobile.fuvxie.cn/Article/193348.shtml
- http://h5.mobile.cvsifc.cn/Article/06725.shtml
- http://h5.mobile.fuvxie.cn/Article/428039.shtml
- http://h5.mobile.hcbezg.cn/Article/572195.shtml
- http://h5.mobile.fuvxie.cn/Article/36181.shtml
- http://h5.mobile.hcbezg.cn/Article/2069.shtml
- http://h5.mobile.cvsifc.cn/Article/568485.shtml
- http://h5.mobile.fuvxie.cn/Article/033867.shtml
- http://h5.mobile.fuvxie.cn/Article/2650.shtml
- http://h5.mobile.fuvxie.cn/Article/39832.shtml
- http://h5.mobile.fuvxie.cn/Article/879563.shtml
- http://h5.mobile.hcbezg.cn/Article/6586.shtml
- http://h5.mobile.cvsifc.cn/Article/5864.shtml
- http://h5.mobile.cvsifc.cn/Article/9421711.shtml
- http://h5.mobile.cvsifc.cn/Article/3732.shtml
- http://h5.mobile.cvsifc.cn/Article/232303.shtml
- http://h5.mobile.hcbezg.cn/Article/4681499.shtml
- http://h5.mobile.hcbezg.cn/Article/7261885.shtml
- http://h5.mobile.hcbezg.cn/Article/57574.shtml
- http://h5.mobile.hcbezg.cn/Article/33941.shtml
- http://h5.mobile.hcbezg.cn/Article/972263.shtml
- http://h5.mobile.cvsifc.cn/Article/416177.shtml
- http://h5.mobile.fuvxie.cn/Article/3820136.shtml
- http://h5.mobile.hcbezg.cn/Article/7310.shtml
- http://h5.mobile.hcbezg.cn/Article/1715.shtml
- http://h5.mobile.fuvxie.cn/Article/42679.shtml
- http://h5.mobile.cvsifc.cn/Article/2131567.shtml
- http://h5.mobile.cvsifc.cn/Article/47677.shtml
- http://h5.mobile.fuvxie.cn/Article/8025.shtml
- http://h5.mobile.cvsifc.cn/Article/722886.shtml
- http://h5.mobile.fuvxie.cn/Article/091946.shtml
- http://h5.mobile.fuvxie.cn/Article/31511.shtml
- http://h5.mobile.hcbezg.cn/Article/6645070.shtml
- http://h5.mobile.cvsifc.cn/Article/09107.shtml
- http://h5.mobile.fuvxie.cn/Article/1919.shtml
- http://h5.mobile.fuvxie.cn/Article/184606.shtml
- http://h5.mobile.fuvxie.cn/Article/1573694.shtml
- http://h5.mobile.hcbezg.cn/Article/7539775.shtml
- http://h5.mobile.cvsifc.cn/Article/9958849.shtml
- http://h5.mobile.hcbezg.cn/Article/5253.shtml
- http://h5.mobile.fuvxie.cn/Article/4895.shtml
- http://h5.mobile.cvsifc.cn/Article/3909.shtml
- http://h5.mobile.cvsifc.cn/Article/06582.shtml
- http://h5.mobile.hcbezg.cn/Article/6989.shtml
- http://h5.mobile.cvsifc.cn/Article/833229.shtml
- http://h5.mobile.cvsifc.cn/Article/848865.shtml
- http://h5.mobile.fuvxie.cn/Article/3973.shtml
- http://h5.mobile.hcbezg.cn/Article/43981.shtml
- http://h5.mobile.hcbezg.cn/Article/0458174.shtml
- http://h5.mobile.cvsifc.cn/Article/058359.shtml
- http://h5.mobile.fuvxie.cn/Article/59897.shtml
- http://h5.mobile.cvsifc.cn/Article/9420.shtml
- http://h5.mobile.hcbezg.cn/Article/2314493.shtml
- http://h5.mobile.fuvxie.cn/Article/38368.shtml
- http://h5.mobile.hcbezg.cn/Article/9626947.shtml
- http://h5.mobile.fuvxie.cn/Article/1520138.shtml
- http://h5.mobile.fuvxie.cn/Article/040127.shtml
- http://h5.mobile.hcbezg.cn/Article/132085.shtml
- http://h5.mobile.cvsifc.cn/Article/741243.shtml
- http://h5.mobile.hcbezg.cn/Article/776526.shtml
- http://h5.mobile.hcbezg.cn/Article/2020.shtml
- http://h5.mobile.fuvxie.cn/Article/8279031.shtml
- http://h5.mobile.fuvxie.cn/Article/8568169.shtml
- http://h5.mobile.cvsifc.cn/Article/66182.shtml
- http://h5.mobile.hcbezg.cn/Article/1314930.shtml
- http://h5.mobile.cvsifc.cn/Article/667330.shtml
- http://h5.mobile.cvsifc.cn/Article/790560.shtml
- http://h5.mobile.fuvxie.cn/Article/661558.shtml
- http://h5.mobile.fuvxie.cn/Article/6328765.shtml
- http://h5.mobile.fuvxie.cn/Article/6964577.shtml

## 项目结构

```
webindex-hub/
├── src/                                 # 核心源代码目录
│   ├── core/                           # 数据导入、批次管理与校验模块
│   │   ├── importer.ts                # 支持 CSV/JSON/TXT 格式的链接导入器
│   │   ├── batch-validator.ts         # 检查 URL 格式与批次唯一性
│   │   └── link-normalizer.ts         # 仅做空白字符清理，不修改协议/域名
│   ├── api/                           # 只读 JSON API 实现（基于 Express 或 Next.js）
│   │   ├── routes/                    # 路由定义：/api/links, /api/batches
│   │   └── middleware/                # 跨域、请求日志、限流中间件
│   ├── checker/                       # 链接健康检查模块
│   │   ├── http-client.ts             # 基于 undici 或 axios 的异步 HTTP 检测
│   │   ├── reporter.ts                # 生成健康报告 JSON/Markdown
│   │   └── scheduler.ts               # 定时任务触发器（node-cron）
│   ├── generator/                     # 静态站点生成器
│   │   ├── template-engine.ts         # 基于 EJS 或 Handlebars 的模板渲染
│   │   ├── page-builder.ts            # 组装首页、批次页、详情页
│   │   └── asset-pipeline.ts          # CSS/JS 资源打包与指纹化
│   └── cli/                           # 命令行工具入口
│       ├── commands/                  # import, build, check, export 子命令
│       └── runner.ts                  # 命令解析与执行器
├── data/                               # 数据存储目录（不纳入版本控制）
│   ├── batches/                       # 按批次存放原始导入文件
│   ├── db/                            # SQLite 数据库文件（links.db, meta.db）
│   └── reports/                       # 健康检查报告输出目录
├── templates/                          # 静态站点模板文件
│   ├── layouts/                       # 基础布局（header, footer, sidebar）
│   ├── pages/                         # 首页、批次列表、链接详情页模板
│   └── partials/                      # 可复用组件（链接卡片、标签云）
├── public/                             # 无需构建的静态资源（favicon, robots.txt）
├── scripts/                            # 辅助运维脚本（备份、迁移、数据校验）
├── tests/                              # 单元测试与集成测试（Jest / Vitest）
│   ├── unit/                          # 核心模块单测
│   └── integration/                   # API 与生成器端到端测试
├── .env.example                        # 环境变量配置模板
├── package.json                        # Node.js 依赖与脚本声明
├── tsconfig.json                       # TypeScript 编译配置
├── README.md                           # 项目说明文档（本文件）
└── LICENSE                             # MIT 许可证
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并克隆至本地开发环境。请确保本地 Node.js 版本与项目要求一致，建议使用 pnpm 管理依赖。

2. 创建新分支进行功能开发或问题修复，分支命名建议采用 `feat/` 或 `fix/` 前缀，例如 `feat/support-rss-import` 或 `fix/batch-validator-empty-url`。

3. 编写代码时请遵守项目 ESLint 与 Prettier 配置，提交前执行 `pnpm run lint` 与 `pnpm run test` 确保代码风格与测试用例通过。若新增功能，请补充相应的单元测试或集成测试。

4. 提交变更时使用语义化提交信息格式，例如 `feat(importer): support wildcard domain filter` 或 `docs(readme): update deployment section`。提交前请确保所有测试通过且构建无错误。

5. 发起 Pull Request 至主仓库的 `main` 分支，并在 PR 描述中清晰说明变更目的、影响范围及测试情况。项目维护者将在 3 个工作日内进行评审并反馈。

## 常见问题

**问：导入链接时提示“URL 格式无效”，但我的链接确实可以正常访问，是什么原因？**

答：导入器默认使用 WHATWG URL 标准进行格式校验，要求链接必须包含协议头（http:// 或 https://）。请检查链接前后是否包含不可见字符（如零宽空格、制表符）或多余的空格。若链接中包含中文或特殊符号，建议先进行百分号编码再导入。若仍无法通过，可使用 `--strict=false` 参数关闭严格校验模式，但此时需自行确保链接可用性。

**问：健康检查模块报告大量超时，是否意味着这些链接全部失效？**

答：超时并不等同于链接永久失效。可能的原因包括目标服务器限流、网络抖动、防火墙策略或 CDN 节点响应缓慢。默认超时阈值为 5000 毫秒，您可通过环境变量 `CHECKER_TIMEOUT` 调整该值。建议在非高峰时段重新运行检查，或使用 `--retry=3` 参数开启自动重试。若连续三次检查均超时或返回 5xx 状态码，则基本可判定为异常链接。

**问：如何将现有浏览器书签或 Pocket 收藏批量导入到 WebIndex Hub？**

答：项目未直接集成浏览器书签解析器，但您可以将书签导出为 HTML 文件，再使用 `scripts/parse-bookmarks.js` 辅助脚本提取所有 `<a>` 标签的 href 属性，生成纯文本 URL 列表后通过标准导入流程处理。Pocket 用户可先导出 CSV 文件，使用 `src/core/importer.ts` 的 `--format=csv` 选项指定列映射关系进行导入。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
