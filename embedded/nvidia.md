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

- Steps:
  1.  Download the Jetpack image for the specific module
  2.  Flash the image into the SD card
      - Recommanded tool: Ethcher
      - it is recommanded to have a SD card with at least 64GB memory size
  3.  Plugin the SD and connect the power, and I/O devices to the carrier board or the module
- If the module has less than 4 GB memory, create a swap file
- Use serial connection for headless mode
- For models with both USB and DC power supply, use the on borad jumper properly if DC power supply is preferred
