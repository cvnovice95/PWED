# Personal Work Environment based on Docker

This docker image `(cvnovice/pwed)` is mainly used to the personal work environment about computer vision and machine learning. Currently, it contains some software as follows:

``` 
cmake-3.5.1
gcc/g++-5.4.0
gdb -7.11.1 
make-4.1
python2-2.7.12
python3-3.5.2
kdevelop-4.7.3
opencv-3.3.1
pkg-config-0.29
pip-8.1.1
cuda-8.0
cudnn-5.0
java-12.0.2
pycharm
vncserver
```

This image runs in Ubuntu 16.04 and Docker 18.09. I will briefly introduce the usage of some software. I have built the virtual environment of python2 and python3. In this virtual-env, I have installed tools, such as numpy, scipy, matplotlib, scikit-images, scikit-learn,ipython. 
```
[container] workon python2_env (or python3_env) // you can enter into the virtual-env 
````
PS: for opencv, it supports cuda. if you need to use GPU, you must config nvidia-docker-2. I have installed vncserver, you can use it. And this image contains a Ubuntu Desktop. By vnc-client, you can work on Ubuntu Desktop.
```
// This command helps you create a container (You must install Ubuntu 16.04 and Docker 18.09 , nvidia-docker-2) 
[host] docker run -it -v /home/yourname/workspace:/workspace -p 50001:5901 --name work_gpu --privileged --runtime=nvidia cvnovice/pwed:v1 // 50001:5901 is the port mapping of vncserver
```

```
// This command is used to open the pycharm
[container] charm
```
Of course, you can also install tensorflow and pytorch in the virtual-env of python. 

```
// This is demo about OpenCV
[container] g++ your_demo.cpp `pkg-config --libs --cflags opencv` -o demo
```