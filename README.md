# abc4pwm

============================Affinity Based Clustering for Position weight Matrices============================


A new tool for the clustering of Transcription Factors is designed. Details are as follows

usage: abc4pwm [-h] {cleandatabase_for_classification, classification, clustering, representative_motif, quality_assessment, visualize, plot_cluster_motifs, text_tfdb}

positional arguments:
{cleandatabase_for_classification,classification,clustering,representative_motif,quality_assessment,visualize,plot_cluster_motifs,text_tfdb}                        


Tasks available for using:
    cleandatabase_for_classification
    classification
    clustering
    representative_motif
    quality_assessment
    visualize
    plot_cluster_motifs
    text_tfdb
    ensemble_learning
    ensemble_investigate
    conversion
    searching


optional arguments:
  -h, --help            show this help message and exit

You should run the pipeline in the following order to generate all necessary files:
1- 'cleandatabase_for_classification' :In the first step you should generate clean database to classify inputs files
2- 'classification' :In this step classify files according to their DBD by adding labels
3- 'clustering ' :In the step apply clustering on output folder produced by step 2 
4- 'quality_assessment' :This step calculates quality of clusters and remove bad quality pwms from clusters 
5- 'representative_Motif': This step prepare a representative motif of the cluster

Example of tasks:

------------------------------------cleandatabase_for_classification----------------------------------

usage: abc4pwm cleandatabase_for_classification [-h]
                                                      [--pwm_files_directory FOLDER]
                                                      [--read_new NUMBER]


Arguments:
  --pwm_files_directory FOLDER       This folder should contain the input pwm files in . mlp formate


optional arguments:
  --read_new NUMBER     (Optional) Select 1 if you want a new updated read from sources(internet Connection Required). Default 0
  -h, --help            show this help message and exit



----------------------------------classification----------------------------------

usage: abc4pwm classification [-h] [--pwm_files_directory FOLDER]
                                        [--output_directory FOLDER]
                                        [--original_pwm_files_directory FOLDER]
                                        [--load_new_db NUMBER]


Arguments:
  --pwm_files_directory             FOLDER      This folder should contain the input pwm files in . mlp formate
  --output_directory                FOLDER      This folder should point to folder where files should go after getting labels of DBD
  --original_pwm_files_directory    FOLDER      This folder should contain a copy of input pwm files in . mlp formate

optional arguments:
  --load_new_db                     NUMBER      (Optional) This should be 1 if you want to download a new update db from sources 0 by default
  -h, --help            show this help message and exit


----------------------------------clustering----------------------------------


usage: abc4pwm clustering [-h] [--dbd_folders_directory FOLDER]
                                    [--output_directory FOLDER]
                                    [--minimum_pwms_in_dbd NUMBER]
                                    [--mean_threshold NUMBER]
                                    [--z_score_threshold NUMBER]
                                    [--top_occurrences NUMBER]
                                    [--occurrences_threshold NUMBER]

Arguments:
--dbd_folders_directory 	FOLDER	This folder should contain DBD folders. Output of classifcation_pwm should be this task input
  --output_directory 		FOLDER	This folder should to output folder. Output of classifcation_pwm should be input to this task


optional arguments:
  -h, --help            show this help message and exit
  --in_dbd 			NUMBER       	(Optional) This should be 0 if you want to cluster all together (non DBD) 1 by default 
  --minimum_pwms_in_dbd 	NUMBER		(Optional) minimum number of pwms in a dbd to be clusteredDefault value is 5
  --max_processors 		NUMBER		(Optional) maximum number of processors for paralle processingDefault value is 5



----------------------------------quality_assessment----------------------------------

usage: abc4pwm quality_assessment [-h] [--dbd_folders_directory FOLDER]
                                     [--output_directory FOLDER]
                                     [--dbd_for_plotting FOLDER]
                                     [--load_new_assesment <class 'bool'>]
                                     [--mean_threshold NUMBER]
                                     [--z_score_threshold NUMBER]
                                     [--top_occurrences NUMBER]
                                     [--occurrences_threshold NUMBER]


