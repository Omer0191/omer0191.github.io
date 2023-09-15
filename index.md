![helsesorost](https://user-images.githubusercontent.com/79196757/116503417-50eaa000-a8b6-11eb-9925-382c86dc97c9.png) ![ous](https://user-images.githubusercontent.com/79196757/116503445-652e9d00-a8b6-11eb-8985-df71a9a4b9f2.png)

# ABC4PWM

abc4pwm is a software tool for clustering of pwms, classficiation of pwms to their DNA binding Domain, motif search, and other supportive modules.

## Authors:

  <p align="center"><strong> Omer Ali <sup>1</sup>, Amna Farooq <sup>1</sup>, Mingyi Yang <sup>3,4</sup>, Magnar Bjørås <sup>4,7</sup>, Victor Jin<sup>5</sup>,  Junbai Wang <sup>1*,2,6</sup> </strong></p>
  
  <p align="center">1. Department of Pathology, Oslo University Hospital - Norwegian Radium Hospital, Oslo, Norway </p>
  <p align="center">2. Department of Clinical Molecular Biology in University of Oslo, Norway </p>
  <p align="center">3. Department of Medical Biochemistry, Oslo University Hospital and University of Oslo, Oslo, Norway</p>
  <p align="center">4. Department of Microbiology, Oslo University Hospital and University of Oslo, Oslo, Norway. </p>
  <p align="center">5. Department of Molecular Medicine, University of Texas Health San Antonio, San Antonio, TX, USA </p>
  <p align="center">6. Department of clinical molecular biology (EpiGen), Akershus University Hospital, Lørenskog, Norway </p>
  <p align="center">7. Department of Clinical and Molecular Medicine, Norwegian University of Science and Technology, Trondheim, Norway </p>
<p align="center">*To whom correspondence should be addressed.Email: junbai.wang@medisin.uio.no </p>

<head>
	
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-197803461-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-197803461-1');
</script>

</head>



## Abstract
<div class="container-fluid abstract_des">

<div class="row"> 
	<p> 
	<b>Background:</b> Applications of high throughput sequencing technology in protein-DNA interactions generate transcription factor (TF) binding motifs with an ever-increasing number of collections, which are maintained in different databases generated from numerous sources. There is lack efficient tools to cluster biologically relevant or similar motifs such as position weight matrices (PWMs), from either experimental detection or in silico predictions. Moreover, an automatic clustering quality assessment method is needed for the quality evaluation of clusters of PWMs.</p>
	<p><b>Results:</b> This work presents a new package Affinity Based Clustering for Position Weight Matrices (abc4pwm), either with or without DNA-Binding Domain (DBD) information. Abc4pwm is able to generate a representative motif for each cluster, to evaluate the clustering quality of PWMs automatically, and filter out wrongly clustered PWMs. Additionally, it can update human DBD family database automatically, classify known human TF PWMs to the respective DBD family, and perform TF motif searching and motif discovery by a new ensemble learning approach.</p>
	<p><b>Conclusion:</b> Applications of abc4pwm in the DNA sequence analysis for several high throughput sequencing data (e.g., RNA-seq and ChIP-seq data) are demonstrated by using ~1770 human TF PWMs. It not only recovers known TF motifs at gene promoters based on gene expression profiles, but also identifies true TF binding targets according to ChIP- seq experiments. Both the clustering of PWMs and the automatic quality assessment for the clusters significantly reduce the computational time in data analysis, and enhance the biological meaningful interpretations. Abc4pwm is a useful tool in DNA sequence analysis.
</p>
	
</div>


## How to start:
<div class="container-fluid abstract_des">
abc4pwm is written in python. It can be installed and accessed from command line and is avalible for both linux and mac operating systems. The package can be downloaded <strong><a href="[abc4pwm_code_demo.tgz](https://github.com/abc4pwm/abc4pwm)">The package can be downloaded here</a></strong>(www.github.com/abc4pwm)

Prior to installing the package, dependencies must be fulfilled. List of dependencies is as follows:
<ul>
	<li>weblogo</li>
	<li>setuptools</li>
	<li>itertools</li>
	<li>pandas</li>
	<li>numpy</li>
	<li>argparse</li>
	<li>os</li>
	<li>shutil</li>
	<li>multiprocessing</li>
	<li>matplotlib</li>
	<li>seaborn</li>
	<li>datetime</li>
	<li>scipy</li>
	<li>tempfile</li>
	<li>time</li>
	<li>matlab.engine</li>
	<li>numba</li>
	<li>beautifulsoup4==4.9.3</li>
	<li>bs4==0.0.1</li>
	<li>fpdf==1.7.2</li>
	<li>joblib==1.0.1</li>
	<li>kiwisolver==1.3.1</li>
	<li>matplotlib==3.3.4</li>
	<li>Pillow==8.1.2</li>
	<li>pyparsing==2.4.7</li>
	<li>requests==2.22.0</li>
	<li>scikit-learn==0.24.1</li>
	<li>sklearn==0.0</li>
	<li>urllib3==1.24.2</li>
	</ul>
It is advised to install dependencies using miniconda.
Package contains a file requirments.txt which can be used for automatic installation of dependencies from conda or pip.
To install the package, go to the AffinityPropogation_Clustering directory and type: python setup.py install
For more detials, follow the readme file in the package
</div>
	
## Contents of the package:
<div class="container-fluid abstract_des">
		
<p>The package folder will contain following:</p>
<ul>
	<li><code>demo</code> : Contains demo data sets.</li>
	<li><code>abc4pwm</code> : Contains python soruce code of pipeline.</li>
	<li><code>readme.txt</code> : Instructions about usage of package.</li>
	<li><code>requirments.txt</code> :  List of requirments. Can be used for automatic installation from miniconda or pip.</li>
	<li><code>setup.py</code>: Setup file for package.</li>
	<li><code>data</code>: Contains in and out for demo.</li>


</ul>	


## Pipeline Tasks:
<div class="container-fluid abstract_des">
<p>The pipeline consists of follwoing tasks. To run a task, type abc4pwm <task> [<args>]. To see what are the options for each task of the pipeline, please run: abc4pwm -h </p>

<ul>
	<li><code>cleandatabase_for_classification</code> : Uniformly TF named database for associating pwms with DNA binding domain.</li>
	<li><code>classification</code> : Classification of input pwms into their DNA binding domains.</li>
	<li><code>clustering</code> : Clustering of similar looking position weight matrices.</li>
	<li><code>representative_motif</code> : This module makes a representative mofit of the cluster.</li>
	<li><code>quality_assessment</code>: This modules automatically asses the quality of clusters of pwms.</li>
	<li><code>visualize</code>: To visualize the clusters through boxplots etc.</li>
	<li><code>plot_cluster_motifs</code> : To plot the sequence motif of clusters' pws and representative motif.</li>
	<li><code>text_tfdb</code> : Obtaining a database in text formate with details of sources and names used in package.</li>
	<li><code>ensemble_learning</code> : A module to predict pwms using bayesPI with ensemble learning.</li>
	<li><code>ensemble_investigate</code>: A module to cluster and search the predicted pwms against a database.</li>
	<li><code>conversion</code>: Conversion of files from one (e.g., ab4pwm) to other (e.g., TRANSFAC, JASPAR).</li>
	<li><code>searching</code>: A module to search a TF pwm (motif) against the database..</li>



</ul>	

## Demo
<div class="container-fluid abstract_des">

<p>Test run is available on human pwms data, present in demo folder.
In folder abc4pwm/demo , there demos of all modules and study cases which can be run by entering: ./demo , in the command line to run the demo automatically.
In folder abc4pwm/demo , there demos of all modules and study cases. </p>

Having trouble with package? Contact us @ omerali.0191@gmail.com, junbai.wang@medisin.uio.no and we will be glad to help you.
