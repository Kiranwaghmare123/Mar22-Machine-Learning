
Day 7: Classification

================================================

Date: 20/07/2022

Topics:
------------------
      -Revision of Regression
      -Preprocessing Techniques






Steps for Regression Model:
-----------------------------
          1.Importing the libraries
          2.Importing dataset
            -head,shape,describe
            -X,Y
          3.Identify Independent and Dependent variables
            -Assign values to X,y
          -----MLR----------
          #Pre-processing
            Encoder
            scaling
          -----------------------
          4.Splitting the dataset into Training and Testing
            -Split train & Test
            -Model building-SLR/MLR/PLR
          5.Predicting the Training Results
            -testing data
          6.Visualising the Training and Testing Results
            -X_test,y_pred
          7.Metrics
            -intercept, coeff
            -MSE,R2,Accuracy




MLR: 
        -Preprocessing
        -Categorical data---->numeric data
        -Encoder: OneHotEncoder




======================================================================================

Simple Linear Regression
============================

        1.Importing the libraries
        --------------------------

        import numpy as np
        import matplotlib.pyplot as plt
        import pandas as pd


        2.Importing Dataset
        ----------------------
        dataset = pd.read_csv('Salary_Data.csv')


        ​3.Identify Independent and Dependent variables
        ----------------------------------------------
        X = dataset.iloc[:, :-1].values
        y = dataset.iloc[:, -1].values


        4.Splitting the dataset into the Training set and Test set
        --------------------------------------------------------------
        from sklearn.model_selection import train_test_split
        X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 1/3, random_state = 0)
        Training the Simple Linear Regression model on the Training set


        5.Apply Linear Regression()
        ---------------------------
        from sklearn.linear_model import LinearRegression
        regressor = LinearRegression()
        regressor.fit(X_train, y_train)


        6.Predicting the Training set results
        ---------------------------------------
        y_pred = regressor.predict(X_test)


        7.Visualising the Training set results
        ---------------------------------------
        #Training dataset:
        ------------------
        plt.scatter(X_train, y_train, color = 'red')
        plt.plot(X_train, regressor.predict(X_train), color = 'blue')

        #Testing dataset:
        -----------------
        plt.scatter(X_test, y_test, color = 'red')
        plt.plot(X_train, regressor.predict(X_train), color = 'blue')


        8.Meteris
        -------------
          -reg coefficient
          -intercept
          -MSE
          -Model Summary
          -R2


======================================================================================


Multiple Linear Regression
============================

          1.Importing the libraries
          --------------------------

          import numpy as np
          import matplotlib.pyplot as plt
          import pandas as pd


          2.Importing Dataset
          ----------------------
          dataset = pd.read_csv('50_Startups.csv')


          ​3.Identify Independent and Dependent variables
          ----------------------------------------------
          X = dataset.iloc[:, :-1].values
          y = dataset.iloc[:, -1].values


          4.Preprocessing: Converting Catergorical data into numeric data
          -----------------------------------------------------------------
          from sklearn.compose import ColumnTransformer
          from sklearn.preprocessing import OneHotEncoder
          ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [3])], remainder='passthrough')
          X = np.array(ct.fit_transform(X))


          5.Splitting the dataset into the Training set and Test set
          --------------------------------------------------------------
          from sklearn.model_selection import train_test_split
          X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 1/3, random_state = 0)
          Training the Simple Linear Regression model on the Training set


          6.Apply Linear Regression()
          ---------------------------
          from sklearn.linear_model import LinearRegression
          regressor = LinearRegression()
          regressor.fit(X_train, y_train)


          7.Predicting the Training set results
          ---------------------------------------
          y_pred = regressor.predict(X_test)


          8.Visualising the Training set results
          ---------------------------------------
          plt.scatter(y_test, y_pred, color = 'red')
          #plt.plot(y_test, y_pred, color = 'blue')

          9.Meteris
          -------------
            -MSE
            -Model Summary
            -R2


