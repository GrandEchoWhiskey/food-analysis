# 🍎 Food Analysis Project

## 📌 Overview
This project analyzes daily food nutrition data, providing insights into calorie intake, macronutrient distribution, and meal patterns. The dataset contains various food items with nutritional values such as calories, protein, carbohydrates, fat, fiber, sugars, sodium, cholesterol, and water intake.

## 📂 Dataset
The dataset used in this project is **`daily_food_nutrition_dataset.csv`** with the following selected columns:

- `Food_Item` - Name of the food item
- `Category` - Category of the food (e.g., Fruits, Meat, Dairy)
- `Calories (kcal)` - Energy content in kilocalories
- `Protein (g)` - Protein content in grams
- `Carbohydrates (g)` - Carbohydrate content in grams
- `Fat (g)` - Fat content in grams
- `Fiber (g)` - Fiber content in grams
- `Sugars (g)` - Sugar content in grams
- `Sodium (mg)` - Sodium content in milligrams
- `Cholesterol (mg)` - Cholesterol content in milligrams
- `Meal_Type` - Type of meal (e.g., Breakfast, Lunch, Dinner, Snack)
- `Water_Intake (ml)` - Water intake in milliliters

## 🚀 Features
- **Data Cleaning & Processing**: Ensures the dataset is formatted correctly and ready for analysis.
- **Macronutrient Breakdown**: Analyzes protein, carbs, and fat composition for each food item.
- **Meal-Type Insights**: Examines how different meal types contribute to daily nutrition.
- **Visualization**: Generates stacked bar charts and histograms for better understanding of dietary patterns.

## 📊 Usage
### 1️⃣ Load Dataset
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('daily_food_nutrition_dataset.csv')
df = df[[
    'Food_Item', 'Category', 'Calories (kcal)', 'Protein (g)',
    'Carbohydrates (g)', 'Fat (g)', 'Fiber (g)', 'Sugars (g)',
    'Sodium (mg)', 'Cholesterol (mg)', 'Meal_Type', 'Water_Intake (ml)'
]]
df.head()
```

### 2️⃣ Analyze Macronutrient Breakdown
```python
df_percent = df.groupby("Food_Item")[["Protein (g)", "Carbohydrates (g)", "Fat (g)", "Fiber (g)", "Sugars (g)"]].mean()

df_percent = df_percent.div(df_percent.sum(axis=1), axis=0) * 100

df_percent.plot(kind="bar", stacked=True, figsize=(10, 5), colormap="viridis")
plt.ylabel("Percentage (%)")
plt.xlabel("Food Item")
plt.title("Macronutrient Breakdown per Food Item (Percentage)")
plt.legend(title="Macronutrient")
plt.show()
```

## 🔧 Requirements
To run the analysis, install the following dependencies:
```bash
pip install pandas matplotlib seaborn
```

## 📌 Next Steps
- Implement machine learning models for predicting meal nutrition.
- Add interactive visualizations using Plotly.
- Enhance dataset by including user demographics and activity levels.

## 📝 License
This project is open-source under the MIT License.

