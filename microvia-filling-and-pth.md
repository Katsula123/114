---
title: "盲孔填充、高縱橫比通孔電鍍與同鍍槽權衡"
type: concept
tags:
  - electroplating
  - microvia-filling
  - plating-through-hole
  - fluid-dynamics
  - concept
created: 2026-11-12
updated: 2026-11-12
sources:
  - "[[1706-microvia-pth-one-bath]]"
status: growing
---

# 盲孔填充、高縱橫比通孔電鍍與同鍍槽權衡

在 HDI 印刷電路板製造中，盲孔填充（Microvia Filling）與通孔電鍍（PTH）分別對應不同的幾何邊界與質傳挑戰（來源：[[1706-microvia-pth-one-bath]]）。

## 1. 品質評估指標
- **填孔率（Filling Performance, FP）**：盲孔中心銅沉積高度相對於板面基準高度的百分比（$\text{FP} = H_2 / H_1 \times 100\%$）。目標為無空洞（Void-free）且無隙縫（Seam-free）的孔底上移（Bottom-up）填充。
- **均擲力（Throwing Power, TP）**：通孔中心側壁銅厚相對於孔口/板面平均銅厚的百分比（$\text{TP} = [(C_1+C_2)/2] / [(H_1+H_2+H_3+H_4)/4] \times 100\%$）。目標為避免「狗骨頭（Dog-bone）」效應，維持孔內外厚度均一。

## 2. 兩者的物理與電化學衝突

| 比較維度 | 盲孔填充 (Microvia Filling) | 通孔電鍍 (PTH, 高縱橫比) | 同鍍槽折衷設計 (One-Bath) |
| :--- | :--- | :--- | :--- |
| **典型幾何** | 孔徑 $95\text{–}115\ \mu\text{m}$、深 $85\ \mu\text{m}$ | 孔徑 $250\ \mu\text{m}$、深 $1500\text{–}1600\ \mu\text{m}$ | 同時包含上述盲孔與通孔 |
| **銅酸比例** | 高銅低酸（$0.88\text{ M Cu}^{2+}$ / $0.54\text{ M H}_2\text{SO}_4$） | 低銅高酸（$0.24\text{ M Cu}^{2+}$ / $1.88\text{ M H}_2\text{SO}_4$） | 中濃度平衡（$0.72\text{ M Cu}^{2+}$ / $1.32\text{ M H}_2\text{SO}_4$） |
| **流場需求** | 需板面與孔底存在**顯著對流差異**（$\Delta m$ 大）以驅動 CDA | 需將銅離子與添加劑有效送入孔心，**縮小孔內外濃度/覆蓋率差** | 空氣攪拌（產生間歇反轉流）+ 低電流密度（$1.29\text{ A}\cdot\text{dm}^{-2}$） |
| **關鍵添加劑** | 高度依賴平整劑（NTBC 38.6%）與 SPS/電流密度 | 高度依賴電流密度（71.0%）與 SPS（22.5%），對平整劑較不敏感 | 雙平整劑（1 ppm NTBC + 1 ppm ABPV）+ 1.5 ppm SPS |
| **實證極限** | 單獨最佳化 **FP = 97%**（若用於通孔 TP 僅 60%） | 單獨最佳化 **TP = 104%**（若用於盲孔 FP 僅 10%） | 同步達成 **FP = 90%**（$\phi 95\ \mu\text{m}$）與 **TP = 83%** |

## 3. 流場攪拌機制對通孔質傳的決定性影響
根據 [[1706-microvia-pth-one-bath]] 第 5 章的多重物理耦合數值模擬（Navier-Stokes + Nernst-Planck + Butler-Volmer）：
- **陰極旋轉系統**：實驗板兩側壓力對稱（$P_1 = P_2$），軸向流場被限制於孔口附近，通孔中心（$0\text{ to }\pm 600\ \mu\text{m}$）幾乎無對流，導致 $\text{Cu}^{2+}$ 嚴重耗盡。
- **空氣（曝氣）攪拌系統**：兩側氣泡通過孔口的時間不同步，製造出週期性的壓力差（$P_1 > P_2$ 與 $P_1 < P_2$ 交替），在孔內誘發**間歇性反轉流（Periodic Reversal Flow）**，將銅離子與添加劑穩定輸送至孔心，搭配 `PEG-Cl⁻-SPS` 競爭吸附將覆蓋率差異壓低至 $\Delta\theta \approx 0.08$。

## 4. 相關頁面
- [[1706-microvia-pth-one-bath]]
- [[copper-electroplating-additives]]
- [[taguchi-method-in-electroplating]]
