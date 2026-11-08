# RoMAP

<p align="center">
  <strong>Robust Multi-modal Affordance Prediction</strong><br>
  <em>Language-guided 3D affordance prediction under non-ideal point clouds</em>
</p>

<p align="center">
  <a href="./index.html">Project page source</a> ·
  <a href="./figure">Figures</a> ·
  <a href="./video">Qualitative animations</a>
</p>

## Overview

**RoMAP** studies language-guided 3D affordance prediction when object point clouds are affected by outliers, irregular sampling, and missing surface regions. Given an object observation and a natural-language query (e.g., *Where can I grasp this object?*), the goal is to localize the corresponding functional region at the point level.

The approach follows a **calibrate-then-enhance** design:

- **RFC — Reliability-Aware Feature Calibration:** uses point features and local geometric cues to adjust how much potentially unreliable observations contribute during feature interaction.
- **CFE — Context-aware Feature Enhancement:** uses calibrated features to retrieve and aggregate relevant context from other visible points, including points outside a local spatial neighborhood, to compensate for incomplete local observations.

For image inputs, a **mask-guided 3D Gaussian Splatting** reconstruction stage provides an object-centric 3D representation. Point features are subsequently combined with language information for per-point affordance prediction.

## Motivation

<p align="center">
  <img src="figure/motivation.png" alt="RoMAP motivation illustration" width="950">
</p>

Point-cloud degradations can affect affordance localization differently depending on their spatial relationship to the region specified by the language query. RoMAP focuses on reliable feature calibration and complementary context aggregation under these non-ideal observations.

## Framework

<p align="center">
  <img src="figure/framework.png" alt="Overview of the RoMAP framework" width="950">
</p>

**Pipeline:** Object-centric reconstruction (when using images) → hierarchical point-cloud encoding → **RFC** → **CFE** → language-guided affordance prediction.

## Results and visualizations

### Comparison on HANDAL

<p align="center">
  <img src="figure/HANDAL.png" alt="Affordance prediction comparison on HANDAL" width="950">
</p>

The figure summarizes the HANDAL comparison under reconstructed and native point-cloud evaluation settings.

### Qualitative robustness examples

The animations below show ground-truth (GT) and predicted affordance regions for individual queries.

| Query | Ground truth | RoMAP prediction |
|:---:|:---:|:---:|
| Faucet — Open | <img src="video/407_Faucet_open_GT.gif" width="270" alt="Ground truth for faucet open"> | <img src="video/407_Faucet_open_Pred.gif" width="270" alt="RoMAP prediction for faucet open"> |
| Scissors — Cut | <img src="video/493_Scissors_cut_GT.gif" width="270" alt="Ground truth for scissors cut"> | <img src="video/493_Scissors_cut_Pred.gif" width="270" alt="RoMAP prediction for scissors cut"> |

More visualizations are available in [`video/`](./video).

### Qualitative ablation

<p align="center">
  <img src="figure/ablation.png" alt="RoMAP qualitative ablation results" width="950">
</p>

## Repository contents

- [`index.html`](./index.html) — project-page HTML.
- [`figure/`](./figure) — motivation, framework, result, and ablation illustrations.
- [`video/`](./video) — ground-truth/prediction animations.

**Status:** This repository currently contains the project webpage and visual assets. Training and inference instructions are not included here yet.

## Contact

For project-related questions, please contact [long.tian@swjtu.edu.cn](mailto:long.tian@swjtu.edu.cn).
