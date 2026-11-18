# Dataset of Breast Ultrasound Images (BUSI)

- **Authors**: Walid Al-Dhabyani, Mohammed Gomaa, Hussien Khaled, Aly Fahmy
- **Affiliation**: Cairo University, Faculty of Computers and Artificial Intelligence, National Cancer Institute, Egypt
- **Venue**: Data in Brief, Volume 28, February 2020, 104863
- **DOI**: 10.1016/j.dib.2019.104863

## Abstract
Breast cancer is one of the most common causes of death among women worldwide. Early detection helps in reducing the number of early deaths. The data of breast ultrasound images are categorized into three classes: normal, benign, and malignant images. Breast ultrasound images are among the most powerful diagnostic tools for diagnosing breast abnormalities. The dataset consists of breast ultrasound images gathered in 2018. The number of patients was 600 female patients, ages between 25 and 75 years old. The dataset consists of 780 images with an average image size of 500x500 pixels. The images are categorized into three classes: normal (133 images), benign (487 images), and malignant (210 images). The ground truth images are presented with original images in PNG format. The data can be used for deep learning segmentation, classification, and detection of breast tumors.

## Dataset Characteristics & Clinical Context
1. **Device & Modality**:
   - Acquired using LOGIQ E9 ultrasound system and LOGIQ 7 system with 8-15 MHz linear transducers.
   - Standard B-mode grayscale ultrasound.
2. **Breakdown of Classes**:
   - **Normal**: 133 cases with no detectable lesion.
   - **Benign**: 487 cases (fibroadenomas, cysts) characterized by circumscribed oval/round shapes, hypoechoic or anechoic texture, horizontal orientation (wider than tall), and posterior acoustic enhancement.
   - **Malignant**: 210 cases (invasive ductal carcinoma, lobular carcinoma) characterized by irregular margins, non-parallel orientation (taller than wide), microcalcifications, and posterior acoustic shadowing.
3. **Ground Truth Annotations**:
   - Manually segmented binary masks drawn by expert radiologists from the National Cancer Institute, Cairo University.
   - Multi-lesion cases contain multiple ground-truth mask files.
4. **Primary Benchmark Tasks**:
   - **Binary & 3-Class Classification**: Distinguishing Benign vs. Malignant vs. Normal using CNNs/ViTs.
   - **Semantic Segmentation**: Delineating the precise tumor contour (evaluated via Dice Similarity Coefficient, IoU, and Hausdorff Distance).
5. **Key Challenges & Domain Insights**:
   - Extreme class imbalance between benign and malignant cases.
   - High speckle noise, low contrast, inhomogeneous internal echoes, and acoustic shadowing obscuring deep tumor boundaries.
   - Multiple lesions in a single field of view requiring instance-aware separation.
