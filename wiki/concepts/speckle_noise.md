---
title: "斑點噪聲 (Speckle Noise) 與聲學統計特性"
aliases: ["Speckle Noise", "斑點雜訊", "聲學散斑"]
category: "concept"
tags: ["physics", "acoustics", "noise", "rayleigh-distribution"]
last_updated: "2026-11-17"
sources: ["[[ronneberger2015_unet]]", "[[luchies2018_dnn_beamforming]]", "[[jiao2020_uscl_contrastive]]"]
---

# 斑點噪聲 (Speckle Noise)

## 1. 物理成因與聲學干涉
在超音波成像中，**斑點噪聲（Speckle Noise）**並非感測器熱噪聲或高斯隨機白噪聲，而是一種**具備物理確定性的同調聲學干涉（Coherent Interference）現象**。
- 當探頭發射的超音波脈衝進入人體實質組織（如肝臟、乳腺間質、心肌）時，會遇到大量尺寸遠小於聲波波長 $\lambda$ 的微小散射子（Micro-scatterers，如細胞膜、小血管、膠原纖維）。
- 每個散射子產生微弱的子波回聲，這些子波在空間中相互疊加：
  - **建設性干涉（Constructive Interference）**：相位相同，回聲增強，形成亮點（Bright Speckle）。
  - **破壞性干涉（Destructive Interference）**：相位相反，回聲抵消，形成暗點（Dark Speckle）。
- 最終在 B-mode 影像中形成顆粒狀、隨機紋理外觀。

---

## 2. 統計分佈數學模型
當解析單元（Resolution Cell）內含有大量獨立且相位均勻分佈的隨機散射子時，依照中心極限定理，接收到射頻（RF）信號的包絡振幅 $A$ 遵循 **瑞利分佈（Rayleigh Distribution）**：
$$P(A) = \frac{A}{\sigma^2} \exp\left(-\frac{A^2}{2\sigma^2}\right), \quad A \ge 0$$
在乘性噪聲模型（Multiplicative Noise Model）中，含噪超音波影像 $I(x, y)$ 可表示為：
$$I(x, y) = S(x, y) \cdot \eta_m(x, y) + \eta_a(x, y)$$
其中 $S(x, y)$ 為真實組織反射率，$\eta_m$ 為乘性斑點噪聲，$\eta_a$ 為加性噪聲。

---

## 3. 對深度學習的雙重影響與演算法因應
1. **負面影響**：
   - 劇烈降低影像的信噪比（SNR）與對比雜訊比（CNR）。
   - 模糊腫瘤邊界，導致傳統邊緣檢測與通用自然大模型（如 SAM）發生邊界漂移。
2. **正面診斷價值**：
   - 斑點的統計分佈直接反映了組織的微觀病理結構（如脂肪肝與正常肝實質的斑點統計特性迥異）。
   - 斑點追蹤超音波心動圖（Speckle Tracking Echocardiography, STE）利用心肌內斑點圖案追蹤局部變形，評估心肌應變（Myocardial Strain）。
3. **AI 應對策略**：
   - **波束成形優化**：[[deep_beamforming|深度神經網路波束成形]] 直接在 RF 域抑制離軸旁瓣雜波。
   - **聲學感知增強**：[[jiao2020_uscl_contrastive|USCL]] 與 [[ultrasound_contrastive_learning|超音波對比學習]] 在預訓練時注入瑞利分佈干涉擾動，迫使模型學習斑點不變性的解剖特徵。

---

## 4. 關聯頁面 (Wiki Links)
- **前端物理**：[[beamforming_physics|波束成形物理]]
- **抑制方法**：[[deep_beamforming|深度學習波束成形]]、[[ultrasound_contrastive_learning|超音波對比學習]]
- **臨床任務挑戰**：[[breast_lesion_segmentation|乳腺結節分割]]、[[echocardiography_lvef|心臟超音波心內膜勾勒]]
