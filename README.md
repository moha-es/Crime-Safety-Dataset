# 🕵️ Crime & Safety Dataset Analysis (SQL Project)

This project explores a dataset of 1,000 real crime reports collected over two years in an urban area.  
Each record contains details such as the crime type, location, time, and victim demographics including age, gender, and race.  
The project uses SQL to uncover patterns in crime frequency, time of day, demographics, and location.

---

## 🎯 Objectives

- Identify patterns in crime by time of day
- Analyze crimes based on victim gender, age, and race
- Compare crime rates across cities and crime types
- Highlight crimes involving minors or older populations

---

## 📁 Files Included

| File | Description |
|------|-------------|
| `crime_safety_dataset.csv`| Raw dataset from Kaggle |
| `crimes_by_city.sql` | Query for crime totals by city |
| `crimes_by_city.png` | Chart showing total crimes per city |
| `crimes_involving_Victims Under 18.png` | Crimes involving victims under age 18 |
| `Crimes_against_Race_Groups_by_Type.png` | Crime types affecting racial groups |
| `crime_type_by_avg_age.png` | Average victim age by crime type |
| `crimes_time_day.png` | Crime frequency by hour of day |

---

## 📊 Key Insights from SQL Analysis

### 📍 Crimes by City
- **Houston** recorded the highest number of crimes in the dataset, with a total of 106 incidents.
- Query grouped records by `city` and counted total entries.

### 👶 Crimes Involving Victims Under 18
- **Assault** was the most common crime among minors, with **9 victims under age 18**.
- Query filtered rows where `victim_age < 18`.

### 🧑‍🦳 Average Victim Age by Crime Type
- **Vandalism** had the highest average victim age: **56.4 years**.
- Suggests older individuals are more affected by property-related crimes.

### 🧑🏽 Crimes Against Racial Groups by Type
- **Robbery** was the most reported crime for **Asian victims**, with **32 incidents**.
- Query grouped by `victim_race` and `crime_type`.

### 🕒 Crime by Time of Day
- Most crimes occurred around **18:00 (6 PM)** with a peak of **54 incidents**.
- Surprisingly, **44 crimes** also occurred during the **00:00 hour (midnight)**.
- Query extracted the hour from the time column using `SUBSTR(time, 1, 2)`.

---

## 🧠 Example SQL Query

```sql
-- Crimes by gender and city
SELECT city, victim_gender, crime_type, COUNT(*) AS total
FROM crimes
WHERE victim_gender IS NOT NULL
GROUP BY city, victim_gender, crime_type
ORDER BY city, total DESC;
