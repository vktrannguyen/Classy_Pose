# Classy_Pose

![Graphical_Abstract](https://github.com/vktrannguyen/Classy_Pose/blob/main/ClassyPose_GraphicalAbstract.jpg)

You will find herein the code and data related to our paper:

**Tran-Nguyen, V.K. & Taboureau, O. ClassyPose: A Machine-Learning Classification Model for Correct Ligand Pose Selection (2024).**

1. The code is stored in the **Code** folder:

- *PLEC_extraction.py*: the Python code for extracting PLEC<sup>[1]</sup> fingerprints from target-bound ligand poses (e.g., docking poses).
- *Pose_Classification_Models.ipynb*: the Jupyter notebook for training, testing and evaluating machine-learning (ML) models for ligand pose classification. Here, we provide the code for four supervised learning algorithms: random forest (RF), extreme gradient boosting (XGB), support vector machine (SVM), and artificial neural network (ANN). The code for computing six evaluation metrics is also provided: ROC-AUC, PR-AUC, balanced accuracy, Matthews correlation coefficient, specificity, and recall.
- *ClassyPose.ipynb*: the Jupyter notebook for training and applying **ClassyPose**, our best-performing pose classification model employing the SVM algorithm.

2. All data are stored in the **Data** folder. Inside, you will find the following sub-folders:

2.1. The **training_data** sub-folder:

- *training_data_poses.csv*: the CSV data file for training our ML classification models in *Pose_Classification_Models.ipynb* and *ClassyPose.ipynb*.
- *training_data_PLEC.zip*: the zipped CSV file containing all PLEC fingerprints of 21,647 ligand poses (both native and redocked) in our training set. You need to unzip this file (using the *unzip* command), then use it to train our ML classification models in *Pose_Classification_Models.ipynb* and *ClassyPose.ipynb*.

2.2. The **test_data** sub-folder:

- *test_data_poses.csv*: the CSV data file of our test set.
- *test_data_PLEC.zip*: the zipped CSV file containing all PLEC fingerprints of 5,427 ligand poses (both native and redocked) in our test set. You need to unzip this file beforehand.

2.3. The **hard_test_data** sub-folder:

- *hard_test_data_poses.csv*: the CSV data file of our hard test set.
- *hard_test_data_PLEC.zip*: the zipped CSV file containing all PLEC fingerprints of 12,536 ligand poses (both native and redocked) in our hard test set. You need to unzip this file beforehand.

2.4. The **test_results** and **hard_test_results** sub-folders:

The scores that all ligand poses in the test and hard test sets received from each evaluated scoring function:

- Our ML classification models (RF, XGB, SVM, ANN): the **good pose probability**. We provide results of five training-test runs per learning algorithm.
- Smina: the Smina docking scores<sup>[2]</sup>.
- RF-Score-VS: scores issued by the RF-Score-VS v.2 scoring function<sup>[3]</sup>.
- CNN-Score: scores issued by the CNN-Score scoring function<sup>[4]</sup>.

2.5. The **cross_validation** sub-folder:

- Inside **subsets**: the data related to our different sub-training and validation sets, including CSV data files and zipped CSV files containing all PLEC fingerprints.
- Inside **results**: the classification results (good pose probability, pose classification) of our ML models (RF, XGB, SVM, ANN) on each validation set. We provide results of five training-test runs per learning algorithm.
- Inside **test_on_training_set**: the classification results (good pose probability, pose classification) of our ML models (RF, XGB, SVM, ANN) on the entire training set. We provide results of five training-test runs per learning algorithm.

2.6. The **clustering** sub-folder:

- *all_Xtal_PLEC_IDs.csv*: the CSV file containing all PLEC fingerprints extracted from the co-crystallographic ligand poses (no redocked pose) of the 1,102 PDB entries retained for clustering.
- **100_clusters.xlsx*: the clustering results of 1,102 PDB entries (100 clusters and their members) and their partition into the training set and the test set.

2.7. The **virtual_screening** sub-folder:

Virtual screening results on five data sets whose targets are not part of the data used to train our ML models:

- **PPARA_OTS**: an "own test set" featured in a recently published protocol<sup>[5]</sup>. Target: the peroxisome proliferator activated receptor alpha.
- 

