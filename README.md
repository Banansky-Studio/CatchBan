# CatchBan 2.0 Beta

> 捕获灵感，而后掌控。  
> Catch the spark. Command the workflow.

CatchBan 2.0 Beta 是面向视频创作者的 macOS 素材库工作台。  
它把采集、管理、预览与轻创作整合到同一条本地工作流中，让素材从“下载完成”直接进入“可创作状态”。

## 现在发布

- 版本: `V2.0 Beta`
- 状态: 公开测试中，免费开放
- 平台: macOS 12+（Apple Silicon 原生推荐，同时兼容 Intel）
- 更新时间: 2026 年 4 月

## 立即下载

- 最新版本页: [GitHub Releases](https://github.com/Banansky-Studio/CatchBan/releases/latest)
- 直接下载 DMG: [CatchBan.dmg](https://github.com/Banansky-Studio/CatchBan/releases/latest/download/CatchBan.dmg)

## 产品定位

CatchBan 2.0 Beta 的市场定位是「视频创作者素材库工作台」。

它解决的不是“把文件下下来”这一个动作，而是完整的素材准备链路:

- 采集: 把高价值参考素材快速拉入本地
- 管理: 在本地库内持续归档、检索、复用
- 预览: 在工作台内快速检视、逐帧回看与标记
- 输出: 直接完成高频轻创作处理并回流到库

## 核心能力全景

### 精准采集

- 链接粘贴与内置浏览器双入口采集
- 支持 4K 高清视频下载（视源站可用性）
- 下载结果可直接进入素材库，减少二次搬运

### 灵活归档

- 本地 Creator Library Workspace（新建或接入已有目录）
- 支持按项目/主题/阶段组织素材
- 覆盖全库搜索、最近记录、稍后整理（Inbox）等常用入口
- 提供重复候选、同来源归档与元数据补全建议，降低素材混乱

### 原生级检视

- 在库内快速预览，减少 Finder 与外部播放器来回切换
- 支持逐帧查看、重点片段回看与标记动作
- 本地优先链路，兼顾高频检视时的稳定与响应

### 创作工具箱

- 无损转换为 H.264（Compatible MP4）
- 截取片段
- 抓取关键帧
- GIF 导出
- 音频提取
- 批量缩略图抓图

## V2.0 Beta 更新摘要

- 创作者素材库工作台正式成型，支持 4K 高清视频下载，采集、整理、预览与轻创作进入同一条工作流
- 新增全库搜索、最近记录、稍后整理、重复识别与同来源归档建议
- 优化预览、逐帧查看与关键帧标记体验，筛镜头与回看重点更高效
- 选定素材可直接拖入 Premiere Pro、DaVinci Resolve、Final Cut Pro 等后期软件继续处理
- 现有本地素材库结构与资产可延续到后续版本

## 支持平台（持续优化）

- YouTube
- Bilibili
- Vimeo
- TikTok
- Instagram
- X / Twitter
- 小红书
- 其他通用链接（Generic）

## 创作场景

- 影视广告
- 短视频创作
- 混剪剪辑
- 选题储备
- 自媒体运营

## 本地优先与数据掌控

- 素材与库数据默认由你本地持有与管理
- 无需注册，无需订阅，即可开始使用 Beta
- 素材库可放在系统盘、外接 SSD 或已挂载存储设备

## 安装提示

首次打开若遇到系统安全提示，请前往：

`系统设置 -> 隐私与安全性 -> 仍要打开`

## 从源码运行（开发者）

```bash
git clone https://github.com/Banansky-Studio/CatchBan.git
cd CatchBan
open CatchBan.xcodeproj
```

发布前校验脚本：

```bash
scripts/validate_release_architectures.sh
scripts/verify_dual_arch_build.sh
```

完整发布流程见: [RELEASE.md](./RELEASE.md)

## 反馈与协作

- 问题反馈与建议: [Issues](https://github.com/Banansky-Studio/CatchBan/issues)

## 使用声明

请仅在符合当地法律法规与目标平台条款的前提下使用 CatchBan，并确保你对所采集与处理的内容拥有合法权限。
