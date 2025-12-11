# Web Dragon - 3D 沉浸式网页展示项目

这是一个基于 **Three.js** 和 **WebGL** 构建的高性能 3D 网页实验合集。本项目展示了如何利用现代 Web 技术实现电影级的视觉特效、程序化场景生成、AR 风格的虚实融合以及 3D 网页游戏开发。

## 📂 项目演示 (Demos)

本项目包含多个独立的演示页面，每个页面都通过不同的技术手段展示了 3D 交互的可能性：

### 1. [phoenix.html](phoenix.html) - 神兽·凤凰 (Divine Phoenix)
**核心亮点：** 极致的视觉表现与交互。
*   **神性光照**：鼠标移动时会有神圣光源跟随，照亮模型细节。
*   **交互控制**：支持“栖息”、“巡游”、“疾飞”三种状态切换。
*   **涅槃特效**：点击“涅槃”按钮，触发全屏光爆与粒子重组特效 (Bloom + Tween)。
*   **灵视系统**：凤凰头部会跟随鼠标位置转动。

### 2. [phoenix_flight.html](phoenix_flight.html) - 神鸾御风 (Infinite Flight)
**核心亮点：** 程序化生成的无限 3D 场景。
*   **实时生成**：摒弃视频背景，使用 Three.js 代码实时生成无尽的 3D 环境。
*   **多场景切换**：
    *   🏮 **皇家长廊**：无尽的红墙金瓦与宫灯。
    *   🌃 **霓虹夜都**：赛博朋克风格的高速穿梭，随机生成的摩天大楼。
    *   ☁️ **云海仙境**：层层叠叠的体积感云雾。
*   **飞行物理**：模拟真实的飞行姿态，包括侧身翻滚 (Banking) 和气流颠簸。

### 3. [phoenix_world.html](phoenix_world.html) - 降临现世 (AR World)
**核心亮点：** 伪 AR 视觉增强与照片融合。
*   **环境融合**：将 3D 模型融入高清真实摄影背景（雪山、森林、冰岛、都市）。
*   **拟真视差**：通过鼠标移动制造背景与前景的视差效应，产生强烈的深度感。
*   **智能光照**：根据背景图片的色调，自动调整环境光和雾气颜色，使模型完美融入环境。

### 4. [game.html](game.html) - 深渊疾行 (Abyss Drift)
**核心亮点：** 第三人称 3D 动作小游戏。
*   **物理系统**：为静态模型编写了程序化移动逻辑，包括惯性滑行、身体前倾加速和侧身压弯。
*   **游戏机制**：控制原神角色（或备用发光体）在无尽平面上收集光球、躲避深渊尖刺。
*   **稳健加载**：包含自动错误检测与备用模型机制，确保游戏始终可玩。

### 5. [gallery.html](gallery.html) - 珍藏阁 (Model Gallery)
**核心亮点：** 通用 3D 资产浏览器。
*   **自动适配**：无论模型尺寸大小，加载时自动归一化缩放并居中对齐地面。
*   **智能驱动**：对于没有动画数据的静态骨骼模型（Rigged Model），系统会自动接管骨骼，赋予其呼吸、漂浮和注视的程序化动画。
*   **高质量渲染**：使用 PMREMGenerator 生成室内环境光，还原 PBR 材质质感。

---

## 🛠️ 技术栈 (Tech Stack)

*   **Core**: [Three.js (r160)](https://threejs.org/) - 核心 3D 引擎
*   **Loaders**: GLTFLoader - 模型加载
*   **Animation**: TWEEN.js - 补间动画与平滑过渡
*   **Post-processing**: UnrealBloomPass - 辉光与影视级后期特效
*   **Environment**: RoomEnvironment / PMREMGenerator - 基于物理的渲染 (PBR) 环境光

---

## 🚀 如何运行 (How to Run)

由于项目使用了 ES Modules 和外部 3D 资源加载，浏览器的安全策略（CORS）不允许直接双击 `.html` 文件打开。

**必须使用本地服务器运行：**

### 方法 A: 使用 VS Code (推荐)
1.  安装扩展 **Live Server**。
2.  右键点击任意 `.html` 文件，选择 **"Open with Live Server"**。

### 方法 B: 使用 Node.js
在项目根目录下运行：
```bash
npx http-server
# 或者
npx serve
```
然后访问终端显示的地址 (例如 `http://127.0.0.1:8080/phoenix.html`)。

### 方法 C: 使用 Python
```bash
python -m http.server
```

---

## 📂 目录结构

```
D:\WebProject\web_dragon\
├── *.glb                # 3D 模型资产 (Phoenix, Dragon, Characters...)
├── phoenix.html         # 交互式凤凰展示
├── phoenix_flight.html  # 3D 场景飞行模拟
├── phoenix_world.html   # AR 风格背景融合
├── game.html            # 3D 躲避小游戏
├── gallery.html         # 通用模型浏览器
└── README.md            # 项目说明文档
```

## ⚠️ 注意事项
*   如果遇到模型加载失败（黑屏或报错），请确保 `.glb` 文件与 HTML 文件在同一目录下。
*   部分模型可能较大，初次加载需要几秒钟，请留意屏幕上的加载提示。
