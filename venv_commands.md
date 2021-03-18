# ------>> Requires UBUNTU 16.04 !!!

# install CUDA Toolkit v8.0
sudo apt-get install nvidia-384 
sudo apt-get install cuda-8-0

# install cuDNN v6.0
CUDNN_TAR_FILE="cudnn-8.0-linux-x64-v6.0.tgz"
wget http://developer.download.nvidia.com/compute/redist/cudnn/v6.0/${CUDNN_TAR_FILE}
tar -xzvf ${CUDNN_TAR_FILE}
sudo cp -P cuda/include/cudnn.h /usr/local/cuda-8.0/include
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-8.0/lib64/
sudo chmod a+r /usr/local/cuda-8.0/lib64/libcudnn*

# set environment variables
export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

# Install Pyton 3.6
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.6
sudo apt-get install python3.6-dev python3.6-venv
sudo apt-get install python3.6-tk

# Setup and start virtualenv
python3.6 -m venv .papervenv
. .papervenv/bin/activate 
pip install -r requirements.txt