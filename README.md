# 🛒 E-Commerce Sales, Customer & Product Analytics | Power BI

An interactive, multi-page **Power BI** report for an India-focused e-commerce business. Four related datasets were cleaned, modeled and analyzed with **Power Query** and **DAX** to deliver insights on sales, customers, products, orders, payments and retention, plus a one-page Executive Summary for management.

<img width="1917" height="1067" alt="Dashboard 1" src="https://github.com/user-attachments/assets/7e53195e-1740-4e9d-abf2-a37412df16e3" />

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Business Questions](#-business-questions)
- [Tools & Technologies](#-tools--technologies)
- [Dataset](#-dataset)
- [Data Preparation](#-data-preparation)
- [Data Model](#-data-model)
- [DAX Measures](#-dax-measures)
- [Dashboard Pages](#-dashboard-pages)
- [Key Results](#-key-results)
- [Business Recommendations](#-business-recommendations)
- [Repository Structure](#-repository-structure)
- [How to Use](#-how-to-use)
- [Future Scope](#-future-scope)
- [Author](#-author)

---

## 📖 Project Overview

E-commerce businesses generate large volumes of data about customers, products, orders and payments. The goal of this project is to turn that data into a decision-support dashboard that helps management understand:

- how the business is performing financially,
- who the customers are and how they behave,
- which products and categories drive revenue,
- how orders and payments are performing operationally, and
- how well customers are being retained.

The project follows a practical BI workflow: **Business Understanding → Data Understanding → Data Cleaning → Data Modeling → KPI Definition → DAX Development → Dashboard Design → Insights & Recommendations.**

---

## ❓ Business Questions

- How much revenue is generated, and how does it change over time?
- How many orders and units are sold, and what is the average order value (AOV)?
- Which categories, products and cities contribute most to revenue?
- How many customers order, and how many become repeat customers?
- Which payment methods are used most?
- How many orders are delivered, cancelled or returned?
- Which customers are high-value?
- Does purchasing frequency differ across customer tenure groups?

---

## 🧰 Tools & Technologies

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Data modeling and interactive dashboard development |
| **Power Query** | Data preparation and transformation |
| **DAX** | Calculated columns, measures and KPIs |
| **CSV files** | Source data |

---

## 🗂 Dataset

Four related tables represent the e-commerce process:

| Table | Rows | Columns | Key Fields |
|---|---:|---:|---|
| `customers` | 100 | 5 | customer_id, customer_name, city, country, signup_date |
| `products` | 50 | 5 | product_id, product_name, category, price, stock |
| `orders` | 500 | 5 | order_id, customer_id, order_date, status, payment_method |
| `order_items` | 1,500 | 5 | order_item_id, order_id, product_id, quantity, unit_price |

**Business values in the data**

- **Categories:** Electronics, Sports, Home & Kitchen, Clothing, Books
- **Cities:** Bengaluru, Hyderabad, Pune, Mumbai, Chennai, Kolkata, Ahmedabad, Delhi
- **Order status:** Delivered, Pending, Cancelled, Returned
- **Payment methods:** Net Banking, Debit Card, Cash on Delivery, Credit Card, UPI

---

## 🧹 Data Preparation

The supplied data was already clean, so the focus was on **validation** and correct preparation in Power Query rather than unnecessary edits.

| Check | Result |
|---|---|
| Missing values | None significant |
| Duplicate records | None found |
| Quantity / price / stock | All positive and within expected range |
| Date fields | Valid |
| Category, status & payment labels | Consistent |
| Keys | Reviewed for relationships |

A calculated column **Order Value = Quantity × Unit Price** was created at the order-item level and aggregated to compute revenue.

<p align="center">
<img width="1917" height="1096" alt="Power Query1" src="https://github.com/user-attachments/assets/4feab404-235b-4d52-ba13-e3446efd238e" />
<img width="1911" height="1066" alt="Power Query 2" src="https://github.com/user-attachments/assets/63b89f53-3e30-44a4-8ed9-c9cad35f5630" />
</p>
<p align="center">
<img width="1917" height="1066" alt="Power Query 3" src="https://github.com/user-attachments/assets/8f43046d-015e-4666-a870-e7f76367a60c" />
<img width="1917" height="1062" alt="Power Query 4" src="https://github.com/user-attachments/assets/cbbcce6f-826f-430a-b39d-9d54bdaf02ba" />
</p>

---

## 🔗 Data Model

A star-style relational model connects the four tables plus a dedicated **Date** table (built from the minimum and maximum order dates, with Year, Month Number, Month Name and Year-Month fields).

| Relationship | Cardinality | Purpose |
|---|:---:|---|
| Customers → Orders | 1 : * | One customer can place many orders |
| Orders → Order Items | 1 : * | One order can contain many items |
| Products → Order Items | 1 : * | One product can appear in many order items |
| Date → Orders | 1 : * | Order-date filtering and time analysis |

<img width="1917" height="1065" alt="Model View" src="https://github.com/user-attachments/assets/8fed517b-24f7-46b6-a486-da838ee3be15" />

---

## 🧮 DAX Measures

| Area | Measures |
|---|---|
| **Sales** | Total Revenue, Total Orders, Total Quantity Sold, Average Order Value, Revenue Growth % (month over month) |
| **Customers** | Total Customers, Customers Who Ordered, New Customers, Repeat Customers, Repeat Customer Rate, Average Revenue per Customer, Average Orders per Customer, High Value Customers |
| **Products** | Total Products Sold, Product Quantity Sold, Average Product Price, Top Category |
| **Operations** | Delivered Orders, Cancelled Orders, Delivery Rate, Cancellation Rate |
| **Classifications** | Stock Status (Out of Stock / Low / Medium / Healthy), Customer Type (Repeat / One-Time) |

> Thresholds for Stock Status and High Value Customers are analyst-defined business assumptions.

---

## 📊 Dashboard Pages

The report contains **six pages**:

| # | Page | Focus |
|---|---|---|
| 1 | **Sales Performance** | Revenue, orders, AOV, quantity, growth, monthly trend, revenue by category / product / city, with Category, City, Date and Order Status slicers |
| 2 | **Customer Analytics** | Customer base, new vs. repeat customers, customers by city, customer type, signup trend, customer-level revenue |
| 3 | **Product & Category** | Products sold, quantity, average price, category revenue and quantity, top/bottom products, stock status |
| 4 | **Orders & Payment** | Delivered/cancelled orders, delivery and cancellation rate, payment method usage and revenue, cancellations by city and payment method, status trend |
| 5 | **Customer Value & Retention** | Repeat rate, high-value customers, average orders per customer, tenure vs. frequency, top customers |
| 6 | **Executive Summary** | Eight headline KPIs with monthly revenue trend, revenue by category and orders by status |

### Screenshots

**Sales Performance** — `images/Dashboard 1.png`
<img width="1917" height="1067" alt="Dashboard 1" src="https://github.com/user-attachments/assets/48f449e7-69b6-4538-9f16-074f829a0c0f" />

**Customer Analytics** — `images/Dashboard 2.png`
<img width="1917" height="1068" alt="Dashboard 2" src="https://github.com/user-attachments/assets/cf0f2ccb-0dd2-4cef-b6b7-0edd62616421" />

**Product & Category** — `images/Dashboard 3.png`
<img width="1917" height="1065" alt="Dashboard 3" src="https://github.com/user-attachments/assets/d80efc2a-92f0-44b5-b7ce-f934248c83f8" />

**Orders & Payment** — `images/Dashboard 4.png`
<img width="1916" height="1067" alt="Dashboard 4" src="https://github.com/user-attachments/assets/fb6a2b09-9baa-448b-ac52-d3f1a382382e" />

**Customer Value & Retention** — `images/Dashboard 5.png`
<img width="1917" height="1061" alt="Dashboard 5" src="https://github.com/user-attachments/assets/4cbcdc9d-b86b-45bf-9ed1-2cb30e863ca3" />

**Executive Summary** — `images/Dashboard 6.png`

---

## 🔑 Key Results

Headline figures from the Executive Summary (with no filters applied):

| KPI | Value |
|---|---|
| Total Revenue | ₹116.15M |
| Total Orders | 500 |
| Average Order Value | ₹232.31K |
| Total Customers | 100 |
| Total Quantity Sold | ~5K units |
| Repeat Customer Rate | 95.96% (95 of 99 ordering customers) |
| Cancellation Rate | 10.60% |
| Top Category | Electronics |

**Highlights**

- **Electronics** and **Sports** are the largest revenue categories, followed by Books, Home & Kitchen and Clothing.
- Of 500 orders, **349 were delivered**, 71 pending, 53 cancelled and 27 returned.
- Revenue by category: Electronics ≈ ₹38.5M, Sports ≈ ₹33.2M, Books ≈ ₹20.5M, Home & Kitchen ≈ ₹12.6M, Clothing ≈ ₹11.2M.
- Only **5 of 100 customers are one-time buyers**; repeat customers generate nearly all revenue (≈ ₹116M vs ≈ ₹1M).
- **Cash on Delivery** and **Net Banking** have the most cancelled orders; **Mumbai** has the most cancellations by city.
- Revenue is spread across all eight cities, with **Mumbai, Bengaluru and Chennai** leading.

> Values may change when slicers are applied. Always confirm final figures in the `.pbix` file.

---

## 💡 Business Recommendations

| Recommendation | Suggested Action |
|---|---|
| Strengthen repeat purchasing | Loyalty benefits, targeted offers and personalized communication |
| Focus on strong categories | Prioritize top categories while reviewing weaker ones |
| Monitor high-value customers | Build retention strategies for customers above the threshold |
| Investigate cancellations | Track by city, payment method and time period |
| Optimize product availability | Use stock status together with sales performance |
| Use payment insights | Review payment adoption alongside cancellation patterns |
| Track monthly trends | Review revenue and order trends regularly |
| Expand segmentation | Add recency, frequency and monetary (RFM) segments |

---

## 📁 Repository Structure

```
├── E Commerce Power BI Website.pbix        # Power BI report file
├── E_Commerce_Power_BI_Doc.docx            # Full project documentation
├── README.md
└── images/
    ├── Dashboard 1.png                     # Sales Performance
    ├── Dashboard 2.png                     # Customer Analytics
    ├── Dashboard 3.png                     # Product & Category
    ├── Dashboard 4.png                     # Orders & Payment
    ├── Dashboard 5.png                     # Customer Value & Retention
    ├── Dashboard 6.png                     # Executive Summary
    ├── Model View.png                      # Data model
    ├── Power Query1.png                    # Power Query screenshots
    ├── Power Query 2.png
    ├── Power Query 3.png
    └── Power Query 4.png
```

---

## ▶️ How to Use

1. Clone or download this repository.
2. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
3. Open `E Commerce Power BI Website.pbix`.
4. Use the page tabs at the bottom and the slicers (Category, City, Date, Order Status) to explore the data.

For a detailed walkthrough of the methodology, see `E_Commerce_Power_BI_Doc.docx`.

---

## 🚀 Future Scope

- Cohort retention analysis
- RFM customer segmentation
- Revenue forecasting
- Drill-through customer profiles
- Automated data refresh
- Additional operational KPIs and advanced customer behavior analysis

---

## 👤 Author

**Abhinav Yadav**

Skills demonstrated: Power BI · Power Query · DAX · Data Modeling · Dashboard Design · Business Analytics

⭐ If you found this project useful, consider giving the repository a star!
