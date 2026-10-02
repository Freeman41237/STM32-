# STM32-
# ⚡ STM32F407 最小系統板設計 (4 Layer PCB)

基於 STM32F 主控，設計了電源、串口通訊與最小系統電路，

---

## 🖼️ 3D 外觀與電路圖

![PCB 3D 外觀](把這裡換成你在第二步複製的圖片網址)

---

## ⚙️ 這塊板子有什麼功能？

* **主晶片**：STM32F407VET6
* **供電介面**：Type-C 介面（5V 輸入，透過 LDO 轉成 3.3V 給單片機）
* **電腦通訊**：板載 CH340X 晶片，插上 Type-C 就能跟電腦傳資料
* **其他配置**：
  * 8MHz 外部高精度晶振
  * 按鍵（復位按鍵 + 下載模式切換按鍵）
  * LED 燈（電源指示燈 + 測試點燈）
  * 排針引出常用 IO 引腳，方便以後接感測器

---

## 🛠️ 我的 Layout 設計重點

1. **採用 4 層板結構**：
   * 頂層/底層：走信號線與擺放零件
   * 中間地層 (GND)：整片鋪銅，減少電磁干擾 (EMI)
   * 中間電源層 (3.3V)：方便給各零件供電
2. **電源安全**：5V 主要電源線特別加寬（20mil），防止發熱。
3. **電容近放**：去耦電容緊貼晶片引腳，保證供電穩定。

## 📐 硬體規格 (Hardware Specifications)

| 參數 | 規格細節 |
| :--- | :--- |
| **主控晶片 (MCU)** | [例如：ESP32-S3-WROOM-1 / STM32F4] |
| **輸入電源** | 5V DC (透過 USB Type-C 或外接端子) |
| **板層結構** | 4 層板 (Top, GND, 3V3, Bottom) |
| **總板厚度** | 1.6258 mm (標準板厚) |
| **成品銅厚** | 1 oz (0.035 mm) |
| **最小線寬 / 線距**| 6 mil / 6 mil |

---

## 🥞 PCB 層疊結構 (Stackup)

採用 **嘉立創 JLCPCB `JLC041611-7628 (Default)`** 標準四層板疊層範本：

| 圖層 (Layer) | 類型 | 材質 | 厚度 (mm) | 作用與說明 |
| :--- | :--- | :--- | :--- | :--- |
| **頂層 (L1 - Top)** | 銅箔 (Copper) | 外層銅箔 | 0.035 | 訊號走線與高速線路 |
| 介質層 1 (Dielectric 1) | 絕緣基材 | 7628 半固化片 | 0.2104 | 絕緣介質 |
| **內層 1 (L2 - GND)** | 銅箔 (Copper) | 內層銅箔 | 0.035 | **完整接地參考平面 (GND)** |
| 介質層 2 (Dielectric 2) | 絕緣基材 | 1.1mm FR-4 板芯 | 1.065 | 主核心基板 |
| **內層 2 (L3 - 3V3)** | 銅箔 (Copper) | 內層銅箔 | 0.035 | **3.3V 主電源平面** |
| 介質層 3 (Dielectric 3) | 絕緣基材 | 7628 半固化片 | 0.2104 | 絕緣介質 |
| **底層 (L4 - Bottom)**| 銅箔 (Copper) | 外層銅箔 | 0.035 | 電源走線與輔助佈線 |

---

## 🔍 設計驗證與品質 (Quality Verification)

- **原理圖 ERC**：通過（0 錯誤，0 警告）。
- **PCB DRC**：依據 JLCPCB 四層板製程規範檢查通過（0 錯誤，0 警告）。

![DRC 檢查結果截圖](docs/drc_report.png)

---

## 📂 生產製造檔案 (Production Files)


- 📦 **Gerber 預備包**：[`production/Gerber_v1.0.zip`](production/Gerber_v1.0.zip)
- 📊 **物料清單 (BOM)**：[`production/BOM.csv`](production/BOM.csv)
- 📄 **原理圖 PDF**：[`docs/schematic.pdf`](docs/schematic.pdf)

---

## 📁 專案目錄結構 (Repository Structure)

```text
├── docs/                      # 相關圖檔與文件
│   ├── drc_report.png         # DRC 零錯誤驗證截圖
│   ├── stackup.png            # 層疊結構截圖
│   └── schematic.pdf          # 原理圖 PDF 檔
├── production/                # 工廠打樣與生產檔
│   ├── Gerber_v1.0.zip        # Gerber 與鑽孔檔案包
│   ├── BOM.csv                # 含 LCSC 料號的零件清單
│   └── ibom.html              # 互動式 HTML BOM
├── README.md                  # 專案說明文件



