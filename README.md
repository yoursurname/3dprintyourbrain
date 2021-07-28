# 3D print your brain using WSL

This is an updated version of [miykael/3dprintyourbrain](https://github.com/miykael/3dprintyourbrain) adapted to work under Windows using the Subsystem for Linux (WSL2 using Ubuntu).

For this project I'm using

1. [Ubuntu 18 on WSL2 (Windows 10)](https://ubuntu.com/wsl)

2. [FreeSurfer 7-dev](https://surfer.nmr.mgh.harvard.edu/fswiki/FS7_wsl_ubuntu)

3. [MeshLab 2020.09 for Windows](https://github.com/cnr-isti-vclab/meshlab/releases/download/Meshlab-2020.09/MeshLab2020.09-windows.exe)

4. NIFTI T1 image of a brain

I adapted the script in such a way that you can simply use the following command and retrieve a fully reconstructed brain from a NIFTI file.

```
sh create_3d_brain.sh subjectname.nii.gz
```

## How to use this repo

### 1. Install requirements

#### 1.1 Setup WSL

 Setup WSL and install Ubuntu 18 according to this article [WSL | Ubuntu](https://ubuntu.com/wsl)

#### 1.2 Install FreeSurfer in Ubuntu

Inside WSL, run the following commands to install Freesurfer

```shell
wget https://surfer.nmr.mgh.harvard.edu/pub/dist/freesurfer/dev/freesurfer_7-dev_amd64.deb
sudo apt-get update
sudo apt-get --yes install ./freesurfer_7-dev_amd64.deb
echo "export FREESURFER_HOME=/usr/local/freesurfer/7-dev" >> $HOME/.bashrc
echo "export FS_LICENSE=$HOME/license.txt" >> $HOME/.bashrc
echo "source /usr/local/freesurfer/7-dev/SetUpFreeSurfer.sh" >> $HOME/.bashrc
```

Register your copy of FreeSurfer here [FreeSurfer Registration form](https://surfer.nmr.mgh.harvard.edu/registration.html) and place the license.txt in your WSL home directory. The easiest way to do this is to open WSL via command line `wsl`, then switch to your home directory `cd ~` and then open the regular windows explorer inside your WSL home directory with `explorer.exe .`. Now copy your `license.txt` to this folder

#### 1.3. Install MeshLab 2020.09 for Windows

Inside the Windows host machine, install [MeshLab 2020.09](https://github.com/cnr-isti-vclab/meshlab/releases/download/Meshlab-2020.09/MeshLab2020.09-windows.exe). It's important to use this version as it's the last version containing the MeshLab Server.

### 2. Setup the script

Copy the contents of this repository inside your home dir in WSL.

Your home dir should look like this

![](C:\Users\Simon\Desktop\3dprintyourbrain\md_assets\2021-07-28-09-50-41-image.png)

type `nano create_3d_brain.sh` and check if the MESHLAB_SERVER in line 8 points to the correct location of your `meshlabserver.exe` on your windows machine

### 3. Run the script

Copy your NIFTI file (`subjectname.nii.gz`) to the home dir and simply run `sh create_3d_brain.sh subjectsname.nii.gz`. The whole process will take a few hours, depending on your machine speed. In the end there should be a `final.stl` in the folder `~/3dbrains/subjectname/output/final.stl`

Have fun with it :)
