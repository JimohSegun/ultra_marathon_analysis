# Introduction

This project delves into a large dataset of ultra marathon running that I downloaded from Kaggle, comprising over 7 million race records registered between 1978 and 2022.

# Background

Driven by a quest to navigate the ultra marathon data, this project was born out of a desire to identify the race that took place in the United States in 2022 and the performance of the athletes who ran the 50-mile and 50-kilometer races. Extensive data cleaning was conducted in the project to ensure proper analysis.

### The questions I wanted to answer through my Python exploratory data analysis.

1. What are the race lengths in the ultra marathon race?
2. What is the count of male and female participants in the ultra marathon race?
3. What is the count of athletes average speed in the 2022 ultra marathon race?
4. What is the relationship between race length, athlete average speed, and athlete gender?
5. What is the average speed of athletes in the 2022 ultra marathon race with respect to their gender and race length?
6. Which age groups are the top 10 in the 50mi ultra marathon race in 2022?
7. Which age groups are the bottom 10 in the 50mi ultra marathon race in 2022?

# Tools I Used

For my deep dive into the ultra marathon data, I utilized several key tools:

- **Python:** The backbone of my analysis, allowing me to dive into the ultra marathon data and gain insights into the race length, average speed of the athletes, top 10 age groups, and bottom 10 age groups.
- **Git & GitHub:** Essential for version control and sharing my Python and analysis, ensuring collaboration and project tracking.

# Analysis

Each code for this project was designed to investigate specific aspects of the ultra marathon data.

## Steps followed

- Step 1: Imported a CSV file of ultra marathon data for analysis.

- Step 2: Cleaned the data by dropping null and duplicate entries.

- Step 3: Wrote code to filter the data for USA races, 50k and 50mi distances for the year 2022.

- Step 4: Dropped unwanted columns from the data, namely "Athlete club," "Athlete country," "Athlete year of birth," and "Athlete
  age category."

- Step 5: Wrote code to address data type issues accordingly.

# Insight Of each question

### 1. The race lengths in the ultra marathon race

To identify the race lengths, I plotted a histogram chart using the race length column and assigned xlabel for race length and ylabel for count. Here is how the code helps analyze the insights:

```python

plt.title('Race Length Distribution')
plt.xlabel('Race Length')
plt.ylabel('Count')
sns.histplot(df['race_length'])
plt.show()

```

Here is the insight from the data in the graph below.
The results show that the 50km race has a higher count than the 50mi race.

