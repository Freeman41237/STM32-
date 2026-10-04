# STM32-


# 🚀 [STM32 4-Layer Minimal System Board design]

本專案為基於 **STM32F4 (ARM Cortex-M4)** 的高性能微控制器開發板，採用 4 層板架構設計。
整合完整接地平面 (GND) 與 3.3V 電源平面、USB Type-C 介面及 SWD 偵錯埠，適合用於嵌入式系統開發、物聯網驗證的實驗專案。

---

## 📌 專案特點 (Features)

- **高性能 STM32F4 核心**：採用 ARM Cortex-M4 架構主控，具備浮點運算單元 (FPU) 與高時脈運算能力。
- **標準 4 層板結構優化**：採用完整接地平面 (GND) 與 3.3V 電源平面，顯著提升 EMI/EMC 效能並降低電源噪聲。
- **USB Type-C 介面**：支援 5V 供電與 USB 數據通訊，板載高效率 LDO 轉 3.3V 穩壓電路。
- **標準 SWD 偵錯介面**：引出 SWDIO / SWCLK 腳位，方便使用 ST-Link / J-Link 進行快速程式燒錄與除錯。
- **生產即戰力 (Production Ready)**：通過完整原理圖 ERC 與 PCB DRC 檢查（0 Errors, 0 Warnings），符合嘉立創打樣規範。
- **物料與焊接優化**：元件 BOM 表包含立創 (LCSC) 料號，並提供 Interactive HTML BOM (iBOM) 方便手動焊接對照。

---

## 📐 硬體規格 (Hardware Specifications)

| 參數 | 規格細節 |
| :--- | :--- |
| **主控晶片 (MCU)** | STM32F4 系列 (LQFP 封裝) |
| **輸入電源** | 5V DC (經由 USB Type-C 介面) / LDO 轉 3.3V 系統供電 |
| **通訊與偵錯介面** | USB 2.0 Full-Speed, SWD 偵錯介面 |
| **板層結構** | 4 層板 (Top, GND, 3V3, Bottom) |
| **層疊範本** | JLCPCB `JLC04161H-7628` (Default) |
| **總板厚度** | 1.6258 mm |
| **成品銅厚** | 1 oz (0.035 mm) |
| **最小線寬 / 線距**| 6 mil / 6 mil |
| **最小鑽孔 / 焊盤**| 0.3 mm / 0.5 mm (Via) |
| **板材材質** | FR-4 (Tg 130-140) |
---

## 🥞 PCB 層疊結構 (Stackup)

| 圖層 (Layer) | 類型 | 材質 | 厚度 (mm) | 作用與說明 |
| :--- | :--- | :--- | :--- | :--- |
| **頂層 (L1 - Top Layer)** | 銅箔 (Copper) | Outer layer thickness | 0.035 | 訊號走線與元件貼片層 |
| 介質層 1 (Dielectric1) | 絕緣基材 (Substrate) | 7628 RC49% 8.6mil | 0.2104 | 絕緣介質 |
| **內層 1 (L2 - GND)** | 銅箔 (Copper) | - | 0.035 | **完整接地參考平面 (GND)** |
| 介質層 2 (Dielectric2) | 絕緣基材 (Substrate) | 1.1mm H/HOZ Copper | 1.065 | 主核心基板 (FR-4 Core) |
| **內層 2 (L3 - 3V3)** | 銅箔 (Copper) | - | 0.035 | **3.3V 主電源平面** |
| 介質層 3 (Dielectric3) | 絕緣基材 (Substrate) | 7628 RC49% 8.6mil | 0.2104 | 絕緣介質 |
| **底層 (L4 - Bottom Layer)**| 銅箔 (Copper) | Outer layer thickness | 0.035 | 電源走線與輔助佈線層 |

---

## 🔍 設計驗證與品質 (Quality Verification)

本專案在發布生產檔前已完成嚴格的工程驗證：
- **原理圖 ERC**：通過（0 錯誤，0 警告）。
- 📄 **DRC 檢查結果截圖**：[`STM32/Docs/Image/ERC.png`](STM32/Docs/Image/ERC.png)
- **PCB DRC**：四層板製程規範檢查通過（0 錯誤，0 警告）。
- 📄 **DRC 檢查結果截圖**：[`STM32/Docs/Image/DRC.png`](STM32/Docs/Image/DRC.png)

---

## 📂 生產製造檔案 (Production Files)

所有生產所需檔案均已整理於 [`production/`](production/) 資料夾中，可直接上傳工廠打樣：

- 📦 **Gerber 預備包**：[`production/Gerber_v1.0.zip`](production/Gerber_v1.0.zip)
- 📊 **物料清單 (BOM)**：[`production/BOM.csv`](STM32/Production/BOM.csv.csv)
- 📄 **原理圖 PDF**：[`docs/schematic.pdf`](STM32/Docs/Schematic.pdf/Schematic.pdf.pdf)

---

## 📁 專案目錄結構 (Repository Structure)

```text
├── docs/                      # 相關圖檔與文件
│   ├── drc.png                # DRC 零錯誤驗證截圖
│   ├── erc.png                # 層疊結構截圖
│   ├── stackup.png            # 層疊結構截圖
│   └── schematic.pdf          # 原理圖 PDF 檔
├── production/                # 工廠打樣與生產檔
│   ├── Gerber_v1.0.zip        # Gerber 與鑽孔檔案包
│   ├── BOM.csv                # 含 LCSC 料號的零件清單
├── README.md                  # 專案說明文件
