---
name: keyframe_to_video_prompt
description: 视频运镜指令专家。将剧情大纲转化为符合影视工业标准的 8s 视频动力学提示词。v10.0 精简叙事版。
---

# 🎞️ 视频叙事动力学生产标准 (v10.0)

> [!DANGER]
> **核心生产原则（违反则输出作废）：**
> 1. 一个 Prompt = 一个情绪 + 一个动作 + 一个景别
> 2. 多景别 = 多段生成，严禁在单个 Prompt 中堆叠多个场景
> 3. 提示词越少越好，只保留"最能触发 AI 正确生成"的关键词
> 4. 词汇堆叠是画面崩坏的主要原因

---

## 0. 🏛️ 剧情锚定协议 (Plot Anchor) [MANDATORY]
在生成任何提示词前，必须先从剧情大纲中完成：
- **关键场景抽离**：这一段最重要的一个画面是什么？
- **人物心理解读**：此刻角色的内心状态是什么？（不是动作，是情绪）
- **情绪触发词**：将心理状态转化为可视化的物理信号（瞳孔/手部/呼吸）

---

## 1. 📐 单段生成标准 (Single Shot Standard)
每个 Prompt 只包含：
```
[景别] + [运镜] + [主体] + [一个核心动作] + [情绪触发词] + [光影]
```
**严禁同时出现：**
- 两个人物各自的动作描述
- 场景切换（远→近）
- 多个情绪状态

---

## 2. 🎬 多景别处理原则 (Multi-Shot Protocol)
当一个叙事段落需要多个景别时：
- **不堆叠**：拆分为独立的 Shot 1、Shot 2、Shot 3
- **每段只做一件事**：
  - Shot 1：建立空间关系（远景）
  - Shot 2：锁定情绪核心（中景）
  - Shot 3：放大心理触发（特写）
- **用运镜连接**：Dolly-In / Rack Focus / Push-In 代替"然后"的语言堆叠
- **[Harness 约束] 时序锚点传递 (Temporal Sequence Anchor)**：为了通过 `VideoSegment` 审计引擎的审查，Shot N+1 的第一帧（坐标、服饰、姿态）必须在逻辑上严格继承 Shot N 的最后一帧，任何物理参数的不连贯都会被判定为“切镜穿帮”。

---

## 3. 🧠 情绪优先原则 (Emotion-First Protocol) [v9.9]
**动作是情绪的结果，不是起点。**
- 先写情绪触发：`His jaw tightens` / `Her grip loosens`
- 再写动作结果：`He sets the cup down`
- 严禁直接跳到物理动作（抓人、推门等）

---

## 4. 🚫 背景封禁词 (Background Prohibition) [v9.6]
每个宫廷场景必须包含：
```
NO foreign sculptures, NO modern curtains, NO small rooms,
NO round modern tables, NO modern props. 
VAST HALL with 30 meters of depth.
```

---

## 5. 💡 光影死锁 (Lighting Deadlock) [v9.0]
- `[TIME: MIDNIGHT]` = 冷月光主 + 琥珀烛光辅
- `[TIME: EVENING]` = 暖红宫烛主
- 严禁无时间声明（AI 默认白天）

---

## 6. 🎭 视觉去名化 (Visual De-naming) [v8.4]
- 李翾 → `The man in black silk dragon robe`
- 顾昭 → `The young woman in purple silk`
- 丁嬷嬷 → `The elderly woman in dark blue silk`
- 大皇子 → `The man in red and gold silk robe`

---

## 7. Veo 3 专项标准 (Veo 3 Protocol)
- 加入 `AUDIO:` 段落描述环境音
- 加入 `A FICTIONAL CHARACTER, not based on any real person`
- 移除 `--ar` `--v` 等 Midjourney 参数
- 人脸描述使用性格词而非外貌词
