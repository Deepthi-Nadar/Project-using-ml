# Car Price Prediction Model

## Project Description
This project aims to predict car selling prices using various features such as year of manufacture, present price, kilometers driven, fuel type, seller type, transmission, and owner count. The model is built using Linear Regression and Lasso Regression algorithms, and their performance is evaluated based on the R-squared error.

## Features
- Data loading and initial inspection using `pandas`.
- Data preprocessing including handling categorical features using label encoding.
- Splitting data into training and testing sets.
- Implementation of Linear Regression for price prediction.
- Implementation of Lasso Regression for price prediction.
- Model evaluation using R-squared error.
- Visualization of actual vs. predicted prices.

## Installation
To run this project, you need to have Python and the following libraries installed:

```bash
pip install pandas matplotlib seaborn scikit-learn
```

## Usage
1.  **Clone the repository (or download the notebook):**

    ```bash
    git clone <your-repository-url>
    cd <your-repository-name>
    ```

2.  **Ensure you have the data file:** Make sure `car data.csv` is in the same directory as the notebook or update the path in the code.

3.  **Run the Jupyter Notebook (or Google Colab notebook):**

    Open and run the cells in the provided notebook. The notebook will guide you through:
    - Importing necessary libraries.
    - Loading and inspecting the dataset.
    - Preprocessing the data.
    - Training and evaluating both Linear Regression and Lasso Regression models.
    - Visualizing the model predictions.

    The key steps for running are already in the notebook:

    ```python
    # loading the data from csv file to pandas dataframe
    car_dataset = pd.read_csv('/content/car data.csv')

    # encoding categorical columns
    car_dataset.replace({'Fuel_Type':{'Petrol':0,'Diesel':1,'CNG':2}},inplace=True)
    car_dataset.replace({'Seller_Type':{'Dealer':0,'Individual':1}},inplace=True)
    car_dataset.replace({'Transmission':{'Manual':0,'Automatic':1}},inplace=True)

    # Splitting the data
    X = car_dataset.drop(['Car_Name','Selling_Price'],axis=1)
    Y = car_dataset['Selling_Price']
    X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size = 0.1, random_state=2)

    # Linear Regression Model
    lin_reg_model = LinearRegression()
    lin_reg_model.fit(X_train,Y_train)
    # Evaluate...

    # Lasso Regression Model
    lass_reg_model = Lasso()
    lass_reg_model.fit(X_train,Y_train)
    # Evaluate...
    ```

## Dataset
The dataset used for this project is `car data.csv`, which contains information about used cars. Key columns include:
- `Car_Name`: Name of the car (dropped during feature selection)
- `Year`: Manufacturing year
- `Selling_Price`: Selling price of the car (target variable)
- `Present_Price`: Current ex-showroom price of the car
- `Kms_Driven`: Kilometers driven
- `Fuel_Type`: Fuel type (Petrol, Diesel, CNG)
- `Seller_Type`: Seller type (Dealer, Individual)
- `Transmission`: Transmission type (Manual, Automatic)
- `Owner`: Number of previous owners

## Model Performance
**Linear Regression:**
- R-squared Error on Training Data: 0.8799
- R-squared Error on Test Data: 0.8366

**Lasso Regression:**
- R-squared Error on Training Data: 0.8428
- R-squared Error on Test Data: 0.8709

Both models show good performance, with Lasso Regression performing slightly better on the test data in this particular run.

## License
This project is open-source and available under the [MIT License](LICENSE-optional-if-applicable).
