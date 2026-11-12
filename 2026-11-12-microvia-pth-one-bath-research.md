---
title: "專題研究筆記：HDI PCB 盲孔填充與通孔電鍍之同鍍槽技術機制與最佳化"
type: research-note
tags:
  - electroplating
  - hdi-pcb
  - microvia-filling
  - plating-through-hole
  - taguchi-method
created: 2026-11-12
updated: 2026-11-12
wiki_sources:
  - "[[overview]]"
  - "[[1706-microvia-pth-one-bath]]"
  - "[[copper-electroplating-additives]]"
  - "[[microvia-filling-and-pth]]"
  - "[[taguchi-method-in-electroplating]]"
---

# 專題研究筆記：HDI PCB 盲孔填充與通孔電鍍之同鍍槽技術機制與最佳化

> **知識邊界聲明**：本筆記正文 **100% 僅依據現有 `wiki/` 知識庫內容** 撰寫，未混入任何尚未收錄於 `wiki/` 的外部文獻內容。文末所列之「建議參考文獻」僅供後續下載並依 `ingest` 流程擴充知識庫使用。

---

## 1. 研究背景與核心工程衝突

在高密度互連（HDI）印刷電路板製造中，傳統製程必須將**盲孔填充（Microvia Filling）**與**通孔電鍍（Plating Through Hole, PTH）**拆分為兩道獨立工序，造成重複鑽孔、除膠渣（Desmear）、無電電鍍與多道水洗成本（來源：[[1706-microvia-pth-one-bath]]、[[overview]]）。

兩者之所以難以在單一鍍槽同步完成，源自其對電解液組成與流場質傳的本質衝突（來源：[[microvia-filling-and-pth]]）：

- **品質定義差異**：
  - 盲孔填孔率（Filling Performance, $\text{FP}$）：
    $$\text{FP} = \frac{H_2}{H_1} \times 100\%$$
    目標為孔底上移（Bottom-up）之無空洞（Void-free）與無隙縫（Seam-free）填充。
  - 通孔均擲力（Throwing Power, $\text{TP}$）：
    $$\text{TP} = \frac{(C_1 + C_2)/2}{(H_1 + H_2 + H_3 + H_4)/4} \times 100\%$$
    目標為抑制孔口過度沉積的「狗骨頭（Dog-bone）」效應，維持通孔側壁厚度均一。
- **配方衝突實證**：
  - 填孔最佳配方（高銅低酸：$0.88\text{ M CuSO}_4 + 0.54\text{ M H}_2\text{SO}_4$）雖可達 $\text{FP} = 97\%$，但直接用於通孔時 $\text{TP}$ 僅剩 **$60\%$**。
  - 通孔最佳配方（低銅高酸：$0.24\text{ M CuSO}_4 + 1.88\text{ M H}_2\text{SO}_4$）雖可達 $\text{TP} = 104\%$，但用於盲孔時無法產生 Bottom-up 填充，$\text{FP}$ 僅 **$10\%$**（來源：[[1706-microvia-pth-one-bath]]、[[microvia-filling-and-pth]]）。

---

## 2. 有機添加劑與對流相依性吸附（CDA）機制

在基礎酸性硫酸銅系統中，各組分透過協同與競爭吸附決定沉積輪廓（來源：[[copper-electroplating-additives]]）：

