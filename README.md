Introduction
============

This project helps to predict the survival rate of the patients who is suffering from the problem of glioblastoma( A type of aggressive cancer due to which brain loses it's normal functionality). So, basically we are using the deep learning algorithims and mathematical calculations for prediction of survival rate. For prediction we are using the mRNA expression dataset.

Installation
============

Prerequisites
-------------
GBMrate requires:

	* Python (>= 2.6 or >= 3.3)
	* NumPy (>= 1.6.1): http://www.numpy.org/
	* SciPy (>= 0.9): http://www.scipy.org/
	* Scikit-learn (>= 0.17): http://scikit-learn.org/
	* Pandas (>= 0.16.0): http://pandas.pydata.org/

If you already have a working installation of numpy and scipy, the easiest way to install scikit-learn and pandas is using pip::

	pip install -U scikit-learn

	pip install -U pandas

or using conda::

	conda install scikit-learn

	conda install pandas


Install GBMrate
-------------------------
You can install GBMrate either from PyPi using pip and install it from the source.

Install from PyPi::

	pip install survivalPredictor


Using GBMrate


	survivalPredictor --help


Demo

	survivalPredictor --demo

Path of Folder

	survivalPredictor --demo --output ~/path/to/your/folder


Define features and feature subsets
-----------------------------------
To tell the model to use specific features you need to type::

	survivalPredictor --model svm --feature "Top 10", "Top 100", "Top 200"

Make sure the features names are comma separated. 

If you want to compare the individual predictive power or combinatorial predictive power of different features, you need to pass the argument ``--compare`` with ``--features``::

	survivalPredictor --model nb --feature "Top 10", "Top 100", "Top 200" --compare


Run model with cross-validation
-------------------------------
By default all models use 3-fold cross-validation. If you want to set different fold lets say 5, set ``--cv`` parameter as::

	survivalPredictor --model rf --feature "Top 200" --cv 5


Make predictions
------------------
To make predictions should have computed available features and saved a tab-delimited file. Next, you need to tell the model the features you have to make prediction with using ``--feature`` and also provide the Tab delimetd file to ``--input`` and next type ``--pred`` to make predictions::

	survivalPredictor --model rf --feature "Top 200" --input ~/path/to/test/file.txt --pred

This will save the predictions results as CSV file ``survivalPredictor_[MODEL_NAME]_predictions.csv``. In the CSV file the field Class is 1=alive and 0=dead. We also report  probability score for each prediction to tell the user how good and bad a prediction is. This will help to decide which candidates to select for further analysis.