---
title: "BUSI: 乳腺超音波基準資料集 (Al-Dhabyani et al., 2020)"
aliases: ["BUSI Dataset Paper", "Al-Dhabyani 2020"]
category: "paper"
tags: ["ultrasound", "breast-cancer", "dataset", "segmentation", "classification"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/02_aldhabyani2020_busi.md]]"]
---

# Dataset of Breast Ultrasound Images (BUSI)

- **作者**：Walid Al-Dhabyani, Mohammed Gomaa, Hussien Khaled, Aly Fahmy
- **發表場合**：Data in Brief, 2020
- **原始文獻依據**：[[raw/papers/02_aldhabyani2020_busi.md]]

---

## 1. 論文核心貢獻
本文公開釋出了全球乳腺超音波研究中引用頻率最高的開源基準資料集 **BUSI (Breast Ultrasound Images Dataset)**。資料集包含 780 張高品質臨床 B-mode 超音波影像與相應的放射科專科醫師手繪病灶金標準（Ground Truth Masks），為電腦輔助診斷（CAD）與深度學習模型提供了標準評測基準。

---

## 2. 資料集臨床分佈與特徵解析
- **病例規模**：採集自 600 名年齡介於 25 至 75 歲女性患者。
- **類別分佈**：
  - **正常 (Normal)**：133 張（無明顯結節/囊腫結構）。
  - **良性 (Benign)**：487 張（纖維腺瘤、單純囊腫等），聲學特徵通常為邊界清晰（Circumscribed）、橫徑大於縱徑（Wider-than-tall）、均質低回聲並伴隨後方聲學增強（Posterior Acoustic Enhancement）。
  - **惡性 (Malignant)**：210 張（浸潤性導管癌等），典型聲學特徵為微浸潤邊緣不規則（Spiculated margins）、縱橫比大於 1（Taller-than-wide）、微鈣化點，以及顯著的[[acoustic_shadowing|後方聲影 (Posterior Acoustic Shadowing)]]。

---

## 3. 在超音波 AI 研究中的挑戰與基準地位
1. **多病灶與極端類別不平衡**：資料集中單張影像可能包含多個良惡性混合病灶，且良性樣本數為惡性樣本的兩倍以上。
2. **聲影干擾邊界閉合**：惡性腫瘤引起的聲學衰減導致深部後壁回聲消失，使得標準 [[unet_architecture|U-Net]] 難以閉合輪廓。
3. **評測基準**：目前成為檢驗 [[samus_adapter|SAMUS]]、TransUNet 與各類注意力機制的標準測試集。

---

## 4. 關聯頁面 (Wiki Links)
- **實體資料集**：[[busi_dataset|BUSI 資料集專題]]
- **臨床任務**：[[breast_lesion_segmentation|乳腺超音波病灶分割與分類]]
- **聲學效應**：[[acoustic_shadowing|後方聲影效應 (Acoustic Shadowing)]]
- **演算法評測**：[[unet_architecture|U-Net]]、[[samus_adapter|SAMUS]]
