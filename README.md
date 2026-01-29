# 🌦️ Australian Weather Rainfall Predictor (Melbourne Region)

This project builds a **machine learning pipeline** to predict whether it will rain **today** in the Melbourne region using historical Australian weather data.  
The focus is not just on accuracy, but on understanding **seasonality**, **geographic effects**, and **class imbalance** in real-world weather prediction.

---

## 🎯 Problem Statement

Rainfall prediction is a classic classification problem with:
- Strong **seasonal patterns** 🌤️❄️
- Significant **geographic variation** 📍
- Severe **class imbalance** ⚖️

In Melbourne, rain occurs far less frequently than dry days.  
A naïve model that always predicts *“No Rain”* would already be correct about **76% of the time** — without learning anything meaningful.

This project explores how to go beyond that illusion of accuracy.

---

## 📊 Dataset

- **Source:** Australian weather dataset  
- **Original size:** ~145,000 records  
- **Target variable:** `RainToday` (Yes / No)

### 🧹 Data Cleaning & Selection
- Dropped rows with missing values due to heavy sparsity in sunshine and cloud features
- Focused on **Melbourne**, **Melbourne Airport**, and **Watsonia** to reduce geographic noise
- Renamed target variables for clarity (`RainYesterday`, `RainToday`)

### 📦 Final Dataset
- **7,557 observations**
- **16 numerical features**
- **7 categorical features**

---

## 🛠️ Feature Engineering

- 🌦️ **Season extraction** from date (Summer, Autumn, Winter, Spring)
- 🔢 **Standard scaling** for numerical features
- 🔠 **One-hot encoding** for categorical variables
- 📍 Location retained as a categorical feature to capture local weather patterns

---

## ⚖️ Class Imbalance Insight

Only **~24%** of observations correspond to rainy days ☔.  
This imbalance can easily trick models into favoring dry-day predictions.

To address this:
- Stratified train-test splitting was used
- Evaluation focused on **precision, recall, F1-score**, not just accuracy
- Confusion matrices were analyzed to inspect model behavior

---

## 🤖 Models Used

### 🌲 Random Forest Classifier
- Hyperparameter tuning via **GridSearchCV**
- 5-fold **StratifiedKFold** cross-validation

**Best parameters:**
- `n_estimators = 100`
- `max_depth = 20`
- `min_samples_split = 2`

**Performance:**
- ✅ Cross-validation accuracy: **~85%**
- ✅ Test accuracy: **~84%**
- ⚠️ Recall for rainy days: **~51%**

🔍 Feature importance analysis highlighted:
- Humidity
- Pressure
- Cloud cover
- Rainfall
- Seasonal effects

---

### 📐 Logistic Regression (Baseline Comparison)

- Tested with L1 and L2 regularization
- Evaluated with and without class weighting

**Performance:**
- Slightly lower accuracy (**~83%**)
- Similar recall for rainy days
- Useful as a baseline and for interpretability

---

## 📈 Evaluation Metrics

- 📄 Classification Report (Precision, Recall, F1-score)
- 🧩 Confusion Matrix visualizations
- 📊 Feature importance plots (Random Forest)

These metrics provide a more realistic picture than accuracy alone.

---

## 🧠 Key Takeaways

- 📍 Localized models outperform global ones
- ⚖️ Class imbalance must be handled carefully
- 🌲 Random Forest performed better than Logistic Regression
- ☔ Predicting rainy days remains the hardest challenge

---

## 🧰 Tools & Libraries

- 🐍 Python
- 🐼 Pandas
- 🔢 NumPy
- 🤖 Scikit-learn
- 📊 Matplotlib
- 🎨 Seaborn

---

## 🚀 Future Improvements

- Apply resampling techniques (SMOTE, undersampling)
- Optimize models for **recall** or **F1-score**
- Extend the approach to other Australian regions
- Incorporate time-based and rolling weather features

---

## 📌 Status

✅ Baseline model completed  
🔧 Further experimentation and improvements planned
