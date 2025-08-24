# GScream with Depth Confidence Weighting

This repository contains an implementation of GScream with depth confidence weighting, building upon the original [GScream](https://github.com/W-Ted/GScream) work. The implementation focuses on improving depth estimation quality through confidence weighting mechanisms.

## Installation

1. Clone the repository:
```bash
git clone https://github.com/gulshanhatzade/GScream-Depth-Confidence-Weighting.git
cd GScream-Depth-Confidence-Weighting
```

2. Set up the conda environment:
```bash
conda env create -f gscream.yaml
conda activate gscream
```

3. Install dependencies:
```bash
cd submodules/diff-gaussian-rasterization/ && pip install -e .
cd ../simple-knn && pip install -e .
cd ../..
```

**Note for different GPU architectures**: 
- For RTX 3090: Use default settings (compute_86, sm_86)
- For Tesla V100: Modify to 'compute_70' and 'sm_70' in `submodules/diff-gaussian-rasterization/setup.py` before compiling

## Dataset

Download the processed SPIN-NeRF dataset with Marigold depths:

```bash
cd data
pip install gdown
gdown 'https://drive.google.com/uc?id=1EODx3392p1R7CaX5bazhkDrfrDtnqJXv'
unzip spinnerf_dataset_processed.zip
cd ..
```

## Training & Evaluation

To train the model with depth confidence weighting:

```bash
python scripts/run.py --use_confidence_weighting=True
```

Configuration options can be modified in `configs/default.yaml`:
- `depth_confidence_weight`: Weight for depth confidence term
- `confidence_threshold`: Threshold for valid depth confidence
- Other model parameters

## Modifications from Original GScream

1. Added depth confidence weighting mechanism
2. Modified loss function to incorporate depth confidence
3. Updated data loading for confidence maps
4. Enhanced visualization of confidence-weighted depth

## Results

[Add your results/visualizations here]

## Acknowledgements

This project builds upon:
- [GScream](https://github.com/W-Ted/GScream)
- [Scaffold-GS](https://city-super.github.io/scaffold-gs)
- [SPIN-NeRF](https://spinnerf3d.github.io/) dataset
- Depth estimation from [Marigold](https://marigoldmonodepth.github.io/)

## Citation

```bibtex
@inproceedings{original_gscream,
  title={GScream: Learning 3D Geometry and Feature Consistent Gaussian Splatting for Object Removal},
  author={Yuxin Wang, Qianyi Wu, Guofeng Zhang, Dan Xu},
  booktitle={ECCV},
  year={2024}
}
```
