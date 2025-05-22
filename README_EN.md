# Data Analysis (Amazon Product Database)

## Description

This project analyzes a dataset of electronic products from Amazon. It was developed as part of the personal portfolio of Leonardo Jeremías Polidori to practice data cleaning, normalization, exploratory analysis, statistical visualization, and SQL queries.

## Work context

ChatGPT was asked to act as a "project manager" and define a list of realistic objectives based on a public dataset from Kaggle.

- The objectives set by the AI were:

**1. Data transformation and cleaning**
- Convert `discounted_price`, `actual_price`, `discount_percentage`, `rating`, and `rating_count` to appropriate numeric types (removing symbols such as ₹, %, ,, etc.).
- Properly separate the values in `user_id`, `user_name`, `review_id`, `review_title`, and `review_content` (they are grouped by commas and need to be normalized or at least counted).
- Check for duplicates and incomplete records.

**2. Exploratory analysis**
- What is the average product discount?
- Which categories are the most frequent?
- How many products have a rating above 4?
- What are the 5 most expensive products (real price, not discounted)?
- What is the relationship between price and rating?

**3. Suggested visualizations (using Python)**
- Bar chart of the most frequent categories.
- Scatter plot: price vs. rating.
- Histogram of product ratings.
- Pie chart showing the percentage of products by discount range (0–25%, 26–50%, etc.).

## Objectives

- Clean and transform the raw data from the file _`amazon.csv`_  
- Explore patterns in pricing, ratings, and categories  
- Visualize product distribution and price–quality relationship  
- Simulate a real working environment with deliverables and iterations

## Dataset

- Source: _`amazon.csv`_ ([Kaggle dataset](https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset/data))  
- Rows: 1,465 products and reviews  
- Fields: product name, price, discount, rating, review content, etc.

## Tools

- Python 3, Visual Studio Code  
- Pandas, Matplotlib, SQLite  
- ChatGPT / Google Gemini

## Performed analysis

- Data cleaning: price conversion, text normalization  
- Table division up to 3rd Normal Form (NF3) — further normalization was limited due to data structure  
- Descriptive statistics  
- Visualizations by category, price, and rating

## Challenges and decisions

- While normalizing the dataset, the information was split into multiple tables to avoid partial dependencies and redundancy. However, fields such as `review_id`, `user_id`, `review_title`, and `review_content` contained multiple values grouped in single cells, with no consistent delimiter.
- Because of this ambiguous structure, it was decided **not to split these values into individual rows**, as automatic separation could create **data inconsistencies** and negatively affect performance and analysis quality.
- It is recommended that if a more precise separation is required, a **manual or semi-automatic** cleaning process be applied after validating the data.

- To simplify the graph of most sold categories, a trimmed version of category names was saved in _`:database/most_sold_categorys_short_names.csv`_ to preserve the integrity of the main database.

## Key results

- The average product discount is **47.69%**  
- Top 5 most sold categories:
  1. _USB Cables_ – 233 products  
  2. _SmartWatches_ – 76 products  
  3. _Smartphones_ – 68 products  
  4. _SmartTVs_ – 63 products  
  5. _In-Ear Headphones_ – 52 products  

- **930 products** have a rating above 4 — that’s **63.48%** of all products  
- Top 5 most expensive products:
  1. _Fire-Boltt Phoenix Smart Watch..._  
  2. _Fire-Boltt India's No..._  
  3. _Fire-Boltt Phoenix Smart Wa..._  
  4. _Fire-Boltt Gladiator..._  
  5. _Fire-Boltt Ring 3 Smart Wa..._  

  *(A different brand appears only at position 9: “MI REDMI 9i Sport”, followed by Boult at position 14)*

- The 50 most expensive products have an average rating of **4.19**, showing strong perceived value.
- In the _`figures`_ folder you’ll find:
  1. _`Figure_1_most_sold_categorys.webp`_ – Bar chart of most sold categories  
  2. _`Figure_2_scatter_rating_rated.webp`_ – Scatter plot (price vs. rating) of the 20 top-rated products  
  3. _`Figure_3_scatter_rating_expensive.webp`_ – Scatter plot for the 50 most expensive products  
     _*Note: Many premium items share the same price and brand; further review by brand is advised*_  
  4. _`Figure_4_rating_distribution.webp`_ – Histogram of product ratings (starts at 2 — no products rated below that)  
  5. _`Figure_5_discount_percentages.webp`_ – Bar chart showing product count by discount range

## Final conclusion

- The dataset requires **manual or semi-assisted cleaning** for full normalization.  
- It's recommended to review the prices of top-tier products due to unusual repetition.  
- Discount and rating distributions appear consistent and logical.  
- Over **60%** of products are rated above 4, showing clear customer satisfaction.

---

## Notes

- This project was developed between **May 21 and 22, 2025**, as part of my training as a data analyst.  
- My CV is included in the folder: _`Leonardo_Polidori_CV.docx`_
