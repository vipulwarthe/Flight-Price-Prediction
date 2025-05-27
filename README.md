# Flight-Price-Prediction

- I did this project just to perform some next level feature engineerings to elevate the performane of this model.  
- I have also created a gui using HTML,Bootstrap,CSS and implemnted the backend in Flask for this project and will be uploading that on Heroku soon.  
- Actually this was a Kaggle problem.  
- Initially I used RandomForestRegressor but that was not giving very satisfying results so I used RandomSearchCV to find best hyerparameters and came up witha a  good model with r2 score of around 0.82.  
- Also used ExtraTreeRegressor to visualize the importances of all the features.  
- Just run app.py to see the gui on local host.  
  
Do visit my blog for better explanations: https://machinelearningprojects.net/flight-price-prediction/
  
![](ss.png)

# orignal github link: https://github.com/sharmaji27/Flight-Price-Prediction

# install the python environment, dependancies and run the ipynb file and deploy the app

    sudo apt update  
    sudo apt install python3-venv -y         
    python3 -m venv mlenv               
    source mlenv/bin/activate                
    deactivate                               
    mkdir mlproject                          
    cd mlproject                             
    git clone https://github.com/vipulwarthe/Flight-Price-Prediction.git
    ls  
    cd Flight-Price-Prediction
    pip install -r requirements.txt
    python app.py

# requirements file added and update in ipynb file

# Error resolved:

1) add the library to read the dataset in requirements.txt  or you can add below code in ipynb file directly (error resolved for this library)
   
       !pip install openpyxl

2) value error for Indigo resolved - Use only the numeric columns for the correlation matrix and updated the code in ipynb

       import matplotlib.pyplot as plt
       import seaborn as sns

       # Filter numeric columns only
       numeric_data = train_data.select_dtypes(include=['number'])

       plt.figure(figsize=(10,10))
       sns.heatmap(numeric_data.corr(), cmap='viridis', annot=True)
       plt.show()

3) Plotting the residuals - error resolved distplot function is depricated and recommended to use sns.histplot() or sns.kdeplot() instead and updated the code in ipynb

       plt.figure(figsize=(8,8))
       sns.histplot(y_test - prediction, kde=True)
       plt.title("Residuals Distribution")
       plt.xlabel("Residuals")
       plt.ylabel("Frequency")
       plt.show()

# Deployment using ECR and ECS

* create one instance with t2.medium and connect
* Install docker
* Install awscli
* configure aws
* create ECR repo and run push commands on server
* create ECS cluster, task definaton and then create task and run the task
* access the application using cluster IP
   
   
