# LLM Wiki 操作日誌 (Operation Log)

本文件依據 [[AGENTS.md]] 規範維護，採 Append-only 形式記錄每次文獻攝取（Ingest）、問答沉澱（Query & Compound）及健康維護（Lint）。

---

## [2026-11-17] ingest | 01_ronneberger2015_unet
- **來源文獻**：`raw/papers/01_ronneberger2015_unet.md`
- **新增檔案**：`wiki/papers/ronneberger2015_unet.md`
- **更新實體**：`wiki/methods/unet_architecture.md`, `wiki/concepts/speckle_noise.md`
- **摘要**：提取了 U-Net 編解碼與跳躍連接架構，分析其在超音波低信噪比與斑點噪聲下恢復細微解剖邊界的核心價值。

---

## [2026-11-17] ingest | 02_aldhabyani2020_busi
- **來源文獻**：`raw/papers/02_aldhabyani2020_busi.md`
- **新增檔案**：`wiki/papers/aldhabyani2020_busi.md`, `wiki/datasets/busi_dataset.md`
- **更新實體**：`wiki/tasks/breast_lesion_segmentation.md`, `wiki/concepts/acoustic_shadowing.md`
- **摘要**：建立 BUSI 乳腺超音波基準資料集專頁，梳理良惡性腫瘤聲學特徵（後方聲影 vs 後方回聲增強）及 BI-RADS 診斷標準。

---

## [2026-11-17] ingest | 03_leclerc2019_camus
- **來源文獻**：`raw/papers/03_leclerc2019_camus.md`
- **新增檔案**：`wiki/papers/leclerc2019_camus.md`, `wiki/datasets/camus_dataset.md`
- **更新實體**：`wiki/tasks/echocardiography_lvef.md`
- **摘要**：建立 CAMUS 臨床超音波心動圖資料集專頁，建立左心室、心肌、左心房多結構分割評測標準與雙平面辛普森法 LVEF 計算流程。

---

## [2026-11-17] ingest | 04_lin2023_samus
- **來源文獻**：`raw/papers/04_lin2023_samus.md`
- **新增檔案**：`wiki/papers/lin2023_samus.md`, `wiki/methods/samus_adapter.md`
- **更新實體**：`wiki/methods/foundation_models_ultrasound.md`
- **摘要**：解析通用基礎模型 SAM 在超音波領域遭遇的斑點噪聲與聲影干擾瓶頸，建立 SAMUS 雙分支與跨分支注意力適配器（CBA）分析。

---

## [2026-11-17] ingest | 05_ouyang2020_echonet_dynamic
- **來源文獻**：`raw/papers/05_ouyang2020_echonet_dynamic.md`
- **新增檔案**：`wiki/papers/ouyang2020_echonet_dynamic.md`, `wiki/datasets/echonet_dynamic_dataset.md`
- **更新實體**：`wiki/methods/echonet_spatiotemporal.md`, `wiki/tasks/echocardiography_lvef.md`
- **摘要**：攝取萬例級動態視訊超音波心動圖研究，建立 R(2+1)D 時空解耦卷積模型與逐心搏（beat-to-beat）LVEF 自動回歸管線。

---

## [2026-11-17] ingest | 06_vandenheuvel2018_hc18
- **來源文獻**：`raw/papers/06_vandenheuvel2018_hc18.md`
- **新增檔案**：`wiki/papers/vandenheuvel2018_hc18.md`, `wiki/datasets/hc18_dataset.md`
- **更新實體**：`wiki/tasks/fetal_biometry_measurement.md`
- **摘要**：建立 HC18 產前胎兒頭圍自動測量資料集頁面，提煉神經網路結合強健代數橢圓擬合克服顱骨側向聲影缺失的混合方案。

---

## [2026-11-17] ingest | 07_errico2015_ulm_super_resolution
- **來源文獻**：`raw/papers/07_errico2015_ulm_super_resolution.md`
- **新增檔案**：`wiki/papers/errico2015_ulm_super_resolution.md`, `wiki/concepts/ultrasound_super_resolution.md`
- **更新實體**：`wiki/tasks/super_resolution_vascular_imaging.md`, `wiki/concepts/beamforming_physics.md`
- **摘要**：建立超快超音波定位顯微術（ULM）概念頁面，梳理微氣泡造影、SVD 時空雜波濾波與亞像素質心定位突破繞射極限的機制。

---

## [2026-11-17] ingest | 08_luchies2018_dnn_beamforming
- **來源文獻**：`raw/papers/08_luchies2018_dnn_beamforming.md`
- **新增檔案**：`wiki/papers/luchies2018_dnn_beamforming.md`, `wiki/methods/deep_beamforming.md`
- **更新實體**：`wiki/concepts/beamforming_physics.md`, `wiki/concepts/speckle_noise.md`
- **摘要**：建立深度神經網路前端 RF 通道波束成形頁面，分析非線性空間濾波在消除組織聲速非均勻性相位像差與旁瓣雜波上的成效。

---

