<div align="center">

# 干掉评论区

<a href="https://github.com/Xposed-Modules-Repo/io.github.qiuxi903.hidecomments/releases"><img alt="GitHub all releases" src="https://img.shields.io/github/downloads/Xposed-Modules-Repo/io.github.qiuxi903.hidecomments/total?label=Downloads"></a>
<a href="https://github.com/Xposed-Modules-Repo/io.github.qiuxi903.hidecomments/releases/latest"><img alt="GitHub latest release" src="https://img.shields.io/github/v/release/Xposed-Modules-Repo/io.github.qiuxi903.hidecomments"></a>
<a href="https://www.android.com/"><img src="https://img.shields.io/badge/Android-8.0--brightgreen?style=flat&logo=android&logoColor=white"></a>
<a href="https://github.com/LSPosed/LSPosed"><img src="https://img.shields.io/badge/框架-LSPosed%20%2F%20Vector-blue?style=flat&logo=github&logoColor=white"></a>
<a href="https://github.com/qiuxi903/HideComments"><img src="https://img.shields.io/badge/源码仓库-black?style=flat&logo=github&logoColor=white"></a>
<a href="https://github.com/Xposed-Modules-Repo/io.github.qiuxi903.hidecomments"><img src="https://img.shields.io/badge/LSPosed仓库-orange?style=flat&logo=xdadevelopers&logoColor=white"></a>

**抖音、快手、哔哩哔哩的评论区，从入口到内容到手势，整条抹掉。**
按钮不显示、评论打不开、左右滑也滑不进去。

[📖 完整说明与常见问题](https://github.com/qiuxi903/HideComments#readme)

</div>

---

## 效果

| 位置 | 表现 |
|---|---|
| 评论区入口按钮 / 顶栏 Tab | 不显示，也不会闪一下再消失 |
| 评论区面板 | 根本不加载，点开是空的 |
| 左右滑动切到评论页 | 手势被挡，画面纹丝不动 |
| 点击评论按钮、分享链接、深链 | 没反应 |
| 搜索页、简介页、推荐列表 | **完全不受影响** |

最后一行是特意保证的。屏蔽做得太猛是这类模块最常见的翻车方式——搜不到视频、顶栏少一格，那模块就废了。

## 支持的 App

| App | 包名 | 状态 |
|---|---|---|
| 抖音 | `com.ss.android.ugc.aweme` | ✅ 已验证 |
| 抖音极速版 | `com.ss.android.ugc.aweme.lite` | ✅ 已验证 |
| 快手 | `com.smile.gifmaker` | ✅ 已验证 |
| 快手极速版 | `com.kuaishou.nebula` | ✅ 已验证 |
| 哔哩哔哩国际版 | `com.bilibili.app.in` | ✅ 已验证 |
| 哔哩哔哩 / HD / 播放版 / 概念版 | `tv.danmaku.bili` 等 | ⚠️ 同框架，未逐一验证 |

## 安装

1. 从上面的 [Releases 页面](https://github.com/Xposed-Modules-Repo/io.github.qiuxi903.hidecomments/releases/latest) 下载 APK 并安装
2. 打开 **LSPosed / Vector 管理器** →「模块」→ 勾选 **干掉评论区**
3. 「作用域」里勾选要屏蔽的 App（默认 9 个包名都预置好了）
4. **强制停止**目标 App，重新打开

第 4 步的「强制停止」别省 —— 模块是在 App 进程启动时注入的，进程还活着的话改了设置也不会生效。

装好后打开模块主页，顶部显示 `LSPosed … · API 101 · 已授权 4/4` 就说明接通了。

### 环境要求

| 项目 | 要求 |
|---|---|
| 系统 | Android 8.0 及以上 |
| Root | Magisk / KernelSU / APATCH 任一 |
| 注入框架 | **LSPosed 2.2+** 或 **Vector 2.1+**（需支持 libxposed API 101） |
| Zygisk | 已启用（NeoZygisk / Zygisk Next） |

## ⚠️ 使用前请了解

- 本模块**只改界面，不碰网络**。服务端收到的请求和你正常刷视频时完全一样。
- 但**你的 Root 环境本身可能被检测**。本模块**不处理** Root 检测绕过，需要自己配合 Shamiko、Play Protect 之类的隐藏方案。
- 在 Root 设备上注入第三方 App 可能违反目标 App 的服务条款，使用风险自负。

## 已知限制

- 抖音部分新界面用 Compose 渲染，传统 View 树扫描覆盖不到，只能靠 dex 索引在 Fragment 层兜底，覆盖率不确定
- App 改版后内部控件名可能变，识别会失效 —— 但**失效只是少一层保险，不会反过来误伤**
- 只在 App 进程内生效；通知栏、系统分享面板里的评论摘要管不了
- B站国内版结构大概率与国际版相同，但未实机验证

## 文档

| 文档 | 内容 |
|---|---|
| [ARCHITECTURE.md](https://github.com/qiuxi903/HideComments/blob/main/ARCHITECTURE.md) | 架构与使用方法：模块划分、五道防线、配置项、排查流程 |
| [TECHNICAL.md](https://github.com/qiuxi903/HideComments/blob/main/TECHNICAL.md) | 技术详解：三个 App 的真实结构、核心算法、踩坑记录、扩展指南 |

## 许可

[MIT License](https://github.com/qiuxi903/HideComments/blob/main/LICENSE) · Copyright (c) 2026 邱息
