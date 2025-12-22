# docker-services

## Enable Nvidia GPU

Install packages (Debian Trixie)

```bash
sudo apt install nvidia-driver-pinning-580 # latest with support for gtx 1060/1080
sudo apt install nvidia-driver nvidia-driver-cuda

curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
sudo apt-get update
sudo apt install nvidia-container-toolkit

sudo reboot

# test that containers work
docker run --gpus all nvidia/cuda:11.5.2-base-ubuntu20.04 nvidia-smi
```

