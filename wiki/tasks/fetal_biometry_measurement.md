---
title: "產前胎兒超音波生物測量與頭圍 (Head Circumference, HC) 自動估算"
aliases: ["Fetal Biometry", "胎兒頭圍測量", "HC18 測量", "產前超音波"]
category: "task"
tags: ["obstetrics", "fetal-biometry", "head-circumference", "ellipse-fitting", "segmentation"]
last_updated: "2026-11-17"
sources: ["[[vandenheuvel2018_hc18]]", "[[ronneberger2015_unet]]"]
---

# 產前胎兒超音波生物測量與頭圍 (HC) 自動估算

## 1. 臨床意義與標準測量切面
產前超音波是監測胎兒健康與發育最重要的工具。
四大核心生物測量參數包括：
1. **頭圍 (Head Circumference, HC)**；
2. **雙頂徑 (Biparietal Diameter, BPD)**；
3. **腹圍 (Abdominal Circumference, AC)**；
4. **股骨長度 (Femur Length, FL)**。

臨床指南要求測量 HC 必須在嚴格的**丘腦水平橫切面（Transthalamic Plane）**進行，標準影像必須同時清晰顯示透明隔腔（CSP）、大腦鐮（Falx）與丘腦，且兩側顱骨呈對稱橢圓形。測量偏差將直接導致胎齡（Gestational Age）估算錯誤或漏診胎兒生長受限（IUGR）與小頭畸形。

---

## 2. 聲學物理難題：陰影下的殘缺邊緣
在真實產檢超音波中，胎兒顱骨為鈣化骨質，具有極強的聲波阻擋能力：
- 聲束在顱骨側壁切線方向產生嚴重的全反射與臨界角折射，形成[[acoustic_shadowing|側向聲影 (Lateral Acoustic Shadowing)]]；
- 顱骨後壁通常呈現模糊、甚至完全缺失的中斷狀態；
- 若母體脊柱或恥骨聯合恰好遮蔽聲路，局部邊界信號將徹底丟失。

---

## 3. 混合式幾何深度學習解決方案
[[vandenheuvel2018_hc18|van den Heuvel et al. (2018)]] 透過建立 [[hc18_dataset|HC18 標竿競賽]]，確立了「深度語意分割 + 強健幾何橢圓擬合」的兩階段標準流水線：
1. **邊緣概率圖預測**：使用 [[unet_architecture|U-Net]] 預測胎兒顱骨邊緣的像素概率分佈；
2. **幾何閉合補全 (Direct Least Squares Fitting)**：利用 Fitzgibbon 最小二乘橢圓代數約束或 RANSAC 演算法，從破碎的邊緣特徵中直接反解出完整的橢圓幾何參數（長半軸 $a$、短半軸 $b$）：
   $$\text{HC} \approx \pi [3(a+b) - \sqrt{(3a+b)(a+3b)}]$$
3. **精度**：在全孕期影像上達到 1.76 mm 的平均絕對誤差，成功跨越了人類專家觀察者間變異的門檻。

---

## 4. 關聯頁面 (Wiki Links)
- **競賽資料集**：[[hc18_dataset|HC18 產前超音波資料集]]
- **聲學機制**：[[acoustic_shadowing|聲學聲影效應]]
- **核心演算法**：[[unet_architecture|U-Net 卷積架構]]
