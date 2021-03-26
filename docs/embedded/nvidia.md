# NVIDIA

- Nvidia is an American multinational technology company incorporated in Delaware and based in Santa Clara, California
- It designs graphics processing units (GPUs) for the gaming and professional markets, as well as system on a chip units (SoCs) for the mobile computing and automotive market
  - 80% GPU market share in 2020
- GPUs are optimized for training artificial intelligence and deep learning models as they can process multiple computations simultaneously. Compared to CPU, They have a large number of cores, which allows for better computation of multiple parallel processes
- CUDA(Compute Unified Device Architecture) is a software layer that enable GPU to perform GPGPU (general-purpose computing on graphics processing units)
  - It is a parallel computing platform and application programming interface (API) model
  - It is created by NVIDIA in 2007
  - It only runs on supported GPU
  - It provides C/C++ language extension and APIs for programming and managing GPUs.
- NVIDIA® CUDA-X, built on top of NVIDIA CUDA®, is a collection of libraries which utilize GPU computing
  - CUDA-X AI - it includes the following AI libraries:
    - cuDNN - NVIDIA CUDA Deep Neural Network (cuDNN) library is a GPU-accelerated library of primitives for deep neural networks
    - Optimized Frameworks - The NVIDIA Optimized Frameworks such as Kaldi, NVIDIA Optimized Deep Learning Framework, powered by Apache MXNet, NVCaffe, PyTorch, and TensorFlow (which includes DLProf and TF-TRT) offer flexibility with designing and training custom deep neural networks (DNNs) for machine learning and AI applications
    - TensorRT - it is an SDK for high-performance deep learning inference
    - DALI - NVIDIA Data Loading Library (DALI) is a collection of highly optimized building blocks, and an execution engine, to accelerate the pre-processing of the input data for deep learning applications
    - Triton Inference Server - (formerly TensorRT Inference Server) provides a cloud inferencing solution optimized for NVIDIA GPU
  - CUDA-X HPC - it includes libraries for HPC applications
- The [NGC catalog](https://ngc.nvidia.com/catalog/collections) site has GPU-optimized softwares configured in docker containers, pre-trained models and SDKs
  - It is available for download and can be deployed on NVIDIA hardwares for deep learning (DL), machine learning (ML), and high-performance computing (HPC) purpose
  - The following NVIDIA platforms can run softwares from NGC
    - NVIDIA-Certified Systems
    - NVIDIA DGX™ systems
    - NVIDIA TITAN and NVIDIA Quadro® GPUs powered workstations
    - NVIDIA Virtual Compute Server
    - Cloud platforms instance which using NVIDIA hardware
    - NVIDIA IoT devices (Autonomous Machines)
- NVIDIA Metropolis Project focuses on building tools to empower NVIDIA IoT with AI, It includes:
  - Transfer Learning Toolkit - it includes production quality pre-trained models and deploy as is or apply minimal fine-tuning for various computer vision and conversational AI use-cases
  - DeepStream SDK - it delivers a complete streaming analytics toolkit for AI-based multi-sensor processing, video, audio and image understanding
- NVIDA's GPU Technology Conference (GTC) is a popular annual event in the GPU computing industry

## Jetson

- Jetson is the branch name for NVIDIA embedded development board powered by its GPU
- Jetson supports CUDA-X
- JetPack is the OS image for Jetson devices, with pre-installed drivers and tools
- L4T is the OS name for Jetson devices, it is based on Ubuntu 18.04
- Jetson Modules is a card containing processing units, it can be plugged into a carrier board for development, the carrier board and the modules are sold together as a development kit
- It currently has the following active modules from slow to fast:
  - Jetson Nano
  - Jetson TX2 Series
  - Jetson Xavier NX
  - Jetson AGX Xavier Series

### Setup

- First boot up:
  1.  Download the Jetpack image for the specific module
  2.  Flash the image into the SD card
      - Recommanded tool: Ethcher
      - it is recommanded to have a SD card with at least 64GB memory size
  3.  Plugin the SD and connect the power, and I/O devices to the carrier board or the module
- Use serial connection with `115200` Baudrate for headless mode
- Jetson Nano Developer Kit doesn't come with WiFi module, use USB WiFi adapter instead
- When in `USB Device Mode` without network connection, the Jetson device can be accessed through `ssh`, `scp`, `sftp` using IP address `192.168.55.1` pre-configured with `l4tbr0` interface
- For models with both USB and DC power supply, use the on borad jumper properly if DC power supply is preferred
- A 4GB swap file is recommended
  - run `sudo systemctl disable nvzramconfig` before creating swap file
  - use path `/mnt/4GB.swap` for swap file
- For remote host identity changed warning, run `ssh-keygen -R HOSTNAME.local`
- To clock control
  - `sudo /usr/bin/jetson_clocks --show` to see the current status
  - `sudo /usr/bin/jetson_clocks --fan` To run the fan at max speed
  - `sudo /usr/bin/jetson_clocks --store` export clock setting to `~/l4t_dfs.conf`
  - `sudo /usr/bin/jetson_clocks --restore` restore clock setting from `~/l4t_dfs.conf`
- [Click](https://developer.nvidia.com/embedded/learn/tutorials/vnc-setup) to see steps for configuring VNC server

#### CLI

- nvpmodel
  - This CLI tool switches the module into different modes. Each mode specify which CPU cores are used, and the maximum frequency of the CPU and GPU being used
  - Each mode has different energy usage and performance scenarios
  - `sudo nvpmodel -m <modeID>`
  - `sudo nvpmodel -q –verbose` query which mode is currently being used
- `cat nv_tegra_release` check the current version of the `L4T`
- nmcli
  - `nmcli d` list all network interface
  - `nmcli r wifi on` enable wifi if available
  - `nmcli d wifi list` show list of WiFI SSIDs
  - `sudo nmcli d wifi connect [SSID] password [PASSWORD]` connect to a WiFi
  - `nmcli c show` show a list of current connections
  - `sudo nmcli c mod <CONNECTION_NAME> ipv4.address <STATIC_IP>/24` set static IP
  - `sudo nmcli c mod <CONNECTION_NAME> ipv4.gateway <GATEWAY_IP>` set gateway IP
  - `sudo nmcli c mod <CONNECTION_NAME> ipv4.method manual` Disable DHCP and use static IP
  - `sudo nmcli c mod <CONNECTION_NAME> ipv4.dns "<DNS_SERVER_IP1>,<DNS_SERVER_IP2>"` set DNS server
  - `sudo nmcli c up <CONNECTION_NAME>` save changes
