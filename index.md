![helsesorost](https://user-images.githubusercontent.com/79196757/116503417-50eaa000-a8b6-11eb-9925-382c86dc97c9.png) ![ous](https://user-images.githubusercontent.com/79196757/116503445-652e9d00-a8b6-11eb-8985-df71a9a4b9f2.png)

# ABC4PWM

abc4pwm is a software tool for clustering of pwms, classficiation of pwms to their DNA binding Domain, motif search, and other supportive modules.

## Authors:

**Omer Ali<sup>1</sup>, Amna Farooq<sup>1</sup>, Mingyi Yang<sup>3,4</sup>, Magnar Bjørås<sup>4,7</sup>, Victor Jin<sup>5</sup>, Junbai Wang<sup>1*,2,6</sup>**

1. Department of Pathology, Oslo University Hospital - Norwegian Radium Hospital, Oslo, Norway
2. Department of Clinical Molecular Biology in University of Oslo, Norway
3. Department of Medical Biochemistry, Oslo University Hospital and University of Oslo, Oslo, Norway
4. Department of Microbiology, Oslo University Hospital and University of Oslo, Oslo, Norway.
5. Department of Molecular Medicine, University of Texas Health San Antonio, San Antonio, TX, USA
6. Department of clinical molecular biology (EpiGen), Akershus University Hospital, Lørenskog, Norway
7. Department of Clinical and Molecular Medicine, Norwegian University of Science and Technology, Trondheim, Norway

*To whom correspondence should be addressed. Email: junbai.wang@medisin.uio.no*

## Abstract

**Background:**
Applications of high throughput sequencing technology in protein-DNA interactions generate transcription factor (TF) binding motifs with an ever-increasing number of collections, which are maintained in different databases generated from numerous sources. There is lack efficient tools to cluster biologically relevant or similar motifs such as position weight matrices (PWMs), from either experimental detection or in silico predictions. Moreover, an automatic clustering quality assessment method is needed for the quality evaluation of clusters of PWMs.

**Results:**
This work presents a new package Affinity Based Clustering for Position Weight Matrices (abc4pwm), either with or without DNA-Binding Domain (DBD) information. Abc4pwm is able to generate a representative motif for each cluster, to evaluate the clustering quality of PWMs automatically, and filter out wrongly clustered PWMs. Additionally, it can update human DBD family database automatically, classify known human TF PWMs to the respective DBD family, and perform TF motif searching and motif discovery by a new ensemble learning approach.

**Conclusion:**
Applications of abc4pwm in the DNA sequence analysis for several high throughput sequencing data (e.g., RNA-seq and ChIP-seq data) are demonstrated by using ~1770 human TF PWMs. It not only recovers known TF motifs at gene promoters based on gene expression profiles, but also identifies true TF binding targets according to ChIP-seq experiments. Both the clustering of PWMs and the automatic quality assessment for the clusters significantly reduce the computational time in data analysis, and enhance the biological meaningful interpretations. Abc4pwm is a useful tool in DNA sequence analysis.

## How to start:

abc4pwm is written in python. It can be installed and accessed from command line and is available for both linux and mac operating systems. The package can be downloaded [here](https://github.com/abc4pwm/abc4pwm).

Prior to installing the package, dependencies must be fulfilled. List of dependencies is as follows:

- weblogo
- setuptools
- itertools
- pandas
- numpy
- argparse
- os
- shutil
- multiprocessing
- matplotlib
- seaborn
- datetime
- scipy
- tempfile
- time
- matlab.engine
- numba
- beautifulsoup4==4.9.3
- bs4==0.0.1
- fpdf==1.7.2
- joblib==1.0.1
- kiwisolver==1.3.1
- matplotlib==3.3.4
- Pillow==8.1.2
- pyparsing==2.4.7
- requests==2.22.0
- scikit-learn==0.24.1
- sklearn==0.0
- urllib3==1.24.2

It is advised to install dependencies using miniconda. Package contains a file `requirements.txt` which can be used for automatic installation of dependencies from conda or pip. To install the package, go to the AffinityPropogation_Clustering directory and type: `python setup.py install`. For more details, follow the readme file in the package.

## Contents of the package:

The package folder will contain the following:

- `demo` : Contains demo data sets.
- `abc4pwm` : Contains python source code of pipeline.
- `readme.txt` : Instructions about usage of package.
- `requirements.txt` : List of requirements. Can be used for automatic installation from miniconda or pip.
- `setup.py`: Setup file for package.
- `data`: Contains in and out for demo.

## Pipeline Tasks:

The pipeline consists of following tasks. To run a task, type `abc4pwm <task> [<args>]`. To see what are the options for each task of the pipeline, please run: `abc4pwm -h`

- `cleandatabase_for_classification` : Uniformly TF named database for associating pwms with DNA binding domain.
- `classification` : Classification of input pwms into their DNA binding domains.
- `clustering` : Clustering of similar looking position weight matrices.
- `representative_motif` : This module makes a representative motif of the cluster.
- `quality_assessment` : This module automatically assesses the quality of clusters of pwms.
- `visualize` : To visualize the clusters through boxplots etc.
- `plot_cluster_motifs` : To plot the sequence motif of clusters' pws and representative motif.
- `text_tfdb` : Obtaining a database in text format with details of sources and names used in package.
- `ensemble_learning` : A module to predict pwms using bayesPI with ensemble learning.
- `ensemble_investigate` : A module to cluster and search the predicted pwms against a database.
- `conversion` : Conversion of files from one (e.g., ab4pwm) to other (e.g., TRANSFAC, JASPAR).
- `searching` : A module to search a TF pwm (motif) against the database..

## Demo

Test run is available on human pwms data, present in demo folder. In folder abc4pwm/demo , there demos of all modules and study cases which can be run by entering: `./demo` , in the command line to run the demo automatically. In folder abc4pwm/demo , there demos of all modules and study cases.

Having trouble with package? Contact us @ omerali.0191@gmail.com, junbai.wang@medisin.uio.no and we will be glad to help you.

