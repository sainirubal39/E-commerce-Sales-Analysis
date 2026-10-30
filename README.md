# 🛒 E-commerce Sales Data Analysis Using R

## 📌 1. Introduction

E-commerce has transformed the way businesses operate by enabling online buying and selling of products and services. With the rapid growth of digital platforms, a huge amount of sales data is generated daily.

This data contains valuable insights about customer behavior, purchasing patterns, product performance, and market trends.

**E-commerce Sales Data Analysis** involves examining and interpreting sales data to extract meaningful information that can support business decisions.

This project uses the **R Programming Language** to clean, process, analyze, and visualize e-commerce sales data. It helps identify sales trends, best-selling products, category-wise performance, and regional sales distribution.

---

## 🎯 2. Objectives

- To import and preprocess e-commerce sales data using R.
- To perform data cleaning and transformation for accurate analysis.
- To analyze sales trends and customer purchasing behavior.
- To visualize data using graphs and charts.
- To identify best-selling products and high-revenue categories.
- To derive meaningful insights to support business decision-making.

---

## 📊 3. Data Description

The dataset used in this project contains information related to 100 online sales transactions.

### Main Attributes

| Attribute | Description |
|---|---|
| Order_ID | Unique ID for each order |
| Order_Date | Date when the order was placed |
| Customer_ID | Unique ID of the customer |
| Product_Name | Name of the product |
| Category | Product category |
| Quantity | Number of items purchased |
| Price | Price per product |
| Total_Sales | Total revenue (Quantity × Price) |
| Region | Location of the customer |

The dataset is generated using R with sample product, customer, date, and region information.

---

## 🛠️ 4. Tools and Technologies Used

| Tool / Technology | Purpose |
|---|---|
| R Programming | Data analysis and computation |
| RStudio | IDE for writing and executing R code |
| dplyr | Data manipulation and transformation |
| ggplot2 | Data visualization and graphical representation |

---

## 💻 5. Complete Project Code

The following is the R code used in this project.

### Step 1: Load Required Libraries

```r
library(dplyr)
library(ggplot2)
```

### Step 2: Create Dataset of 100 Records

```r
set.seed(123) # for reproducibility

data <- data.frame(
  Order_ID = 1:100,

  Order_Date = sample(
    seq(as.Date("2024-01-01"), as.Date("2024-03-31"), by="day"),
    100, replace = TRUE
  ),

  Customer_ID = sample(1001:1100, 100, replace = TRUE),

  Product_Name = sample(
    c("Laptop", "Mobile", "Tablet", "Shoes",
      "Shirt", "Watch", "Headphones"),
    100, replace = TRUE
  ),

  Category = sample(
    c("Electronics", "Clothing", "Footwear", "Accessories"),
    100, replace = TRUE
  ),

  Quantity = sample(1:5, 100, replace = TRUE),

  Price = sample(
    c(500, 1000, 2000, 5000, 10000, 20000, 50000),
    100, replace = TRUE
  ),

  Region = sample(
    c("North", "South", "East", "West"),
    100, replace = TRUE
  )
)

# View first few rows
head(data)
```

### Step 3: Data Cleaning

```r
# Check missing values
sum(is.na(data))

# Remove missing values
data <- na.omit(data)
```

### Step 4: Create Total Sales Column

```r
data <- data %>%
  mutate(Total_Sales = Quantity * Price)

# View updated dataset
head(data)
```

### Step 5: Category-wise Sales Analysis

```r
category_sales <- data %>%
  group_by(Category) %>%
  summarise(Total_Sales = sum(Total_Sales))

print("Category-wise Sales:")
print(category_sales)
```

### Step 6: Bar Chart - Category Sales

```r
ggplot(category_sales, aes(x = Category, y = Total_Sales, fill = Category)) +
  geom_bar(stat = "identity") +
  theme_minimal() +
  ggtitle("Sales by Category") +
  xlab("Category") +
  ylab("Total Sales")
```

### Step 7: Top Selling Products

```r
top_products <- data %>%
  group_by(Product_Name) %>%
  summarise(Total_Sales = sum(Total_Sales)) %>%
  arrange(desc(Total_Sales))

print("Top Selling Products:")
head(top_products, 5)
```

### Step 8: Region-wise Sales

```r
region_sales <- data %>%
  group_by(Region) %>%
  summarise(Total_Sales = sum(Total_Sales))

print("Region-wise Sales:")
print(region_sales)
```

### Step 9: Pie Chart - Region Sales

```r
pie(
  region_sales$Total_Sales,
  labels = region_sales$Region,
  main = "Sales Distribution by Region"
)
```

### Step 10: Sales Trend Over Time

```r
sales_trend <- data %>%
  group_by(Order_Date) %>%
  summarise(Daily_Sales = sum(Total_Sales))

print("Sales Trend:")
head(sales_trend)
```

