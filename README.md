Project Stages:
1) Preliminary Data Analysis:
   
Import initially required libraries - any necessary libraries are imported at the start of the section for which they will be needed.

As there are many columns, but not an overwhelming amount, it is helpful to set the max display to show all the columns.

Exploring the data uses numerous techniques such as looking at the first few rows, describing the data, and determining the type of data. Immediately, a nonsense column at the end is dropped.

Histograms are generated for all quantitative features to explore distribution. Most tend to be normally distributed.

Correlations are explored via heatmaps to see if there are any clearly evident patterns. 
   
2) Data Cleaning:

The first step is to quantify the dependent variable ("Fraud Reported"). If Fraud was reported, it is assigned a "1", where there was no fraud, it is assigned a "0").

Sex is also quantified: Female = 1 and Male = 0

Education level is quantified as it can mostly be seen as increasing on a scale even though JD, MD, Masters are all graduate level:
High School : 0
College : 1
Associate : 2
Masters : 3
JD : 4
MD : 5
PhD : 6
   
4) Balancing the Data:
There may be issues with imblearn to import SMOTE, this is the code needed to fix:
  !pip uninstall scikit-learn --yes
  !pip uninstall imblearn --yes
  !pip install scikit-learn==1.2.2
  !pip install imblearn
OR 
  conda install -c conda-forge imbalanced-learn
5) Individual Models:
6) Ensemble Learning:
