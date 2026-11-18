# Automated Measurement of Fetal Head Circumference Using 2D Ultrasound Images (HC18)

- **Authors**: Thomas L. A. van den Heuvel, Dagmar de Bruijn, Chris L. de Korte, Bram van Ginneken
- **Affiliation**: Diagnostic Image Analysis Group, Radboud University Medical Center, Nijmegen, The Netherlands
- **Venue**: PLOS ONE 13(8): e0199890 (2018) / Grand Challenge HC18
- **DOI**: 10.1371/journal.pone.0199890

## Abstract
Biometric measurements of the fetus from 2D ultrasound images are vital for monitoring fetal growth and estimating gestational age. Head circumference (HC) is one of the most important parameters. However, manual ellipse fitting of the fetal cranium requires expert sonographer experience and suffers from operator subjectivity and acoustic shadowing from the skull or maternal pelvic bones. We present an automated method based on deep learning and ellipse fitting to segment the fetal head and calculate HC. Furthermore, we release the HC18 challenge dataset consisting of 1,334 2D ultrasound images acquired across all three trimesters from 751 pregnant women, annotated with expert manual ellipse measurements. Our deep learning method achieves an average absolute difference of 1.76 mm compared to human experts, which is within the range of inter-observer variation (2.0 mm).

## Methodology & Pipeline
1. **Clinical Importance of Fetal Biometry**:
   - Biometric parameters: Head Circumference (HC), Biparietal Diameter (BPD), Abdominal Circumference (AC), Femur Length (FL).
   - Used for estimating Gestational Age (GA) and identifying Intrauterine Growth Restriction (IUGR) or macrosomia.
   - Standard measurement plane: Transventricular plane or transthalamic plane displaying the cavum septi pellucidi (CSP) and midline falx.
2. **Two-Stage Detection & Fitting Pipeline**:
   - **Step 1: Fully Convolutional Segmentation Network**: A custom U-Net or Hough-CNN predicts binary boundary probability maps of the fetal skull bone (hyperechoic calvarium ring).
   - **Step 2: Robust Ellipse Fitting**: Direct Least Squares Fitting of Ellipses (Fitzgibbon algorithm) or Random Sample Consensus (RANSAC) applied to segmented skull border probabilities, ensuring topological closure even when acoustic shadows or reverberations break bone continuity.
3. **HC Formula**:
   $$\text{HC} = \pi \cdot [3(a + b) - \sqrt{(3a + b)(a + 3b)}]$$
   where $a$ and $b$ are the semi-major and semi-minor axes of the fitted ellipse in millimeters.
4. **Dataset Details (HC18 Challenge)**:
   - 999 training images and 335 test images from all trimesters (first, second, third).
   - Pixel sizes vary from 0.052 to 0.326 mm/pixel depending on gestational age and probe depth.
5. **Key Ultrasound Challenges Addressed**:
   - Incomplete cranial border due to acoustic shadowing from fetal spine or maternal pubic symphysis.
   - Low contrast against amniotic fluid and maternal soft tissues.
   - High variation in fetal skull orientation, acoustic attenuation, and head shape across trimesters.
