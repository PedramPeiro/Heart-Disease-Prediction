### 1. Data Preprocessing

#### 1.1. Data Set Preprocessing

##### 1.1.1. Feature Type Conversion

In the initial step of our project, we import the dataset using the "file>Import Data" option. As part of data preprocessing, we focus on certain columns that need to be converted from integer to categorical types to facilitate further analysis. These categorical types are divided into "binomial" and "polynomial" categories in RapidMiner. The specific conversions are as follows:

- `sex`: Converted to "binomial"
- `cp`: Converted to "polynomial"
- `fbs`: Converted to "binomial"
- `restecg`: Converted to "polynomial"
- `exang`: Converted to "binomial"
- `slope`: Converted to "polynomial"
- `thal`: Converted to "polynomial"
- `target`: Converted to "binomial"

These transformations are achieved using the "Blending>Types>Numerical to Binomial" and "Blending>Types>Numerical to Polynomial" operators, respectively.

##### 1.1.2. Feature Normalization

Subsequently, we perform feature normalization on the numerical attributes. We choose to normalize the following columns: `age`, `chol`, `oldpeak`, `thalach`, and `trestbps`. Normalization ensures that all numerical features are on a similar scale, which can be crucial for some machine learning algorithms.

Furthermore, we inspect the histograms of these normalized features to identify potential outliers. During this process, we find 14 records that qualify as outliers. To address this, we set the parameter for outlier detection to 14, following the method explored in a previous exercise.

##### 1.1.3. Feature Preparation for Modeling

In preparation for model implementation, we convert real values to integers and remove the column related to outliers from our dataset. This step ensures that our features are in the appropriate format for training the machine learning models.

### 2. Model Implementation

Next, we proceed with model implementation to predict heart disease.

#### 2.1. Data Splitting

In this stage, we divide the dataset into an 80-20 split for training and testing. The training set will be used to build the model, while the testing set will be used to evaluate its performance on unseen data.

We employ the decision tree model for this classification task with the "maximal depth=7" parameter and other default settings. The decision tree is a widely used and interpretable machine learning algorithm that can handle both categorical and numerical data.

#### 2.2. 5-fold Cross Validation Implementation

To further assess the performance of our model, we employ 5-fold cross validation. This technique divides the dataset into five equal subsets, and the model is trained and evaluated five times, each time using a different subset as the test set and the rest as the training set. This process provides a more robust evaluation of the model's performance.

During cross-validation, we evaluate the model's accuracy, classification error, and kappa metric. These metrics help us understand how well the model is performing in different aspects.

### 3. Results and Evaluation

After implementing the models and performing the evaluations, we examine the results and evaluate the models' performance.

#### Decision Tree Model (Train-Test Split)

The decision tree model trained on the 80% training set shows promising results with an accuracy greater than 80%, indicating that the model can correctly classify heart disease cases in the testing set with a high rate of success. The Kappa metric also suggests a reasonable agreement between predictions and actual values.

We further calculate Precision, Recall, and F1-Score. Precision indicates the proportion of true positive predictions among all positive predictions, Recall represents the proportion of true positive predictions among all actual positive cases, and F1-Score is the harmonic mean of Precision and Recall. These metrics reveal that the model performs well in identifying positive cases.

#### Decision Tree Model (5-fold Cross Validation)

The 5-fold cross-validation results demonstrate that the model's accuracy is greater than 70%, indicating decent performance on different subsets of data. However, the Kappa value suggests that the model's agreement with actual values is weaker compared to the train-test split results.

Similarly, Precision, Recall, and F1-Score show satisfactory values, but they are not perfect. The model performs well in identifying positive cases, but there is room for improvement in handling false positives and false negatives.

### 4. Scatter Plots of Features

To gain insights into the relationships between certain features and the presence of heart disease, we create scatter plots to visualize the data. For example, we explore how features like "age" and "cp" (chest pain) are related to the presence or absence of heart disease. The scatter plots allow us to observe trends and patterns that might provide valuable information for model interpretation and potential feature selection.
