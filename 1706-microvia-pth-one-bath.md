title: "盲孔填充與通孔電鍍之同鍍槽電鍍技術之研究（許家福, 2017）"
type: paper
tags:

* electroplating

* copper-plating

* hdi-pcb

* microvia-filling

* plating-through-hole

* taguchi-method

* comsol-simulation

* paper
  created: 2026-11-12
  updated: 2026-11-12
  sources:

* "raw/papers/2017-許家福-盲孔填充與通孔電鍍之同鍍槽電鍍技術之研究.pdf"
  status: growing

# 盲孔填充與通孔電鍍之同鍍槽電鍍技術之研究

* **作者 / 指導教授**：許家福 (Chia-Fu Hsu) / 竇維平 博士 (Wei-Ping Dow)

* **發表單位 / 時間**：國立中興大學化學工程學系 博士學位論文 / 2017 年 6 月

* **英文題目**：*Study of Microvia Filling and Plating Through Hole in One Copper Plating Bath*

* **一句話總結**：結合電化學分析（CP/CV）、COMSOL 流場與多重物理耦合數值模擬、以及田口實驗設計法，成功開發出以「雙平整劑（NTBC + ABPV）」搭配中濃度銅酸比與低電流密度的單一鍍槽同鍍技術，同時達成盲孔填孔率 90% 與通孔均擲力 83%。

## 1. 核心問題與動機 (Motivation)

傳統高密度互連（HDI）印刷電路板製造中，盲孔填充（Microvia Filling）與通孔電鍍（Plating Through Hole, PTH）必須分開在兩個不同鍍槽與工序中執行，造成繁複的鑽孔、除膠渣（Desmear）、無電電鍍與水洗流程。然而兩者對電鍍液配方存在根本衝突：

* **填孔製程**：需「高銅低酸」（如 $0.88\text{ M CuSO}_4$ + $0.54\text{ M H}_2\text{SO}_4$），藉高銅離子供給與低導電度產生板面與孔底過電位差，達成孔底上移（Bottom-up）無空洞填充。若直接拿去鍍通孔，均擲力（TP）僅 **60%**。

* **通孔製程**：需「低銅高酸」（如 $0.24\text{ M CuSO}_4$ + $1.88\text{ M H}_2\text{SO}_4$），藉高導電度降低濃差極化與歐姆電位差，維持高均擲力。若直接拿去填盲孔，無法產生 Bottom-up 填充，填孔率（FP）僅 **10%**。

## 2. 核心方法與實驗設計 (Methodology)

### 2.1 電化學分析與雙平整劑系統

* **基礎添加劑**：$60\text{ ppm Cl}^-$（NaCl）、$200\text{ ppm PEG}$（抑制劑）、$1\text{ ppm SPS}$（加速劑）。

* **雙平整劑（Dual Levelers）**：$1\text{ ppm NTBC}$ + $1\text{ ppm ABPV}$。

  * **NTBC**：帶正電含氮雜環與 $-\text{NO}_2$ 官能基，吸附後會進行電化學開環消耗，具強烈抑制與對流相依性吸附（CDA）行為，但單獨使用易形成「W 型」沉積輪廓並產生鬆散/空洞結構。

  * **ABPV**：帶正電含氮雜環，透過凡德瓦力與電遷移吸附且**不易電化學消耗**，能修飾沉積輪廓為「平台式（Platform-like）」孔底上移，改善單用 NTBC 的結構缺陷。

  * 計時電位法（CP, $100\text{ rpm}$ vs. $1000\text{ rpm}$）顯示兩者具強烈獨立性與加成性（$\Delta\eta_3 = 18\text{ mV}$、$\Delta\eta_4 = 25\text{ mV}$）。

### 2.2 數值模擬（COMSOL）

* **盲孔流場模擬**：定義對流強度比值 $m = V_{\max}/Y_h$，建立其與旋轉圓盤電極（RDE）轉速之等效關係，並以板面與孔底對流強度差 $\Delta m = m_{\text{surface}} - m_{\text{bottom}}$ 解釋電鍍 $15\text{–}30\text{ min}$ 孔底表面積縮減（等效轉速由 $73\text{ rpm}$ 降至 $17\text{ rpm}$）如何誘發 V 型優先沉積與孔底上移。

* **通孔多重物理耦合模擬**：比較「陰極旋轉」與「空氣（曝氣）攪拌」。陰極旋轉因板兩側壓力相等（$P_1 = P_2$）導致通孔中心無顯著對流；空氣攪拌因兩側氣泡通過時間差造成壓力差，產生**間歇性反轉流（Periodic Reversal Flow）**，有效將 $\text{Cu}^{2+}$ 與添加劑送入孔心。

