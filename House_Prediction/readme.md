
# Handling Missing Values

Missing values can be handled using methods like mean, median, or mode imputation, or by using techniques like KNN imputation.
In Pandas, df.fillna(value) or SimpleImputer from sklearn.impute can be used

# Outlier Detection

Outliers can be detected using Z-score, IQR (Interquartile Range), or visualization techniques like box plots.
Z-score: np.abs(stats.zscore(df)) > threshold
IQR: Q1 - 1.5*IQR and Q3 + 1.5*IQR to find outliers.

# Handling Outliers

Methods include capping, removing, or transforming outliers.
Clipping: df[column] = np.clip(df[column], lower_bound, upper_bound)
Log transformation: df[column] = np.log1p(df[column]) (useful for skewed data).

# Handling Categorical to Numerical Conversion

Categorical features need to be converted into numbers before feeding them into the model.
Two main techniques: Label Encoding (LabelEncoder()) and One-Hot Encoding (OHE) (pd.get_dummies() or OneHotEncoder() from sklearn).

# One-Hot Encoding (OHE) Usage

Converts categorical variables into binary vectors.
Example: If a "city" column has values ['NY', 'LA', 'SF'], OHE will create three columns: city_NY, city_LA, city_SF with 0s and 1s.

# Handling Large Numeric Values in X (Feature Scaling)

If feature values have very large differences in magnitude, they can dominate the learning process.
Scaling ensures that all features contribute equally.

# Ensuring Proper Data Scaling

Techniques like Min-Max Scaling and Standardization bring data to a consistent range.
Min-Max Scaling: X_scaled = (X - X.min()) / (X.max() - X.min())
Standardization: X_scaled = (X - X.mean()) / X.std()

# Min-Max Scaling with Sklearn

MinMaxScaler() from sklearn.preprocessing scales values between a defined range (default 0 to 1).

Example:
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)

# Linear Regression Model Training

After preprocessing, the data is fed into the Linear Regression model.
LinearRegression() from sklearn.linear_model is commonly used.

Example:
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
Performance can be evaluated using metrics like Mean Squared Error (MSE), R-squared, or Mean Absolute Error (MAE).
