-> conda install


sudo apt update; sudo apt upgrade

wget -qO - https://keys.anydesk.com/repos/DEB-GPG-KEY | sudo apt-key add -

sudo gedit /etc/apt/sources.list.d/anydesk.list
-> deb http://deb.anydesk.com/ all main

ubuntu-drivers devices

sudo apt install nvidia-driver-470

sudo apt update

sudo apt install -y build-essential

sudo apt-get install -y freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev libglfw3-dev libgles2-mesa-dev

sudo apt-get install -y libfreeimage3 libfreeimage-dev

wget https://developer.download.nvidia.com/compute/cuda/11.1.0/local_installers/cuda_11.1.0_455.23.05_linux.run

sudo sh cuda_11.1.0_455.23.05_linux.run

(continue -> 드라이버 빼고 설치)

sudo reboot

sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/7fa2af80.pub

sudo add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/ /"

sudo gedit ~/.bashrc
(sudo gedit ~/.profile)
{export PATH=$PATH:/usr/local/cuda-11.1/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.1/lib64 
export CUDADIR=/usr/local/cuda-11.1}
source ~/.bashrc
(source ~/.profile)

sudo apt-get install cuda-toolkit-11-1

(에러슈팅, 부팅 후 검은 화면 나올 때 TTY 진입 후 로그인, sudo apt-get purge nvidia-* 이후 재설치)

wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu2004/x86_64/nvidia-machine-learning-repo-ubuntu2004_1.0.0-1_amd64.deb

sudo dpkg -i nvidia-machine-learning-repo-ubuntu2004_1.0.0-1_amd64.deb

sudo bash -c 'echo "deb http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64 /" >> /etc/apt/sources.list.d/nvidia-machine-learning.list'


-> https://developer.nvidia.com/compute/machine-learning/cudnn/secure/8.1.1.33/11.2_20210301/cudnn-11.2-linux-x64-v8.1.1.33.tgz


tar xvzf cudnn-11.2-linux-x64-v8.1.1.33.tgz

sudo cp cuda/include/cudnn* /usr/local/cuda/include

sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64

sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*

ldconfig -N -v $(sed 's/:/ /' <<< $LD_LIBRARY_PATH) 2>/dev/null | grep libcudnn

(바탕화면)
conda create --name multibox --file spec-file.txt

sudo apt install git

git clone https://github.com/OpenKinect/libfreenect2.git
cd libfreenect2
sudo apt-get install build-essential cmake pkg-config
sudo apt-get install libusb-1.0-0-dev
sudo apt-get install libturbojpeg0-dev -y
sudo apt-get install libglfw3-dev -y
sudo apt-get install libopenni2-dev -y
mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/freenect2
make
make install
cmake -Dfreenect2_DIR=$HOME/freenect2/lib/cmake/freenect2

export LIBFREENECT2_INSTALL_PREFIX=~/freenect2
export LD_LIBRARY_PATH=$HOME/freenect2/lib:$LD_LIBRARY_PATH

./bin/Protonect

안되면
{sudo cp ../platform/linux/udev/90-kinect2.rules /etc/udev/rules.d/

sudo service udev restart
}

pip install wheel
pip install numpy
pip install cython
pip install opencv-python
pip install pylibfreenect2

cd examples/
python multiframe_listener.py

pip install ktb


