# Lecture VR Shooting Game

大學工作坊教學專案 — 使用 Unity 開發科幻風格 VR 射擊遊戲，同時支援 PC 與 HTC Vive 操作。

## 專案簡介

本專案是為大學短期工作坊設計的 VR 遊戲開發教學專案，帶領學員建立一款科幻場景的第一人稱射擊遊戲。玩家使用科幻武器射擊不斷逼近的變異怪物，體驗從 PC 到 VR 的完整遊戲開發流程。

相較於基礎版教學，本專案採用更成熟的程式架構 — 輸入系統抽象化、XML 文件註解、元件化設計，適合有一定基礎的學員進一步學習。

## 技術資訊

| 項目 | 版本/內容 |
|---|---|
| Unity | 2017.3.1f1 |
| 語言 | C# |
| VR 支援 | SteamVR（HTC Vive） |
| 建立時間 | 2020 年 5 月 |

## 教學大綱與學習目標

### 核心概念

- **Raycast 射擊系統** — 使用射線偵測實現武器射擊，搭配射速控制與傷害計算
- **NavMesh 敵人 AI** — 敵人自動尋路追蹤玩家，具備移動、停止、攻擊、死亡等狀態切換
- **動畫事件系統** — 透過 Animation Event 與 SendMessageUpwards 實現攻擊判定時機
- **玩家血量系統** — 玩家可受到敵人攻擊傷害，血量歸零觸發 Game Over
- **敵人生成器** — 使用可設定的生成點陣列與間隔時間動態生成敵人

### 進階內容

- **輸入系統抽象化** — 將 PC 滑鼠輸入（StandardInput）與 VR 控制器輸入（ViveInput）分離，透過共用 `Gun.SetFireState()` 介面統一控制射擊
- **SteamVR Input 系統** — 使用 SteamVR 2.0 的 Action-based Input 綁定 VR 控制器操作
- **特效管理** — 槍口火焰、場景擊中、敵人擊中等不同特效的生成與自動銷毀
- **動畫混合與過渡** — 使用 CrossFade 實現動畫間的平滑過渡

### 學習成果

完成本工作坊後，學員將能夠：

1. 理解 Unity 專案架構與 VR 開發基本流程
2. 使用 C# 實作遊戲核心邏輯，包含射擊、AI、血量等系統
3. 設計可擴展的輸入系統架構，支援多種輸入裝置
4. 使用 NavMesh 建立具備多種行為狀態的敵人 AI
5. 整合 SteamVR 2.0 開發 HTC Vive 應用程式
6. 運用動畫事件實現精準的攻擊判定時機

## 專案結構

```
Assets/
├── LectureResources/           # 教學用資源
│   ├── Scripts/                # 遊戲腳本（含中文註解）
│   ├── Prefabs/                # 預製物件（敵人、武器、環境、BGM）
│   ├── Effect/                 # 特效（槍口火焰、擊中效果）
│   └── Scenes/                 # 場景（Example、MyVRGame）
├── GameResources/              # 遊戲素材
│   ├── Biomechanical_Mutant/   # 變異怪物模型與動畫
│   ├── Free LowPoly SciFi Pack/ # 科幻場景素材
│   ├── Sci-Fi Weapons/         # 科幻武器模型
│   ├── JMO Assets/             # WarFX 戰鬥特效
│   ├── GunSound/               # 槍械音效
│   ├── Monster SFX/            # 怪物音效
│   └── Ultra SF Game Audio.../  # 環境背景音
├── SteamVR/                    # SteamVR Plugin
└── SteamVR_Input/              # SteamVR Input 設定
```

### 腳本說明

| 腳本 | 說明 |
|---|---|
| `Gun.cs` | 射擊系統 — Raycast 偵測、特效生成、音效播放、射速控制 |
| `Enemy.cs` | 敵人 AI — NavMesh 尋路、攻擊/移動/死亡狀態機、血量系統 |
| `Player.cs` | 玩家系統 — 血量管理與死亡處理 |
| `Spawner.cs` | 敵人生成器 — 可設定生成點、間隔時間、生成物件 |
| `StandardInput.cs` | PC 輸入 — 滑鼠視角控制與射擊觸發 |
| `ViveInput.cs` | VR 輸入 — SteamVR Action 綁定 HTC Vive 控制器 |
| `AttackEventReciver.cs` | 動畫事件接收器 — 接收攻擊動畫事件並向上傳遞傷害 |

## 授權

本專案為教學用途。第三方資源（SteamVR、Asset Store 素材包）各自遵循其原始授權條款。
