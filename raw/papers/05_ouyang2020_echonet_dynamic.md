# Video-based AI for Beat-to-Beat Assessment of Cardiac Function (EchoNet-Dynamic)

- **Authors**: David Ouyang, Bryan He, Amirata Ghorbani, Neal Yuan, Joseph Ebinger, Curt P. Langlotz, Paul A. Heidenreich, Robert A. Harrington, David H. Liang, Matthew P. Lungren, James Y. Zou
- **Affiliation**: Stanford University School of Medicine, Stanford, CA; Cedars-Sinai Medical Center, Los Angeles, CA
- **Venue**: Nature 580, 252–256 (2020)
- **DOI**: 10.1038/s41586-020-2145-8

## Abstract
Echocardiography is the most common imaging modality in cardiology, providing real-time evaluation of cardiac mechanics and hemodynamics. However, interpretation requires specialized training, and clinical assessment exhibits notable intra-operator and inter-operator variability. We present EchoNet-Dynamic, an end-to-end deep learning framework that analyzes full echocardiogram videos to evaluate cardiac function beat by beat. Trained on 10,030 echocardiogram videos from Stanford University Medical Center, EchoNet-Dynamic accurately segments the left ventricle across cardiac cycles, estimates left ventricular ejection fraction (LVEF), and predicts systemic phenotypes such as cardiomyopathy. Our model achieved an area under the curve (AUC) of 0.97 for detecting heart failure with reduced ejection fraction, and an absolute mean error of 4.1% in predicting LVEF, matching or surpassing board-certified cardiologists while operating at milliseconds per heartbeat.

## Methodology & Architecture
1. **Video Spatiotemporal Architecture**:
   - 3D Convolutional Neural Network (R2+1D or 3D-ResNet) processing sequences of 32-112 video frames sampled at 50 Hz.
   - Decomposes spatial 2D convolutions and temporal 1D convolutions:
     $$\text{Conv3D}(k_t \times k_s \times k_s) \to \text{Conv2D}(1 \times k_s \times k_s) + \text{Conv1D}(k_t \times 1 \times 1)$$
   - Captures continuous cyclic motion of myocardium and mitral valve displacement over multiple cardiac cycles.
2. **Two-Stage Workflow**:
   - **Stage 1 (Weakly-supervised semantic segmentation)**: Generates beat-by-beat endocardial contours across all frames in apical 4-chamber (A4C) view.
   - **Stage 2 (Direct Regression)**: Predicts continuous numerical left ventricular volumes (EDV, ESV) and Left Ventricular Ejection Fraction (LVEF).
3. **Clinical Phenotyping**:
   - Classification of Heart Failure with Reduced Ejection Fraction (HFrEF, defined as $\text{LVEF} \le 35\%$ or $\le 50\%$).
   - Assessment of wall motion abnormalities and longitudinal myocardial strain.
4. **Data Scale & Benchmark Openness**:
   - Released 10,030 de-identified echocardiogram videos with paired human expert annotations, becoming the gold standard video echocardiography benchmark.
5. **Key Conclusions**:
   - Deep learning can process temporal dynamics in ultrasound directly, bypassing the need for manual frame selection of End-Diastole and End-Systole.
   - Eliminates inter-reader variability in echocardiography and enables real-time point-of-care ultrasound (POCUS) triage in emergency departments.
