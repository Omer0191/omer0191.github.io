![helsesorost](https://user-images.githubusercontent.com/79196757/116503417-50eaa000-a8b6-11eb-9925-382c86dc97c9.png) ![ous](https://user-images.githubusercontent.com/79196757/116503445-652e9d00-a8b6-11eb-8985-df71a9a4b9f2.png)

# ABC4PWM

abc4pwm is a software tool for clustering of pwms, classficiation of pwms to their DNA binding Domain, motif search, and other supportive modules.

## Authors:

  <p align="center"><strong> Omer Ali <sup>1</sup>, Amna Farooq <sup>1</sup>, Mingyi Yang <sup>3</sup>, Magnar Bjørås <sup>3,4</sup>, Junbai Wang <sup>1*</sup> </strong></p>
  
  <p align="center">1. Department of Pathology, Oslo University Hospital - Norwegian Radium Hospital, Oslo, Norway </p>
  <p align="center">2. Department of Clinical Molecular Biology in University of Oslo, Norway </p>
  <p align="center">3. Department of Microbiology, Oslo University Hospital Rikshospitalet, Oslo, Norway </p>
  <p align="center">4. Department of Microbiology, Oslo University Hospital and University of Oslo, Oslo, Norway. </p>

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
	<b>Background:</b> With the advent of information technology and its use for biological applications, new high throughput methods have produced motifs with an ever-increasing number of collections. These collections are maintained in different Transcription Factor (TF) databases generated from numerous sources. These collections are combined by Meta-Databases which produces redundancy as there is no any efficient and automatic way of combining biologically relevant motifs by making groups of similar looking position weight matrices(PWMs). During the analysis of genome wide datasets, production of motifs is another cause of redundancy. This require a tool which can efficiently group together similar position weight matrices and may replace this group with the help of representative motif.</p>
	<p><b>Results:</b> This work presents a pipeline package for clustering the PWMs and then calculate a representative consensus motif for each cluster. This task is done by first assigning a DNA-Binding Domain (DBD) family name to every motif and classifying them on the basis of respective DBDs. Affinity Propagation Clustering is then applied within each DBD family which make clusters of similar motifs. The mean or consensus of these clusters is then calculated which act as representative of the respective cluster. This work also shows a unique way of calibrating cluster quality with four different measures and extracts non similar motifs from the clusters. A clean uniform database creation of TFs, classification of pwms, quality measurement, motif searching, ensemble learing, reports of classification and database in text files are some other features of the package.</p>
	<p><b>Conclusion:</b> Similar TFs were assigned a cluster and representative was calculated for each cluster. It helped to reduce redundancy by many folds. Automatic cluster quality analysis is a feature of this pipeline which makes it unique from existing tools and solves the complexity of pwms which is variable length matrices. A command line software pipeline is available online for both mac and linux.
</p>
	
</div>


## How to start:

abc4pwm is written in python. It can be installed and accessed from command line and is avalible for both linux and mac operating systems. The package can be downloaded [here] (www.github.com/abc4pwm)

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

## Contents of the package:


		
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
	<li><code>conversion</code>: A module to search a TF pwm (motif) against the database..</li>



</ul>	


  
  ## Demo
  

<p>Test run is available on human pwms data, present in demo folder.
In folder abc4pwm/demo , there demos of all modules and study cases which can be run by entering: ./demo , in the command line to run the demo automatically.
In folder abc4pwm/demo , there demos of all modules and study cases. </p>

Having trouble with package? Contact us [here] (omerali.0191@gmail.com) (junbai.wang@medisin.uio.no) and we’ll help you sort it out.