Arguments:
  --dbd_folders_directory 			FOLDER	This folder should contain clustered DBD folders. Output of clusterings should be this task input
  --out_path_for_qa_clusters 			FOLDER	This folder should point to output folderwhere quality assessed clusters will be stored.
  --output_folder_for_text_report 		FOLDER	Specify a folder where report in txt file will be stored.

optional arguments:
  -h, --help            show this help message and exit
  --output_path_for_quality_assessment_file 	FOLDER	(Optional) folder where quality assessment .json file will be stored.Default, data/in/
  --load_new_assesment 				NUMBER	(Optional)1 if you want to do new assesment, 0 if you want load existing assesment
  --mean_threshold 				NUMBER	(Optional) mean threshold for uncertain clustersDefault value is 0.80
  --z_score_threshold 				NUMBER	(Optional) max negative threshold of zscore for similarity values of pwmDefault value is -1.0
  --top_occurrences 				NUMBER	(Optional) This value corresponds to occurrence of a pwm less than a threshold z-scoreValue is between 0 to 1. Default value is 0.15
  --occurrences_threshold 			NUMBER	(Optional) This value corresponds to threshold of occurrence from top occurrencesValue is between 0 to 1. Default value is 0.05


----------------------------------representative_motif------------------------------------
usage: abc4pwm representative_motif [-h] [--path_to_clusters FOLDER]
                                          [--dbd string] 
					  [--clusters string]
                                          [--best_match_initial_motif NUMBER]
                                          [--mean_threshold NUMBER]
                                          [--z_score_threshold NUMBER]
                                          [--top_occurrences NUMBER]
                                          [--occurrences_threshold NUMBER]

Arguments:
  --path_to_clusters 		FOLDER		This folder should contain the clusters folders
  --clusters 			string     	This argument should be cluster numbers as string For example, 0,1,2,3,4 if you want to plot these clusterswrite 'all' if you want to make 						representative for all clusters 
optional arguments:
  -h, --help            show this help message and exit

  --dbd 			string          Default value is 'selected'. Representative of clusters pathmentioned in --path_to_clusters parameter will be calculated.  						Write 'all' if representative calculation of all dbd and all clusters is required.
  --best_match_initial_motif 	NUMBER		(Optional) This should be 0 if you want initial motif to be random 1 by default 
  --mean_threshold	 	NUMBER		(Optional) mean threshold for uncertain clustersDefault value is 0.80
  --z_score_threshold	 	NUMBER		(Optional) max negative threshold of zscore for similarity values of pwmDefault value is -1.0
  --top_occurrences 		NUMBER		(Optional) This value corresponds to occurrence of a pwm less than a threshold z-scoreValue is between 0 to 1. Default value is 0.15
  --occurrences_threshold 	NUMBER		(Optional) This value corresponds to threshold of occurrence from top occurrencesValue is between 0 to 1. Default value is 0.05
  --ic 				NUMBER          (Optional) Information Content for trimming edges.Default value is 0.4

----------------------------------plot_cluster_motifs----------------------------------
usage: abc4pwm plot_cluster_motifs [-h] 
				[--path_to_clusters FOLDER]
                [--output_folder FOLDER]
				[--clusters string]
				[--dbd string]

Arguments:
  --path_to_clusters    FOLDER      This folder should contain clusters of a DBD, Write all if you want to plot all dbds.
  --output_folder       FOLDER      This folder should contain clusters of a DBD
  --clusters            string      This arguement should be cluster numbers as string For example, 0,1,2,3,4 if you want to plot these clusters. write 'all' if you want to plot all clusters
optional arguments:
  -h, --help            show this help message and exit

  --dbd 		string       Default value is 'selected'. Clusters pathmentioned in --path_to_clusters parameter will be printed  Write 'all' if plotting of all dbd and all clusters is required.



