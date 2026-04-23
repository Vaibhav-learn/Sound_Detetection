# PVR Lab Project — Underwater Vessel Noise Classification (ShipsEar / QiandaoEar22)

## Group Members
- Member 1: [Vaibhav Balwant Singh] — SAP ID: 500122528
- Member 2: [Mann Rana] — SAP ID: 500120528
- Member 3: [Mohammad Asad Saifi] — SAP ID: 500120661
---

## Dataset

- **Dataset:** QiandaoEar22 (Du & Hong, 2024)
- **GitHub:** https://github.com/xiaoyangdu22/QiandaoEar22
- **Papers:** https://arxiv.org/abs/2406.04354 | https://arxiv.org/abs/2406.04353v1
- **Classes:** SpeedBoat · KaiYuan · UUV · noise_target
- **Google Drive (raw data):** [PASTE YOUR DRIVE LINK HERE]

> The notebook auto-downloads the dataset via `git clone` on first run.  
> If cloning fails, synthetic data is generated automatically as a fallback.

---

## Project Structure

```
submission/
├── qiandaoear2.ipynb
├── oceanship.ipynb
├── report/                      
│   └── pvr_report.pdf                      # Compiled IEEE report
├── README.md                               # This file
└── outputs_qiandaoear22/                   # Generated on first run
│    ├── dataset_manifest.csv
│    ├── splits.json
│    ├── X_train.npy / X_val.npy / X_test.npy
│    ├── y_train.npy / y_val.npy / y_test.npy
│    ├── scaler.pkl
│    ├── knn.pkl / svm.pkl / rf.pkl
│    ├── cnn_scratch.pth / resnet18.pth / resnet50.pth
│    ├── final_results.csv
│    ├── ablation.csv
│    ├── multiseed_rf.csv
│    └── *.png  (all plots)
└── outputs_oceanship/
    ├── dataset_manifest.csv
    ├── splits.json
    ├── X_train.npy / X_val.npy / X_test.npy
    ├── y_train.npy / y_val.npy / y_test.npy
    ├── scaler.pkl
    ├── knn.pkl / svm.pkl / rf.pkl
    ├── cnn_scratch.pth / resnet18.pth / resnet50.pth
    ├── final_results.csv
    ├── ablation.csv
    ├── multiseed_rf.csv
    └── *.png  (all plots)
```

---

## Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| Python | 3.9+ | Runtime |
| numpy | any | Numerical ops |
| pandas | any | Data handling |
| matplotlib | any | Plotting |
| seaborn | any | Heatmaps |
| librosa | 0.10.2 | Audio processing |
| soundfile | any | WAV I/O |
| scipy | any | Signal processing |
| scikit-learn | any | Classical ML |
| torch | any | Deep learning |
| torchvision | any | Pretrained CNNs |
| tqdm | any | Progress bars |
| joblib | any | Model saving |
| Pillow | any | Image resizing |

---

## How to Run

### 1. Install dependencies

```bash
pip install librosa==0.10.2 soundfile matplotlib seaborn numpy scipy pandas \
            tqdm joblib scikit-learn Pillow torch torchvision
```

Or let the notebook install them automatically — the first cell does this via `subprocess`.

### 2. Open the notebook

```bash
jupyter notebook pvr_qiandaoear22_complete_fixed.ipynb
```

### 3. Run all cells top-to-bottom

**Section 0** — Installs packages and downloads the dataset via `git clone`.  
If the clone fails (no internet / firewall), synthetic data is auto-generated so all subsequent cells still run.

**Parts 1–6** — Run in order. Each part depends on variables set in earlier parts.

> **Do NOT skip cells.** Variables like `manifest`, `SPLITS`, `X_tr`, `knn`, `CNN_M` etc. are defined progressively.

### 4. Expected runtime

| Section | CPU time (approx.) |
|---------|-------------------|
| Section 0 (clone) | 1–3 min |
| Part 2 (EDA) | 2–5 min |
| Part 3 (preprocessing) | 5–15 min |
| Part 4 (feature extraction) | 10–20 min |
| Part 5 (classical ML) | 5–10 min |
| Part 5 (deep learning, CPU) | 60–120 min |
| Part 5 (deep learning, GPU) | 10–20 min |
| Part 6 (evaluation) | 5–10 min |

GPU is **strongly recommended** for Part 5 deep learning training.  
CUDA is detected automatically: `DEVICE = torch.device("cuda" if torch.cuda.is_available() else "cpu")`

### 5. Outputs

All outputs (CSV files, `.npy` arrays, `.pkl` models, `.pth` weights, plots) are saved automatically to `./outputs_qiandaoear22/`.

---

## Hardware / Software Configuration

- **OS:** Windows 10 / 11 (tested), Linux/macOS compatible
- **Python:** 3.9–3.12
- **GPU (optional):** NVIDIA CUDA-compatible GPU (tested on RTX 3060)
- **RAM:** Minimum 8 GB recommended (16 GB for deep learning)
- **Disk:** ~2 GB free for dataset + outputs

---

## References

- Santos-Domínguez et al. (2016). *ShipsEar: An underwater vessel noise database.* Applied Acoustics. https://doi.org/10.1016/j.apacoust.2016.06.008  
- Du & Hong (2024). *QiandaoEar22 dataset.* arXiv:2406.04354
