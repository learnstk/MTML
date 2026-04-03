# MTML
## Datasets

This project is evaluated on two publicly available motor imagery EEG datasets: **BCI Competition IV Dataset 2A** and the **High-Gamma Dataset**.

### BCI Competition IV Dataset 2A

The **BCI Competition IV Dataset 2A** is a four-class motor imagery EEG dataset collected from **9 subjects**. Each subject performed **left hand, right hand, tongue, and foot** motor imagery tasks. The dataset contains **288 trials per subject**, with **72 trials for each class**, and the trials are divided into temporally separated **training** and **testing** sessions.

In our experiments, the model is trained on each subject’s training set and evaluated on the corresponding test set. EEG signals were recorded using **22 channels** at a sampling rate of **250 Hz** with amplifiers of **100 μV resolution**. In each trial, a visual cue appears at **2 s**, followed by the motor imagery period from **3 s to 6 s**. The raw signals were preprocessed with a **0.5–100 Hz bandpass filter** and a **50 Hz notch filter**, and artifactual trials were flagged through expert inspection.

### High-Gamma Dataset

The **High-Gamma Dataset** is a large-scale EEG dataset containing **14 subjects** performing four-class motor imagery tasks: **left hand, right hand, feet, and rest**. Each subject completed **13 runs**, resulting in approximately **1000 trials per subject** (**963.1 ± 150.9** on average), with each trial corresponding to **4-second executed movements**.

Following the standard split used in our experiments, the first **11 runs** (**880 trials**) are used for training, and the last **2 runs** (**160 trials**) are used for testing. EEG signals were originally collected from **128 channels** and resampled to **250 Hz**. The recording setup included electromagnetic shielding, specialized amplifiers, and actively shielded electrodes. To maintain consistency with the original implementation in this work, we use **44 selected channels** for experiments.

### Preprocessing Used in This Work

To preserve the feature learning capability of the EEG models, only minimal preprocessing was applied. Specifically, we extracted a **4.5 s EEG segment** from **0.5 s before** to **4 s after** the onset of the motor imagery cue. The EEG signals were then filtered using either a **0–38 Hz** bandpass filter or a **4–38 Hz** bandpass filter before being fed into the feature extractor.

### Recommended dependencies

You can install the required Python packages with:

```bash
braindecode==0.4.7
python==3.8
pytorch==2.2.2
pytorch-metric-learning==2.6.0