---------------------------------visualize----------------------------------
usage: abc4pwm visualize [-h]
                               [--path_to_folder_of_assessment_file FOLDER]
                               [--path_to_folder_of_DBDs FOLDER]
                               [--output_folder FOLDER]
                               [--dbd_for_plot FOLDER] [--task string]

Arguments:
  --path_to_folder_of_assessment_file 	FOLDER		folder path from where quality assessment file should be taken
  --path_to_folder_of_DBDs 		FOLDER		this folder should contain clustered DBD folders
  --output_folder 			FOLDER		folder where visualization output should be saved
  --dbd_for_plot 			FOLDER		path of dbd which is needed to be visualized. Write 'all' if you want to plot for all dbds.


optional arguments:
  -h, --help            show this help message and exit
  --task 				string         (Optional) Specify visualization taskFor example, boxplot, pichart, etc Default is boxplot.





----------------------------------text_tfdb---------------------------------
usage: abc4pwm text_tfdb [-h] [--pwm_files_directory FOLDER]

optional arguments:
  -h, --help            show this help message and exit
Arguments:
  --pwm_files_directory FOLDER      This folder should contain the input pwm files in . mlp format



----------------------------------searching----------------------------------
usage: abc4pwm searching [-h] 
			[--pwm . mlp file] 
			[--db_path path or list]
                        [--output_directory FOLDER] 
			[--db_type string]
                        [--db_format string] 
			[--top_n NUMBER]

optional arguments:
  -h, --help            show this help message and exit
  --pwm 		. mlp file      position weight matrix file (motif) which you want to search. .mlp format
  --db_path 		path or list	path to clustered dbds according to the hierarchy of abc4pwm.if db_type=list then then this paramter should be list of pwms, against whcih you are searching the pwm
  --output_directory 	FOLDER		This folder should to output folder. search_result.pdf output file will be stored here.
  --db_type 		string      	(Optional) If database for comparison is folder hierarchy like abs4pwm then this willbe db_type=path. Write list if providing list of pwms for comparison
  --db_format 		string    	(Optional) If database for comparison have format, please mention.Supported formats are abc4pwm, Tranfac, Jaspar. default is abc4pwm
  --top_n 		NUMBER        	(Optional) Number of top matches from the database. Default 5
  --input_count NUMBER  (Optional) 1 if input file contains values in counts
  --db_count NUMBER     1 if database file contains values in counts
  --db_file_type String
                        mention the extension of file type. e.g., .mlp, .txt
  --input_file_type String
                        mention the extension of file type. e.g., .mlp, .txt
  --input_prob Number   (Optional) 1 if input file contains values in probabilities
  --db_prob Number      (Optional) 1 if databas file contains values in probabilities
----------------------------------conversion----------------------------------
usage: abc4pwm conversion [-h]
                    [--pwm_files_directory FOLDER]
                    [--in2out string]
                    [--output_folder FOLDER]

optional arguments:
  -h, --help                            show this help message and exit
  --pwm_files_directory     FOLDER      This folder should contain the input pwm files in . mlp formate  which you want to convert
  --in2out                  string      Specify conversion like the following.
                                        --in2out 'abc4pwm2transfac'
                                        --in2out 'transfac2abc4pwm'
  					--in2out 'abc4pwm2jaspar'
                                        --in2out 'jaspar2abc4pwm'
  --output_folder           FOLDER      folder where converted files should be saved

----------------------------------ensemble learning----------------------------
usage: abc4pwm ensemble_learning [-h] [--opt_dependence Number]
                                 [--numP Number] [--opt_numOfWeakReads Number]
                                 [--number_of_genes Number]
                                 [--expFile File path]
                                 [--opt_weak_expFile File path]
                                 [--opt_seqFile File path]
                                 [--opt_out File path.] [--opt_loops Number]
                                 [--opt_min_L Number] [--opt_max_L Number]
                                 [--opt_iteration Number]
                                 [--opt_p_value float] [--opt_strand Number]
                                 [--opt_normalization Number]
                                 [--max_processors Number]

