## Restaurant Ratings Analysis

An interactive Power BI project analyzing restaurant ratings, consumer demographics, dining preferences, hospitality factors, and restaurant performance based on consumer data from Mexico (2012).

---

## 📑 Table of Contents

- [Case Study](#-case-study)
- [Dataset Description](#-dataset-description)
- [ER Diagram](#-er-diagram)
- [Data Cleaning](#-data-cleaning)
- [Calculated Fields](#-calculated-fields)
- [Data Analysis](#-data-analysis)
- [Dashboard](#-dashboard)
- [Tools & Technologies](#-tools--technologies)
- [Key Takeaways](#-key-takeaways)

---

## 📌 Case Study

Restaurant ratings in Mexico by real consumers from 2012, including additional information about each restaurant, their cuisines, consumers, and consumer preferences.

The objective of this project is to analyze:

* Consumer demographics
* Restaurant characteristics
* Consumer preferences
* Food, service, and overall ratings
* Alcohol and smoking policies
* Transportation behavior
* Restaurant pricing
* Consumer behavior
* Restaurant performance

---

# 📊 Dataset Description

The dataset consists of the following tables:

## 1. Consumers

| Column                | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| Consumer_ID           | Unique identifier for each consumer                                  |
| City                  | City where the consumer lives                                        |
| State                 | State where the consumer lives                                       |
| Country               | Country where the consumer lives                                     |
| Latitude              | Latitude where the consumer lives                                    |
| Longitude             | Longitude where the consumer lives                                   |
| Smoker                | Whether the consumer smokes or not                                   |
| Drink_Level           | Whether the consumer is an abstemious, casual, or social drinker     |
| Transportation_Method | Whether the consumer travels on foot, by public transport, or by car |
| Marital_Status        | Consumer's marital status                                            |
| Children              | Whether the consumer has dependent/independent children or kids      |
| Age                   | Consumer's age                                                       |
| Occupation            | Consumer's occupation                                                |
| Budget                | Consumer's budget                                                    |

## 2. Consumer_Preferences

| Column            | Description                         |
| ----------------- | ----------------------------------- |
| Consumer_ID       | Unique identifier for each consumer |
| Preferred_Cuisine | Types of food the consumer prefers  |

## 3. Ratings

| Column         | Description                           |
| -------------- | ------------------------------------- |
| Consumer_ID    | Unique identifier for each consumer   |
| Restaurant_ID  | Unique identifier for each restaurant |
| Overall_Rating | Overall rating given by the consumer  |
| Food_Rating    | Food rating given by the consumer     |
| Service_Rating | Service rating given by the consumer  |

### Rating Scale

* `0` = Unsatisfactory
* `1` = Satisfactory
* `2` = Highly Satisfactory

## 4. Restaurants

| Column          | Description                                                          |
| --------------- | -------------------------------------------------------------------- |
| Restaurant_ID   | Unique identifier for each restaurant                                |
| Name            | Restaurant name                                                      |
| City            | Restaurant city                                                      |
| State           | Restaurant state                                                     |
| Country         | Restaurant country                                                   |
| Zip_Code        | Restaurant zip code                                                  |
| Latitude        | Restaurant latitude                                                  |
| Longitude       | Restaurant longitude                                                 |
| Alcohol_Service | Whether the restaurant serves no alcohol, wine & beer, or a full bar |
| Smoking_Allowed | Restaurant smoking policy                                            |
| Price           | Restaurant price level                                               |
| Franchise       | Whether the restaurant is a franchise                                |
| Area            | Whether the restaurant is in an open or closed area                  |
| Parking         | Restaurant parking availability                                      |

## 5. Restaurant_Cuisines

| Column        | Description                            |
| ------------- | -------------------------------------- |
| Restaurant_ID | Unique identifier for each restaurant  |
| Cuisine       | Types of food served by the restaurant |

---

# 🔗 ER Diagram

The dataset contains multiple related tables connected using `Consumer_ID` and `Restaurant_ID`.
<img width="1622" height="736" alt="Screenshot 2026-09-09 180641" src="https://github.com/user-attachments/assets/ae00a4e2-2883-47c4-9b62-49271df43b26" />


# 🧹 Data Cleaning

The datasets were imported into Power BI using the **Folder Connector**.

### Steps to Import Multiple Dataset Files

1. Go to **Get Data**
2. Select **More**
3. Select **Folder**
4. Click **Connect**
5. Select the folder containing the datasets
6. Click **OK**
7. Select **Transform Data**
8. Duplicate the required query
9. Expand the **Binary** column
10. Repeat the process for the required datasets
11. Perform necessary data cleaning and transformation
12. Load the transformed data into Power BI

---

# 🧮 Calculated Fields

## Age Group

The `AgeGroup` calculated column categorizes consumers into different age groups.

```DAX
AgeGroup =
SWITCH(
    TRUE(),
    consumers[Age] <= 18, "Children and Adolescents",
    consumers[Age] <= 30, "Young Adults",
    consumers[Age] <= 45, "Adults",
    consumers[Age] <= 60, "Middle-aged Adults",
    "Seniors"
)
```

## Service Rating Category

```DAX
Service_Rating_Category =
SWITCH(
    TRUE(),
    ratings[Service_Rating] = 0, "Unsatisfactory",
    ratings[Service_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)
```

## Overall Rating Category

```DAX
Overall_Rating_Category =
SWITCH(
    TRUE(),
    ratings[Overall_Rating] = 0, "Unsatisfactory",
    ratings[Overall_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)
```

## Food Rating Category

```DAX
Food_Rating_Category =
SWITCH(
    TRUE(),
    ratings[Food_Rating] = 0, "Unsatisfactory",
    ratings[Food_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)
```

---

# 📈 Data Analysis

## 📍 Local Insights

### Consumer Distribution by City and State

Most of the consumer population is from **San Luis Potosí, San Luis Potosí**, followed by **Cuernavaca, Morelos**.

### Age Distribution by State

Young adults under 30 years of age form the majority of consumers across the three states.

In San Luis Potosí and Morelos, the second-largest demographic consists of seniors aged over 60 years.

### Smoking Behavior by City

The vast majority of consumers across the cities are non-smokers.

Jiutepec has a 100% non-smoking consumer population, while smokers account for approximately 25% of the consumer population in Cuernavaca.

### Restaurant Parking Availability

The majority of restaurants across the cities do not provide parking facilities.

Valet parking is available at some restaurants in San Luis Potosí and Cuernavaca, while public parking is available in San Luis Potosí, Ciudad Victoria, and Cuernavaca.

---

# 🍴 Dining Insights

### Restaurant Distribution by State

| State           | Number of Restaurants |
| --------------- | --------------------: |
| San Luis Potosí |                    84 |
| Morelos         |                    23 |
| Tamaulipas      |                    23 |

### Restaurant Franchise vs Non-Franchise

The majority of restaurants are non-franchises.

Both franchise and non-franchise restaurants have ratings distributed across unsatisfactory, satisfactory, and highly satisfactory categories.

### Consumer Cuisine Preferences

**Mexican cuisine** is the most preferred cuisine, followed by **American cuisine**.

### Parking and Restaurant Price

Higher-priced restaurants generally show greater availability of parking facilities, while low- and medium-priced restaurants have more varied parking availability.

---

# 🍷 Hospitality Insights

### Alcohol Service Distribution

Across Jiutepec, San Luis Potosí, Cuernavaca, and Ciudad Victoria:

* **66.92%** — No Alcohol
* **26.15%** — Wine & Beer
* **6.93%** — Full Bar

### Transportation Methods

* **61%** — Public Transportation
* **27%** — Car
* **11%** — Walking

### Alcohol Service and Consumer Ratings

Among consumers visiting restaurants with different alcohol-service options:

* **No Alcohol:** 303 highly satisfactory, 289 satisfactory, 170 unsatisfactory
* **Wine & Beer:** 146 highly satisfactory, 105 satisfactory, 68 unsatisfactory
* **Full Bar:** 37 highly satisfactory, 27 satisfactory, 16 unsatisfactory

### Smoking Policies

Approximately **73% of restaurants maintain smoke-free policies**.

Around **7% of restaurants permit smoking overall**, while approximately **18.46% offer designated smoking areas**.

---

# 👥 Consumer Behavior Insights

## Occupation Distribution

In San Luis Potosí, approximately 93% of the consumer population consists of students, with the remaining population comprising employed and unemployed individuals.

In Morelos, the population is more evenly distributed between employed individuals and students.

In Tamaulipas, approximately 94% of consumers are students, while the remaining 6% are employed.

## Drink Level by State

### San Luis Potosí

* 40% Social Drinkers
* 36% Casual Drinkers
* 23% Abstemious

### Morelos

* 45% Abstemious
* 41% Casual Drinkers
* 12% Social Drinkers

### Tamaulipas

* 52% Abstemious
* 31% Casual Drinkers
* 15% Social Drinkers

## Marital Status, Smoking & Drinking

The analysis shows differences in smoking and drinking behavior across single and married consumers.

Single non-smokers represent the largest group, while smoking consumers are more concentrated among casual and social drinkers.

## Occupation vs Budget

Among students:

* 67 have a medium budget
* 33 have a low budget
* 4 have a high budget

Additionally, 15 employed individuals and 1 unemployed individual have a medium budget.

---

# ⭐ Review Insights

## Top 5 Restaurants by Food Rating

1. **Tortas Locas Hipocampo**
2. **Puesto de Tacos**
3. **Cafeteria y Restaurante El Pacífico**
4. **Gorditas Doña Gloria**
5. **La Cantina Restaurante**

Tortas Locas Hipocampo and Puesto de Tacos show high levels of customer satisfaction based on food ratings.

## Top 5 Restaurants by Service Rating

1. **Tortas Locas Hipocampo**
2. **Puesto de Tacos**
3. **Cafeteria y Restaurante El Pacífico**
4. **Gorditas Doña Gloria**
5. **La Cantina Restaurante**

Tortas Locas Hipocampo, Puesto de Tacos, Cafeteria y Restaurante El Pacífico, and Gorditas Doña Gloria show strong customer satisfaction based on service ratings.

## Top 5 Restaurants by Overall Rating

1. **Tortas Locas Hipocampo**
2. **Puesto de Tacos**
3. **Cafeteria y Restaurante El Pacífico**
4. **La Cantina Restaurante**
5. **Restaurant la Chalita**

---

# 📊 Dashboard

The final Power BI dashboard provides an interactive view of:
<img width="1361" height="781" alt="Screenshot 2026-09-09 180901" src="https://github.com/user-attachments/assets/5d0359f4-1e40-48c4-999f-70287cb2a14b" />
<img width="1362" height="780" alt="Screenshot 2026-09-09 180924" src="https://github.com/user-attachments/assets/57014241-3c80-4f5d-9dfc-fcf5cc7260d5" />
<img width="1358" height="782" alt="Screenshot 2026-09-09 180940" src="https://github.com/user-attachments/assets/346d86ae-57b8-46d9-9fe8-f4ff0f712b22" />
<img width="1362" height="785" alt="Screenshot 2026-09-09 180956" src="https://github.com/user-attachments/assets/0d8570e6-4314-435a-8f37-1a719c47aa22" />
<img width="1358" height="780" alt="Screenshot 2026-09-09 181013" src="https://github.com/user-attachments/assets/5eeb1345-44a0-4b88-96f3-4a730cd810b6" />

---

# 🛠️ Tools & Technologies

* **Power BI**
* **Power Query**
* **DAX**
* **Data Cleaning**
* **Data Transformation**
* **Data Modeling**
* **Data Visualization**
* **Interactive Dashboards**

---

# 💡 Key Takeaways

* Young adults represent the largest consumer demographic.
* Mexican cuisine is the most preferred cuisine.
* San Luis Potosí has the highest number of restaurants in the dataset.
* Public transportation is the most commonly used transportation method.
* Most restaurants do not serve alcohol.
* Most consumers are non-smokers.
* A large majority of restaurants maintain smoke-free policies.
* Restaurant parking availability varies by city and price level.
* Consumer occupation and budget show noticeable patterns.
* Tortas Locas Hipocampo and Puesto de Tacos are among the strongest-performing restaurants based on customer ratings.

---

# 👨‍💻 Author

**Akash Kumar**

**Data Analyst | SQL | Power BI | Excel | Python**

Interested in Data Analytics, Business Intelligence, MIS Reporting, and Data Operations.

---
