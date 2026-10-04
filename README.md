# STM32-
STM32 4-Layer Minimal System Board design

# 🚀 [專案名稱]

![License](https://img.shields.io/badge/License-CC--BY--4.0-blue.svg)
![EDA](https://img.shields.io/badge/EDA-EasyEDA%20Pro-orange.svg)
![PCB Status](https://img.shields.io/badge/PCB-Manufacture%20Ready-brightgreen.svg)

[這裡用 1~2 句話簡述專案用途] 例如：基於 ESP32-S3 的高性能四層板設計，專為低噪聲與高訊號完整性優化，符合嘉立創 (JLCPCB) 生產規範。

---

## 📌 專案特點 (Features)

- **標準 4 層板架構**：具備完整的接地平面 (GND) 與電源平面 (3V3)，提供極佳的 EMC/EMI 表現與低噪聲環境。
- **極小化板型設計**：尺寸僅 [例如：50mm x 30mm]。
- **生產即戰力 (Production Ready)**：已通過完整原理圖 ERC 與 PCB DRC 檢查（0 Errors, 0 Warnings）。
- **完整物料備齊**：BOM 表已包含立創 (LCSC) 零件料號，方便直接進行 SMT 貼片打樣。

---

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

本專案在發布生產檔前已完成嚴格的工程驗證：

- **原理圖 ERC**：通過（0 錯誤，0 警告）。
- **PCB DRC**：依據 JLCPCB 四層板製程規範檢查通過（0 錯誤，0 警告）。

![DRC 檢查結果截圖](docs/drc_report.png)

---

## 📂 生產製造檔案 (Production Files)

所有生產所需檔案均已整理於 [`production/`](production/) 資料夾中，可直接上傳工廠打樣：

- 📦 **Gerber 預備包**：[`production/Gerber_v1.0.zip`](production/Gerber_v1.0.zip)
- 📊 **物料清單 (BOM)**：[`production/BOM.csv`](production/BOM.csv)
- 🌐 **互動式 BOM (iBOM)**：🔗 [點此開啟線上焊盤對照表](https://htmlpreview.github.io/?https://github.com/YourUsername/YourRepo/blob/main/production/ibom.html)
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
└── LICENSE                    # 開源硬體授權條款
