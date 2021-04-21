---
layout: posts
title:  "How to use GPU on Tensorflow for Windows"
classes: wide
---

Using GPU for training **Deep Learning** models is almost mandatory these days. In this post I'll guide you step by step throughout the (tedious) process of installing all the necessary components to use your GPU with **Tensorflow** models in Python. 

## What do you need?
_________________
There are some things that you will need to check before start.

1. Install [Python](https://www.python.org/).
2. Install [pip](https://pypi.org/project/pip/) running the following command on the Windows Terminal.
```bash
pip install --upgrade pip
```
3. Check the specifications of your GPU opening the Windows program: [dxdiag](https://en.wikipedia.org/wiki/DxDiag). You can search it in the search box on the Windows 10 taskbar.
4. Check the latests **requirements** from official [Tensorflow Website](https://www.tensorflow.org/install/source#gpu). In my case, I'm downloading the following version:
   
| Version          | Python Version | Compiler  | Compiler Tool | cuDNN | CUDA |
| ---------------- | -------------- | ---------	| ------------- | -----	| ---- |
| tensorflow-2.4.0 | 3.6 to 3.8     | GCC 7.3.1	| Bazel 3.1.0   |	8.0	| 11.0 |

## Steps
_________________
Now that we have everything. Let's jump into it.

1. Find and download the [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit-archive) of your version. This process may take a while, so be patiente.  
2. Download and install [cuDNN](https://developer.nvidia.com/cudnn). You need to **create an account** in Nvidia to do it (it should be fairly simple). Once it downloads, extract the file somewhere in your computer. In my case, I extracted the folder named *cuda* in my Desktop. The extracted folder should contain the following items:
```
|- cuda/
	|- bin/
	|- include/
	|- lib/
	|- NVIDIA_SLA_cuDNN_Support.txt
```
3. Copy and replace the folders *bin/*, *include/* and *lib/* and paste them into the following path in your machine:<br><br>
**C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0**<br><br>
1. Create the following Environment Variables in **PATH**. To do that, just search for *Environment variables* in the search box on the Windows taskbar. Open the program "*Edit environment variables for your system*" and then search and select the variable *Path* from the list and click edit. Then, add the paths to the list and click Ok.
   - **C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\bin**
   - **C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\libnvvp** 
2. **Restart your computer**, so we make sure all the changes have been done correctly.
3. Install or update the latest version of [Tensorflow 2](https://www.tensorflow.org/) using pip. It already includes GPU support, so you don't need to install any other package.
```bash
pip install --upgrade tensorflow
```
7. Now, test that everything works fine by running the the following code in a python file or via CLI:
```py
import tensorflow as tf 
print("Num GPUs Available: ", len(tf.config.list_physical_devices('GPU')))
```
It should print **more than 0 GPUs Available** if everything worked fine. 


Hope you found this post relevant. 

See you in the next one! 🐍