# CL-HPE

**CL-HPE: Enhancing Human Pose Estimation via Lightweight Structural Attention Mechanisms**

---

## ✨ Overview 

CL-HPE is a lightweight attention-driven human pose estimation framework designed to balance **accuracy** and **efficiency** for deployment on resource-constrained devices. It introduces three key lightweight modules:

* **DDA (Decoupled and Distributed Attention)** for enhancing channel/spatial representation and improving distal joint localization
* **LCS (LiteCSP-SiLU Block)** to replace heavy blocks and drastically reduce parameters/FLOPs
* **LDU (Lightweight Dynamic Upsampling)** for content-adaptive refinement during upsampling

CL-HPE achieves **73.4% AP** and **76.3% AR** on **MSCOCO** with about **5.4M parameters** and **2.7 GFLOPs**, while reducing parameters by ~**80%** compared to the HRNet baseline. 

---

## ⭐ Features 

* **Lightweight but strong**: ~80% parameter reduction with minimal accuracy drop 
* **Better distal joints**: attention and upsampling design focuses on wrists/ankles under compression 
* **Plug-and-play modules**: DDA / LCS / LDU can be integrated into HRNet-style backbones 
* **End-to-end trainable**: heatmap regression with MSE loss 

---

## 🧪 Experimental Environment 

- Python >= 3.8
- PyTorch + CUDA 
- MMCV / MMEngine / MMPose 

## 🏗️ Architecture 

```
Input Image
  → Backbone (HRNet-style multi-branch)
      +DDA
      +LCS
  → Multi-scale Feature Fusion
      +LDU
  → Heatmap Head
  → Keypoint Decoding

```
---

## 🚀 Quick Start 

### 1) Clone this repo 

```bash
git clone https://github.com/SCNU-RISLAB/CL-HPE.git
cd CL-HPE
```

### 2) Install dependencies 

```bash

pip install -r requirements.txt
```


---

## 📦 Dataset Preparation 

### Supported datasets 

* **MSCOCO** (main benchmark) 
* **MPII** (ablation study) 

### Recommended folder structure 

```
dataset/
  coco/
    images/
      train2017/
      val2017/
    annotations/
      person_keypoints_train2017.json
      person_keypoints_val2017.json

  mpii/
    images/
    annotations/
```


---

## 🏋️ Training 

Paper setting (reference):

* input resolution: **256×192** 
* optimizer: **Adam**, weight decay **0.001** 
* epochs: **210** 
* learning rate: **2e-4 (constant)** 
* trained **from scratch** (no pretrained weights) 

Example command:

```bash
python train.py \
  --config  configs\body_2d_keypoint\topdown_heatmap\cl_hpe_256x192.py
```

---




## 📌 Notes 

* This repo is intended to reproduce the paper results and provide clean module implementations.
* For fair comparison, the paper reports training **from scratch** and focuses on the **accuracy–efficiency trade-off**.

---

## 📄 Citation

If you use this repository or models in your work, please cite:
```
@article{liu2025clhpe,
  title  = {CL-HPE: Enhancing Human Pose Estimation via Lightweight Structural Attention Mechanisms},
  author = {Liu, Yuehan and She, Shuyi and Li, Yating and Tang, Xiaoyu},
  note   = {Under review at The Visual Computer},
  year   = {2025}
}
```

## ✉️ Contact 

If you have any questions or collaborations, please reach out to **[202481313616@m.scnu.edu.cn](mailto:202481313616@m.scnu.edu.cn)** 


---

## 🙏 Acknowledgement 

This work benefits from the open-source MMPose project (OpenMMLab): https://github.com/open-mmlab/mmpose

---


## 🌟 Star 🌟

If you find this project helpful, please consider giving it a ⭐!
