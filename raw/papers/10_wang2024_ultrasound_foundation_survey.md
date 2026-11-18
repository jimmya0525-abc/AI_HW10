# Foundation Models for Ultrasound Image Analysis: A Survey and Benchmarking Study

- **Authors**: Haoran Wang, Jiazhen Pan, Yingying Fang, Zhiwei Wang, Qi Dou, Pheng-Ann Heng
- **Affiliation**: The Chinese University of Hong Kong (CUHK); Shanghai AI Laboratory; Imperial College London
- **Venue**: Medical Image Analysis (MedIA) / arXiv:2401.12984, 2024
- **DOI / ArXiv**: arXiv:2401.12984

## Abstract
Ultrasound (US) imaging is the most accessible, safe, and real-time medical imaging modality worldwide. However, automated analysis faces formidable barriers: severe operator dependency, diverse acoustic artifacts, low tissue contrast, and significant domain shifts across scanner vendors and clinical probes. While foundation models (such as CLIP, Segment Anything Model / SAM, DINOv2, and multimodal LLMs) have revolutionized natural image processing and radiology (CT/MRI), ultrasound presents unique acoustic and physical characteristics that challenge standard architectures. This comprehensive survey provides the first systematic review of Foundation Models in Ultrasound (US-FMs). We review foundation architectures across three core paradigms: Vision Foundation Models (VFMs), Vision-Language Models (VLMs), and Self-Supervised Acoustic Pretraining. Furthermore, we establish an open multi-center benchmark across 14 ultrasound datasets covering cardiac, abdominal, obstetric, thyroid, and breast imaging, analyzing zero-shot generalization, parameter-efficient fine-tuning (PEFT), and clinical diagnostic robustness.

## Taxonomy & Core Analysis
1. **The Three Waves of Ultrasound AI**:
   - **Wave 1 (2015-2020: Task-Specific CNNs)**: Standard U-Net, ResNet, VGG trained from scratch on small, private single-center datasets (<1,000 images); highly prone to domain shifts.
   - **Wave 2 (2020-2022: Self-Supervised Pretraining & Vision Transformers)**: Contrastive learning (MoCo, SimCLR, USCL) and Swin-Unet adapting to temporal video sequences and multi-view echocardiograms.
   - **Wave 3 (2023-Present: Ultrasound Foundation Models & Multimodal Agents)**: Universal vision encoders (MedSAM, SAMUS, Ultra-FM), vision-language report generation models (BiomedCLIP, US-LLaVA), and real-time point-of-care ultrasound (POCUS) assistants.
2. **Ultrasound Foundation Model Design Patterns**:
   - **Domain Adaptation via Adapters / LoRA**: Freezing large ViT weights and inserting low-rank adaptation layers or acoustic feature conditioning modules to prevent catastrophic forgetting.
   - **Multi-task Prompt Engineering**: Combining point prompts, text prompts ("hypoechoic nodule with acoustic shadow"), and anatomical bounding boxes.
   - **Ultrasound Multi-Modal Vision-Language Alignment**: Jointly embedding ultrasound cine-loops with free-text sonographer sonographic reports using contrastive objectives.
3. **Open Challenges Identified in the Benchmark**:
   - **Acoustic Physics Blindness**: Standard vision transformers lack explicit awareness of beamforming physics, depth attenuation, sound speed inhomogeneities, and probe geometry.
   - **Vendor Domain Discrepancies**: Models trained on high-end cart-based systems (e.g. Philips EPIQ, GE Vivid E95) suffer 15-25% performance degradation on ultra-portable handheld scanners (e.g. Butterfly iQ, Clarius).
   - **Video Temporal Coherence**: 2D slice-by-slice foundation models flicker and lack temporal consistency when applied to dynamic cardiac and fetal ultrasound cine loops.
