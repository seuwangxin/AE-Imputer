# AE-Imputer: An autoencoder-based tool for accurate imputation of phenotypes in plants
### The Python project 'AE-Imputer' can be used to impute multi-trait phenotypes in plants. More information can be found in the User manual.
## The masked data that support the findings of this study are available in the 'Data' directory.
The original data is referenced as follows:<br>
Rapeseed403: https://www.nature.com/articles/s41588-022-01055-6<br>
Rice565: https://www.nature.com/articles/s41467-023-39534-x<br>
Rice575: https://www.nature.com/articles/hdy201687<br>
Maize392: https://doi.org/10.1016/j.molp.2022.11.004<br>
Maize945: https://doi.org/10.1111/pbi.70011<br>
Pine926: https://doi.org/10.1111/j.1469-8137.2011.04038.x<br>

## The user manual of AE-Imputer v1.0

System Requirements:

PyTorch installation (mandatory)

GPU-enabled PyTorch version (recommended)

Here are the install commands of PyTorch. Scroll down for the step-by-step instructions.

**1 Step-by-step instructions of installing PyTorch**

**1.1 Install Miniconda**

Miniconda is the recommended approach for installing PyTorch with GPU support. It creates a separate environment to avoid changing any installed software in your system. This is also the easiest way to install the required software especially for the GPU setup. Download the Miniconda Windows Installer (https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86\_64.exe) or the Miniconda Linux Installer (https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86.sh). Follow the on-screen instructions and choose the default options.

**1.2 Create a Conda environment**

Open a terminal (by clicking on the “Anaconda Prompt” button through the Start menu in Windows). Create a Conda virtual environment named phim\_env (other names are also acceptable) with the following commands [in a terminal window](http://dict.cn/To%20do%20this%2C%20just%20issue%20the%20following%20command%20in%20a%20terminal%20window) (taking python 3.8 as an example).

*conda create --name phim\_env python=3.8*

You can deactivate and activate it with the following commands.

*conda deactivate*

*conda activate phim\_env*

Make sure it is activated for the rest of the installation.

**1.3 Install PyTorch**

Install PyTorch (with GPU support) using the following command (taking NVIDIA RTX 4090 as an example).

*pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118*

If you are not using a GPU (not recommended), run the following command.

*pip3 install torch torchvision torchaudio*

**2 Install AE-Imputer**

You should download the AE-Imputer v1.0 package. If under the Windows operating system, open [a terminal window](http://dict.cn/To%20do%20this%2C%20just%20issue%20the%20following%20command%20in%20a%20terminal%20window) and navigate to the download directory (taking “D:\ AE-Imputer v1.0” as an example). Then activate your Conda environment that has already installed PyTorch, and install AE-Imputer v1.0 with the following commands.

*D:*

*conda activate phim\_env*

*cd AE-Imputer* *v1.0*

*python install.py（You can use the - i parameter to specify the source, for example: python install. py - i* [*https://pypi.tuna.tsinghua.edu.cn/simple*](https://pypi.tuna.tsinghua.edu.cn/simple)*）*

*phim --h (Command to view how to use the software)*

**3 Usage**

**3.1 For the Windows operating system**

The software supports CSV files as input, with rows presenting samples and columns presenting traits. Input/output format examples are shown in Fig. 1.

Taking the dataset Maize392 as an example, 392.csv is the complete dataset without any missing data. testyin.csv is the missing dataset containing the header and the index. testyin-noheader.csv is the missing dataset without the header. testyin-noindex.csv is the missing dataset without the index, and testyin-noheader&noindex.csv is the missing dataset without the header and the index. result.csv represents the output result. result-noheader.csv represents the output result without the header. result-noindex.csv represents the output result without the index. result-noheader&&noindex.csv represents the output result without the header and the index.

Please note that the following operations assume the required data is placed in a specific directory. As an example, the path could be D:\data, but you may use any directory of your choice. Once your data is ready, you can proceed with the following command:

*phim --fulldata D:\data\392.csv*

*--missingdata D:\data\testyin.csv*

*--outputfile D:\data\result.csv*

*or*

*phim --missingdata D:\data\testyin.csv*

*--outputfile D:\data\result.csv*

*or*

*phim --missingdata D:\data\testyin.csv*

*or*

*phim --missingdata D:\data\testyin.csv*

*--aug 20*

*--outputfile D:\data\result.csv*

*or*

*phim --missingdata D:\data\testyin-noheader.csv*

*--outputfile D:\data\result-noheader.csv*

*--no-header*

*or*

*phim --missingdata D:\data\testyin-noindex.csv*

*--outputfile D:\data\result-noindex.csv*

*--no-index*

*or*

*phim --missingdata D:\data\testyin-noheader&&noindex.csv*

*--outputfile D:\data\result-noheader&&noindex.csv*

*--no-header --no-index*

The introduction of different parameters in the above commands is as follows:

1. --fulldata: Set the path to the original file. Leave this out if the file is not available or not needed.

2. --missingdata: Input path for the dataset with missing values to be imputed.

3. --aug: Set the data augmentation factor.

4. --outputfile: Set the output file path for the imputation results. If omitted, results will be saved to output.csv by default.

5. --no-header: Specifies that the input file has no header. (By default, the first row is read as the header.)

6. --no-index: Specifies that the input file has no index. (By default, the first column is read as the index.)

![Fig 1](images/fig1.png)

Fig. 1 | Examples of the file format. **a,** The input example of AE-Imputer. **b,** The output example of AE-Imputer. The first row of the data records the name of each trait, and the first column records the ID of each sample.

**3.2 For the Linux operating system**

This operation assumes that a data folder already exists under the root directory (/) of the Linux system. You can then process the data using the following AE-Imputer commands:

*phim --fulldata /data/392.csv*

*--missingdata /data/testyin.csv*

*--outputfile /data/result.csv*

*or*

*phim --missingdata /data/testyin.csv*

*--outputfile /data/result.csv*

*or*

*phim --missingdata /data/testyin.csv*

*or*

*phim --missingdata /data/testyin.csv*

*--aug 2*

*--outputfile /data/result.csv*

*or*

*phim --missingdata /data/testyin-noheader.csv*

*--outputfile /data/result-noheader.csv*

*--no-header*

*or*

*phim --missingdata /data/testyin-noindex.csv*

*--outputfile /data/result-noindex.csv*

*--no-index*

*or*

*phim --missingdata /data/testyin-noheader&&noindex.csv*

*--outputfile /data/result-noheader&&noindex.csv*

*--no-header --no-index*

The installation and imputation commands in Linux environment must be consistent with those in Windows environment, and the format must strictly comply with the requirements specified in Fig. 1a.
