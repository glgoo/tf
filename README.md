> 创建于2017/10/19

## 用pip原生安装
    pip install xxxx.whl

**1. 更改pip源**

```sh
# windows
notepad c:\user\username\pip\pip.ini
[global]  
index-url=http://mirrors.aliyun.com/pypi/simple
[install]  
trusted-host=mirrors.aliyun.com  
disable-pip-version-check = true  
timeout = 6000

# ubuntu
vi ~/.pip/pip.conf
[global]  
index-url = https://pypi.doubanio.com/simple/  
[install]  
trusted-host=pypi.doubanio.com  
disable-pip-version-check = true  
timeout = 6000  
```

**2. 更改anaconda源**

```sh
# 安装anaconda后直接命令行输入
conda config --add channels 'https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/'
conda config --add channels 'https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge'
conda config --add channels 'https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/'

conda config --set show_channel_urls yes
# 也可以通过其图形化界面管理更新源
```

**3. 安装概述**

先需要安装Microsoft Visual C++ 2015 Redistributable (x64)这个visual studio环境，或者直接安装visual studio这个IDE。

后面安装tensorflow依赖包（或者你别装Python3.x，直接装对应版本发行版Anaconda3[要记得改更新源]），以及N卡GPU加速cuda和cudnn（这俩包一定要对应安装，同时看好tensorflow版本官网要求的对应的版本号）。

### tensorflow-gpu安装

到[Unofficial Windows Binaries for Python Extension Packages](http://www.lfd.uci.edu/~gohlke/pythonlibs/) 下载如下包（当然你也可以通过pip直接安装某些包，也可以在anaconda中建立新的虚拟环境，但为了知道发生什么最好还是下下来一个个安装），或到(pypi.org)下载下列包。

* numpy+mkl
* six
* pypz
* cycler
* pyparsing
* python_dateutil
* h5py
* numpy
* matplotlib（可选）
* scipy
* opencv（可选）
* tensorflow的gpu版本或cpu版本

然后**依次**pip安装这些.whl包，到这里完成了Python科学研究的基本包了。如果你安装的是tensorflow的gpu版本，继续往下，否则完工！

### cuda和cudnn安装

直接到英伟达开发者官网下载[tensorflow版本官方支持的cuda版本](https://developer.nvidia.com/cuda-downloads) 和[对应版本cuda的对应cudnn版本](https://developer.nvidia.com/cudnn) *这里一定要对应好版本支持 !* 或者下载我这里cuda8的百度云分享[链接：http://pan.baidu.com/s/1bo67GSJ 密码：77sv]

下载后直接安装cuda，默认安装就可以（路径啥的自动会添加到Path，不放心可以用命令行nvcc --version试试）[到这里已经可以在机器上运用GPU加速了，你的C++开发，matlab仿真就可以用到这些toolkits了]

下面就是深度神经网络加速Libraries了，它叫cuDNN(Deep Neural Network)专门用来深度学习模型训练加速的，直接解压这个压缩包把对应目录的文件拷贝到cuda安装路径对应文件夹下就行了，大功告成！

### 交流
邮箱：rootoffice@163.com
