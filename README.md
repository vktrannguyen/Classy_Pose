# Classy_Pose

![Graphical_Abstract](https://github.com/vktrannguyen/Classy_Pose/blob/main/ClassyPose_GraphicalAbstract.jpg)

You will find herein the code and data related to our paper:

**Tran-Nguyen, V.K., Camproux, A.C. & Taboureau, O. ClassyPose: A Machine-Learning Classification Model for Ligand Pose Selection Applied to Virtual Screening in Drug Discovery (2024).**

## Code

The code is stored in the **Code** folder:

- *PLEC_extraction.py*: the Python code for extracting PLEC<sup>[1]</sup> fingerprints from target-bound ligand poses (e.g., docking poses).
- *Pose_Classification_Models.ipynb*: the Jupyter notebook for training, testing and evaluating machine-learning (ML) models for ligand pose classification. Here, we provide the code for four supervised learning algorithms: random forest (RF), extreme gradient boosting (XGB), support vector machine (SVM), and artificial neural network (ANN). The code for computing six evaluation metrics is also provided: ROC-AUC, PR-AUC, balanced accuracy, Matthews correlation coefficient, specificity, and recall.
- *ClassyPose.ipynb*: the Jupyter notebook for training and applying **ClassyPose**, our best-performing pose classification model employing the SVM algorithm.

## Data

All data are stored in the **Data** folder. Inside, you will find the following sub-folders:

### The 'training_data' sub-folder:

- *training_data_poses.csv*: the CSV data file for training our ML classification models in *Pose_Classification_Models.ipynb* and *ClassyPose.ipynb*.
- *training_data_PLEC.zip*: the zipped CSV file containing all PLEC fingerprints of 21,647 ligand poses (both native and redocked) in our training set. You need to unzip this file (using the *unzip* command), then use it to train our ML classification models in *Pose_Classification_Models.ipynb* and *ClassyPose.ipynb*.

### The 'test_data' sub-folder:

- *test_data_poses.csv*: the CSV data file of our test set.
- *test_data_PLEC.zip*: the zipped CSV file containing all PLEC fingerprints of 5,427 ligand poses (both native and redocked) in our test set. You need to unzip this file beforehand.

### The 'hard_test_data' sub-folder:

- *hard_test_data_poses.csv*: the CSV data file of our hard test set.
- *hard_test_data_PLEC.zip*: the zipped CSV file containing all PLEC fingerprints of 12,536 ligand poses (both native and redocked) in our hard test set. You need to unzip this file beforehand.

### The 'test_results' and 'hard_test_results' sub-folders:

The scores that all ligand poses in the test and hard test sets received from each evaluated scoring function:

- Our ML classification models (RF, XGB, SVM, ANN): the **good pose probability**. We provide results of five training-test runs per learning algorithm.
- Smina: the Smina docking scores<sup>[2]</sup>.
- RF-Score-VS: scores issued by the RF-Score-VS v.2 scoring function<sup>[3]</sup>.
- CNN-Score: scores issued by the CNN-Score scoring function<sup>[4]</sup>.

### The 'cross_validation' sub-folder:

- Inside **subsets**: the data related to our different sub-training and validation sets, including CSV data files and zipped CSV files containing all PLEC fingerprints.
- Inside **results**: the classification results (good pose probability, pose classification) of our ML models (RF, XGB, SVM, ANN) on each validation set. We provide results of five training-test runs per learning algorithm.
- Inside **test_on_training_set**: the classification results (good pose probability, pose classification) of our ML models (RF, XGB, SVM, ANN) on the entire training set. We provide results of five training-test runs per learning algorithm.

### The 'clustering' sub-folder:

- *all_Xtal_PLEC_IDs.csv*: the CSV file containing all PLEC fingerprints extracted from the co-crystallographic ligand poses (no redocked pose) of the 1,102 PDB entries retained for clustering.
- *100_clusters.xlsx*: the clustering results of 1,102 PDB entries (100 clusters and their members) and their partition into the training set and the test set.

### The 'virtual_screening' sub-folder:

Virtual screening results on five data sets whose targets are not part of the data used to train our ML models:

- **PPARA_OTS**: an "own test set" featured in a recently published protocol<sup>[5]</sup>. Target: peroxisome proliferator activated receptor alpha.
- **HXK4_DUD-E**: the HXK4 data set from the DUD-E data collection<sup>[6]</sup>. Target: hexokinase type IV.
- **ROCK1_DUD-E**: the ROCK1 data set from the DUD-E data collection. Target: Rho-associated protein kinase 1.
- **EGFR_DEKOIS2**: the EGFR data set from the DEKOIS2.0 data collection<sup>[7]</sup>. Target: the epidermal growth factor receptor.
- **11BHSD1_DEKOIS2**: the 11betaHSD1 data set from the DEKOIS 2.0 data collection. Target: 11-beta-hydroxysteroid dehydrogenase 1.

Inside each sub-folder listed above, you will find the following files:

- The mol2 files containing the structure of the unliganded protein target and that of the crystallographic ligand pose, stored separately.
- The zipped mol2 file containing all docking poses of the successfully docked ligands in each data set.
- The scores of all docking poses given by **ClassyPose** (our best-performing SVM model) and three existing scoring functions (Smina, RF-Score-VS, CNN-Score). These scores would determine the outcome of pose selection and ligand ranking, depending on our six virtual screening schemes (as described in the manuscript).

## Attention

To use our code, you need to install **Python (v.3.7)** and set up the **protocol-env** environment beforehand. Please use the file *protocol-env.yml* in our **MLSF-protocol** repository: https://github.com/vktrannguyen/MLSF-protocol, and follow the instructions provided in the README file there.

In brief, the following Python libraries/packages need to be installed:

- pandas (v.0.23.4)
- oddt (v.0.7)
- NumPy (v.1.21.5)
- sklearn (v.1.0.2)
- XGBoost (v.2.0.1)
- joblib (v.1.1.0)
- tqdm (v.4.62.3)

For further information and other queries, please contact **Dr. Viet-Khoa Tran-Nguyen** at: viet-khoa.tran-nguyen@u-paris.fr, or khoatnv1993@gmail.com.

## References

<sup>[1]</sup> Wójcikowski, M., Kukiełka, M., Stepniewska-Dziubinska, M. M. & Siedlecki, P. Development of a protein-ligand extended connectivity (PLEC) fingerprint and its application for binding affinity predictions. *Bioinformatics* **35**, 1334–1341 (2019).

<sup>[2]</sup> Koes, D. R., Baumgartner, M. P. & Camacho, C. J. Lessons learned in empirical scoring with Smina from the CSAR 2011 benchmarking exercise. *J. Chem. Inf. Model.* **53**, 1893–1904 (2013).

<sup>[3]</sup> Wójcikowski, M., Ballester, P. J. & Siedlecki, P. Performance of machine-learning scoring functions in structure-based virtual screening. *Sci. Rep.* **7**, 46710 (2017).

<sup>[4]</sup> Ragoza, M., Hochuli, J., Idrobo, E., Sunseri, J. & Koes, D. R. Protein–ligand scoring with convolutional neural networks. *J. Chem. Inf. Model.* **57**, 942–957 (2017).

<sup>[5]</sup> Tran-Nguyen, V. K., Junaid, M., Simeon, S. & Ballester, P. J. A practical guide to machine-learning scoring for structure-based virtual screening. *Nat. Protoc.* **18**, 3460–3511 (2023).

<sup>[6]</sup> Mysinger, M. M., Carchia, M., Irwin, J. J. & Shoichet, B. K. Directory of useful decoys, enhanced (DUD-E): better ligands and decoys for better benchmarking. *J. Med. Chem.* **55**, 6582–6594 (2012).

<sup>[7]</sup> Bauer, M. R., Ibrahim, T. M., Vogel, S. M. & Boeckler, F. M. Evaluation and optimization of virtual screening workflows with DEKOIS 2.0—a public library of challenging docking benchmark sets. *J. Chem. Inf. Model.* **53**, 1447–1462 (2013).

----------------------------------------------------------------------------------------------------

This work was carried out at the Unit of Functional and Adaptive Biology (BFA), INSERM U1133, CNRS UMR8251, Université Paris Cité, France. The latest version of all data and code provided herein was updated and made available free of charge on March 25, 2024, and is subject to copyright.
