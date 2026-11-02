# 🎵 Music Streaming Behavior Analysis | Python & Pandas

### Comparing Music Listening Patterns Across Cities and Weekdays

**Python • Pandas • Data Cleaning • Exploratory Data Analysis • Data Aggregation**

## 📌 Project Overview

Understanding how people use digital streaming platforms can help businesses identify customer engagement patterns and make more informed decisions.

This project analyzes music streaming activity in two cities, **Springfield** and **Shelbyville**, to investigate how listening behavior differs depending on the city and day of the week.

The analysis uses Python and Pandas to explore, clean, and aggregate streaming data, comparing user activity on Mondays, Wednesdays, and Fridays.

**Business Question:** Does music streaming activity vary by city and day of the week?

## 🎯 Project Objectives

- Explore and understand the structure of a music streaming dataset.
- Identify and handle missing values.
- Standardize column names and music genres.
- Identify and remove duplicate records.
- Analyze the number of music plays by city.
- Compare streaming activity across different weekdays.
- Evaluate the hypothesis that listening behavior differs between Springfield and Shelbyville.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data processing and programming |
| Pandas | Data cleaning, filtering, and aggregation |
| Jupyter Notebook | Interactive analysis and documentation |

## 📂 Dataset Description

The dataset, `music_project_en.csv`, contains information about music streaming activity.

| Column | Description |
|---|---|
| `user_id` | Unique user identifier |
| `track` | Song title |
| `artist` | Artist name |
| `genre` | Music genre |
| `city` | User's city |
| `time` | Time of music playback |
| `day` | Day of the week |

The analysis focuses on two cities: Springfield and Shelbyville.

## 🧹 Data Cleaning and Preprocessing

The preprocessing stage involved several data quality improvements.

### 1. Column Standardization

Column names were standardized by:

- Converting names to lowercase.
- Removing unnecessary whitespace.
- Replacing spaces with underscores.
- Renaming `userid` to `user_id`.

### 2. Handling Missing Values

Missing values in the `track`, `artist`, and `genre` columns were replaced with `"unknown"`.

### 3. Removing Duplicates

Explicit duplicate rows were removed using Pandas, followed by resetting the DataFrame index.

### 4. Standardizing Music Genres

Inconsistent genre labels such as `hip`, `hop`, `hiphop`, and `hip-hop` were standardized to a single category.

These transformations helped improve data consistency before analysis.

## 📊 Exploratory Data Analysis

### 1. Music Streaming Activity by City

The number of music plays was calculated for each city using Pandas aggregation methods.

Springfield recorded a higher total number of plays than Shelbyville during the analyzed days.

### 2. Music Streaming Activity by Weekday

The analysis compared activity on:

- Monday
- Wednesday
- Friday

The results revealed different patterns of engagement between the two cities.

### 3. City and Weekday Comparison

A Python function was developed to count music plays based on both city and day.

| Day | Springfield | Shelbyville |
|---|---:|---:|
| Monday | 16,715 | 5,982 |
| Wednesday | 11,755 | 7,478 |
| Friday | 16,890 | 6,259 |
| **Total** | **45,360** | **19,719** |

## 🔎 Key Findings

**Springfield**

- Recorded higher music streaming activity on all three analyzed days.
- Experienced its highest activity on Friday.
- Showed a noticeable decrease in streaming activity on Wednesday.

**Shelbyville**

- Recorded its highest streaming activity on Wednesday.
- Showed lower activity on Monday and Friday.
- Demonstrated a different weekly listening pattern from Springfield.

## 🧪 Hypothesis Evaluation

### Research Hypothesis

Music streaming activity differs depending on the city and day of the week.

### Findings

The descriptive analysis identified differences in both the total number of plays and the distribution of activity across weekdays.

Springfield showed higher activity on Monday and Friday, while Shelbyville experienced its highest activity on Wednesday.

**Conclusion:** The observed data support the hypothesis that streaming activity patterns differ between the two cities.

This project uses descriptive comparisons rather than formal statistical significance testing.

## 💡 Business Applications

The findings may help streaming platforms better understand regional engagement patterns.

Potential applications include:

**Audience Engagement:** Identifying periods when listeners are more active.

**Content Scheduling:** Exploring whether content promotions should be scheduled differently across locations.

**Regional Marketing:** Developing hypotheses for location-specific marketing strategies.

**Customer Behavior Analysis:** Understanding how usage patterns vary over time.

These applications are potential business implications rather than interventions tested in the project.

## ⚠️ Project Limitations

- The analysis covers only two cities and three weekdays.
- Playback counts do not necessarily represent the number of unique listeners.
- Differences in activity may be influenced by the size of each city's user base.
- The project does not include formal statistical significance testing.
- The findings should not be generalized to all streaming platform users without further analysis.

## 🚀 How to Run the Project

1. Clone or download the repository.
2. Install Python, Pandas, and Jupyter Notebook.
3. Place `music_project_en.csv` in a local data directory.
4. Update the dataset path in the notebook.
5. Run the notebook cells sequentially.

### Install Dependencies

```bash
pip install pandas notebook
```

## 📈 Conclusion

This project demonstrates how fundamental Python and Pandas techniques can be applied to a real-world-style business analytics problem.

Through data cleaning, duplicate handling, filtering, and aggregation, the analysis identified meaningful differences in music streaming behavior between Springfield and Shelbyville.

The project highlights foundational skills in **data preprocessing, exploratory analysis, Python programming, and analytical reasoning**.

## 👩‍💻 Author

**Andressa Miranda**

Computer Science | Data Analytics | Python

[GitHub Profile](https://github.com/Andressa202)

*Developed as part of the TripleTen Data Science program.*
