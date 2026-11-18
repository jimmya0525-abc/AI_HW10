---
title: "BUSI: 乳腺超音波影像基準資料集 (Breast Ultrasound Images Dataset)"
aliases: ["BUSI", "BUSI Dataset", "Breast Ultrasound Dataset"]
category: "dataset"
tags: ["dataset", "breast", "b-mode", "cancer", "segmentation", "classification"]
last_updated: "2026-11-17"
sources: ["[[aldhabyani2020_busi]]", "[[lin2023_samus]]"]
---

# BUSI 資料集 (Breast Ultrasound Images Dataset)

## 1. 資料集規格與概覽
- **釋出年份**：2020 年（[[aldhabyani2020_busi|Al-Dhabyani et al.]]）
- **採集來源**：開羅大學國家癌症研究所（National Cancer Institute, Cairo University）
- **受試者規模**：600 名女性病患（年齡 25 至 75 歲）
- **影像總數**：780 張 B-mode 超音波影像（PNG 格式，平均尺寸 $500 \times 500$）
- **超音波機型**：GE LOGIQ E9 及 LOGIQ 7 系統，搭配 8-15 MHz 線性陣列高頻探頭

---

## 2. 類別分佈與標註資訊
| 類別 | 影像數量 | 典型臨床病理與聲學特徵 | 標註形式 |
| :--- | :--- | :--- | :--- |
| **Normal** (正常) | 133 張 | 正常乳腺導管與纖維脂肪小葉結構，無腫塊 | 無標註遮罩 |
| **Benign** (良性) | 487 張 | 纖維腺瘤、囊腫；形狀規整、縱橫比 $<1$、後方增強 | 專科醫師手工像素級 Mask |
| **Malignant** (惡性) | 210 張 | 浸潤性導管癌；邊緣毛刺不整、縱橫比 $\ge 1$、[[acoustic_shadowing|後方聲影]] | 專科醫師手工像素級 Mask |

---

## 3. 領域挑戰與標竿地位
1. **惡性病灶後方聲影截斷**：惡性腫瘤引發嚴重聲束吸收衰減，導致深層後壁輪廓模糊，為分割模型的主要誤差來源。
2. **多病灶共存**：部分病例在同一視野內同時存在多個良惡性腫瘤，需考量多實例分割。
3. **SOTA 標竿模型表現**：
   - 經典 [[unet_architecture|U-Net]]：Dice 評分約在 76% - 81%。
   - 專用大模型適配 [[samus_adapter|SAMUS]]：Dice 評分提升至 85% - 88%。

---

## 4. 關聯頁面 (Wiki Links)
- **原始論文解析**：[[aldhabyani2020_busi|BUSI 論文精讀]]
- **臨床任務**：[[breast_lesion_segmentation|乳腺腫瘤病灶分割]]
- **評測模型**：[[unet_architecture|U-Net]]、[[samus_adapter|SAMUS]]
- **聲學物理現象**：[[acoustic_shadowing|聲影效應]]
