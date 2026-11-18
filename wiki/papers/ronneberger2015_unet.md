---
title: "U-Net: 卷積神經網路於生物醫學影像分割 (Ronneberger et al., 2015)"
aliases: ["U-Net", "Ronneberger 2015"]
category: "paper"
tags: ["ultrasound", "segmentation", "cnn", "skip-connection", "foundational"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/01_ronneberger2015_unet.md]]"]
---

# U-Net: Convolutional Networks for Biomedical Image Segmentation

- **作者**：Olaf Ronneberger, Philipp Fischer, Thomas Brox
- **發表場合**：MICCAI 2015
- **原始文獻依據**：[[raw/papers/01_ronneberger2015_unet.md]]

---

## 1. 論文核心貢獻
本文提出了奠定現代醫學影像分割基準的 **U-Net** 架構。在訓練樣本極度稀缺（少量標註）的生物醫學領域中，透過「收縮路徑（Contracting Path）」與「對稱擴展路徑（Expanding Path）」的編解碼架構，搭配跨層特徵拼接的 **跳躍連接（Skip Connections）**，實現端到端的高解析度語意像素級預測。

---

## 2. 架構與技術亮點

### 2.1 對稱編解碼與跳躍連接
- **收縮路徑（Encoder）**：反覆應用兩次 $3 \times 3$ 卷積（ReLU）搭配 $2 \times 2$ Max Pooling（stride 2），提取富含高階語意脈絡的特徵圖，並在每次下採樣時將通道數翻倍。
- **擴展路徑（Decoder）**：採用 $2 \times 2$ 反卷積（Up-convolution）將空間解析度減半恢復，並將解碼特徵與來自編碼路徑中對應解析度的特徵圖直接拼接（Concatenate）。
- **跳躍連接本質**：解決了深度網路中空間邊界細節隨連續池化（Downsampling）而消失的痛點，將低階淺層的細粒度邊界信息直接輸送至深層解碼器。

### 2.2 彈性變形資料增強 (Elastic Deformations)
針對軟組織器官的高可塑性，採用粗網格隨機位移向量場插值生成的彈性形變技術，使模型學會形狀不變性，極大抑制過擬合。

---

## 3. 在超音波影像研究中的深遠影響與關聯
在超音波影像（Ultrasound Imaging）領域，由於受到嚴重的[[speckle_noise|斑點噪聲 (Speckle Noise)]]、聲影遮擋（[[acoustic_shadowing|Acoustic Shadowing]]）以及微弱組織界面邊界影響，傳統基於閾值或水平集（Level Set）的方法極易失效。
- U-Net 的跳躍連接結構天然補足了超音波影像微弱聲學邊界的重構能力。
- 本架構直接衍生出後續在超音波領域廣泛應用的變體模型，包含 Attention U-Net、[[unet_architecture|Swin-Unet]]、以及結合基礎大模型的 [[samus_adapter|SAMUS]]。

---

## 4. 關聯頁面 (Wiki Links)
- **核心架構**：[[unet_architecture|U-Net 架構與演進]]
- **聲學現象**：[[speckle_noise|斑點噪聲 (Speckle Noise)]]
- **臨床任務應用**：
  - [[breast_lesion_segmentation|乳腺超音波病灶分割]]（應用於 [[busi_dataset|BUSI 資料集]]）
  - [[echocardiography_lvef|心臟超音波結構分割]]（應用於 [[camus_dataset|CAMUS 資料集]]）
  - [[fetal_biometry_measurement|胎兒產前超音波測量]]（應用於 [[hc18_dataset|HC18 資料集]]）
