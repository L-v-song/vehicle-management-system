# 车辆管理系统

原生 HTML + CSS + JavaScript 实现的车辆管理系统，课程实验作业。无框架、无依赖、无构建，单个 HTML 文件即可运行。

## 在线访问

- 演示地址：<https://l-v-song.github.io/vehicle-management-system/>
- 仓库地址：<https://github.com/L-v-song/vehicle-management-system>

## 功能

| 模块 | 功能 |
| --- | --- |
| 工作台 | 统计卡片、快捷入口、最新月卡动态 |
| 月卡管理 | 关键字/状态/品牌筛选、前端分页、查看、编辑、续费、单条删除、全选批量删除 |
| 增加月卡 | 新增与编辑复用同一表单、必填校验、手机号与车牌正则校验、自动计算剩余有效天数与状态 |

数据保存在浏览器本地存储（localStorage），刷新页面不会丢失。

## 技术要点

- **hash 路由**：`#/home`、`#/list`、`#/add` 三个视图切换，用单文件实现多页面体验
- **数据驱动视图**：HTML 中不含任何业务数据，表格与卡片全部由渲染函数动态生成；数据一变就重新渲染
- **事件委托**：表格行操作、复选框、分页按钮统一在父节点监听一次，避免重复绑定
- **输入转义**：渲染用户输入前做 HTML 转义，防止 XSS
- **本地日期处理**：按本地时间格式化日期，避免 UTC 时区导致的日期偏差
- **状态自动计算**：根据结束日期自动判断「可用 / 已过期」，回读数据时重新计算，不存死

## 目录结构

```
vehicle-management-system/
├── index.html    # 全部源码（HTML + CSS + JavaScript 内联）
└── README.md
```

## 本地运行

直接双击 `index.html` 即可，也可以起一个静态服务器：

```bash
python -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 用 VSCode 推送到 GitHub

> 前置条件：本机需开启加速器（Steam++ / Watt Toolkit），它会修改 hosts 将 github 域名指向本地反代；仓库已配置 `http.sslVerify=false` 以适配加速器的自签证书。

1. 用 VSCode 打开本项目文件夹
2. 左侧点击 **源代码管理** 面板（快捷键 `Ctrl + Shift + G`）
3. 点 **发布分支（Publish Branch）**，按提示登录 GitHub 账号
4. 仓库可见性选择 **Public**（公开仓库才能免费开启 Pages）
5. 推送成功后，到仓库 **Settings → Pages** 按上面的步骤开启

## 部署到 GitHub Pages

1. 在 GitHub 上新建一个公开仓库，例如 `vehicle-management-system`（不要勾选初始化 README）

2. 本地关联远程仓库并推送：

```bash
git remote add origin https://github.com/<你的用户名>/vehicle-management-system.git
git branch -M main
git push -u origin main
```

3. 打开仓库页面，进入 **Settings → Pages**：

   - Source 选择 `Deploy from a branch`
   - Branch 选择 `main`，目录选择 `/ (root)`
   - 点击 Save，等待 1~2 分钟

4. 访问地址：

```
https://<你的用户名>.github.io/vehicle-management-system/
```

## 说明

本项目为课程实验作业，仅用于学习交流。
