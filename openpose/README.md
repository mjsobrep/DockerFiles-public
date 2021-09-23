# OpenPose Demo Testing

This has a dockerfile that makes it easy to run OpenPose against a folder of videos. This just runs the OpenPose demo script.

## On Linux

### Requirements

1.  Modern Nvidia GPU
2.  Ubuntu 20.04 (18.04 might work, not tested)
3.  [Docker installed](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) don't forget the [post-install steps](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user) , you just need the one to not require root privilege
4.  [CUDA installed](https://developer.nvidia.com/cuda-downloads?target_os=Linux\&target_arch=x86\_64\&Distribution=Ubuntu)
5.  Nvidia Docker 2 Installed (`sudo apt install nvidia-docker2`)
6.  [Nvidia Container Runtime set as default](https://docs.nvidia.com/dgx/nvidia-container-runtime-upgrade/index.html#using-nv-container-runtime) (note, you need to restart docker after doing this: `sudo systemctl restart docker`)

### Running:

1.  Put the videos you want to work with in a directory somewhere
2.  Download the dockerfile that this ships with into a more or less empty directory
3.  Build image: `docker build . --tag openpose`
4.  Run image: `docker run --volume <wherever your videos are, ex: ~/Downloads/panda-demo>:/data -it openpose`
5.  Your output is now next to your source videos

### Some tips:

*   you are getting permission errors: check that you did post install step for docker
*   when building image you get something about the compute type not being able to be found or cuda not being installed: make sure you have nvidia docker 2 AND that you set the docker container runtime as the DEFAULT
*   the output is garbage: try rotating video to be upright
*   the output doesn't get the entire video: try transcoding the video using ffmpeg or similar

## On Windows

In theory, on windows, you can just [download the latest release](https://github.com/CMU-Perceptual-Computing-Lab/openpose/releases), the gpu version is preferred if you have a nvidia gpu, unzip the folder, follow the instructions to download the models, and then run any of the examples in the python folder
