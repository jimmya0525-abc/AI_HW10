---
title: "HC18: 胎兒頭圍自動測量與產前超音波基準 (van den Heuvel et al., 2018)"
aliases: ["HC18", "van den Heuvel 2018"]
category: "paper"
tags: ["ultrasound", "obstetrics", "fetal-biometry", "head-circumference", "segmentation"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/06_vandenheuvel2018_hc18.md]]"]
---

# Automated Measurement of Fetal Head Circumference Using 2D Ultrasound Images (HC18)

- **作者**：Thomas L. A. van den Heuvel, Dagmar de Bruijn, Chris L. de Korte, Bram van Ginneken
- **發表場合**：PLOS ONE 2018 / Grand Challenge HC18
- **原始文獻依據**：[[raw/papers/06_vandenheuvel2018_hc18.md]]

---

## 1. 論文核心貢獻
產前胎兒超音波生物測量（Fetal Biometry）是估算胎齡（GA）與監控胎兒生長受限（IUGR）的關鍵臨床手段。本文公開了首個涵蓋全妊娠期（早期、中期、晚期）的超音波頭圍評測競賽基準 **HC18**（1,334 張 2D 超音波影像），並提出將全卷積神經網路（FCN / [[unet_architecture|U-Net]]）與穩健橢圓擬合（Robust Ellipse Fitting）相結合的混合幾何深度學習框架。

---

## 2. 面臨的超音波聲學物理挑戰
1. **強聲影遮擋**：顱骨為高聲阻抗骨質結構，兩側聲束切向入射引發嚴重的臨界角反射與側向聲影（Lateral Acoustic Shadowing），導致深層顱骨邊界信號嚴重中斷。
2. **母體羊水與軟組織雜波**：羊水內混響（Reverberation）與母體恥骨聯合或脊柱之陰影干擾。
3. **幾何擬合補償**：模型透過直接最小二乘橢圓擬合（Direct Least Squares Ellipse Fitting）在幾何拓撲上強制閉合破碎的聲學邊緣，將平均絕對誤差控制在 1.76 mm 以內，達到人類資深超音波技師變異度水平（2.0 mm）。

---

## 3. 關聯頁面 (Wiki Links)
- **實體資料集**：[[hc18_dataset|HC18 胎兒超音波資料集]]
- **臨床任務**：[[fetal_biometry_measurement|產前超音波胎兒生物測量與標準切面]]
- **聲學現象**：[[acoustic_shadowing|聲影效應 (Acoustic Shadowing)]]
- **基礎架構**：[[unet_architecture|U-Net 分割]]
