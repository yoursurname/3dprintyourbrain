# 3D print your brain using WSL



This is an updated version of [miykael/3dprintyourbrain](https://github.com/miykael/3dprintyourbrain) adapted to work under Windows using the Subsystem for Linux (WSL2 using Ubuntu).

For this project I'm using

1. Ubuntu 18 on WSL2 (Windows 10)

2. [FreeSurfer 7-dev](https://surfer.nmr.mgh.harvard.edu/fswiki/FS7_wsl_ubuntu)

3. [MeshLab 2020.09 for Windows](https://github.com/cnr-isti-vclab/meshlab/releases/download/Meshlab-2020.09/MeshLab2020.09-windows.exe)

4. NIFTI T1 image of a brain

I adapted the script in such a way that you can simply use the following command and retrieve a fully reconstructed brain from a NIFTI file.

```
sh create_3d_brain.sh subjectname.nii.gz
```