optional arguments:
  -h, --help                        show this help message and exit
  --opt_dependence      Number      Define dependence, Default is 0.
  --numP                Number      number of times random selections will be done. Default is 15
  --opt_numOfWeakReads  Number      number of weak read if any. Default 0.
  --number_of_genes     Number      number of genes to be selected from input. Default is 200
  --expFile File        path        Strong Expression file path
  --opt_weak_expFile    File path   Weak expression file path.
  --opt_seqFile         File path   Strong sequence file path.
  --opt_out             File path.  output folder path.
  --opt_loops           Number      Number of loops to repeat calculations. Default is 3.
  --opt_min_L           Number      Minimum length for predicted pwm (motif), Default is 9.
  --opt_max_L           Number      Maximum length for predicted pwm (motif). Default is 9.
  --opt_iteration       Number      Number of iterations. Default is 500.
  --opt_p_value         float       p value. Default is 0.0001
  --opt_strand          Number      Strand.     Default is 0
  --opt_normalization   Number      Normalization value. Default is 2.
  --max_processors      Number      Define maximum number of processors for parallel computing. Default is mp.cpu_count()

----------------------------------ensemble investigate--------------------------
usage: abc4pwm ensemble_investigate [-h]
                                    [--path_to_predicted_files . mlp file]
                                    [--db_folder path or list]
                                    [--output_folder FOLDER]
                                    [--tf_name string] [--db_type string]
                                    [--top_n TOP_N]
                                    [--min_pwms_in_cluster MIN_PWMS_IN_CLUSTER]
                                    [--db_format string]
                                    [--input_count NUMBER] [--db_count NUMBER]
                                    [--db_file_type String]
                                    [--input_file_type String]
                                    [--input_prob Number] [--db_prob Number]

optional arguments:
  -h, --help            show this help message and exit
  --path_to_predicted_files     .mlp file       Folder which contain predicted files.
  --db_folder                   path or list    path to clustered dbds according to the hierarchy of abc4pwm.if db_type=list then then this paramter should be list of pwms, against whcih you are searching the pwm
  --output_folder               FOLDER          This folder should to output folder. search_result.pdf output file will be stored here.
  --tf_name                     String          (Optional) If you want to search specific tf in a folder then use this parameter
  --db_type                     String          (Optional) If database for comparison is folder hierarchy like abs4pwm then this willbe db_type=path. Write list if providing list of pwms for comparison
  --top_n                       Number          Specify how many top matches from database is required. Default 2
  --min_pwms_in_cluster         Number          Number of minimum acceptable pwms in a cluster made from predicted pwms. Default 3
  --db_format                   string          (Optional) If database for comparison have format, please mention.Supported formats are abc4pwm, Tranfac, Jaspar. default is abc4pwm
  --input_count                 NUMBER          (Optional) 1 if input file contains values in counts
  --db_count                    NUMBER          1 if database file contains values in counts
  --db_file_type                String          mention the extension of file type. e.g., .mlp, .txt
  --input_file_type             String          mention the extension of file type. e.g., .mlp, .txt
  --input_prob                  Number          (Optional) 1 if input file contains values in probabilities
  --db_prob                     Number          (Optional) 1 if database file contains values in probabilities


----------------------------Example-------------------
Assuming a folder with the name 'data' already exists with two more folders inside. 1. 'in/' 2. 'out/'. 'in' further has two more folders, in_pwms  and pwms_original. It should look like this
data/in/in_pwms (your input files, position weight matrices, in .mlp should be inside in_pwms)
data/in/pwms_original (a copy of input files, position weight matrices, in .mlp should be inside pwms_original)

data/out/

Then run the following while current working directory should be 'data/'

# run following in data folder


# run following in data folder
abc4pwm cleandatabase_for_classification --pwm_files_directory in/in_pwms/ --read_new 0

abc4pwm classification --pwm_files_directory in/in_pwms/ --output_directory out/classification_out/ --original_pwm_files_directory in/pwm_original/

abc4pwm clustering --dbd_folders_directory out/classification_out/ --output_directory out/clustering_out/

