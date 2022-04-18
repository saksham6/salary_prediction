# salary_prediction
## Table of Contents  
1. [Prerequisites](prerequisites)
1. [Problem-Statement](#problem-statement) 

1. [Data-Analysis-And-Data-Cleaning(EDA](#data-analysis-and-data-cleaning)

1. [Model Selection](#model-selection)

1. [Deployment](#deployment)


 

<!-- <a name="header"/> -->
## Prerequisites
1. Scikit Learn
1. Pandas
1. Numpy
1. Flask

## Problem-Statement  

The objective of this exercise is to build a model, using data that provide the 
optimum insurance cost for an individual. i have used the health and habit related parameters for 
the estimation cost of insurance

## Data-Analysis-And-Data-Cleaning

There are few columns where there we can see bit skewness but overall we can data is normally distributed.

1. **Missing Value**
    * There is no missing value.

1. **Duplicate Value**
    * There are 24 rows having duplicate value and we have dropped the value.

1. **Outlier**
   * There are ouliers in few columns which we have treated.  
  
  1. **Removal of unwanted variables (if applicable)**
    
     * capital gain and capital loss are both 0 after removing outliers. These 2 variables can be dropped


## Model-Selection
* **Before model tuning**  

| Model Name                | Accuracy Train| Accuracy Test|
| -------------             |:------------- |--------------|
| Logistic Regression        | 75.62%         | 77.04.7%        |


* **After model tuning**  

| Model Name                | Accuracy Train| Accuracy Test|
| -------------             |:------------- |--------------|
| Logistic Regression        | 80.57%         | 81.02%      

* **Best Params**  
Best: 0.805397 using {'C': 100, 'penalty': 'l2', 'solver': 'newton-cg'}


## Deployment
  * ### **Deploy into Heroku using Flask**
     
    Flask is a web framework that provides libraries to build
lightweight web applications in python.
  
    It is based on WSGI toolkit and jinja2 template engine.
WSGI is an acronym for web server gateway interface which is a standard for
python web application development.
  
    Jinja2 is a web template engine to render the dynamic web pages.
  
    Flask requires python 2.7 or higher  
      
   * ### **Steps to deploy model into Heroku using Flask**
     
     * **Step-1**
       
       Create a “pickle” of the model (i.e. file with an extension as .pkl)
       “Pickling” is the process whereby a Python object hierarchy is converted into a byte stream
  
            **save the model to disk**
  
         Import pickle
         pickle_out = open("adult_flask.pkl","wb")  

            pickle.dump(model, pickle_out)  

            loaded_model = pickle.load(open("adult_flask.pkl", "rb"))  

            result = loaded_model.score(X_test, y_test)
  
            print(result)  


      * **Step-2**
          
          Create an HTML page/file with or without CSS which would
be the index page
One Page could be created both to receive the user input and display the result or
separate page could be created to receive input and then to display result.
These files should have an extension as “.html” and these files should be stored
in the folder “templates”

     * **Step-3**  

       Create an file with an extension “.py” using python editor like
jupyter notebook.

        Import the library files
import numpy as np
import pandas as pd
from flask import Flask, request,render_template
import pickle  

        Initialise the flask
        app= Flask(__name__)  
        Refer app.py file

     * **Step-4**  
        * Folder structure
        1. Flask
        1. Templates  

            1. Adult.html
            1. result.html
        1. adult_flask.pkl
        1. app.py  

      
      * **Step-5**
        
        @ Anconda prompt change the directory to where you have all the files like in our case,
    folder is “Flask”. Once you are at the required directory type   
      
            python app.py   
  

      
      * **Steps-6**
  
        to deploy on heroku we need three files.
              
              1. Procfile
              2. runtime.txt
              3. requirements.txt 
    
        **Procfiles:**
      Note: its should have any extension and "P" in Procfile should in uppercase.
        
        **runtime.txt:**
      we need to declare python version.

        **requirements.txt**
    all the dependecise libraries used in you model should be written here.


      
      * **Step-7**
  
        Login into heroku.
          
          create new app
            
            Go to deploy tab
            there will be two option using Heroku CLI and Github. select any of them and all the steps will be shown below. 
