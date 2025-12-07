# 📚 Dyn-Risk & PAMAP2 Wrist-Motion Feature Dataset

### Dataset Accompanying the Paper

_“On-Device Real-Time Multi-Level Motion Activity Intensity Recognition Using Smartwatch Accelerometer”_

This repository contains two wrist-motion **feature-level datasets** used in our research on **real-time, on-device, multi-level motion intensity recognition**:

1. **Dyn-Risk Dataset** — our self-collected smartwatch accelerometer dataset
2. **Processed PAMAP2 Wrist Dataset** — wrist-accelerometer subset of the public PAMAP2 dataset, preprocessed to match the Dyn-Risk feature format

Both datasets provide **sliding-window statistical features** (svm_mean, svm_std, d_svm_mean, d_svm_std), ensuring license compliance and ease of use.

For inquiries: **20231330@sungshin.ac.kr**

---

# 🗂 Repository Structure

```
Dyn-Risk-Dataset/
│
├── Dyn-Risk/                 # Our self-collected 50Hz wrist-motion feature dataset
│     ├── subject01/
│     ├── subject02/
│     └── ...
│
├── PAMAP2/                   # Processed PAMAP2 wrist-motion feature dataset
│     ├── subject101/
│     ├── subject102/
│     └── ...
│
├── LICENSE                   # CC BY-NC 4.0
└── README.md
```

---

# 1. 📡 Dyn-Risk Dataset (Self-Collected)

## 1.1 🛠 Hardware Setup

All signals were recorded with a **Samsung Galaxy Watch 7 (SM-L300)** on the dominant wrist.

- **Sensor**: 3-axis accelerometer
- **Frequency**: 50 Hz
- **Units**: raw acceleration in _g_
- **OS**: Wear OS 5
- **Environment**: Indoor sports facility

---

## 1.2 👤 Subjects

A total of **8 adult female subjects** participated voluntarily, wearing the watch on their dominant wrist.  
All recordings were supervised for consistency and safety.

---

## 1.3 🎬 Recorded Activities

Dyn-Risk includes **static, dynamic, and high-intensity motions**, such as:

- Lying
- Sitting
- Watching TV
- Board work
- Palm pushing
- Dynamic handclap
- Jumping jacks
- Running
- Slalom running
- Rope jumping
- Ascending stairs
- Descending stairs
- User_Level5 (synthetic struggle/defense motion)

---

## 1.4 📊 Feature Description

Raw accelerometer data were segmented using a sliding window (**300 samples**, step **150**), and four statistical features were computed:

| Feature        | Description                  |
| -------------- | ---------------------------- |
| **svm_mean**   | Mean Signal Vector Magnitude |
| **svm_std**    | SVM standard deviation       |
| **d_svm_mean** | Mean absolute change in SVM  |
| **d_svm_std**  | Std of SVM changes           |

---

# 2. 🎧 Processed PAMAP2 Wrist-Motion Dataset

This repository includes only **processed, feature-level PAMAP2 wrist-acceleration data**  
to ensure **license compatibility** (raw PAMAP2 data cannot be redistributed).

We extracted and processed only the **wrist-related activities** used in our study, then applied:

- **100 → 50 Hz downsampling** (anti-alias filtering)
- **Sliding-window feature extraction** identical to Dyn-Risk

This ensures the two datasets are **directly compatible** for training.

---

## 2.1 📁 PAMAP2 Activities Included

- Lying
- Sitting
- Standing
- Watching TV
- Computer work
- Car driving
- Ironing
- Folding laundry
- Vacuum cleaning
- Cycling
- Walking

All files follow the same feature format as Dyn-Risk.

---

# 3. 🗂 Feature File Structure

Example:

```
PAMAP2/subject101/walking.csv
Dyn-Risk/subject03/jumping_jacks.csv
```

Each CSV contains:

```
svm_mean, svm_std, d_svm_mean, d_svm_std
0.123,     0.0048,  0.115,      0.0071
0.156,     0.0061,  0.142,      0.0084
...
```

---

# 4. 📥 Usage Example (Python)

```python
import pandas as pd

df = pd.read_csv("Dyn-Risk/subject01/jumping_jacks.csv")
print(df.head())

df2 = pd.read_csv("PAMAP2/subject101/walking.csv")
print(df2.head())
```

---

# 5. 📜 License

The Dyn-Risk Dataset and processed PAMAP2 derivatives are released under:

## **Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0)**

✔ Research & educational use  
✔ Modification and derived works (non-commercial)  
✔ Redistribution with attribution

❌ Commercial use prohibited  
❌ Integration into commercial or proprietary systems

See the full license in the **LICENSE** file.

---

# 6. 📌 Citation

If you use this dataset, please cite:

```
Dyn-Risk Dataset (2025). Sungshin Women’s University.
Available at: https://github.com/AILAB-IMU/Dyn-Risk-Dataset
```

---

# 7. 💬 Contact

For questions, please contact: **20231330@sungshin.ac.kr**
