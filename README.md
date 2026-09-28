# Superstore Sales Data Understanding, Cleaning & Exploratory Analysis

## Project Overview

This project focuses on understanding, cleaning, and performing basic exploratory analysis on the **Superstore Sales Dataset** using Python and Pandas.

The project includes data loading, dataset inspection, date conversion, categorical data cleaning, duplicate removal, numerical summary statistics, and basic analysis of Sales and Profit.

##  Objectives

* Load the Superstore Sales dataset using Pandas.
* Inspect the dataset using `head()`, `info()`, and `describe()`.
* Identify the number of rows and columns.
* Check column names and missing values.
* Convert Order Date and Ship Date into proper datetime format.
* Clean categorical columns such as Category, Sub-Category, and Segment.
* Identify and remove duplicate records.
* Calculate summary statistics for numerical attributes.
* Analyze Sales and Profit values.
* Display category, sub-category, and segment counts.

##  Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Google Colab**
* **Jupyter Notebook**

##  Project Files

```text
Superstore-Sales-Analysis/
│
├── superstore.ipynb
├── superstore.py
├── samplesuperstore.csv.xls
└── README.md
```

##  Dataset

The project uses the **Superstore Sales Dataset**.

The dataset contains business-related information used for analyzing sales, profit, categories, customer segments, and order/shipping dates.

The dataset is loaded using:

```python
df = pd.read_csv("/content/samplesuperstore.csv.xls")
```

##  Data Inspection

The project initially examines the dataset using:

```python
df.head()
df.info()
df.describe()
```

It also checks:

* Dataset shape
* Column names
* Missing values
* Numerical attributes

The script prints the number of rows and columns and displays the available column names.

##  Data Cleaning

### Date Conversion

The `Order Date` and `Ship Date` columns are converted into proper datetime objects:

```python
df['Order Date'] = pd.to_datetime(df['Order Date'], dayfirst=True)
df['Ship Date'] = pd.to_datetime(df['Ship Date'], dayfirst=True)
```

This makes the date columns easier to use for further analysis.

### Categorical Data Cleaning

The following categorical columns are cleaned:

```text
Category
Sub-Category
Segment
```

Whitespace is removed and the text is converted into title case.

```python
for column in categorical_columns:
    df[column] = df[column].astype(str).str.strip().str.title()
```

### Duplicate Removal

The project checks for duplicate rows:

```python
df.duplicated().sum()
```

Duplicate records are then removed:

```python
df = df.drop_duplicates()
```

##  Numerical Analysis

The project identifies numerical columns automatically:

```python
numerical_columns = df.select_dtypes(include=np.number).columns
```

It then generates descriptive statistics using:

```python
df[numerical_columns].describe()
```

The analysis includes values such as:

* Count
* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles

##  Sales Analysis

The project calculates:

* Total Sales
* Average Sales
* Minimum Sales
* Maximum Sales

```python
print("Total Sales:", df['Sales'].sum())
print("Average Sales:", df['Sales'].mean())
print("Minimum Sales:", df['Sales'].min())
print("Maximum Sales:", df['Sales'].max())
```

##  Profit Analysis

If the `Profit` column is available, the project calculates:

* Total Profit
* Average Profit
* Minimum Profit
* Maximum Profit

```python
if 'Profit' in df.columns:
    print("Total Profit:", df['Profit'].sum())
    print("Average Profit:", df['Profit'].mean())
    print("Minimum Profit:", df['Profit'].min())
    print("Maximum Profit:", df['Profit'].max())
```

##  Category Analysis

The project counts the number of records in each:

### Category

```python
df['Category'].value_counts()
```

### Sub-Category

```python
df['Sub-Category'].value_counts()
```

### Segment

```python
df['Segment'].value_counts()
```

##  Final Dataset

After cleaning and processing, the project displays the cleaned dataset and its final information:

```python
display(df.head())
df.info()
```

This helps verify that the cleaning operations were successfully applied.

##  How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
```

### 2. Open Google Colab

Upload:

```text
superstore.ipynb
```

### 3. Upload the Dataset

Make sure:

```text
samplesuperstore.csv.xls
```

is available in the Colab environment.

### 4. Run All Cells

Run the notebook from top to bottom to perform:

```text
Data Loading
      ↓
Data Inspection
      ↓
Missing Value Checking
      ↓
Date Conversion
      ↓
Categorical Data Cleaning
      ↓
Duplicate Removal
      ↓
Numerical Analysis
      ↓
Sales Analysis
      ↓
Profit Analysis
      ↓
Category Analysis
      ↓
Final Dataset Verification
```

##  Project Structure

```text
Superstore-Sales-Analysis
│
├── superstore.ipynb       # Google Colab notebook
├── superstore.py          # Python script
├── samplesuperstore.csv.xls # Dataset
└── README.md              # Project documentation
```

##  Key Features

* Data loading using Pandas
* Dataset inspection
* Missing-value checking
* Date formatting
* Text cleaning
* Duplicate detection and removal
* Numerical statistics
* Sales analysis
* Profit analysis
* Category analysis
* Sub-category analysis
* Segment analysis

##  Future Improvements

The project can be extended with:

* Sales by category visualization
* Profit by category visualization
* Monthly sales trends
* Regional sales analysis
* Customer segment analysis
* Correlation analysis
* Interactive dashboards
* Matplotlib/Seaborn visualizations
* Advanced Exploratory Data Analysis (EDA)

##  Author

**Gnana Yoshua**

##  License

This project is created for educational and data-analysis purposes.
