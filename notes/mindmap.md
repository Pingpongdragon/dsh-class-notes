# 《DeepSeek Harness [09]》思维导图（Markdown 版）

> BV144nc6KEA4 · 89:24 · 南京大学蒋炎岩（B站「绿导师原谅你了」）
> 这版用「纯文字树 + Mermaid + 表格」三种写法，任何 Markdown 阅读器至少能看到文字树。

## 一句话

**架构 = 用限制换协作。** 需求会杀死架构；DSH 用 microkernel + append-only session + event bus 把能力让给插件生态，但插件只消除 accidental complexity，消除不了 essential complexity。

---

## 1. 文字版思维导图（不依赖 Mermaid，直接能看）

```text
DeepSeek Harness [09] —— 架构 = 用限制换协作
│
├─ 1. 问题
│  ├─ agent 组织化：你是 CTO，sub-agent 是团队
│  ├─ 版本控制：只读 / 写 / refactor 锁，小 fix 可并行
│  └─ demo ≠ 产品：断网、恢复、客户端/服务端状态一致
│
├─ 2. 需求
│  ├─ PRD 会膨胀：dashboard、skills、沙箱、权限
│  ├─ MVP 是验证假设，不是缩小版产品
│  └─ 需求变更杀死架构：WorkBody → GrokBot
│
├─ 3. 代价
│  ├─ 插件语义冲突：10 个压缩插件 = 输出被压到 1/1000
│  ├─ hook 顺序没有规定：一个要停、一个要继续
│  └─ essential complexity 解决不了，只能减少 accidental
│
├─ 4. 架构
│  ├─ 受限 vs 自由：actor model 式全自由 = 没有架构
│  ├─ LAMP / event sourcing：各有假设与代价
│  └─ MapReduce 2004：用 map/reduce 限制换容错与并行
│
├─ 5. DSH
│  ├─ microkernel / Cordis：服务解析、依赖激活、load/unload
│  ├─ session 唯一事实：append-only 事件日志，模型历史是投影
│  └─ event bus / pre-step：插件可观察、可改未 persist 的事件
│
└─ 6. 生态
   ├─ creator mode：运行时拆装插件
   ├─ WPS / Excel bridge：锁对象 → hand off → 写回
   └─ 动态 UI：HTML+JS 卡片，点击事件注回上下文
```

---

## 2. Mermaid 版（支持 Mermaid 的阅读器会渲染）

```mermaid
mindmap
  root((DeepSeek Harness [09]))
    问题
      agent 组织化
        版本控制锁
      demo 不能当产品
        断网/恢复/状态一致
    需求
      PRD 膨胀
      MVP 验证假设
      需求变更杀死架构
    代价
      插件语义冲突
      hook 顺序
      essential complexity
    架构
      受限 vs 自由
      LAMP / event sourcing
      MapReduce 2004
    DSH
      microkernel / Cordis
      session 唯一事实
      event bus / pre-step
    生态
      creator mode
      WPS / Excel bridge
      动态 UI
```

---

## 3. 分支速查

| 分支 | 关键词 | 一句话 |
|---|---|---|
| 问题 | agent 组织化、版本控制、demo≠产品 | agent 把「一个人写代码」变成「一个人管理组织」，旧假设全被打破 |
| 需求 | PRD、MVP、需求变更 | 需求一变，50 万行和旧架构一起变成负债 |
| 代价 | 语义冲突、hook 顺序 | 插件只减少 accidental complexity，essential 仍在 |
| 架构 | 受限 vs 自由、LAMP、event sourcing、MapReduce | 架构不是越干净越好，是「用限制换协作」 |
| DSH | microkernel、Cordis、session、event bus、pre-step | session 是事实，event bus 是协作接口，插件是投影 |
| 生态 | creator mode、WPS bridge、动态 UI | super app 只需一个薄 bridge，就能接入整个生态 |

---

## 4. 10 章详细笔记目录

| # | 章节 | 时间（约） | 一句话 |
|---|---|---|---|
| 0 | 开场：agent 时代，git 不够用了 | 00:00–10:50 | 组织架构、并行 task、版本控制锁 |
| 1 | 150 行 demo：能玩，不能当产品 | 10:50–20:00 | 3D 校园、断网、重试、支付状态 |
| 2 | 从 demo 到产品：PRD、MVP、需求变更 | 20:00–30:00 | WorkBody、slop、GrokBot |
| 3 | 架构的本质：受限 vs 自由 | 30:00–40:15 | LAMP、event sourcing、MapReduce |
| 4 | DSH 的世界模型 | 40:15–50:00 | Cordis、session、event bus、pre-step |
| 5 | 演示：TUI、PDF、VS Code 式侧边栏 | 50:00–58:30 | 扔掉 UI slots、共享状态、better sidebar |
| 6 | Creator mode：运行时拆装插件 | 58:30–68:20 | 动态插件生命周期、现场许愿 |
| 7 | WPS/Excel bridge：超级应用 AI 原生 | 68:20–76:00 | 锁对象、hand off、写回 |
| 8 | 动态 UI：HTML+JS 卡片 | 76:00–84:00 | 成语接龙、五子棋、1.5KB 协议 |
| 9 | 代价与结论：release nothing | 84:00–89:23 | 语义冲突、essential complexity、生态 |

---

## 5. 关键数字

| 内容 | 数字/细节 |
|---|---|
| mini agent | 150 行 |
| 视频时长 | 89:24（5363 秒） |
| DSH 第一个提交 | 2026-06-10 23:00 |
| MapReduce 论文 | 2004 年，最多 2000 台机器，每 task 100MB 内存 |
| 修 3D 校园图 | 约 10 倍 token |
| 动态 UI 协议 | 1.5KB systemPrompt |
| 十个压缩插件叠加 | 输出被压到约 1/1000 |
| WorkBody 假设崩塌 | 已写 50 万行，老板改需求照 GrokBot 做 |

---

## 6. 链接

- 视频：https://www.bilibili.com/video/BV144nc6KEA4/
- 评论：https://www.bilibili.com/video/BV144nc6KEA4/#reply319063825473
- 详细笔记：`reports/DeepSeek-Harness-详细笔记-261103.md`
