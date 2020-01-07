## tensorFlow-GPU-1.13.1安装文档

- 安装环境：
  - Centos 7.6
  - Tesla P40
  - tensorflow-gpu == 1.13.1
  - CUDA == 10.0
  - CUDNN  == 7.4

### 一、安装anaconda

下载链接：

> https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

注意事项：

- 不要使用**root**用户安装**anaconda**
- 若用户A也想使用用户B配置的**anaconda**环境，需要配置用户A中的环境变量：

配置环境变量：

```bash
vim /etc/profile
export PATH=/home/yexin/anaconda3/bin:$PATH
export PATH="/usr/local/cuda/bin:$PATH"
```

使配置生效：

```bash
source /etc/profile
```



### 二、安装tensorFlow-GPU-1.13.1及其依赖包

所需依赖如下，依此``pip install``各包名即可。

```python
Keras_Preprocessing-1.0.9-py2.py3-none-any.whl
Keras_Applications-1.0.7-py2.py3-none-any.whl
absl-py-0.7.1.tar.gz
Markdown-3.1.1-py2.py3-none-any.whl
grpcio-1.20.1-cp37-cp37m-manylinux1_x86_64.whl
protobuf-3.7.1-cp37-cp37m-manylinux1_x86_64.whl
termcolor-1.1.0.tar.gz
gast-0.2.2.tar.gz
astor-0.8.0-py2.py3-none-any.whl
mock-3.0.5-py2.py3-none-any.whl
tensorboard-1.13.1-py3-none-any.whl
tensorflow_estimator-1.13.0-py2.py3-none-any.whl
tensorflow_gpu-1.13.1-cp37-cp37m-manylinux1_x86_64.whl
```

依赖包下载地址：

```python
https://files.pythonhosted.org/packages/c0/bf/0315ef6a9fd3fc2346e85b0ff1f5f83ca17073f2c31ac719ab2e4da0d4a3/Keras_Preprocessing-1.0.9-py2.py3-none-any.whl

https://files.pythonhosted.org/packages/90/85/64c82949765cfb246bbdaf5aca2d55f400f792655927a017710a78445def/Keras_Applications-1.0.7-py2.py3-none-any.whl

https://files.pythonhosted.org/packages/da/3f/9b0355080b81b15ba6a9ffcf1f5ea39e307a2778b2f2dc8694724e8abd5b/absl-py-0.7.1.tar.gz

https://files.pythonhosted.org/packages/0f/39/bdd75b08a6fba41f098b6cb091b9e8c7a80e1b4d679a581a0ccd17b10373/tensorboard-1.13.1-py3-none-any.whl

https://files.pythonhosted.org/packages/c0/4e/fd492e91abdc2d2fcb70ef453064d980688762079397f779758e055f6575/Markdown-3.1.1-py2.py3-none-any.whl 

https://files.pythonhosted.org/packages/44/3c/0f680a3e2e7720dc1b37bf3163b1f62f0f847dc081a17f2a2f4389e86a38/grpcio-1.20.1-cp37-cp37m-manylinux1_x86_64.whl 

https://files.pythonhosted.org/packages/19/a5/ac51df34cdf4739574492ed4903c11dadd72a7bec4a31bb0496f4f50fc19/protobuf-3.7.1-cp37-cp37m-manylinux1_x86_64.whl 

https://files.pythonhosted.org/packages/8a/48/a76be51647d0eb9f10e2a4511bf3ffb8cc1e6b14e9e4fab46173aa79f981/termcolor-1.1.0.tar.gz

https://files.pythonhosted.org/packages/4e/35/11749bf99b2d4e3cceb4d55ca22590b0d7c2c62b9de38ac4a4a7f4687421/gast-0.2.2.tar.gz

https://files.pythonhosted.org/packages/d1/4f/950dfae467b384fc96bc6469de25d832534f6b4441033c39f914efd13418/astor-0.8.0-py2.py3-none-any.whl

https://files.pythonhosted.org/packages/bb/48/13f49fc3fa0fdf916aa1419013bb8f2ad09674c275b4046d5ee669a46873/tensorflow_estimator-1.13.0-py2.py3-none-any.whl

https://files.pythonhosted.org/packages/05/d2/f94e68be6b17f46d2c353564da56e6fb89ef09faeeff3313a046cb810ca9/mock-3.0.5-py2.py3-none-any.whl
    
http://mirrors.aliyun.com/pypi/packages/2c/65/8dc8fc4a263a24f7ad935b72ad35e72ba381cb9e175b6a5fe086c85f17a7/tensorflow_gpu-1.13.1-cp37-cp37m-manylinux1_x86_64.whl#sha256=931c7d49b1757a0a6f3c577ab465cc53d0c4984ef766122f4f48159f5acdec81
```