![1](https://github.com/user-attachments/assets/fdc684fd-7156-4d2e-be0b-238175a06b3d)

### 2. The count of male and female participants in the ultra marathon race

To better understand the participation of males and females in the ultramarathon race, I plotted a histogram chart that helps classify males and females who participated in the 50km and 50mi races.
Here is how the code provides insights:

```python
plt.title('Race length Distribution for Males and Females')
plt.xlabel('Race length')
plt.ylabel('Count')
sns.histplot(df, x="race_length" , hue="athlete_gender" , palette="Set2")
plt.show()

```

The insights from the data in the graph below show that there were more male participants than female participants in the ultra marathon race of 2022.

![2](https://github.com/user-attachments/assets/8eefc19c-908b-4ae5-847d-0b324b53534b)

### 3. The count of athletes average speed in the 2022 ultra marathon race

This code helps identify the average speed of athletes who participated in the 2022 ultra marathon race.

```python

sns.displot(df[df['race_length'] == '50mi']['athlete_average_speed'])
plt.show()

```

The results show a normal distribution of average speeds among athletes. The highest frequency of average speeds appears around the values of 6 to 8, suggesting that most athletes have average speeds in this range.

![3](https://github.com/user-attachments/assets/669559ed-64d5-41e5-80a4-aedad638600c)

### 4. The relationship between race length, athlete average speed, and gender using a violin plot

This code analyzes the relationship between race length, athlete average speed, and gender to understand the participation of male and female athletes in the 50mi and 50km races.

```python

lt.title('Race length Distribution for Males and Females')
plt.xlabel('Race length')
plt.ylabel('Count')
sns.violinplot(data=df, x ='race_length', y='athlete_average_speed', hue="athlete_gender", split=True, inner='quart')

```

The results show that in the 50km race, there are more male participants than female, and in the 50mi race, the number of male participants also exceeds that of female participants.

![4](https://github.com/user-attachments/assets/16e8174a-28b8-4633-a1f0-ea2cc887aff9)

### 5. The average speed of athletes in the 2022 ultra marathon race with respect to their gender and race length

To better understand the average age of the athletes who participated in the 50mi and 50km races, I used the groupby method to analyze their average speed.

```python
df.groupby(["athlete_gender","race_length"])["athlete_average_speed"].mean()

```

The results show that for race lengths, the average speed of females in the 50km race (7.083011) is higher than in the 50mi race (6.834371). Similarly, the average speed of males in the 50km race (7.738985) is higher than in the 50mi race (7.257633)

![5](https://github.com/user-attachments/assets/fd737b91-7915-4e9c-b9c9-f3315b6fc065)

### 6. Which age groups are the top 10 in the ultra marathon race in 2022 in the 50mi ?

This code helps to analyze the top 10 age groups in the ultra marathon race.

```python
best_age_group= df.query("race_length == '50mi'").groupby('age')['athlete_average_speed'].agg(['mean','count']).sort_values('mean', ascending=False).query('count>19')
best_age_group.head(10)

```

The analysis identifies the top 10 age groups based on average speed in the 50mi marathon race.

![6](https://github.com/user-attachments/assets/01193eac-3227-4702-843d-940911651283)

### 7. Which age groups are the bottom 10 in the 50mi ultra marathon race in 2022?

```python
least_performing_age = df.query("race_length == '50mi'").groupby('age')['athlete_average_speed'].agg(['mean','count']).sort_values('mean', ascending=True).query('count>9')
least_performing_age.head(10)
```

The analysis identifies the top 10 age groups based on average speed in the 50mi marathon race.

![7](https://github.com/user-attachments/assets/2b0b111c-4bfd-4e6e-b45f-81505394ca69)

# Conclusions

###

**1.The race lengths in the ultra marathon race:** The race lengths in the 2022 ultra marathon races in the USA show that the 50km race has a higher count than the 50mi race. This provides a better understanding of how athletes participated in each race.

**2. The count of male and female participants in the ultra marathon race:** The participation of males and females in the ultra marathon race shows that more males participated in the 2022 race than females, in both the 50mi and 50km races in the USA.

**3.The count of athletes average speed in the 2022 ultra marathon race:** The results show a normal distribution of average speeds among athletes. The highest frequency of average speeds appears around the values of 6 to 8, suggesting that most athletes have average speeds in this range.

**4.The relationship between race length, athlete average speed, and athlete gender :** The results show that in the 50km race, there are more male participants than female, and in the 50mi race, the number of male participants also exceeds that of female participants.

**5.The average speed of athletes in the 2022 ultra marathon race with respect to their gender and race length:** The average speed of females in the 50km race (7.083011) is higher than in the 50mi race (6.834371). Similarly, the average speed of males in the 50km race (7.738985) is higher than in the 50mi race (7.257633). This helps us understand the athletes' average speeds in the 2022 race. In the 50km race, the average speed of females is higher than that of females in the 50mi race. Likewise, in the 50km race, the average speed of males is higher than that of males in the 50mi race.

**6. Which age groups are the top 10 in the ultra marathon race in 2022 in the 50mi :** The analysis identifies the top 10 age groups based on average speed in the 50mi marathon race. 

**7. Which age groups are the bottom 10 in the 50mi ultra marathon race in 2022?:** The analysis identifies the top 10 age groups based on average speed in the 50mi marathon race.