======================================================================================

Polynomial Regression
============================

              1.Importing the libraries
              --------------------------

              import numpy as np
              import matplotlib.pyplot as plt
              import pandas as pd


              2.Importing Dataset
              ----------------------
              dataset = pd.read_csv('50_Startups.csv')


              ​3.Identify Independent and Dependent variables
              ----------------------------------------------
              X = dataset.iloc[:, :-1].values
              y = dataset.iloc[:, -1].values


              5.Splitting the dataset into the Training set and Test set
              --------------------------------------------------------------
              from sklearn.model_selection import train_test_split
              X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 1/3, random_state = 0)
              Training the Simple Linear Regression model on the Training set


              6.Apply Linear Regression()
              ---------------------------
              from sklearn.linear_model import LinearRegression
              regressor = LinearRegression()
              regressor.fit(X_train, y_train)


              7.Visualize Linear Regression()
              ---------------------------
              plt.scatter(X_train,y_train,c='red',cmap=None,alpha=0.5)
              plt.plot(X_train,LinModel.predict(X_train),color='blue')


              8.Apply Polynomial Regression()
              ---------------------------
              from sklearn.preprocessing import PolynomialFeatures 
              ##Adding polynomial Terms to simple Linear regression model
              polynom = PolynomialFeatures(degree = 2) 
              X_polynom = polynom.fit_transform(X_train) 
              X_polynom

              9.Fitting into the model
              -----------------------
              PolyModel = LinearRegression() 
              PolyModel.fit(X_polynom, y_train)


              10.Visualize the polynom Model
              --------------------------------
              plt.scatter(X_train,y_train,c='black',cmap=None,alpha=0.7)
              plt.plot(X_train,PolyModel.predict(X_polynom),color='red')


              plt.scatter(X_train,y_train,c='black',cmap=None,alpha=0.8)
              plt.plot(X_train,PolyModel.predict(polynom.fit_transform(X_train)),color='red')

              11.Predicting the Training set results
              ---------------------------------------
              y_pred = regressor.predict(X_test)


              12.Evaluation Model using R-Square for Simple Linear Regression
              -------------------------------------------------------------
              y_pred = PolyModel.predict(polynom.fit_transform(X_test))


              from sklearn import metrics
              r_square = metrics.r2_score(y_test, y_pred)
              print('R-Square Error  with Polynomial Regression is---->:', r_square)


              10.Meteris
              -------------
                -MSE
                -Model Summary
                -R2

======================================================================================

Ridge Regression
------------------------

              1.Importing the libraries
              2.Importing dataset
              3.Identify Independent and Dependent variables
              4.Preprocessing
              -----------------
              #Preprocessing
              from sklearn.preprocessing import StandardScaler
              scaler=StandardScaler()
              X_train=scaler.fit_transform(X_train)
              X_test=scaler.fit_transform(X_test)


              5.Splitting the dataset into Training and Testing
              -------------------------------------------------

              6.Apply Linear Regression
              ---------------------------
              #Linear Regression Model
              from sklearn.linear_model import LinearRegression
              lm=LinearRegression()
              lm.fit(X_train,y_train)
              lm_coeff=pd.Series(lm.coef_,index=data.feature_names)
              lm_coeff.plot(kind="bar")


              7.Apply Ridge Regression
              ---------------------------
              #Ridge Regression Model
              from sklearn.linear_model import RidgeRegression
              rid=RidgeRegression()
              rid.fit(X_train,y_train)
              rid_coeff=pd.Series(rid.coef_,index=data.feature_names)


              8.Visualising the Training and Testing Results
              ------------------------------------------------
              rid_coeff.plot(kind="bar")


              9.Predicting the Training Results
              ----------------------------------
              pred_test_rid=rid.predict(X_test)

              10. Meterics
              -------------
                -MSE
                -R2 
                -Accuracy

	
#same for Lasso and ElasticNet