## [2026-11-17] ingest | 09_jiao2020_uscl_contrastive
- **來源文獻**：`raw/papers/09_jiao2020_uscl_contrastive.md`
- **新增檔案**：`wiki/papers/jiao2020_uscl_contrastive.md`, `wiki/methods/ultrasound_contrastive_learning.md`
- **更新實體**：`wiki/tasks/standard_plane_detection.md`
- **摘要**：建立超音波專用自監督對比學習（USCL）頁面，歸納基於瑞利斑點噪聲與深度衰減的聲學數據增強以及時序正樣本對挖掘機制。

---

## [2026-11-17] ingest | 10_wang2024_ultrasound_foundation_survey
- **來源文獻**：`raw/papers/10_wang2024_ultrasound_foundation_survey.md`
- **新增檔案**：`wiki/papers/wang2024_ultrasound_foundation_survey.md`, `wiki/methods/foundation_models_ultrasound.md`
- **更新實體**：`wiki/synthesis/ultrasound_ai_evolution.md`, `wiki/synthesis/acoustic_challenges_matrix.md`
- **摘要**：系統化歸納超音波大模型（US-FM）三大架構範式（VFMs、VLMs、SSL），並產出跨代際演進史與聲學物理限制對抗矩陣。

---

## [2026-11-17] compound | 全域索引與綜合對比報告發布
- **生成檔案**：`wiki/index.md`, `wiki/synthesis/ultrasound_ai_evolution.md`, `wiki/synthesis/acoustic_challenges_matrix.md`
- **狀態**：完成 10 篇學術論文攝取，構建 26 篇雙向鏈接持久知識頁面。

---

## [2026-11-17] query-compound | 「超音波影像是什麼？」科普教學 HTML 簡報生成
- **觸發請求**：依據 Wiki 編譯內容生成零基礎初學者教學簡報，並公開 Loop/Graph 控制流程。
- **檢索實體**：`wiki/concepts/speckle_noise.md`, `wiki/concepts/acoustic_shadowing.md`, `wiki/concepts/beamforming_physics.md`, `wiki/synthesis/acoustic_challenges_matrix.md`, `wiki/tasks/...`
- **生成檔案**：`wiki/synthesis/ultrasound_intro_slides.html`
- **架構特點**：8 頁現代暗色調卡片式互動投影、支援鍵盤方向鍵導航、進度指示條與隨堂測驗互動。

---

## [2026-11-17] query-compound | 第二版 (v2) 教學簡報發布與概念合約前移驗證
- **優化動機**：依據復盤結論，將檢查點前移至「大綱概念合約」階段，解耦通俗比喻與聲學物理本質，保留 v1 初版檔案供對照。
- **新增檔案**：`wiki/synthesis/ultrasound_intro_slides_v2.html`
- **保留檔案**：`wiki/synthesis/ultrasound_intro_slides.html` (初版存檔)
- **核心升級**：
  1. 內嵌「聲波穿透與回聲即時模擬器 (Acoustic Wave Simulator)」，可動態發射聲波觀察囊腫穿透與骨壁全反射。
  2. 強化聲學物理本質：明辨機械壓力波與光線差異，釐清凝膠消除 3000 倍阻抗失配之物理意義。
  3. 升級為雙道隨堂互動測驗，即時加強聲阻抗與斑點干涉認知。

---

## [2026-11-18] style-update | 第二版 (v2.1) 視覺沉浸度與字體對比度優化
- **優化檔案**：`wiki/synthesis/ultrasound_intro_slides_v2.html`
- **修正重點**：
  1. **字體對比度提升**：全面移除黑底配深色灰字（`text-slate-500/600`），改採亮白（`text-white`、`text-slate-100/200`）、亮青（`text-cyan-200/300`）與亮琥珀（`text-amber-200/300`），確保暗色背景下字字清晰。
  2. **簡報視覺佔比擴大**：投影片容器升級至寬螢幕版（`max-w-[96vw]` / `max-w-6xl`，高度設定 `min-h-[75vh]`），滿版沉浸感大幅增強。
  3. **內文字體放大**：主標題提升至 `4xl~6xl`，內文與卡片敘述提升至 `14~18px`，徹底剔除 10-11px 微型字體，提高遠距離投影與螢幕閱讀舒適度。

---

## [2026-11-18] layout-refactor | 第二版 (v2.2) 視窗滿版最佳化與導航重組
- **優化檔案**：`wiki/synthesis/ultrasound_intro_slides_v2.html`
- **重構重點**：
  1. **頂部冗餘資訊清除**：移除上方 Header 的標題、版本文字、進度條與「清晰大字版」標籤，全數釋出頂部高度。
  2. **版面向上平移**：簡報容器移至視野頂端，設定視窗滿版高度配重（`h-screen max-h-screen overflow-hidden` + 卡片 `max-h-[84vh]`），保證瀏覽器在 100% 縮放顯示時，一屏完整容納簡報與下方導航條，無需向下滾動。
  3. **頁數顯示位置重整**：將頁碼 `1 / 8` 整合至下方「← 上一頁」與「下一頁 →」中央的點狀切換器旁，操作與狀態合一。
