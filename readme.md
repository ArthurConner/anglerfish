# This is our way of configuring for a base machine learning confing



### turn off UEFI protection in bios (other os)

### install ubuntu

### install nvidia stuff from apt-get
sudo apt-get purge nvidia
sudo apt-get install nvidia-current

### download the NVIDIA linux driver from website

### turn of x windows, install nvidia driver
     sudo service lightdm stop
  chmod a+x NVIDIA-Linux-x86_64-367.57.run 
   sudo ./NVIDIA-Linux-x86_64-367.57.run 
reboot
    9  sudo apt-get update
   10  sudo apt-get upgrade

### install anaconda
   39  chmod a+x Anaconda2-4.2.0-Linux-x86_64.sh 
   40  bash Anaconda2-4.2.0-Linux-x86_64.sh 

#download cuda8
  sudo dpkg -i cuda-repo-ubuntu1604_8.0.44-1_amd64.deb 
  sudo apt-get update
   sudo apt-get install cuda
  

~/.theanorc 
[global]
device = cuda
floatX = float32


.bashrc
export PATH="/usr/local/cuda/bin:$PATH"

export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
export CUDA_HOME=/usr/local/cuda







# download cudnn 
     tar zxf cudnn-8.0-linux-x64-v5.1.tgz 
    
   57  sudo cp cuda/include/cudnn.h /usr/local/cuda/include 
   59  sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64  
   60  sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
   


61  sudo apt-get install git
   63  sudo git clone https://github.com/tensorflow/tensorflow

   89  cd tensorflow/
   90  ls
   91  sudo apt-get install python-numpy swig python-dev python-wheel
   92  sudo add-apt-repository ppa:webupd8team/java
   93  sudo apt-get update
   94  sudo apt-get install oracle-java8-installer
   95  echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
   96  curl https://storage.googleapis.com/bazel-apt/doc/apt-key.pub.gpg | sudo apt-key add -
   97  sudo apt-get update && sudo apt-get install bazel
   98  sudo apt-get upgrade bazel
   99  ./configure 
  100  bazel build -c opt --config=cuda //tensorflow/tools/pip_package:build_pip_package

  72  sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
   73  sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
   74  sudo apt-get update
   75  sudo apt-get install ros-kinetic-desktop-full
   76  sudo rosdep init
   77  rosdep update
   78  echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
   79  source ~/.bashrc
   80  sudo apt-get install python-rosinstall


Fixed the tensorflow in an ugly way by relinking the libc++ library from inside anaconda, to system wide one. Not sure why anaconda is using an old C++ library. Need to figure that out.
