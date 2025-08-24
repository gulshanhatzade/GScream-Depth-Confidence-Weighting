
## Installation

```
git clone https://github.com/W-Ted/GScream.git

cd GScream Code
conda env create -f gscream.yaml
conda activate gscream

cd submodules/diff-gaussian-rasterization/ && pip install -e .
cd ../simple-knn && pip install -e .
cd ../..
```
Since we used RTX 3090, in the [setup.py](https://github.com/W-Ted/GScream/blob/e7cc71bf3e878d02d15b524fdb44f038eba59a2a/submodules/diff-gaussian-rasterization/setup.py#L29), we hardcoded the gencode=arch with 'compute_86' and 'sm_86' when compiling 'diff-gaussian-rasterization'. For Tesla V100, you may try changing it to 'compute_70' and 'sm_70' before compiling. [issue#4](https://github.com/W-Ted/GScream/issues/4)

## Dataset

We provide the processed SPIN-NeRF dataset with Marigold depths [here(~9.7G)](https://drive.google.com/file/d/1EODx3392p1R7CaX5bazhkDrfrDtnqJXv/view?usp=sharing). You could download it to the ''data'' directory and unzip it. 

```
cd data
pip install gdown && gdown 'https://drive.google.com/uc?id=1EODx3392p1R7CaX5bazhkDrfrDtnqJXv'
unzip spinnerf_dataset_processed.zip && cd ..
```

Please refer to [SPIN-NeRF dataset](https://drive.google.com/drive/folders/1N7D4-6IutYD40v9lfXGSVbWrd47UdJEC) for the details of this dataset.  

## Training & Evaluation

```
python scripts/run.py
```
All the results will be save in the ''outputs'' directory. 

## Acknowledgements

This project is built upon [Scaffold-GS](https://city-super.github.io/scaffold-gs). The in-painted images are obtained by [SD-inpainting](https://huggingface.co/runwayml/stable-diffusion-inpainting) and [LaMa](https://github.com/advimman/lama). The depth maps are estimated by [Marigold](https://marigoldmonodepth.github.io/). The dataset we used is proposed by [SPIN-NeRF](https://spinnerf3d.github.io/). Kudos to these researchers. 

     booktitle={ECCV},
     year={2024}
     }
```
