# Visualising Data with Pandas and Matplotlib 📊  

In this lesson, we’ll explore **data visualisation** to better understand the patterns in our dataset. 

Graphs help transform raw numbers into meaningful insights.  

We’ll create the following visualizations:  

1. **Bar Chart**: Comparing individual and subject-specific scores.  
2. **Line Chart**: Tracking trends over multiple subjects.  
3. **Pie Chart**: Understanding proportions.  
4. **Histogram**: Visualizing distributions.  

👉 _Ensure you have Pandas and Matplotlib installed._  

````py
import pandas as pd
import matplotlib.pyplot as plt
````  

We’ll use the same dataset as before:  

````py
data = {
    "Name": ["Alice", "Bob", "Charlie", "David", "Eve"],
    "Age": [16, 17, 16, 18, 17],
    "Grade": ["B", "A", "C", "A", "B"],
    "Math_Score": [78, 88, 65, 90, 82],
    "Science_Score": [85, 92, 70, 95, 89],
}

df = pd.DataFrame(data)
df["Total_Score"] = df["Math_Score"] + df["Science_Score"]
df["Percentage_Score"] = (df["Total_Score"] / 200) * 100
print(df)
````  

---

## 1. Bar Chart: Comparing Scores by Students  

Let’s compare **Total Scores** for each student using a bar chart:  

````py
# Bar chart: Total Scores
df.plot(x="Name", y="Total_Score", kind="bar", title="Total Scores by Student", color="skyblue", legend=False)
plt.ylabel("Total Score")
plt.grid(axis="y", linestyle="--", alpha=0.7)
plt.show()
````  

### Adding More Bars  
We can add multiple bars to compare **Math** and **Science** scores side by side:  

````py
# Bar chart: Math and Science scores
df.plot(x="Name", y=["Math_Score", "Science_Score"], kind="bar", title="Scores by Subject", width=0.8)
plt.ylabel("Scores")
plt.show()
````  

---

## 2. Line Chart: Trends in Percentage Scores  

Use a line chart to track how students performed based on their **Percentage Scores**:  

````py
# Line chart: Percentage Scores
df.plot(x="Name", y="Percentage_Score", kind="line", title="Percentage Score Trends", marker="o", color="green")
plt.ylabel("Percentage (%)")
plt.show()
````  

💡 _You can customize markers and colors for clarity._  

---

## 3. Pie Chart: Grade Distribution  

Pie charts help show the distribution of **Grades** in the class:  

````py
# Pie chart: Grade Distribution
grade_counts = df["Grade"].value_counts()
grade_counts.plot(kind="pie", autopct="%1.1f%%", startangle=90, title="Grade Distribution", colors=["gold", "lightblue", "pink"])
plt.ylabel("")  # Removes y-axis label for cleaner look
plt.show()
````  

---

## 4. Histogram: Distribution of Scores  

A **histogram** shows how scores are distributed across bins:  

````py
# Histogram: Total Scores
df["Total_Score"].plot(kind="hist", bins=5, color="purple", title="Distribution of Total Scores")
plt.xlabel("Score Range")
plt.ylabel("Frequency")
plt.show()
````  

---

## Challenges ⚔️ 

Use the dataset to answer these questions by creating your own graphs:  

1. **Bar Chart**: Create a bar chart to compare **Percentage_Score** for each student.  
2. **Line Chart**: Plot a line graph comparing **Math_Score** and **Science_Score** trends.  
3. **Pie Chart**: Visualize the proportion of students in different **Age** groups. _(Hint: Use `df['Age'].value_counts()`.)_  
4. **Histogram**: Plot a histogram of the **Math_Score** column to visualize score ranges.  
5. **Save a Graph**: Save one of your charts to a PNG file using the `plt.savefig("filename.png")` function.  

---

## ✨Extra Credit: Combining Filters and Visualisation  

Want to visualise only the top-performing students? 

Use filters to subset the data and plot it:  

````py
# Filter students with Percentage_Score > 85
top_students = df[df["Percentage_Score"] > 85]

# Bar chart for top students
top_students.plot(x="Name", y="Percentage_Score", kind="bar", title="Top Performing Students", color="lightgreen", legend=False)
plt.ylabel("Percentage (%)")
plt.show()
````  

---

## Summary 📝 

In this lesson, we've explored:  

- Creating bar, line, pie, and histogram charts.  
- Customizing graphs with colors, titles, and gridlines.  
- Filtering data for more focused visualizations.  

These visual tools make it easier to analyse data and present findings effectively.
