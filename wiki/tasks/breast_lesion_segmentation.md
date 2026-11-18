---
title: "乳腺超音波病灶分割與良惡性分類 (Breast Lesion CAD)"
aliases: ["Breast Ultrasound Segmentation", "乳腺腫瘤 CAD", "BI-RADS 超音波"]
category: "task"
tags: ["breast", "cancer", "cad", "segmentation", "classification", "bi-rads"]
last_updated: "2026-11-17"
sources: ["[[aldhabyani2020_busi]]", "[[ronneberger2015_unet]]", "[[lin2023_samus]]"]
---

# 乳腺超音波病灶分割與良惡性分類

## 1. 臨床背景與重要性
乳腺癌高居全球女性惡性腫瘤發病率之首。相較於乳房 X 光攝影（Mammography），超音波無游離輻射，且在亞洲女性高比例的**緻密型乳腺（Dense Breast Tissue）**中檢出率顯著更高。然而，乳腺超音波診斷極度依賴醫師經驗，存在較高的假陽性率與切片率。

---

## 2. 臨床聲學特徵與 BI-RADS 診斷標準
美國放射學會的乳腺影像報告與數據系統（BI-RADS）定義了關鍵聲學指標：
- **良性特徵**：邊界清晰光整（Circumscribed）、形態呈橢圓形或圓形、水平生長（縱橫比 $<1$）、均質低回聲或無回聲，並具有後方回聲增強。
- **惡性特徵**：邊界模糊不規則（Spiculated / Angular）、非水平生長（縱橫比 $\ge 1$，即垂直生長）、內部微鈣化、後方伴隨顯著的[[acoustic_shadowing|後方聲影]]。

---

## 3. 電腦視覺與深度學習任務構建
1. **病灶像素級分割 (Segmentation)**：
   精確勾勒病灶邊緣，用於計算腫瘤幾何長徑、體積與邊界粗糙度。
   - **基準模型**：標準 [[unet_architecture|U-Net]]、Attention U-Net。
   - **大模型新範式**：[[samus_adapter|SAMUS]] 透過醫師在可疑點單擊提示，實現高精度的即時交互式勾勒。
2. **良惡性三分類 (Classification)**：
   將影像自動歸類為 Normal（正常）、Benign（良性）或 Malignant（惡性）。
3. **主流評測基準**：
   全球最廣泛使用的開源基準為 [[busi_dataset|BUSI 資料集]]（780 張標註影像）。

---

## 4. 關聯頁面 (Wiki Links)
- **基準資料集**：[[busi_dataset|BUSI 資料集專題]]
- **核心演算法**：[[unet_architecture|U-Net 架構]]、[[samus_adapter|SAMUS 大模型適配]]
- **聲學機制**：[[acoustic_shadowing|聲影效應]]、[[speckle_noise|斑點噪聲]]
