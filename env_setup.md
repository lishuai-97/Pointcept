## Pointcept Environment Setup Guide

- [Pointcept Environment Setup Guide](#pointcept-environment-setup-guide)
  - [Installation](#installation)

---
### Installation

**Requirements**
- Ubuntu: 18.04 and above. (**22.04 LTS** recommended)
- CUDA: 11.3 and above. (**12.4** recommended)
- PyTorch: 1.10.0 and above. (**2.5.0** recommended)
- Python: 3.8 and above. (**3.10** recommended)


```bash
# install the repo
git clone https://github.com/lishuai-97/Pointcept.git
cd Pointcept

# create conda environment
conda create -n pointcept python=3.10 -y
conda activate pointcept
# Choose version you want here: https://pytorch.org/get-started/previous-versions/
conda install pytorch==2.5.0 torchvision==0.13.1 torchaudio==0.20.0 pytorch-cuda=12.4 -c pytorch -y
conda install h5py pyyaml -c anaconda -y
conda install sharedarray tensorboard tensorboardx wandb yapf addict einops scipy plyfile termcolor timm -c conda-forge -y

pip install pytorch-cluster pytorch-scatter pytorch-sparse -f https://data.pyg.org/whl/torch-2.5.0+cu124.html
pip install torch-geometric

# spconv (SparseUNet)
# refer https://github.com/traveller59/spconv
pip install spconv-cu124

# PPT (clip)
pip install ftfy regex tqdm
pip install git+https://github.com/openai/CLIP.git

# PTv1 & PTv2 or precise eval
cd libs/pointops
# usual
python setup.py install
# docker & multi GPU arch
TORCH_CUDA_ARCH_LIST="ARCH LIST" python setup.py install
# e.g. 7.5: RTX 3000; 8.0: a100 More available in: https://developer.nvidia.com/cuda-gpus
TORCH_CUDA_ARCH_LIST="7.5 8.0" python setup.py install
cd ../..

# Open3D (visualization, optional)
pip install open3d
```