1. **氯離子（$\text{Cl}^-$，$60\text{ ppm}$）**：透過內球架橋（$\text{Cu-Cl-Cu}$）加速電子傳遞，同時作為抑制劑與加速劑吸附的錨定橋樑；在通孔電鍍過程中受電性排斥與還原消耗，使孔內 $\text{Cl}^-$ 濃度顯著低於強對流的板面。
2. **抑制劑（PEG，$200\text{ ppm}$）**：需藉由 $\text{Cl}^-$ 形成 $\text{PEG-Cu}^+-\text{Cl}^-$ 複合阻障層，於強對流處（板面、孔口）覆蓋率高，且可被加速劑取代。
3. **加速劑（SPS，$1\text{–}2\text{ ppm}$）**：$-\text{S-S}-$ 鍵還原為 $-\text{SH}$ 後形成 $\text{Cu(I)-thiolate}$ 錯合物，於低對流區（盲孔底部、通孔中心）累積並加速銅還原。
4. **雙平整劑（Dual Levelers：NTBC + ABPV）**：
   - **NTBC**：帶正電含氮雜環與 $-\text{NO}_2$ 官能基，吸附後進行電化學開環還原消耗，賦予系統強烈 **CDA（Convection-dependent Adsorption）** 能力；但單獨使用易產生「W 型」初期輪廓與孔口鬆散銅層。
   - **ABPV**：帶正電含氮雜環，透過凡德瓦力與電遷移吸附且**不易電化學消耗**，能將輪廓修飾為「平台式（Platform-like）」孔底上移，與 NTBC 具獨立性與加成性（計時電位法 $\Delta\eta_3 = 18\text{ mV}$、$\Delta\eta_4 = 25\text{ mV}$），大幅改善銅層結構緻密性（來源：[[copper-electroplating-additives]]、[[1706-microvia-pth-one-bath]]）。

---

## 3. 流場與多重物理耦合模擬洞見

透過 COMSOL 數值模擬（Navier-Stokes、Nernst-Planck 與 Butler-Volmer 耦合），揭示盲孔與通孔的質傳關鍵（來源：[[1706-microvia-pth-one-bath]]、[[microvia-filling-and-pth]]）：

- **盲孔流場與等效轉速**：定義對流強度比值 $m = V_{\max}/Y_h$ 並換算旋轉圓盤電極（RDE）等效轉速。當電鍍進行至 $15\text{–}30\text{ min}$ 時，盲孔底部表面積縮減使孔底等效轉速由 $73\text{ rpm}$ 降至 $17\text{ rpm}$，板面與孔底對流強度差 $\Delta m = m_{\text{surface}} - m_{\text{bottom}}$ 擴大，促使 SPS 優先於孔底角落累積並啟動 V 型孔底上移。
- **通孔攪拌機制比較**：
  - **陰極旋轉系統**：板兩側壓力對稱（$P_1 = P_2$），軸向流場侷限於孔口，通孔中心（$0\text{ to }\pm 600\ \mu\text{m}$）幾乎無對流，造成 $\text{Cu}^{2+}$ 嚴重耗盡。
  - **空氣（曝氣）攪拌系統**：兩側氣泡通過孔口時間不同步，製造週期性壓力差（$P_1 > P_2$ 與 $P_1 < P_2$ 交替），誘發**間歇性反轉流（Periodic Reversal Flow）**，將 $\text{Cu}^{2+}$ 與添加劑有效送入孔心，使 `PEG-Cl⁻-SPS` 覆蓋率差異壓低至 $\Delta\theta \approx 0.08$（$\text{TP}$ 達 $95.2\%\text{–}98.4\%$）。
- **計時電位法修正**：高縱橫比通孔中心 $\text{Cu}^{2+}$ 會由 $0.24\text{ M}$ 耗盡至 $0.20\text{ M}$，預測 $\text{TP}$ 必須改採雙濃度差指標：
  $$\Delta\gamma = E_{100\text{ rpm},\ 0.20\text{ M CuSO}_4} - E_{1000\text{ rpm},\ 0.24\text{ M CuSO}_4}$$

---

## 4. 田口實驗設計法（L9）與同鍍槽最佳化配方

採用 L9 ($3^4$) 直交表搭配望目特性訊噪比：
$$S/N = -10\log\left[(\bar{y} - m_{\text{target}})^2 + S^2\right]$$
ANOVA 變異數分析明確指出兩製程的因子貢獻度差異（來源：[[taguchi-method-in-electroplating]]）：

