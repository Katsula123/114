---
title: "田口實驗設計法在電鍍製程最佳化之應用"
type: concept
tags:
  - taguchi-method
  - anova
  - electroplating
  - doe
  - concept
created: 2026-11-12
updated: 2026-11-12
sources:
  - "[[1706-microvia-pth-one-bath]]"
status: growing
---

# 田口實驗設計法在電鍍製程最佳化之應用

電鍍銅製程牽涉多種有機添加劑與操作參數間的複雜交互作用。透過田口實驗設計法（Taguchi Method）搭配 L9 ($3^4$) 直交表與變異數分析（ANOVA），能以極少實驗次數（9 組）量化各控制因子對品質特性的貢獻度並預測最佳參數組合（來源：[[1706-microvia-pth-one-bath]]）。

## 1. 品質特性與 S/N 比選擇
- **望目特性（Nominal-the-better）**：在盲孔填孔（目標 $\text{FP} = 100\%$）與通孔均擲力（目標 $\text{TP} = 100\%$）最佳化中，皆採用望目特性公式評估訊噪比（S/N ratio）：
  $$S/N = -10\log\left[(\bar{y} - m_{\text{target}})^2 + S^2\right]$$
- **可信度驗證準則**：確認實驗的實際 S/N 比與疊加預測值差異若小於 $3\text{ dB}$，即代表該直交表設計（假設因子間無強交互作用）具高度可信度。在 [[1706-microvia-pth-one-bath]] 中，填孔確認實驗差異為 $1.913\text{ dB}$（$-9.909$ vs. $-7.996\text{ dB}$），通孔差異僅 $0.075\text{ dB}$（$40.338$ vs. $40.413\text{ dB}$）。

## 2. 因子貢獻度比較（盲孔 vs. 通孔）
固定基礎液（$\text{PEG} + \text{Cl}^-$）與對流強度後，針對四個控制因子（A: NTBC、B: ABPV、C: SPS、D: 電流密度）進行 ANOVA，揭示兩製程的敏感度差異：

| 控制因子 | 盲孔填孔貢獻度 (ANOVA) | 通孔均擲力貢獻度 (ANOVA) | 同鍍槽設計啟示 |
| :--- | :--- | :--- | :--- |
| **A: NTBC (1–3 ppm)** | **38.606%**（最顯著，高濃度使 FP 大降 34%） | 4.573%（可忽略） | 固定於低濃度 **1 ppm**，兼顧填孔與不傷結構 |
| **B: ABPV (1–3 ppm)** | 7.441%（不顯著，但可修飾沉積輪廓） | 0.914%（可忽略） | 固定於 **1 ppm**，協助消除 NTBC 鬆散缺陷 |
| **C: SPS (1–3 ppm)** | **26.859%**（顯著） | **22.462%**（顯著） | 同鍍槽需精準微調（最佳為 **1.5 ppm**，過高會致孔洞） |
| **D: 電流密度 (1.29–1.94 ASD)** | **26.857%**（顯著） | **70.959%**（壓倒性主導因子） | 同鍍槽優先採用低電流密度 **$1.29\text{ A}\cdot\text{dm}^{-2}$** |

## 3. 相關頁面
- [[1706-microvia-pth-one-bath]]
- [[microvia-filling-and-pth]]
