**Project Stages:**
**1) Preliminary Data Analysis:**
   
Import initially required libraries - any necessary libraries are imported at the start of the section for which they will be needed.

As there are many columns, but not an overwhelming amount, it is helpful to set the max display to show all the columns.

Exploring the data uses numerous techniques such as looking at the first few rows, describing the data, and determining the type of data. Immediately, a nonsense column at the end is dropped.

Histograms are generated for all quantitative features to explore distribution. Most tend to be normally distributed.

Correlations are explored via heatmaps to see if there are any clearly evident patterns. 
   
**2) Data Cleaning:**

Quantifying some features:
- Quantify the dependent variable ("Fraud Reported"). If Fraud was reported, it is assigned a "1", where there was no fraud, it is assigned a "0").

- Sex is also quantified: Female = 1 and Male = 0

- Education level is quantified as it can mostly be seen as increasing on a scale even though JD, MD, Masters are all graduate level:
High School : 0
College : 1
Associate : 2
Masters : 3
JD : 4
MD : 5
PhD : 6

- Incident Severity is quantified as it is scaled:
  Trivial Damage: 0
  Minor Damage: 1
  Major Damage: 2
  Total Loss: 3

Created a new column which indicates whether the policy state and incident state are the same.

Remove certain columns:
- Police Report Available - too many "?" and authorities contacted will provide that information; make an additional column to designate whether authorities were contact or not.
- policy number: unquantifiable data and does not provide useful information
- indicent location: difficult to quantify
- incident city: difficult to quantify and also prone to bias/discrimination.
- incident date: unlikely to contribute to fraud
- auto model: information can be captured by auto make
- policy bing date: unlikely to contribute to fraud and captured by "months as customer"
- incident state: important information captured in new column indicating whether the policy and incident state is the same
- policy csl: unlikely to contribute to fraud
- policy state: important information captured in new column indicating whether the policy and incident state is the same

Review the unique values and see if there are categorical features with many unique values

- insured zip dropped due to too much variance and little information. also very susceptible to bias.

  Review for missing values and remove the appropriate columns. There are a significant number of missing values (178 in collision type, and 360 in property damage). That is too many to remove the rows as it would significantly affect the size of the data. Other options were considered such as most frequently occuring values but they seemed illogical. This may be reviewed at a later point depending on model accuracy outcomes.

  Boxplots generated for quantitative features vs. the dependant feature.

[71] Feature Scaling
- use maxmin scaler to scale the data especially because some data has small ranges (1-6) and others reach into the millions.

[78] GetDummies is used to deal with the categorical variables. This increases the number of features to 91

[80] The data is split prior to balancing as only the training set is balance in order to avoid as few changes to the test dataset.

**4) Balancing the Data:**
[83] There may be issues with imblearn to import SMOTE, this is the code needed to fix:
  !pip uninstall scikit-learn --yes
  !pip uninstall imblearn --yes
  !pip install scikit-learn==1.2.2
  !pip install imblearn
OR 
  conda install -c conda-forge imbalanced-learn

[85-87] SMOTE and ENN are used to balance the data as literature has indicated that is a superior method (see: Esenogho, E., Mienye, I. D., Swart, T. G., Aruleba, K., & Obaido, G. (2022). A neural network  ensemble with feature engineering for improved credit card fraud detection. IEEE Access, 10, 16400–16407. https://doi.org/10.1109/access.2022.3148298 )
  
5) Individual Models:
[89] Individual Models are applied to see which provide the strongest results and will therefore be applied in ensemble learning 
7) Ensemble Learning:
