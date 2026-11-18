# Deep Learning for Segmentation Using an Open Large-Scale Dataset in 2D Echocardiography (CAMUS)

- **Authors**: Sarah Leclerc, Erik Smistad, Joao Pedrosa, Andreas Ostvik, Frederic Cervenansky, Sebastien Salles, Dominique Delingette, Olivier Bernard et al.
- **Affiliation**: CREATIS, CNRS UMR 5220, INSERM U1044, Université Lyon 1, France; SINTEF, Norway; Inria Sophia Antipolis, France
- **Venue**: IEEE Transactions on Medical Imaging (TMI), Vol. 38, No. 9, September 2019
- **DOI**: 10.1109/TMI.2019.2900516

## Abstract
Echocardiography is the most widely used imaging modality for cardiac assessment. However, manual delineation of cardiac structures is tedious and subject to intra- and inter-observer variability. Deep learning methods have shown remarkable promise, but their development has been impeded by the lack of large, publicly available datasets. We introduce the CAMUS (Cardiac Acquisitions for Multi-structure Ultrasound Segmentation) dataset, an open-access clinical dataset of 500 patients, containing fully annotated 2D apical two-chamber (A2C) and four-chamber (A4C) echocardiographic sequences at end-diastole (ED) and end-systole (ES). We benchmark state-of-the-art deep learning architectures against expert manual segmentation and quantify their clinical utility in evaluating left ventricular ejection fraction (LVEF) and myocardial longitudinal strain.

## Dataset & Technical Details
1. **Dataset Scale & Demographics**:
   - 500 patients acquired from GE Healthcare systems (Vivid E95, Vivid 7) using M5S and 4V probes.
   - Varied cardiac health statuses: ejection fraction ranging from <45% (heart failure) to >55% (normal).
   - Image quality stratified by experts into Good, Medium, and Poor acoustic windows.
2. **Target Structures**:
   - Left Ventricle Endocardium (LV cavity).
   - Left Ventricle Myocardium (MYO).
   - Left Atrium (LA cavity).
3. **Benchmarked Architectures**:
   - Standard U-Net, Attention U-Net, Anatomically Constrained Neural Networks (ACNN), Stacked Sandglass architectures.
4. **Key Quantitative Findings**:
   - State-of-the-art models achieved average Dice scores of 0.92 (LV cavity), 0.88 (MYO), and 0.89 (LA) on good quality sequences.
   - For poor image quality sequences, performance degraded by 6-10% Dice, reflecting challenges with acoustic dropouts at apical lateral walls.
   - Absolute error on Left Ventricular Ejection Fraction (LVEF) was under 5.0%, rivaling inter-observer cardiologist variability.
5. **Clinical Relevance**:
   - Automated measurement of Left Ventricular Volume (End-Diastolic Volume EDV, End-Systolic Volume ESV) and Biplane Simpson's rule Ejection Fraction ($\text{LVEF} = \frac{\text{EDV} - \text{ESV}}{\text{EDV}} \times 100\%$).
   - Critical for diagnosis of heart failure with reduced ejection fraction (HFrEF).
