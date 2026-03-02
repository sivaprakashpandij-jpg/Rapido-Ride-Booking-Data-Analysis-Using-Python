
**Rapido Ride Booking Data Analysis Using Python**
**Project Overview**

This project performs end-to-end data analysis on a ride booking dataset (rapido 200.xlsx) using Python in Google Colab.

The objective is to analyze booking patterns, cancellation trends, vehicle performance, revenue distribution, and customer satisfaction using data visualization and statistical analysis.

**🎯 Project Objectives**

Perform data cleaning

Analyze booking status distribution

Study cancellation percentage

Evaluate vehicle type performance

Analyze payment method usage

Identify revenue trends

Extract business insights

**🛠 Tools & Libraries Used**

Python

Google Colab

Pandas

NumPy

Matplotlib

Seaborn

**📂 Dataset Information**

File Name: rapido 200.xlsx

Key Columns:

Booking_Status

Booking_Value

Ride_Distance(km)

Ride_Time(min)

Vehicle_Type

Payment_Method

Customer_Rating

Driver_Rating

Canceled_Percentage

Date

**🧹 Data Cleaning Steps**

Removed duplicate records

Checked missing values

Converted Date column to datetime format

Performed data validation

💻 Python Code
# Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

plt.style.use("seaborn-v0_8")

# Load Dataset
df = pd.read_excel("rapido 200.xlsx")

# Basic Information
print(df.shape)
print(df.info())
print(df.describe())

# Remove Duplicates
df.drop_duplicates(inplace=True)

# Convert Date Column
df['Date'] = pd.to_datetime(df['Date'])

# -----------------------------
# 1️⃣ Booking Status Distribution
# -----------------------------
df['Booking_Status'].value_counts().plot(kind='bar')
plt.title("Booking Status Distribution")
plt.xlabel("Booking Status")
plt.ylabel("Count")
plt.xticks(rotation=45)
plt.show()

# -----------------------------
# 2️⃣ Vehicle Type Distribution
# -----------------------------
df['Vehicle_Type'].value_counts().plot(kind='pie', autopct='%1.1f%%')
plt.title("Vehicle Type Distribution")
plt.ylabel("")
plt.show()

# -----------------------------
# 3️⃣ Payment Method Analysis
# -----------------------------
df['Payment_Method'].value_counts().plot(kind='bar')
plt.title("Payment Method Usage")
plt.xticks(rotation=45)
plt.show()

# -----------------------------
# 4️⃣ Ride Distance Distribution
# -----------------------------
plt.hist(df['Ride_Distance(km)'], bins=10)
plt.title("Ride Distance Distribution")
plt.xlabel("Distance (km)")
plt.ylabel("Frequency")
plt.show()

# -----------------------------
# 5️⃣ Ride Time vs Booking Value
# -----------------------------
plt.scatter(df['Ride_Time(min)'], df['Booking_Value'])
plt.title("Ride Time vs Booking Value")
plt.xlabel("Ride Time (min)")
plt.ylabel("Booking Value")
plt.show()

# -----------------------------
# 6️⃣ Correlation Heatmap
# -----------------------------
plt.figure(figsize=(10,8))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()

# -----------------------------
# 7️⃣ Daily Booking Trend
# -----------------------------
daily_bookings = df.groupby('Date')['Total_Bookings'].sum()

plt.figure(figsize=(10,5))
plt.plot(daily_bookings)
plt.title("Daily Booking Trend")
plt.xlabel("Date")
plt.ylabel("Total Bookings")
plt.xticks(rotation=45)
plt.show()
**📈 Sample Output**

After running the code, the following outputs are generated:

Booking Status Bar Chart

Vehicle Type Pie Chart

Payment Method Bar Chart

Ride Distance Histogram

Ride Time vs Booking Value Scatter Plot

Correlation Heatmap

Daily Booking Trend Line Chart

These visualizations help understand business performance.

**📊 Key Insights**

Majority of bookings are completed successfully.

Digital payments are widely used.

Certain vehicle types generate higher revenue.

Ride distance positively impacts booking value.

Cancellation percentage affects revenue significantly.

Peak booking dates identified through trend analysis.

**🏢 Business Recommendations**

Reduce cancellations using predictive models

Improve driver training for better ratings

Optimize surge pricing during peak demand

Promote high-performing vehicle types

Encourage digital payment incentives

📚 Learning Outcomes

Practical experience in data cleaning

Exploratory Data Analysis (EDA)

Data visualization techniques

Business insight generation

Real-world dataset handling

**▶ How to Run This Project**

Open Google Colab

Upload rapido 200.xlsx

Copy and paste the Python code

Run all cells

Analyze generated charts
