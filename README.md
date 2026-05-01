# 个人成长仪表盘（PWA）

这是一个纯前端、无后端、无登录的个人成长记录应用（MVP 版）。
核心理念是「系统优于目标」：长目标负责方向，系统负责日常执行，今日计划负责落地。

## 文件说明

- `index.html`：主应用（包含全部 CSS + JS）
- `manifest.json`：PWA 清单配置
- `service-worker.js`：离线缓存
- `icon-192.png` / `icon-512.png`：PWA 图标

## 本地运行

### 方式 1：直接打开

- 直接双击 `index.html` 即可使用（功能基本可用）
- 注意：部分浏览器对 `file://` 的 Service Worker 支持有限，如果要完整测试 PWA 建议用方式 2

### 方式 2：静态服务器（推荐）

任选一种：

- VS Code Live Server
- Python：`python -m http.server 8080`
- Node：`npx serve .`

然后访问：`http://localhost:8080`（或对应端口）。

## 手机添加到主屏幕

### Android（Chrome）

1. 用 Chrome 打开站点（建议是 http/https 地址，不是 file://）
2. 点击浏览器菜单（右上角三点）
3. 选择「添加到主屏幕」
4. 确认后会在桌面生成应用图标

### iOS（Safari）

1. 用 Safari 打开站点
2. 点击底部分享按钮
3. 选择「添加到主屏幕」
4. 命名后确认添加

## 数据备份：导出 / 导入

- 页面底部有「导出 JSON」按钮：会下载当前所有本地数据
- 点击「导入 JSON」可恢复备份
- 导入会覆盖当前内存数据并写入 localStorage

建议每周导出一次备份 JSON，避免误删。

## 数据结构简介

应用数据存储在 `localStorage` 的 `growth_dashboard_v1` 键中，核心结构：

- `user`：用户信息（姓名、起始日期）
- `systems`：系统列表（频率、关联目标、执行记录）
- `longTermGoals`：长目标列表
- `dailyLogs`：每日计划列表（未完成任务次日自动结转）
- `reflectionEntries`：今日感悟历史
- `gainsEntries`：收获历史
- `sadnessEntries`：伤心历史
- `memories`：美好回忆（可带 base64 图片）

## 当前实现范围（MVP）

已实现：

- 今日计划（添加/删除/完成、历史完成查看、未完成自动结转）
- 系统管理（新增、删除、今日打卡、备注、周/月进度条、12 周热力图、最长连续）
- 本周系统总览
- 今日感悟（新增/编辑/删除）
- 美好回忆（新增/删除，支持 <=500KB 图片）
- 收获/伤心（Tab 切换，新增/编辑/删除）
- 长目标（默认折叠，新增/编辑/删除，展示关联系统）
- JSON 导入导出
- PWA（manifest + service worker）

## 后续可迭代建议

- 系统详情页（更长时间维度统计）
- 数据校验与迁移版本号
- 细化月度/年度复盘模块
- UI 视觉升级与动效
