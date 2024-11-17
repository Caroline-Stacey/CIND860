Project Stages:
1) Preliminary Data Analysis:
2) Data Cleaning:
3) Balancing the Data:
There may be issues with imblearn to import SMOTE, this is the code needed to fix:
  !pip uninstall scikit-learn --yes
  !pip uninstall imblearn --yes
  !pip install scikit-learn==1.2.2
  !pip install imblearn
OR 
  conda install -c conda-forge imbalanced-learn
5) Individual Models:
6) Ensemble Learning:
