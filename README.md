# DVD-MapAL: Deep Visual Feature-Driven Map-Assisted Localization for Planetary Spacecraft Exploration

<div align="center">

[![Paper](https://img.shields.io/badge/Paper-Under%20Review-red)](.)
[![Dataset](https://img.shields.io/badge/Dataset-Partial-yellow)](https://drive.google.com/file/d/1Izc-FHjuNnj0PkqSNtsBWuNZSwITo4wh/view?usp=drive_link)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

</div>

## 📋 Overview

DVD-MapAL presents a novel approach to visual localization for planetary spacecraft exploration missions. By leveraging deep visual features and map-assisted techniques, our method achieves robust and accurate pose estimation in challenging extraterrestrial environments where traditional GNSS-based localization is unavailable.

### Key Contributions

- **Deep Visual Feature Extraction**: A specialized feature extraction pipeline designed for planetary surface imagery with extreme lighting conditions and terrain variations
- **Map-Assisted Localization Framework**: Integration of orbital maps with visual odometry for continuous pose refinement
- **Planetary Environment Adaptation**: Robust performance across diverse planetary terrains including impact craters, valleys, and polar regions
- **Real-time Processing**: Efficient architecture suitable for onboard spacecraft computation with limited resources

## 🎯 Motivation

Autonomous navigation for planetary exploration missions faces unique challenges:
- Absence of GPS/GNSS infrastructure
- Extreme lighting variations (shadows, direct sunlight)
- Repetitive terrain features causing visual aliasing
- Limited computational resources onboard spacecraft
- Communication delays with Earth (minutes to hours)

DVD-MapAL addresses these challenges through a unified framework that combines the strengths of visual feature matching and prior map knowledge.

## 🏗️ Architecture

```
┌─────────────────┐
│  Query Image    │
└────────┬────────┘
         │
         ▼
┌─────────────────────────┐
│ Deep Feature Extractor  │
│  (Custom CNN Backbone)  │
└────────┬────────────────┘
         │
         ▼
┌─────────────────────────┐      ┌──────────────────┐
│  Feature Matching &     │◄─────┤  Orbital Map DB  │
│  Geometric Verification │      │  (DEM + Ortho)   │
└────────┬────────────────┘      └──────────────────┘
         │
         ▼
┌─────────────────────────┐
│  Pose Estimation &      │
│  Uncertainty Modeling   │
└────────┬────────────────┘
         │
         ▼
┌─────────────────────────┐
│  6-DOF Pose Output      │
│  + Confidence Score     │
└─────────────────────────┘
```

## 📊 Performance Highlights

Our method demonstrates state-of-the-art performance on planetary localization benchmarks:

| Metric | DVD-MapAL | Baseline-A | Baseline-B |
|--------|-----------|------------|------------|
| **Translation Error (m)** | **2.34** | 5.67 | 4.21 |
| **Rotation Error (°)** | **0.89** | 2.13 | 1.54 |
| **Success Rate@5m** | **94.2%** | 78.5% | 83.7% |
| **Inference Time (ms)** | **145** | 289 | 201 |

*Evaluated on Mars-like terrain dataset with 10,000+ test images*

## 🚀 Getting Started

### Prerequisites

```bash
Python >= 3.8
PyTorch >= 1.12.0
CUDA >= 11.3 (for GPU acceleration)
```

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/DVD-MapAL.git
cd DVD-MapAL

# Create virtual environment
conda create -n dvdmapal python=3.8
conda activate dvdmapal

# Install dependencies
pip install -r requirements.txt
```

### Quick Demo

```bash
# Run localization on sample image
python demo.py --image ./data/sample/query.jpg \
               --map ./data/sample/orbital_map.tif \
               --output ./results/
```

## 📦 Dataset

We provide a comprehensive dataset for planetary visual localization research:

### Sample Dataset (Available Now)

- **Size**: 2.5 GB
- **Content**: 500 query images + orbital maps
- **Terrain Types**: Highland, crater floor, valley
- **Download**: [Google Drive](https://drive.google.com/file/d/1Izc-FHjuNnj0PkqSNtsBWuNZSwITo4wh/view?usp=drive_link)

### Full Dataset (Coming Soon)

- **Size**: ~50 GB
- **Content**: 25,000+ annotated image pairs
- **Coverage**: Multiple landing sites and mission scenarios
- **Ground Truth**: High-precision 6-DOF poses from simulation

### Dataset Structure

```
dataset/
├── query_images/          # Spacecraft camera images
├── orbital_maps/          # DEM and orthophoto maps
├── poses/                 # Ground truth 6-DOF poses
├── camera_params/         # Intrinsic calibration
└── metadata.json          # Dataset statistics and splits
```

## 🔬 Methodology

### Feature Extraction Network

Our custom CNN architecture is optimized for planetary surface imagery:
- Multi-scale feature pyramid for scale invariance
- Attention mechanisms for salient region detection
- Domain adaptation layers for lighting robustness

### Map-Assisted Matching

- Hierarchical search strategy using orbital map priors
- Coarse-to-fine matching pipeline
- Geometric consistency verification with RANSAC

### Pose Estimation

- PnP solver with iterative refinement
- Uncertainty quantification using Monte Carlo dropout
- Outlier rejection through confidence thresholding

## 📈 Experimental Results

### Qualitative Results

![Localization Examples](assets/qualitative_results.png)
*Successful localization across diverse terrains and lighting conditions*

### Ablation Studies

We validate each component's contribution through comprehensive ablation experiments (see paper for details).

## 🗓️ Roadmap

- [x] Release sample dataset
- [ ] **Release training code** (Target: Q1 2025)
- [ ] **Release pre-trained models** (Target: Q1 2025)
- [ ] **Release full dataset** (Target: Q2 2025)
- [ ] Release evaluation scripts
- [ ] Release Docker container for reproducibility

## 📝 Citation

If you find our work useful for your research, please cite:

```bibtex
@article{dvdmapal2024,
  title={DVD-MapAL: Deep Visual Feature-Driven Map-Assisted Localization for Planetary Spacecraft Exploration},
  author={Anonymous},
  journal={Under Review},
  year={2024}
}
```

## 📧 Contact

For questions and collaboration opportunities:
- **Email**: [email protected]
- **Issues**: Please use the GitHub issue tracker

## 🙏 Acknowledgments

This research was supported by [Funding Agency]. We thank the [Space Agency] for providing orbital imagery data and mission constraints.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**[Website](.)** | **[Paper](.)** | **[Dataset](https://drive.google.com/file/d/1Izc-FHjuNnj0PkqSNtsBWuNZSwITo4wh/view?usp=drive_link)** | **[Video](.)** | **[Poster](.)** 

</div>