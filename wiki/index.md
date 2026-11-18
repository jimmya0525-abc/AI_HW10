# 超音波影像研究 LLM Wiki 全域索引目錄 (Index)

> 本文件是本知識庫的內容導航中心（Content-oriented Catalog）。每當有新文獻攝取（Ingest）、概念沉澱或綜合分析生成時，LLM 代理人皆會同步更新本目錄。

---

## 1. 專題綜合報告與對比分析 (Synthesis)
- [[ultrasound_ai_evolution|超音波 AI 技術演進全景]] — 從傳統濾波、任務專用 CNN 到動態視訊模型與多模態基礎模型的三代技術跨越。
- [[acoustic_challenges_matrix|聲學物理限制與 AI 因應對策矩陣]] — 深度對照斑點噪聲、後方聲影、繞射極限、聲速非均勻性與現代深度學習解法。
- [[ultrasound_intro_slides_v2.html|超音波影像科普互動 HTML 簡報 (第二版 v2)]] — 經過概念合約驗證重構，內嵌「聲波發射與回聲穿透即時模擬器」與雙測驗的進階科普簡報。
- [[ultrasound_intro_slides.html|超音波影像入門科普互動簡報 (初版 v1)]] — 適合零基礎初學者的 8 頁流暢教學簡報（初版存檔供比對）。

---

## 2. 聲學物理與核心理論概念 (Concepts)
- [[speckle_noise|斑點噪聲 (Speckle Noise)]] — 探討亞波長微散射子同調干涉機制、瑞利分佈統計模型與去噪技術。
- [[acoustic_shadowing|聲影效應 (Acoustic Shadowing)]] — 解析強衰減病灶後方聲影、囊腫後方回聲增強及 BI-RADS 診斷標準。
- [[beamforming_physics|超音波波束成形 (Beamforming) 物理]] — 介紹多陣元延遲相加法 (DAS)、相位像差、旁瓣雜波與點擴散函數 (PSF)。
- [[ultrasound_super_resolution|超音波超解析度顯微成像 (ULM)]] — 闡述微氣泡點擴散質心亞像素超定位原理，突破波動聲學繞射極限。

---

## 3. 深度學習模型與演算法架構 (Methods)
- [[unet_architecture|U-Net 架構及其在超音波中的演進]] — 對稱編解碼與跳躍連接保留微弱聲學邊界的機制及 Attention U-Net / Swin-Unet 演進。
- [[samus_adapter|SAMUS: 跨分支注意力超音波大模型適配]] — 針對 SAM 在超音波領域效能滑落提出的雙分支 CNN-ViT 混合高效微調架構。
- [[echonet_spatiotemporal|EchoNet 時空視訊深度學習架構]] — 利用 R(2+1)D 卷積分解實現超音波心動圖連續視訊逐心搏動態評估。
- [[deep_beamforming|深度學習波束成形 (Deep Beamforming)]] — 直接在未成形射頻 (RF) 通道數據上運用神經網路抑制雜波與像差。
- [[ultrasound_contrastive_learning|超音波自監督對比學習 (USCL)]] — 融合斑點噪聲物理增強與掃查視訊時序連續性的無標註預訓練策略。
- [[foundation_models_ultrasound|超音波領域基礎模型 (US-FMs) 發展現狀]] — 綜述視覺基礎模型微調、多模態視覺語言模型 (VLM) 及跨機型泛化挑戰。

---

## 4. 臨床與工程任務 (Tasks)
- [[breast_lesion_segmentation|乳腺超音波病灶分割與良惡性分類]] — 結合 BI-RADS 形態特徵與深度學習輪廓分割之電腦輔助診斷。
- [[echocardiography_lvef|超音波心動圖多結構分割與左心室射血分數 (LVEF) 評估]] — 雙平面辛普森法臨床測量與視訊級 AI 心衰竭篩檢。
- [[fetal_biometry_measurement|產前胎兒超音波生物測量與頭圍 (HC) 自動估算]] — 結合語意分割與代數橢圓擬合克服顱骨側向聲影缺失。
- [[super_resolution_vascular_imaging|深部微血管超解析度顯微造影]] — 突破繞射極限繪製活體大腦與早期腫瘤微米級毛細血管流速圖譜。
- [[standard_plane_detection|超音波標準切面辨識與即時掃查品質控制]] — 床邊掌上型超音波 (POCUS) 臨床掃查智能導引與標準度量化評估。

---

## 5. 公開標竿資料集 (Datasets)
- [[busi_dataset|BUSI 資料集]] — 780 張標註乳腺超音波影像（正常、良性、惡性三分類與像素級病灶標註）。
- [[camus_dataset|CAMUS 資料集]] — 500 位病患臨床 2D 超音波心動圖資料庫（含 A2C、A4C 切面及聲學品質分級）。
- [[echonet_dynamic_dataset|EchoNet-Dynamic 資料庫]] — 史丹佛大學 10,030 支完整超音波心動圖動態視訊與臨床專家標註。
- [[hc18_dataset|HC18 資料集]] — 全孕期 1,334 張產前超音波影像胎兒頭圍國際挑戰賽評測標準。

---

## 6. 論文精讀解析筆記 (Papers)
- [[ronneberger2015_unet|Ronneberger et al. (MICCAI 2015)]] — U-Net 生物醫學影像分割奠基之作。
- [[aldhabyani2020_busi|Al-Dhabyani et al. (Data in Brief 2020)]] — BUSI 乳腺超音波開源資料集標準文獻。
- [[leclerc2019_camus|Leclerc et al. (IEEE TMI 2019)]] — CAMUS 二維超音波心動圖多結構分割評測標準。
- [[lin2023_samus|Lin et al. (IEEE TMI / arXiv 2023)]] — SAMUS 超音波專用 SAM 基礎模型適配。
- [[ouyang2020_echonet_dynamic|Ouyang et al. (Nature 2020)]] — EchoNet-Dynamic 視訊級 AI 心臟功能評估。
- [[vandenheuvel2018_hc18|van den Heuvel et al. (PLOS ONE 2018)]] — HC18 產前胎兒超音波頭圍測量基準。
- [[errico2015_ulm_super_resolution|Errico et al. (Nature 2015)]] — ULM 超快超音波定位顯微術突破繞射極限。
- [[luchies2018_dnn_beamforming|Luchies & Byram (IEEE TUFFC 2018)]] — DNN 射頻 RF 通道數據直接波束成形。
- [[jiao2020_uscl_contrastive|Jiao et al. (MICCAI 2020 / TMI 2023)]] — USCL 超音波聲學物理自監督對比學習。
- [[wang2024_ultrasound_foundation_survey|Wang et al. (MedIA / arXiv 2024)]] — 超音波基礎模型全景綜述與 14 個資料集標竿評測。