## 3. 關鍵實驗結果與最佳化配方 (Experiments & Results)

### 3.1 分別最佳化（田口實驗 L9 $3^4$ 直交表 + ANOVA）

| 製程類型 | 試片規格 | ANOVA 顯著因子與貢獻度 | 最佳條件組合 | 最佳品質表現 | 
| ----- | ----- | ----- | ----- | ----- | 
| **盲孔填孔** | 孔徑 $95/115\ \mu\text{m}$、深 $85\ \mu\text{m}$ | NTBC (**38.61%**)、SPS (**26.86%**)、電流密度 (**26.86%**)；ABPV (7.44%) | `A1B2C2D2`（1 ppm NTBC, 2 ppm ABPV, 2 ppm SPS, $1.62\text{ A}\cdot\text{dm}^{-2}$） | **FP = 97%** | 
| **通孔電鍍** | 孔徑 $250\ \mu\text{m}$、深 $1500\text{–}1600\ \mu\text{m}$ | 電流密度 (**70.96%**)、SPS (**22.46%**)；NTBC (4.57%)、ABPV (0.91%) 可忽略 | `A1B1C1D1`（1 ppm NTBC, 1 ppm ABPV, 1 ppm SPS, $1.29\text{ A}\cdot\text{dm}^{-2}$） | **TP = 104%** | 

* **熱信賴度測試**：所有通孔配方皆通過 IPC-TM-650 規範之 5 次漂錫熱衝擊測試（$28^\circ\text{C}\text{–}288^\circ\text{C}$，浸泡 $10\pm1\text{ s}$），且雙平整劑有效改善單用 NTBC 之孔口鬆散銅層。

* **氯離子分佈驗證（SEM/EDS）**：預浸泡高濃度 $\text{Cl}^-$ 後通電，證實電性排斥與電化學還原會使通孔內部 $\text{CuCl}$ 迅速消耗，板面因強對流仍保留較多 $\text{Cl}^-$。

### 3.2 同鍍槽同步電鍍最佳配方（第 6 章）

透過折衷銅酸濃度並微調 $\text{H}_2\text{SO}_4$、SPS 與電流密度，獲得最佳同鍍條件：

* **基礎鍍液**：$0.72\text{ M CuSO}_4$ + $1.32\text{ M H}_2\text{SO}_4$ + $60\text{ ppm Cl}^-$

* **有機添加劑**：$200\text{ ppm PEG}$ + $1.5\text{ ppm SPS}$ + $1\text{ ppm NTBC}$ + $1\text{ ppm ABPV}$

* **操作條件**：電流密度 $1.29\text{ A}\cdot\text{dm}^{-2}$、時間 $90\text{ min}$、空氣攪拌

* **同鍍成果**：

  * 盲孔填孔率：$\text{FP}_{\phi 95\ \mu\text{m}} = \mathbf{90\%}$（$\phi 115\ \mu\text{m}$ 為 $75\%$）

  * 通孔均擲力：$\text{TP} = \mathbf{83\%}$（孔口 $22.25\ \mu\text{m}$、孔中 $17.80\ \mu\text{m}$、孔底 $20.37\ \mu\text{m}$）

## 4. 限制與未來研究方向 (Limitations & Future Work)

1. **通孔中心耗盡與預測修正**：在傳統計時電位法用於通孔預測時，若未考慮高縱橫比通孔中心 $\text{Cu}^{2+}$ 濃度從 $0.24\text{ M}$ 遞減至 $0.20\text{ M}$ 的質傳效應，預測趨勢會與實際 TP 相違背；需改以雙濃度差 $\Delta\gamma = E_{100\text{ rpm},\ 0.20\text{ M}} - E_{1000\text{ rpm},\ 0.24\text{ M}}$ 評估。

2. **微流道實測需求**：受限於微米級孔內電位難以直接量測，未來建議結合微電極與微流道設計（Micro Channel）實測不同幾何下的孔內電位分佈。

3. **通孔填充（Through-hole Filling）模型**：現有模型尚未將實際添加劑反應動力學完整導入「通孔完全填滿」製程。

## 5. 知識圖譜關聯 (Connections)

* **相關概念**：\[\[copper-electroplating-additives\]\]、\[\[microvia-filling-and-pth\]\]、\[\[taguchi-method-in-electroplating\]\]

* **全局綜述**：\[\[overview\]\]