| 控制因子 | 盲孔填孔貢獻度 | 通孔均擲力貢獻度 | 同鍍槽調校策略 |
| :--- | :--- | :--- | :--- |
| **A: NTBC ($1\text{–}3\text{ ppm}$)** | **38.606%** | 4.573% | 固定低濃度 **$1\text{ ppm}$**（高濃度使 FP 大降 34%） |
| **B: ABPV ($1\text{–}3\text{ ppm}$)** | 7.441% | 0.914% | 固定 **$1\text{ ppm}$**（修飾輪廓、消除鬆散銅層） |
| **C: SPS ($1\text{–}3\text{ ppm}$)** | **26.859%** | **22.462%** | 精準微調至 **$1.5\text{ ppm}$**（避免過高致孔洞） |
| **D: 電流密度 ($1.29\text{–}1.94\text{ ASD}$)** | **26.857%** | **70.959%** | 採低電流密度 **$1.29\text{ A}\cdot\text{dm}^{-2}$** |

### 同鍍槽最佳化配方與實測表現
- **基礎鍍液**：$0.72\text{ M CuSO}_4$ + $1.32\text{ M H}_2\text{SO}_4$ + $60\text{ ppm Cl}^-$
- **有機添加劑**：$200\text{ ppm PEG}$ + $1.5\text{ ppm SPS}$ + $1\text{ ppm NTBC}$ + $1\text{ ppm ABPV}$
- **操作條件**：$1.29\text{ A}\cdot\text{dm}^{-2}$、$90\text{ min}$、空氣攪拌
- **同步成果**：盲孔填孔率 $\text{FP}_{\phi 95\ \mu\text{m}} = \mathbf{90\%}$（$\phi 115\ \mu\text{m}$ 為 $75\%$），通孔均擲力 $\text{TP} = \mathbf{83\%}$（孔口 $22.25\ \mu\text{m}$、孔中 $17.80\ \mu\text{m}$、孔底 $20.37\ \mu\text{m}$）（來源：[[1706-microvia-pth-one-bath]]）。

---

## 建議參考文獻（待整理至 Wiki，點擊即可下載）

> 以下文獻由網路搜尋取得，**尚未納入 `wiki/` 知識庫**，因此未引用於上述正文與簡報中。建議點擊連結下載 PDF 後存入 `raw/papers/`，再執行 `ingest` 流程擴充知識庫：

1. **[Next Generation Pattern Electroplating Process for Microvia Filling and Through Hole](https://www.electronics.org/system/files/technical_resource/E8%26S18_02.pdf)** — Mark Lefebvre, Elie Najjar, Luis Gomez, Leon Barstad（含 Pattern Plating 同時填盲孔與鍍通孔之工業級配方與 RDT 指標分析，點擊直接下載 PDF）。
2. **[Effect of Chemical and Processing Parameters on Hole Filling](https://www.electronics.org/system/files/technical_resource/E5&S19_01.pdf)** — 探討硫酸銅、平整劑濃度、前處理程序與 IPC 2.6.8 熱衝擊信賴度之製程參數最佳化（點擊直接下載 PDF）。
3. **[Investigation of Through-Hole Copper Electroplating with Methyl Orange as A Special Leveler](https://electrochem.xmu.edu.cn/CN/article/downloadArticleFile.do?attachType=PDF&id=10882)** — Jia-Ying Xu 等人，《電化學 (*J. Electrochem.*)》2022（研究具雙官能基之特殊平整劑甲基橙簡化通孔電鍍添加劑系統，點擊直接下載 PDF）。
4. **[Synthesis and Evaluation of Organic Additives for Copper Electroplating](https://jelectrochem.xmu.edu.cn/cgi/viewcontent.cgi?article=3408&context=journal)** — 《電化學 (*J. Electrochem.*)》綜述文章（系統性回顧抑制劑、光亮劑與平整劑分子設計及電化學評估法，點擊直接下載 PDF）。
5. **[2H-tetrazole-5-thione as a leveler for acid copper electroplating of microvias](https://pdfs.semanticscholar.org/b17f/5f211be00ef0e1432a3dd2ea7378565ceae1.pdf)** — 結合電化學測試（GM/LSV/EIS）與 DFT 量子化學計算探討新型含氮雜環平整劑與抑制劑之協同效應（點擊直接下載 PDF）。
