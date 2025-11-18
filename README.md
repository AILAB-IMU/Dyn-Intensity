# 📚 Dyn-Risk Dataset

### Dynamic Wrist-Motion Dataset for Multi-Level Risk Detection

For questions or suggestions, please contact **20231330@sungshin.ac.kr**.😊

---

# I. 📡 Data Collection

## I.1. 🛠 Hardware Setup

All recordings were collected using a **Samsung Galaxy Watch 7 (SM-L300)** worn on the dominant wrist.

- **Sensor:** 3-axis accelerometer
- **Sampling frequency:** 50 Hz
- **Units:** raw acceleration in _g_ (gravity)
- **Operating system:** Wear OS 5
- **Processor:** Exynos W1000
- **RAM:** 2 GB

All experiments were conducted in an **indoor sports facility 🏟**, ensuring stable wireless performance and consistent environmental conditions.

---

## I.2. 👤 Subjects

A total of **8 adult female subjects** participated in the data collection.

All participants wore the smartwatch on their **dominant wrist** and agreed to the use of their anonymized data for research purposes.

Recordings were supervised to ensure consistent placement and proper execution of the defined activities.

---

## I.3. 🎬 Data Collection Protocol

Each participant performed a predefined set of **static, dynamic, and high-intensity wrist motions**, repeated multiple times to capture natural variability in amplitude, speed, and intensity.

This range of actions allows the dataset to represent diverse wrist-motion patterns relevant to multi-level risk detection.

The dataset includes the following activities:

- **Lying 🛏️** — quiet resting posture with minimal movement.
- **Sitting 🪑** — seated posture with small natural adjustments.
- **Watching TV 📺** — relaxed sitting or lying while watching television.
- **Board work ✍️** — standing writing or erasing on a board with moderate arm swings.
- **Palm pushing ✋➡️** — repetitive forward pushing motions resembling resistance or self-defense movement.
- **Dynamic handclap 👏🔥** — vigorous clapping with strong upper-arm motion.
- **Jumping jacks 🦘** — full-body jumping with coordinated arm–leg spreading.
- **Running 🏃‍♀️💨** — high-speed sprinting generating strong wrist and body acceleration.
- **Slalom running 🏃‍♂️🌀** — zig-zag running requiring rapid direction changes.
- **Rope jumping 🤾‍♀️** — repetitive rope-skipping motion with rhythmic impacts.
- **Ascending stairs ⬆️🏢** — moving upstairs across multiple floors.
- **Descending stairs ⬇️🏢** — moving downstairs in a controlled manner.
- **User_level5 ⚠️🔥** — simulated high-intensity struggle motion with rapid arm swings, pushing forces, and evasive actions.

---

## I.4. 📊 Summary of Collected Data

All uploaded files consist of **pre-computed feature sequences** derived from the original smartwatch accelerometer signals.

For each activity, the raw x-, y-, and z-axis acceleration data were segmented using a fixed sliding-window configuration, and four statistical features were extracted from each window:

the SVM mean, SVM variance, ΔSVM mean, and ΔSVM standard deviation.

No additional filtering or smoothing was applied beyond this feature extraction process.

Each CSV file contains a continuous sequence of these four feature values, representing multiple repetitions of each activity and preserving the natural variability of wrist motion.

---

# II. 🗂 Data Format (Feature-Based Dataset)

## II.1. 📁 Raw File Structure

The dataset is organized in a **subject-level directory structure**,

where each subject folder contains one CSV file per performed activity.

Each file consists of a continuous sequence of **four pre-computed features**,

derived from raw accelerometer signals using a fixed sliding-window configuration.

Example directory structure:

```
Dyn-Risk/
  ├── subject01/
  │     ├── jumping_jacks.csv
  │     ├── rope_jumping.csv
  │     └── ...
  ├── subject02/
  └── ...

```

Every CSV file follows a consistent feature-based format,

representing window-level statistics extracted from the original wrist-motion signals.

---

## II.2. 📄 CSV Data Composition

Each CSV file contains the following four feature values computed for every window:

- **svm_mean** — mean Signal Vector Magnitude within the window
- **svm_var** — variance of the Signal Vector Magnitude within the window
- **delta_svm_mean** — mean change in SVM between consecutive windows
- **delta_svm_std** — standard deviation of SVM changes between consecutive windows

Example CSV snippet:

```
svm_mean, svm_var, delta_svm_mean, delta_svm_std
0.123, 0.0048, 0.115, 0.0071
0.156, 0.0061, 0.142, 0.0084
...
```

All feature values were computed directly from the original accelerometer recordings,

and no additional filtering, interpolation, or normalization was applied beyond the

defined feature extraction procedure.

This format allows the data to be used immediately for model training or analysis,

while preserving natural variability in wrist-motion dynamics in a compact and interpretable form.

---

# III. 📥 Usage Example

A basic example of how to load the dataset in Python:

```
import pandas as pd

df = pd.read_csv("Dyn-Risk/subject01/jumping_jacks.csv")
print(df.head())
```

---

# IV. 📜 License (CC BY-NC 4.0)

The Dyn-Risk Dataset is licensed under the
📄 Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0).

✔ Allowed:

Research and educational use

Non-commercial projects

Modification, preprocessing, and derived works

Sharing analysis results with attribution

---

❌ Not Allowed:

Commercial use

Integration into paid products or commercial services

Use in corporate R&D pipelines

---

📌 Attribution Requirement

If you use this dataset, please cite:

Dyn-Risk Dataset (2025), Sungshin Women’s University.