### Step 11: Line Chart - Sales Trend

```r
ggplot(sales_trend, aes(x = Order_Date, y = Daily_Sales)) +
  geom_line(color = "blue") +
  geom_point(color = "red") +
  theme_minimal() +
  ggtitle("Daily Sales Trend") +
  xlab("Date") +
  ylab("Sales")
```

### Step 12: Summary Statistics

```r
print("Summary of Dataset:")
summary(data)
```

### Step 13: Key Insights

```r
cat("\nKey Insights:\n")

cat("- Electronics and high-price products generate more revenue\n")

cat("- Some products are consistently top-selling\n")

cat("- Sales vary across regions\n")

cat("- Daily sales fluctuate over time\n")
```

---

## 📈 6. Data Visualization

This project uses three types of visualizations:

### 1. Bar Chart – Category-wise Sales
Displays total sales for different product categories and helps identify high-revenue categories.

### 2. Pie Chart – Region-wise Sales
Shows the distribution of sales across North, South, East, and West regions.

### 3. Line Chart – Daily Sales Trend
Displays daily sales over time and helps understand changes in sales performance.

---

## 🔍 7. Explanation of Code

| Step | Description |
|---|---|
| Load Libraries | Loads dplyr and ggplot2 |
| Create Dataset | Generates 100 sample sales records |
| Data Cleaning | Checks and removes missing values |
| Total Sales | Calculates Quantity × Price |
| Category Analysis | Calculates sales for each category |
| Bar Chart | Visualizes category-wise sales |
| Top Products | Identifies the five highest-revenue products |
| Region Analysis | Calculates sales for each region |
| Pie Chart | Visualizes regional sales distribution |
| Sales Trend | Calculates daily sales |
| Line Chart | Displays sales trends over time |
| Summary | Generates statistical information |
| Key Insights | Displays important findings |

---

## 💡 8. Key Insights

The project helps identify the following business insights:

- Electronics and high-price products can generate more revenue.
- Some products perform better than others in terms of total sales.
- Sales performance varies across different regions.
- Daily sales fluctuate over time.
- Data visualization makes it easier to understand sales patterns.

*Note: These are the insights described in the project. Actual rankings and values depend on the generated dataset.*

---

## ⭐ 9. Advantages

- Easy to understand and implement.
- Helps analyze large amounts of sales information.
- Identifies top-selling products.
- Provides category-wise and region-wise analysis.
- Visualizes sales trends using graphs.
- Supports data-driven business decisions.

---

## ⚠️ 10. Limitations

- Uses randomly generated sample data.
- Does not use a live e-commerce database.
- Analysis is limited to the available dataset.
- Does not include real-time sales tracking.
- Does not include a predictive analytics model.

---

## 🚀 11. Future Scope

The project can be improved by adding:

- Real-world e-commerce datasets.
- Database integration.
- Customer purchasing behavior analysis.
- Monthly and yearly sales analysis.
- Sales forecasting using machine learning.
- Interactive dashboards.
- Advanced data visualization.
- Automated sales reports.

---

## ▶️ 12. How to Run the Project

Follow these steps to execute the project:

**Step 1:** Install R Programming Language.

**Step 2:** Install RStudio.

**Step 3:** Open RStudio.

**Step 4:** Install the required libraries:

```r
install.packages("dplyr")
install.packages("ggplot2")
```

**Step 5:** Create a new R script.

**Step 6:** Copy the complete project code into the script.

**Step 7:** Save the file as:

```text
ecommerce_sales_analysis.R
```

**Step 8:** Run the script in RStudio to generate the analysis and visualizations.

---

## 📁 13. Project Structure

```text
E-commerce-Sales-Analysis/
│
├── ecommerce_sales_analysis.R
├── README.md
└── Document1.pdf
```

*The file names above are suggested. Keep the names consistent with your actual uploaded files.*

---

## 🏁 14. Conclusion

The E-commerce Sales Data Analysis project successfully demonstrates how data can be used to gain meaningful insights into business performance.

Using R Programming, the dataset is created, cleaned, and analyzed to understand various aspects of online sales.

Through this analysis, important patterns such as category-wise sales, top-selling products, and region-wise performance can be examined. Visualizations like bar charts, pie charts, and line charts make it easier to interpret data and observe trends over time.

Overall, this project helps develop practical knowledge of data analysis, data visualization, and the application of R Programming in solving real-world business problems.

---

## 👨‍💻 15. Author

**GitHub Username:** [sainirubal39](https://github.com/sainirubal39)

**Project Name:** E-commerce Sales Data Analysis

**Programming Language:** R

**Tools:** RStudio, dplyr, ggplot2

⭐ If you find this project useful, feel free to explore the repository!