### 三、安装对应版本CUDA、CUDNN

**版本：**

```tensorflow-gpu```：**1.13.1**

```CUDA```：10.0

```CUDNN```：7.4

```
CUDA下载地址：
https://developer.download.nvidia.cn/compute/cuda/10.0/secure/Prod/local_installers/cuda_10.0.130_410.48_linux.run?16YC5vl4fHVwW9_tblnCTPXvjPwJ2t0fuYKq-e3TaEGJxbSeJWgiMvn6IdNuAwkdtKg8afCXrAAWeMdjSGAcCcOpcZXot5CGsb4IS88mg_KO5CDzjuiJj4WOASDARThIT-GdiV_Zgd2KiG6OxwspGJrIuCQa4jMouvqWzS0IFf4ymcWhwH3IYWIR3LY

CUDNN下载地址：
https://developer.download.nvidia.cn/compute/machine-learning/cudnn/secure/v7.4.1.5/prod/10.0_20181108/cudnn-10.0-linux-x64-v7.4.1.5.tgz?hto3YQJW3-zeVy5f-c42ftJ06hm-fiPRKUr2ICeeDl4roq2Tgyacz7mFmgNJ0Ngu3SWKzPDFMm0agaB4BcRqWy4vfxxPRC5eCvKXXHZiTlIA8FVKzgFUsoJMpC9i0Y5i0L6Lqz6KjSGK5PJc7N_IgD6SZMDy0pMaLzCH1ehFm6vWZZ68Sy6KsAkaF0zBGbpMGQnyFwevIg5rh_1IkHJdXATN
```

- 安装CUDA

设置可执行权限

```bash
chmod a+x cuda_9.0.28_linux.run
```

运行安装

```bash
sudo ./cuda_10.0.130_410.48_linux.run
```



- 安装CUDNN

重命名：

```bash
mv cudnn-10.0-linux-x64-v7.4.1.5.solitairetheme8 cudnn-10.0-linux-x64-v7.4.1.5.solitairetheme8.tgz
```

解压：

```bash
tar -zxvf cudnn-10.0-linux-x64-v7.4.1.5.solitairetheme8.tgz
```

进入解压之后的**include**目录:

```bash
cd cuda/include
sudo cp cudnn.h /usr/local/cuda/include
```

进入解压之后的**lib64**目录:

````bash
cd cuda/lib64
sudo cp libcudnn.* /usr/local/cuda/lib64/
````



### 四、遇到的坑

**导入tensorflow时：**

问题一：

```python
ImportError: libcublas.so.10.0: cannot open shared object file: No such file or directory
```

解决：

```
sudo ldconfig /usr/local/cuda-10.0/lib64
```



问题二：

```python
ImportError: libcudnn.so.7: cannot open shared object file: No such file or directory
```

解决：

```
cd /usr/local/cuda/lib64
sudo rm -rf libcudnn.so libcudnn.so.7  #删除原有版本号，版本号在cudnn/lib64中查询
sudo ln -s libcudnn.so.7.4.1 libcudnn.so.7 #生成软连接，注意自己下载的版本号
sudo ln -s libcudnn.so.7 libcudnn.so 
sudo ldconfig #立即生效
```



问题三：

```python
ImportError:  /lib64/libm.so.6: version `GLIBC_2.23' not found
```

解决：

- **下载对应安装包：**

```python
https://ftp.gnu.org/gnu/glibc/glibc-2.23.tar.gz
```

- ##### 解压、新建编译目录目录:

```bash
tar xf glibc-2.23.tar.gz
cd glibc-2.23/
mkdir glibc-build
cd glibc-build (一定要在新建的目录中操作)
```

- **安装**

```bash
../configure --prefix=/usr
make
make install
```

- **在make install 时可能会跳出错误（类似的应该是因为软链接的版本不对造成的）**

```bash
gawk '/\.gnu\.glibc-stub\./ { \
          sub(/\.gnu\.glibc-stub\./, "", $2); \
          stubs[$2] = 1; } \
        END { for (s in stubs) print "#define __stub_" s }' > /root/glibc-2.23/glibc-build/math/stubsT
gawk: error while loading shared libraries: /lib64/libm.so.6: invalid ELF header
make[2]: *** [/root/glibc-2.23/glibc-build/math/stubs] Error 127
make[2]: Leaving directory `/root/glibc-2.23/math'
make[1]: *** [math/subdir_install] Error 2
make[1]: Leaving directory `/root/glibc-2.23'
make: *** [install] Error 2
```

- **解决：**(另启一个终端窗口)

```bash
cd /lib64
unlink libm.so.6
ln -s libm-2.23.so libm.so.6
```

- **然后再次执行**`make install`

- **验证**

```
ldd --version
ldd (GNU libc) 2.23
Copyright (C) 2016 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
```

- 成功升级



