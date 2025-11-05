# Exploratory Data Analysis: Ultra-Marathon Runner Performance

This project is a comprehensive Exploratory Data Analysis (EDA) on a large dataset of ultra-marathon races. The goal is to clean, transform, and visualize the data to uncover insights and answer questions about runner performance based on age, gender, race distance, and seasonality.


## 🛠️ Tools & Libraries

* **Python**
* **Pandas:** For data loading, manipulation, and cleaning.
* **Seaborn:** For advanced statistical data visualization.
* **Matplotlib:** (Used by Seaborn) for plotting.

---

## 🚀 Project Pipeline

The analysis follows a structured pipeline from raw data to final insights.

### 1. Data Import and Initial Exploration
* Loaded the large ultra-marathon CSV file into a Pandas DataFrame.
* Conducted initial inspection using `.head()`, `.shape()`, and `.info()` to understand the dataset's structure and identify data types.

### 2. Data Cleaning and Filtering
This was the most intensive step and involved:
* **Filtering:** Focused the dataset on:
    * Races in the **USA**.
    * Specific distances: **50km** and **50-mile**.
    * Races that took place in the year **2020**.
* **Feature Engineering:**
    * Calculated an `athlete_age` column by subtracting the `Year of Birth` from the `Year of event`.
    * Created `race_month` and `race_season` columns using a Lambda function on the `race_day` column to analyze seasonal performance.
* **Data Cleaning:**
    * Standardized event names (e.g., removing "USA" from the name).
    * Cleaned the `Athlete Performance` column (e.g., removing 'h' characters).
    * Dropped irrelevant or redundant columns (`Athlete Club`, `Country`, `Year of Birth`, etc.).
    * Handled null values by dropping rows with missing `athlete_age`.
    * Checked for and confirmed no duplicate entries.
* **Type Conversion:**
    * Converted `athlete_age` to integer.
    * Converted `average_speed` to float for numerical analysis.

### 3. Column Renaming and Reordering
* Renamed columns for better readability and easier access (e.g., `Year of event` to `year`, `Event dates` to `race_day`).
* Reordered the DataFrame columns into a more logical layout.

---

## 📊 Visualizations and Key Questions

After cleaning, the data was visualized using Seaborn to answer specific questions.

### Q1: What is the distribution of 50km vs. 50-mile races and male vs. female participation?
* A histogram was used to show the counts of each race type and the gender breakdown within them.

`[Add a screenshot of your histogram: 50k vs 50-mile distribution]`

### Q2: What is the average speed distribution for 50-mile races?
* A distribution plot (displot) was created to visualize the spread of average speeds.

`[Add a screenshot of your displot: Average Speed]`

### Q3: How do average speeds compare between male and female athletes across different race lengths?
* A violin plot was used to show the distribution of speeds for both genders across the 50k and 50-mile distances.

`[Add a screenshot of your violin plot: Speed by Gender and Distance]`

### Q4: What is the relationship between an athlete's age and their average speed?
* An LM plot (regression plot) was used to show the trend between `athlete_age` and `average_speed`, further broken down by `gender`.

`[Add a screenshot of your LM plot: Age vs. Speed]`

---

## 💡 Key Insights

The analysis successfully answered several key questions using `groupby` and `query` methods:

1.  **Gender Performance:** Calculated the mean average speed for male and female runners in both 50k and 50-mile races to quantify the performance difference.
2.  **Age Group Performance:** Identified the fastest and slowest age groups in 50-mile races (for groups with a minimum of 20 participants).
3.  **Seasonal Impact:** Analyzed if runners are statistically slower in the summer months compared to the winter by comparing average speeds by the created `race_season` column.

