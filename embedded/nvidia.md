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
- NVIDIA® CUDA-X, is a collection of CUDA based libraries which utilize GPU computing
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
- NVIDIA Metropolis Project focuses on building tools to empower NVIDIA IoT with AI, It includes (see all available docs at [here](https://docs.nvidia.com/metropolis/)):
  - Transfer Learning Toolkit - it includes production quality pre-trained models and deploy as is or apply minimal fine-tuning for various computer vision and conversational AI use-cases
  - DeepStream SDK - it delivers a complete streaming analytics toolkit for AI-based multi-sensor processing, video, audio and image understanding
- NVIDA's GPU Technology Conference (GTC) is a popular annual event in the GPU computing industry
- `iGPU` is an integrated GPU, GPU that's in the CPU. `dGPU` is a dedicated GPU, it is the actual graphic card

## GPUs

### Types of Drivers

- Tesla drivers
  - These drivers are intended primarily for compute workloads, which use GPUs for computational tasks
  - They are good for parallelized floating-point calculations for machine learning and fast Fourier transforms for high performance computing applications
- GRID drivers
  - These drivers are certified to provide optimal performance for professional visualization applications that render content such as 3D models or high-resolution videos
  - One can configure GRID drivers to support two modes
    - Quadro Virtual Workstations provide access to four 4K displays per GPU
    - GRID vApps provide RDSH App hosting capabilities
- Gaming drivers
  - These drivers contain optimizations for gaming and are updated frequently to provide performance enhancements
  - They support a single 4K display per GPU
- [Click Here](https://www.nvidia.com/Download/Find.aspx) to serach and download specific driver version based on the GPU type and Host OS
  - [Click Here](https://docs.nvidia.com/datacenter/tesla/tesla-installation-notes/index.html) for steps to install drivers
  - Use run script option to have a better control on which version to install
  - If certain path can't be found during installation on a new machine, it can potentially break in the future. When it happens check driver status again and reinstall. Optionally install related packages that will create those paths
- [Click Here](https://docs.nvidia.com/cuda/index.html) to see docs for CUDA

  - [Click Here](https://developer.nvidia.com/cuda-downloads) for steps to install CUDA
  - In CUDA installation, its compatible GPU driver will also be intalled
  - Use the following Environment variables in the dot file

  ```bash
  # CUDA
  export CUDA=XX.X
  export PATH=/usr/local/cuda-$CUDA/bin${PATH:+:${PATH}}
  export CUDA_PATH=/usr/local/cuda-$CUDA
  export CUDA_HOME=/usr/local/cuda-$CUDA
  export LIBRARY_PATH=$CUDA_HOME/lib64:$LIBRARY_PATH
  export LD_LIBRARY_PATH=/usr/local/cuda-$CUDA/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
  export LD_LIBRARY_PATH=/usr/local/cuda/extras/CUPTI/lib64:$LD_LIBRARY_PATH
  export NVCC=/usr/local/cuda-$CUDA/bin/nvcc
  export CFLAGS="-I$CUDA_HOME/include $CFLAGS"
  ```

- [Click Here](https://docs.nvidia.com/deeplearning/cudnn/developer-guide/index.html) to see docs for cuDNN
  - [Click Here](https://developer.nvidia.com/rdp/cudnn-download) sign in to download the Runtime and Developer cuDNN Library for selected CUDA version
  - run `sudo dpkg -i *.deb` to install download libraries
- Steps to install OpenCV using CUDA

  ```bash
  # Install build tools
  sudo apt install python3-dev python3-pip python3-testresources
  sudo apt install build-essential cmake pkg-config unzip yasm git checkinstall
  sudo apt install libjpeg-dev libpng-dev libtiff-dev
  sudo apt install libavcodec-dev libavformat-dev libswscale-dev libavresample-dev
  sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
  sudo apt install libxvidcore-dev x264 libx264-dev libfaac-dev libmp3lame-dev libtheora-dev
  sudo apt install libfaac-dev libmp3lame-dev libvorbis-dev
  sudo apt install libopencore-amrnb-dev libopencore-amrwb-dev
  sudo apt-get install libgtk-3-dev
  sudo apt-get install libtbb-dev
  sudo apt-get install libatlas-base-dev gfortran
  sudo apt-get install libprotobuf-dev protobuf-compiler
  sudo apt-get install libgoogle-glog-dev libgflags-dev
  sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen
  pip3 install numpy
  # Download OpenCV source
  # replace X.X.X with a openCV version number
  mkdir opencvbuild && cd opencvbuild
  wget -O opencv.zip https://github.com/opencv/opencv/archive/X.X.X.zip
  wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/X.X.X.zip
  unzip opencv.zip
  unzip opencv_contrib.zip
  mv opencv-X.X.X opencv
  mv opencv_contrib-X.X.X opencv_contrib
  cd opencv
  mkdir build && cd build
  # generate build instruction
  # find the compute capability version for the GPU card and use it as the value for the CUDA_ARCH_BIN option
  # Go to https://en.wikipedia.org/wiki/CUDA#GPUs_supported for a list of compute capability version
  # Run it in virtual environment can build under that environment
  cmake \
  -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_C_COMPILER=/usr/bin/gcc-7 \
  -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_PYTHON_EXAMPLES=ON \
  -D INSTALL_C_EXAMPLES=ON -D WITH_TBB=ON -D WITH_CUDA=ON -D WITH_CUDNN=ON \
  -D OPENCV_DNN_CUDA=ON -D CUDA_ARCH_BIN=7.5 -D BUILD_opencv_cudacodec=OFF \
  -D ENABLE_FAST_MATH=1 -D CUDA_FAST_MATH=1 -D WITH_CUBLAS=1 \
  -D WITH_V4L=ON -D WITH_QT=OFF -D WITH_OPENGL=ON -D WITH_GSTREAMER=ON \
  -D WITH_FFMPEG=ON -D OPENCV_GENERATE_PKGCONFIG=ON \
  -D OPENCV_PC_FILE_NAME=opencv4.pc -D OPENCV_ENABLE_NONFREE=ON \
  -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
  -D PYTHON_EXECUTABLE=$(which python) \
  -D PYTHON_LIBRARY=$(python -c "import distutils.sysconfig as sysconfig; print(sysconfig.get_config_var('LIBDIR'))") \
  -D PYTHON_INCLUDE_DIRS=$(python -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
  -D PYTHON_DEFAULT_EXECUTABLE=$(which python3) -D BUILD_EXAMPLES=ON ..
  # Build
  make -j$(nproc)
  sudo make install
  # Link opencv with virtual environment
  ln -s /usr/local/lib/python3.6/site-packages/cv2 ~/anaconda3/envs/<env>/lib/python3.6/site-packages/cv2
  # Check result
  pkg-config --libs --cflags opencv4
  ```

### CLI

#### Env Setup

- `PATH` includes `/usr/local/cuda/bin`
- `LD_LIBRARY_PATH` includes `/usr/local/cuda/lib64`,
  - or, add `/usr/local/cuda/lib64` to `/etc/ld`.so conf and run ldconfig as root

#### Command

- `nvidia-smi` return GPU driver info
  - If it suddenly prompts `Failed to initialize NVML: Driver/library version mismatch` when a proper driver is installed and worked, a reboot might fix the issue
- To uninstall the CUDA Toolkit, run `cuda-uninstaller`
  - Uninstall first before update
- To uninstall the NVIDIA Driver, run `nvidia-uninstall`

## Jetson

- Jetson is the branch name for NVIDIA embedded development board powered by its GPU
- Jetson supports CUDA-X
- JetPack is the OS image for Jetson devices, with pre-installed drivers and tools
  - The pre-installed opencv wasn't compiled using CUDA, refer to this [link](https://qengineering.eu/install-opencv-4.5-on-jetson-nano.html) to install openCV on a Jetson
- L4T is the OS name for Jetson devices, it is based on Ubuntu 18.04
- Jetson Modules is a card containing processing units, it can be plugged into a carrier board for development, the carrier board and the modules are sold together as a development kit
- It currently has the following active modules from slow to fast:
  - Jetson Nano
  - Jetson TX2 Series
  - Jetson Xavier NX
  - Jetson AGX Xavier Series
- [Click here](https://developer.nvidia.com/embedded/downloads) to go the download center for Jetson Development

### Setup

#### First Boot Up

1. Download the Jetpack image for the specific module, or using the NVIDIA SDK Manager on a Ubuntu or CentOS host and skip step 2
2. Flash the image into the SD card
   - Recommanded tool: Ethcher
   - it is recommanded to have a SD card with at least 64GB memory size
   - The OS will not recongize the drive after flashing is completed
3. Plugin the SD and connect the power, and I/O devices to the carrier board or the module

#### Connections

- Use serial connection with `115200` Baudrate for headless mode
- Jetson Nano Developer Kit doesn't come with WiFi module, use USB WiFi adapter instead
- When in `USB Device Mode` without network connection, the Jetson device can be accessed through `ssh`, `scp`, `sftp` using IP address `192.168.55.1` pre-configured with `l4tbr0` interface
- For models with both USB and DC power supply, put a jumper on J48 properly if DC power supply is preferred
- For remote host identity changed warning, run `ssh-keygen -R <RemoteIPAddress>`

#### Swap File

- A 4GB swap file is recommended
  - run `sudo systemctl disable nvzramconfig` before creating swap file

#### Clock Control

- `sudo /usr/bin/jetson_clocks --show` to see the current status
- `sudo /usr/bin/jetson_clocks --fan` To run the fan at max speed
- `sudo /usr/bin/jetson_clocks --store` export clock setting to `~/l4t_dfs.conf`
- `sudo /usr/bin/jetson_clocks --restore` restore clock setting from `~/l4t_dfs.conf`

#### VNC

- [Click](https://developer.nvidia.com/embedded/learn/tutorials/vnc-setup) to see steps for configuring VNC server
  - `VNC` is only available when login the GUI interface, one can use command line to enable automatic login
  - `VNC` instruction can be found in the USB drive when connected in USB mode, it also contain config info on changing screen resolution

#### Backup

- Clone the entire SD drive, `sudo dd if=/dev/sdc conv=sync,noerror bs=4096 | gzip -c > ~/backup_image.img.gz`
- Restore the entire SD drive, `gunzip -c ~/backup_image.img.gz | dd of=/dev/sdc bs=4096`

#### CLI

- `nvcc --version` or `/usr/local/cuda/bin/nvcc --version` returns cuda version
- nvpmodel
  - This CLI tool switches the module into different modes. Each mode specify which CPU cores are used, and the maximum frequency of the CPU and GPU being used
  - Each mode has different energy usage and performance scenarios
  - `sudo nvpmodel -m <modeID>`
  - `sudo nvpmodel -q –verbose` query which mode is currently being used
  - `cat /etc/nvpmodel.conf` to see all the modes available
    - For Jetson Nano mode `1` is 10W mode with Barrel jack 5V 4A power supplies, `2` is 5W mode with Micro USB power supplies
- `cat /etc/nv_tegra_release` check the current version of the `L4T`
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
- `tegrastats` - shows details on temperature and power usage.

### SDKs

#### Deepstream

- It is a group of GStreaner Plugins that can work with NVIDIA GPUs
  - also known asHardware Accelerated GStreamer plugins)
  - GStreamer is a framework for creating streaming media applications
- the following list of plugins are tools that can be inserted into the GStreamer pipeline
  - `Gst-nvinfer` implements TensorRT-based inferencing
    - It takes a key based config file as the element property, inference models and details are defined there, keys are placed in the following key groups:
      - The `[property]` group configures the general behavior and file paths settings. It is the only mandatory group, [Click here](https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_plugin_gst-nvinfer.html#gst-nvinfer-file-configuration-specifications) to see related documentation
        - The `labelfile-path` points to the `label.txt` file which specifies class IDs
      - The `[class-attrs-all]` group configures detection parameters for all classes
      - The `[class-attrs-<ClassID>]` group configures detection parameters for a specific class, e.g. `[class-attrs-2]`, it uses the same key properies as `[class-attrs-all]`, and the key value are used to override settings in the `[class-attrs-all]` for a specific class
    - The `Gst-nvinfer` plugin finds objects and provides metadata about them as an output on its source pad
    - Multiple `Gst-nvinfer` plugin can be chained together, `SGIE` can do futher classification on objects detected by `PGIE`
      - The first instance of the `Gst-nvinfer` plugin serves as the `Primary GPU Inference Engine` (`PGIE`), they have property `process-mode=1` in config file
      - Subsequent instances of the Gst-nvinfer plugin are `Secondary GPU Inference Engines` (`SGIE`), they have property `process-mode=2` in config file
      - Each `Gst-nvinfer` must have an unique id, defined as `sgie1_unique_id` property in the config file
  - `Gst-nvstreammux` - Batch streams before sending for AI inference, manage metadata for video stream
  - `Gst-nvvideo4linux2` - Decode video streams using the hardware accelerated decoder (NVDEC); Encode RAW data in I420 format to H264 or H265 output video stream using hardware accelerated encoder (NVENC).
  - `Gst-nvvideoconvert` - Perform video color format conversion. The first Gst-nvvideoconvert plugin before Gst-nvdsosd plugin converts stream data from I420 to RGBA and the second Gst-nvvideoconvert plugin after Gst-nvdsosd plugin converts data from RGBA to I420.
    - A buffer is created with nvvideoconvert so that bounding boxes can be overlaid on the video images with an appended `nvdsosd` plugin
  - `Gst-nvdsosd` - Draw bounding boxes, text, and region of interest (ROI) polygons.
    - The input or "sink pad" of this plugin is a good place to extraction or process the meta data, a `probe` will be used to take snapshot of this sink pad, it is a callback function that is invoked whenever a frame is received at `Gst-nvdsosd`'s sink pad
  - `Gst-nvtracker` - Track object between frames
    - Low level setting is defined by `` config file
  - `Gst-nvmultistreamtiler` - Composite a 2D tile from batched buffers.
  - `Gst-nvv4l2decoder` - Decode a video stream.
  - `Gst-Nvv4l2h264enc` - Encode a video stream.
  - `Gst-NvArgusCameraSrc` - Provide options to control ISP properties using the Argus API.
- [Click here](https://developer.nvidia.com/deepstream-getting-started) for more resources
- GStreamer is a `C` framework, it also supports Python using Gst Python which is GStreamer framework's Python bindings
  - Python bindings is a compiled module included in the DeepStream SDK, it is generated using Pybind11
  - [Click here](https://github.com/NVIDIA-AI-IOT/deepstream_python_apps#metadata_bindings) to explore sample apps in Python
- In NGC, there are docker containers available with deepstream installed for a quick start, `dGPU` container is called `deepstream` and the `Jetson` container is called `deepstream-l4t`
