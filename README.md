# TCP-Random-NH
This code is part of my doctoral research at PPG-CC/DC/UFSCar. Test Random Partitions - Non Hierarchical Comunity Detection Methods.

## How to cite 
@misc{Gatto2021, author = {Gatto, E. C.}, title = {Test Random Partitions using Communities Detection Methods for Multilabell Classification}, year = {2022}, publisher = {GitHub}, journal = {GitHub repository}, howpublished = {\url{https://github.com/cissagatto/TCP-Random-NH}}}

## Multi-Label Datasets (original)
Click [here](https://cometa.ujaen.es/datasets/) to go to the cometa page

## 10-Fold Cross Validation Multi-Label Datasets
Click [here](https://www.4shared.com/s/dYpGZWzjQ) to download

## Computed Partitions

Jaccard, Cosine, Roger-Tanimoto and Russel-Rao: Click [here](https://www.4shared.com/s/dS5g0oJPb) to download

Random: Click [here](https://www.4shared.com/s/dhsxOnLwH) to download

## Conda Environment
[download txt](https://www.4shared.com/s/fUCVTl13zea)

[download yml](https://www.4shared.com/s/f8nOZyxj9iq)

[download yaml](https://www.4shared.com/s/fk5Io4faLiq)

To use conda environment to run this experiment, please consult [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) 

## Flowchart
<img src="" width="300">

## Scripts
This source code consists of an R project for R Studio and the following R scripts:

1. libraries.R
2. utils.R
3. validate.R
4. testClus.R
5. run.R
6. tcp.R


## Preparing your experiment

### Step-1
This code is executed in X-fold cross-validation. First, you have to obtain the X-fold cross-validation files using this [code]( https://github.com/cissagatto/CrossValidationMultiLabel). All the instructions to use the code are in the Github. After that, put the results generated in the *Datasets* folder in this project as "tar.gz".

### Step-2
Confirms if the folder *utils* contains the following files: *Clus.jar*, *R_csv_2_arff.jar*, and *weka.jar*, and also the folder *lib* with *commons-math-1.0.jar*, *jgap.jar*, *weka.jar* and *Clus.jar.* Without these jars, the code not runs. 

### Step-3
A file called _datasets_2022.csv_ must be in the *root project* folder. This file is used to read information about the datasets and they are used in the code. All 74 datasets available in *Cometa* are in this file. If you want to use another dataset, please, add the following information about the dataset in the file:

_Id, Name, Domain, Labels, Instances, Attributes, Inputs, Labelsets, Single, Max freq, Card, Dens, MeanIR, Scumble, TCS, AttStart, AttEnd, LabelStart, LabelEnd, xn, yn, gridn_

The *Id* of the dataset is a mandatory parameter in the command line to run all code. The fields are used in a lot of internal functions. Please, make sure that this information is available before running the code. *xn* and *yn* correspond to a dimension of the quadrangular map for kohonen, and *gridn* is (xn * yn). Example: xn = 4, yn = 4, gridn = 16.

### Step-4
To run this code you will need the partitions generated from this [code](https://github.com/cissagatto/GeneratePartitionsCommunities). Please, read the instructions there.

## Software Requirements
This code was develop in RStudio Version 1.4.1106 © 2009-2021 RStudio, PBC "Tiger Daylily" (2389bc24, 2021-02-11) for Ubuntu Bionic Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) QtWebEngine/5.12.8 Chrome/69.0.3497.128 Safari/537.36. The R Language version was: R version 4.1.0 (2021-05-18) -- "Camp Pontanezen" Copyright (C) 2021 The R Foundation for Statistical Computing Platform: x86_64-pc-linux-gnu (64-bit).

**Please, make sure all the dependencies are installed (verify libraries.R). This code does not provide any installation of the packages.**

## Hardware Requirements
This code may or may not be executed in parallel, however, it is highly recommended that you run it in parallel. The number of cores can be configured via the command line (number_cores). If number_cores = 1 the code will run sequentially. In our experiments, we used 10 cores. For reproducibility, we recommend that you also use ten cores. This code was tested with the birds dataset in the following machine:

*System:*

Host: bionote | Kernel: 5.8.0-53-generic | x86_64 bits: 64 | Desktop: Gnome 3.36.7 | Distro: Ubuntu 20.04.2 LTS (Focal Fossa)

*CPU:*

Topology: 6-Core | model: Intel Core i7-10750H | bits: 64 | type: MT MCP | L2 cache: 12.0 MiB | Speed: 800 MHz | min/max: 800/5000 MHz Core speeds (MHz): | 1: 800 | 2: 800 | 3: 800 | 4: 800 | 5: 800 | 6: 800 | 7: 800 | 8: 800 | 9: 800 | 10: 800 | 11: 800 | 12: 800 |

Then the experiment was executed in a cluster at UFSCar.

**Important: we used the CLUS classifier in this experiment. This implies generating all physical ARFF training, validating, and testing files. Our code generates the files first in RAM and then saves them to the HD. However, to avoid memory problems, immediately after saving to HD, the files are validated (or tested) and then deleted. Even so, make sure you have enough space on your HD and RAM for this procedure.**


## RUN
To run the code, open the terminal, enter the */TCP-TR-H/R/* folder, and type

```
Rscript tcp.R [number_dataset] [number_cores] [number_folds] [similarity] [name_folder_results]
```

Where:

_number_dataset_ is the dataset number in the datasets.csv file

_number_cores_ is the total cores you want to use in parallel execution.

_number_folds_ is the number of folds you want for cross-validation

_similarity_ is similarity measure that were used to build the graph

_name_folders_results_ is the name of the folder to save the results


All parameters are mandatory. Example:

```
Rscript tcp.R 17 5 10 "Jaccard" "/dev/shm/results/"

```

This will execute the code for the dataset number 17 in the _dataset.csv_, with 5 cores, 10 folds and the process will be store in the _/dev/shm/results/_. This code automatically makes a copy of the */dev/shm/results* in the folder *Reports* - which is in the root of the project. In this way, you can run the code using a temporary folder, like *scratch* and *shm*, to speed up the execution.


## Results
The results are store in the Reports folder

## Video Demonstration
Click [here]() to watch a video that demonstrate how to run this code


## Acknowledgment
This study is financed in part by the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior - Brasil (CAPES) - Finance Code 001

## Links

[Post-Graduate Program in Computer Science](http://ppgcc.dc.ufscar.br/pt-br)

[Biomal](http://www.biomal.ufscar.br/)

[Computer Department](https://site.dc.ufscar.br/)

[CAPES](https://www.gov.br/capes/pt-br)

[Embarcados](https://www.embarcados.com.br/author/cissa/)

[Linkedin](https://www.linkedin.com/in/elainececiliagatto/)

[Linkedin](https://www.linkedin.com/company/27241216)

[Instagram](https://www.instagram.com/cissagatto/)

[Twitter](https://twitter.com/cissagatto)

## Report Error

Please contact me: elainececiliagatto@gmail.com

# Thanks