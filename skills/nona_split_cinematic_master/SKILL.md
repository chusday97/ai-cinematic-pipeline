---
name: nona_split_cinematic_master
description: 工业级九宫格（3x3）分镜大师。执行 v5.1 全封禁协议，强制执行空间礼制死锁、背景封禁词、场景全锚定与人物先行。
---

# 📐 工业化分镜标准 (v5.1)

> [!DANGER]
> **以下三项是底层死锁，违反任意一条将导致输出作废：**
> 1. 场景全锚定协议必须在分镜前完成
> 2. 三层空间坐标必须在每一格中明确声明
> 3. 背景封禁词必须出现在每一个分镜提示词中

---

## 0. 🏛️ 场景全锚定协议 (Source-Visual Anchor) [MANDATORY v9.1]
在每次输出分镜前，必须先完成以下锚定：
- **原文场景 (Source Scene)**：该场景的故事背景
- **时间锚点 (Time Anchor)**：`[TIME: MIDNIGHT]` 或 `[TIME: EVENING]` + 光影风格
- **核心逻辑 (Core Logic)**：该场景的情绪/叙事主轴（情绪层优先于动作层）
- **环境死锁 (Environmental Deadlock)**：必须出现/严禁出现的道具清单

---

## 1. 🎭 人物先行协议 (Character-First Protocol) [MANDATORY]
在输出任何分镜提示词前，必须先声明 [角色身份死锁]：
- **格式**：[角色名] → `视觉描述词` + `[空间坐标位置]`
- **禁止使用人名**：严禁出现 "Gu Zhao"、"Li Xuan" 等。只使用视觉描述词。

---

## 2. 📍 坐标死锁逻辑 (Spatial Coordinate Lock) [CRITICAL]
**每一个分格（P1-P9）必须明确三个坐标：**
- **X轴**：`LEFT` / `CENTER` / `RIGHT`
- **Y轴**：`FOREGROUND` / `MIDGROUND` / `BACKGROUND`
- **Z轴**：`ELEVATED`(高位) / `GROUND LEVEL`(平位) / `KNEELING`(跪伏)

### 宫廷礼制空间硬锁（宫宴适用）：
| 角色等级 | 空间坐标 | 姿态 |
|---|---|---|
| 皇帝/帝王 | BACKGROUND CENTER / ELEVATED | 坐于高台，与其他人距离至少30米 |
| 妃嫔/贵族 | MIDGROUND / GROUND LEVEL | 独立低矮漆案，不与他人共桌 |
| 嬷嬷/侍女 | FOREGROUND / STANDING | 站立服侍，永远不坐 |

> **严禁**：不同礼制等级的角色共用同一张桌子或同一景深平面。

---

## 3. 🚫 背景封禁词协议 (Background Prohibition Lock) [MANDATORY]
**以下封禁词必须出现在每一个涉及宫廷场景的提示词中：**

```
BACKGROUND PROHIBITION: NO foreign sculptures, NO modern curtains, 
NO blue drapes, NO small intimate rooms, NO modern door knobs, 
NO modern pillows, NO modern food, NO round modern dining tables.
THE SETTING IS A VAST PUBLIC HALL with depth extending at least 
30 meters into the background.
```

### 宫宴专项封禁：
- 严禁圆形现代宴桌 → 必须是**低矮漆案 (Low Lacquer Table)**
- 严禁现代食物造型 → 必须是**青瓷食器与宋代食物**
- 严禁异域雕像 → 必须是**宋代建筑装饰（梁柱、屏风）**
- 严禁现代帷幔 → 必须是**宋代素色布幔或无布幔**

---

## 4. 🎬 情绪动机协议 (Emotion-First Protocol) [v9.9]
**动作必须是情绪积累的结果，不能是第一个发生的事件。**
- 三段式结构：**情绪建立 → 眼神对峙 → 物理爆发**
- 严禁"直接抓人"等无前置情绪的动作描述
- 阻尼演技 v3.0：严禁尖叫、发疯、夸张表情。用瞳孔收缩、下颌紧绷代替。

---

## 5. 💡 光影死锁协议 (Lighting Deadlock) [v9.0]
- 深夜场景：必须声明 `[TIME: MIDNIGHT]`，双色温（冷月光+暖烛光）
- 宫宴场景：必须声明 `[TIME: EVENING]`，暖红宫烛主光
- 严禁无指定光源的提示词（AI 会默认生成白天）
- 严禁"死黑"：通过 `Bright Silver Moonlight` 或 `Multiple Amber Lanterns` 保证可见度

---

## 6. ⚙️ 物理咬合协议 (Physical Binding Protocol) [v8.8]
- 人物与家具必须有接触阴影 (Contact Shadows)
- 服饰与家具接触点必须有受力形变（堆褶、压痕）
- 严禁人物"漂浮"于背景之上
- 关键道具必须锁定到具体手部动作（如：`GRIPPING IN RIGHT HAND`）

---

## 7. 📐 技术参数标准 (Technical Standard)
```
Technical: ARRI Alexa 65, 35mm, High Dynamic Range, 
Song Dynasty aesthetic, no text, no modern props. 
--ar 16:9 --v 6.1 --stylize 500
```

---

## 8. 🛡️ Harness 约束层 (Harness Constraint Layer)
- **[定向修复]**：若某一个宫格（如 P4）因为视觉穿帮被 Auditor 拦截，必须触发 `Targeted Repair`，仅重写 P4 的坐标与动作词，原封不动保留 P1-P3, P5-P9。
- **[时序伪切镜]**：P1 到 P9 的动作演绎必须符合 `VideoSegment` 的连续性逻辑。P(n) 结尾时的姿态必须自然过渡为 P(n+1) 起始姿态。
- **[模糊匹配宽容度]**：人物特征词必须具备同义词替换能力（如：`Crimson silk` 可与 `Dark red silk` 互通），配合质检引擎的 `Fuzzy Semantic Match`。
