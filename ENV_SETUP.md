# Installation and Setup of CUDA Toolkit 11.8 on Ubuntu 22.04

This guide provides step-by-step instructions for installing and setting up the CUDA Toolkit 11.8 on Ubuntu 22.04. The steps include downloading the CUDA repository key, installing the toolkit, and configuring environment variables.

## Step 1: Download the CUDA repository key

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
```

## Step 2: Install the CUDA repository key

```bash
sudo dpkg -i cuda-keyring_1.1-1_all.deb
```

## Step 3: Update the package list

```bash
sudo apt-get update
```

## Step 4: Install the CUDA Toolkit 11.8

```bash
sudo apt-get install cuda-toolkit-11-8
```

## Step 5: Open the bash configuration file

```bash
nano ~/.bashrc
```

## Step 6: Add environment variables (append to the end of ~/.bashrc)

```bash
export PATH=/usr/local/cuda-11.8/bin:$PATH
```

```bash
export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64:$LD_LIBRARY_PATH
```

## Step 7: Reload the bash configuration

```bash
source ~/.bashrc
```

## Step 8: Verify the installation

```bash
nvcc --version
```

# Installing Requirements

Follow these steps to set up the ReGen environment and install required packages.

```bash
conda env create -f setup.yml
```

```bash
conda activate regen
```

```bash
pip install --user 'nltk>=3.6.3'
```

**Important**: If you encounter PyTorch compatibility issues, uninstall the previous version and install the working version:

```
conda activate regen
pip uninstall torch torchvision torchaudio -y
pip install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 --index-url https://download.pytorch.org/whl/cu118
```

Install additional required dependencies:

```
conda activate regen
pip install scikit-learn beautifulsoup4==4.9.3 nervaluate
python -c "import nltk; nltk.download('punkt')"
python -c "import nltk; nltk.download('punkt_tab')"
```