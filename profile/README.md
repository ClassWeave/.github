<div align="center">
  <h1>ClassWeave</h1>
  <p><strong>面向真实课堂的多端协同系统：macOS 主控 · iOS / Android 学生端 · USB↔蓝牙中继</strong></p>
  <p>
    <a href="https://classweave.mem.report/"><img alt="Website" src="https://img.shields.io/badge/website-classweave.mem.report-1f6feb.svg"></a>
    <img alt="License" src="https://img.shields.io/badge/license-Apache%202.0-blue.svg">
    <img alt="Repos" src="https://img.shields.io/badge/repos-4-3DDC84.svg">
  </p>
  <p>
    <a href="https://github.com/ClassWeave/classweave-host">Host (macOS)</a>　·　
    <a href="https://github.com/ClassWeave/classweave-client">Client (iOS / Android)</a>　·　
    <a href="https://github.com/ClassWeave/classweave-bridge">Bridge (Android / OrangePI)</a>　·　
    <a href="https://github.com/ClassWeave/classweave-prompts">Prompts (Vibe Coding)</a>
  </p>
</div>

---

## 我们在做什么

**ClassWeave** 是一套部署在真实课堂里的**多端协同系统**：

- 教师在 **macOS** 上讲 PowerPoint，
- 学生通过 **iOS / Android** 接收课件、回答互动、发送弹幕，
- 老旧无网络的多媒体教室靠一台 **OrangePI 5B** 做 **USB ↔ 蓝牙** 中继，
- 全程**不依赖外网、不依赖学校 Wi-Fi**，开机即用。

```
[iOS A]  \
[iOS B]   >── MultipeerConnectivity ──▶  [macOS Host]  ── USB-C / TCP ──▶  [Bridge]  ── BT RFCOMM ──▶  [Android A/B]
[iOS C]  /                                  ▲
                                            └─ 业务权威端：课件分发 / 白板状态 / 翻页监听 / 弹幕队列
```

设计目标是**在最差网络条件下保证课堂可用**：所有跨端协议被统一抽象成一个
`Envelope` JSON 信封，承载层（MPC / USB-TCP / Bluetooth RFCOMM）任意可替换。

## 仓库一览

| 仓库 | 角色 | 平台 | 主要技术 |
| --- | --- | --- | --- |
| [`classweave-host`](https://github.com/ClassWeave/classweave-host) | 教师主控端 / 业务权威端 | macOS 14+ | SwiftUI · MultipeerConnectivity · AppleScript · OSS |
| [`classweave-client`](https://github.com/ClassWeave/classweave-client) | 学生端 App | iOS / Android | Flutter 3.19+ · Riverpod · Freezed |
| [`classweave-bridge`](https://github.com/ClassWeave/classweave-bridge) | USB↔蓝牙 中继桥接 | Android 12+ (OrangePI 5B) | Kotlin · Jetpack Compose · Bluetooth RFCOMM |
| [`classweave-prompts`](https://github.com/ClassWeave/classweave-prompts) | Vibe Coding 提示词档案 | — | 真实开发过程中给 AI 的 62 段提示词 |

> 4 个仓库**完全独立**：可单独 clone、单独构建、单独提 Issue / PR；
> 任意一端可以被替换成你自己的实现，只要遵守 `Envelope` 协议。

## 怎么开始

| 你是谁 | 推荐路径 |
| --- | --- |
| **想在自己课堂部署一套** | 先看 [`classweave-host`](https://github.com/ClassWeave/classweave-host) 的 README，按需决定要不要带 Bridge |
| **想直接用学生端** | iOS：[App Store](https://apps.apple.com/cn/app/classweave/id6761185109) · Android：从 [`classweave-client`](https://github.com/ClassWeave/classweave-client) 源码自行编译 |
| **想了解协议 / 自己实现一端** | 看任意仓库 README 的"协议"章节，所有端都基于同一个 `Envelope` JSON 信封 |
| **想学习如何与 AI 协同开发** | [`classweave-prompts`](https://github.com/ClassWeave/classweave-prompts)：62 段真实脱敏后的 Cursor / Claude Code 提示词 |

## 开源与协作

- 全部仓库采用 **Apache License 2.0**。
- 每个仓库都包含 `CONTRIBUTING.md` 与 `SECURITY.md`，欢迎 Issue / PR。
- 安全问题请按各仓库 `SECURITY.md` 里给出的方式私下报告，**不要**直接开公共 Issue。

## 链接

- 官方网站：<https://classweave.mem.report/>
- iOS 下载：<https://apps.apple.com/cn/app/classweave/id6761185109>
- 组织主页：<https://github.com/ClassWeave>
