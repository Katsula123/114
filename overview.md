---
title: "研究知識庫全局綜述與核心脈絡"
type: overview
tags:
  - overview
  - electroplating
  - hdi-pcb
created: 2026-11-12
updated: 2026-11-12
sources:
  - "[[1706-microvia-pth-one-bath]]"
status: growing
---

# 研究知識庫全局綜述與核心脈絡

本頁彙整目前知識庫所涵蓋的研究脈絡、核心技術發現與待探索問題，隨著 `raw/` 中新文獻的吸收持續演進。

## 1. HDI PCB 電鍍銅與同鍍槽技術
- **核心挑戰**：盲孔填充（高銅低酸、依賴對流差驅動 CDA）與高縱橫比通孔電鍍（低銅高酸、依賴高導電與間歇反轉流縮小孔內外差異）在電鍍液配方上存在本質衝突（來源：[[1706-microvia-pth-one-bath]]）。
- **突破方向**：透過「雙平整劑（NTBC + ABPV）」互補協同效應，搭配中濃度銅酸配方（$0.72\text{ M CuSO}_4$ / $1.32\text{ M H}_2\text{SO}_4$）、低電流密度（$1.29\text{ A}\cdot\text{dm}^{-2}$）與空氣攪拌，已證實可在單一鍍槽中同步達成 **90% 盲孔填孔率** 與 **83% 通孔均擲力**（詳見 [[microvia-filling-and-pth]]、[[copper-electroplating-additives]]）。
- **製程最佳化方法論**：[[taguchi-method-in-electroplating]] 證實電流密度與 SPS 濃度同時主導填孔與通孔品質，是同鍍槽調校的兩大核心槓桿。

## 2. 待探索的開放問題 (Open Questions)
- 如何在微米級通孔與盲孔內部直接量測實際電位分佈（例如透過微流道與微電極設計）？
- 將實際添加劑反應動力學完整導入「通孔完全填滿（Through-hole Filling）」的數值模型。
- 其他領域文獻（如 LLM 相關研究）待後續存入 `raw/` 後擴展對應分類。