abc4pwm quality_assessment --dbd_folders_directory out/clustering_out/ --out_path_for_qa_clusters out/quality_assessed_out/ --output_folder_for_text_report out/reports_in_text/ --output_path_for_quality_assessment_file in/ --load_new_assesment 1

abc4pwm representative_motif --path_to_clusters out/quality_assessed_out/HMG/out/ --clusters 0,1,2
#representative for all dbds and all folders
abc4pwm representative_motif --path_to_clusters out/quality_assessed_out/ --clusters all --dbd all

abc4pwm visualize --path_to_folder_of_assessment_file in/ --path_to_folder_of_DBDs out/quality_assessed_out/ --output_folder out/plots/boxplots/ --dbd_for_plot out/quality_assessed_out/HMG/
#to visualize all dbds box plots
abc4pwm visualize --path_to_folder_of_assessment_file in/ --path_to_folder_of_DBDs out/quality_assessed_out/ --output_folder out/plots/boxplots/ --dbd_for_plot all


abc4pwm plot_cluster_motifs --path_to_clusters out/quality_assessed_out/HMG/out/ --output_folder_pdfs out/plots/pdfs --clusters 0,1,4
#plot motifs for all cluster of a dbd
abc4pwm plot_cluster_motifs --path_to_clusters out/quality_assessed_out/HMG/out/ --output_folder_pdfs out/plots/pdfs --clusters all
#plot motifs for all cluster of all dbd
abc4pwm plot_cluster_motifs --path_to_clusters out/quality_assessed_out/ --output_folder_pdfs out/plots/pdfs --clusters all --dbd all


abc4pwm text_tfdb --pwm_files_directory in/in_pwms/ --output_directory out/reports_in_text/


#for clustering the uncertain pwms
abc4pwm clustering --dbd_folders_directory out/uncertain_pwms/ --output_directory out/uncertain_clustering_out/ --in_dbd 0

#for clustering the all together pwms
abc4pwm clustering --dbd_folders_directory in/in_pwms/ --output_directory out/all_clustering_out/ --in_dbd 0


#for searching in a transfac folder
abc4pwm searching --pwm in/in_pwms/AP1_known1_from_AP1_2_from_AP-1_transfac_M00172.mlp --db_path out/convert/to_transfac/ --output_directory out/search_out/ --db_type folder --db_format transfac

#for searching in a jaspar folder
abc4pwm searching --pwm in/in_pwms/AP1_known1_from_AP1_2_from_AP-1_transfac_M00172.mlp --db_path out/convert/to_jaspar/ --output_directory out/search_out/ --db_type folder --db_format jaspar

#for searching in a abc4pwm folder
abc4pwm searching --pwm in/in_pwms/AP1_known1_from_AP1_2_from_AP-1_transfac_M00172.mlp --db_path in/in_pwms/ --output_directory out/search_out/ --db_type folder

#for format conversion
#abc4pwm to transfac
abc4pwm conversion --pwm_files_directory in/in_pwms/ --in2out abc4pwm2transfac --output_folder out/convert/to_transfac/

#transfac to abc4pwm
abc4pwm conversion --pwm_files_directory out/convert/to_transfac/ --in2out transfac2abc4pwm --output_folder out/convert/to_abc/

#abc4pwm to jaspar
abc4pwm conversion --pwm_files_directory in/in_pwms/ --in2out abc4pwm2jaspar --output_folder out/convert/to_jaspar/

#jaspar to abc4pwm
abc4pwm conversion --pwm_files_directory out/convert/to_jaspar/ --in2out jaspar2abc4pwm --output_folder out/convert/to_abc/

#ensemble learning
abc4pwm ensemble_learning --opt_strong_expFile in/expression/demo_swi4_0.5Kseq_cacgaaaa_500.txt --opt_seqFile in/seq/demo_swi4_0.5Kseq_cacgaaaa_500.fa --opt_out out/ensemble/swi4/ --select_random_n 200
