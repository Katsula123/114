---
title: "電鍍銅有機添加劑與吸附競爭機制"
type: concept
tags:
  - electroplating
  - additives
  - cda
  - ceac
  - concept
created: 2026-11-12
updated: 2026-11-12
sources:
  - "[[1706-microvia-pth-one-bath]]"
status: growing
---

# 電鍍銅有機添加劑與吸附競爭機制

在酸性硫酸銅電鍍系統中，單靠銅離子擴散無法滿足高縱橫比通孔或無空洞盲孔填充的需求，必須仰賴微量氯離子與三類有機添加劑的協同及競爭吸附行為（來源：[[1706-microvia-pth-one-bath]]）。

## 1. 四大核心組分與功能

| 類別 | 代表物質 | 核心機制與行為 | 對流相依性 / 關鍵影響 |
| :--- | :--- | :--- | :--- |
| **氯離子** | $\text{Cl}^-$（來源：NaCl/HCl） | 取代 $\text{Cu}^{2+}$ 水分子形成 $\text{Cu-Cl-Cu}$ 內球架橋加速電子傳遞；並作為抑制劑與加速劑吸附於陰極的「錨定橋樑」 | 孔內易受電性排斥與消耗而形成濃度梯度；過高濃度會析出 $\text{CuCl}$ 阻礙還原 |
| **抑制劑 (Suppressor)** | **PEG**（聚乙二醇） | 單獨存在無抑制力，需透過 $\text{Cl}^-$ 形成 $\text{PEG-Cu}^+-\text{Cl}^-$ 圓球狀複合阻障層抑制銅沉積 | 分子量越大極化越強；在強對流（板面/孔口）覆蓋率高，且易被 SPS 取代 |
| **加速劑 (Accelerator)** | **SPS** / **MPS** | $-\text{S-S}-$ 鍵還原為 $-\text{SH}$，與 $\text{Cu}^+$ 形成 $\text{Cu(I)-thiolate}$ 錯合物並藉 $\text{Cl}^-$ 架橋加速還原 | 可於低對流區（盲孔底部、通孔中心）累積並取代 PEG |
| **平整劑 (Leveler)** | **NTBC**、**ABPV**、JGB、BTA | 帶正電含氮雜環化合物，透過電遷移與凡德瓦力優先吸附於高電流密度區（孔口、凸點），抑制過度沉積 | 決定電鍍系統是否具備顯著 **CDA 行為** 與沉積輪廓平順度 |

## 2. 雙平整劑協同效應（NTBC + ABPV）

根據 [[1706-microvia-pth-one-bath]] 的計時電位法與金相實驗，在 `PEG-Cl⁻-SPS` 系統中同時加入 **1 ppm NTBC** 與 **1 ppm ABPV** 具有強烈獨立性與加成性：
- **NTBC 的特性與缺陷**：含雙 $-\text{NO}_2$ 與四唑鹽環，吸附後會發生電化學開環還原消耗，使系統具備強烈的 CDA 填孔能力；但單獨使用時初期沉積呈「W 型」，且極易夾雜於高電流密度區銅層中導致孔口鬆散或熱衝擊後出現微孔洞。
- **ABPV 的互補角色**：結構含帶正電含氮雜環，**不易參與電化學消耗反應**。它能抑制孔口沉積並使盲孔呈現「平台式（Platform-like）」孔底上移，同時大幅改善 NTBC 所造成的銅層鬆散問題。

## 3. 經典填孔電鍍機理比較
1. **ACD（Adsorption Consumption Diffusion）**：平整劑/抑制劑在擴散至孔底過程中被消耗，形成孔口高抑制、孔底低抑制的濃度梯度（適合次微米/奈米級特徵）。
2. **CEAC（Curvature Enhanced Accelerator Coverage）**：隨著孔底幾何面積縮減，吸附於表面的加速劑（SPS）無法消散而濃縮累積，引爆孔底加速（但也易在後期產生孔頂凸塊 Bump）。
3. **AA（Accelerator Accumulation）**：在脈衝與反脈衝（PPR）與缺氧環境下，$\text{Cu(I)-thiolate}$ 錯合物不易被氧化而在高縱橫比孔底累積。
4. **CDA（Convection-dependent Adsorption）**：由強迫對流造成板面與孔底的對流強度差，進而主導 $\text{Cl}^-$、PEG 與平整劑的競爭吸附。在微米級 PCB 盲孔（如 $95\ \mu\text{m}$）與通孔中，CDA 是決定填孔率與均擲力的關鍵機制（來源：[[1706-microvia-pth-one-bath]]）。

## 4. 相關頁面
- [[1706-microvia-pth-one-bath]]
- [[microvia-filling-and-pth]]
