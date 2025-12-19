# 📋 Data Dictionary - Global E-Commerce Sales Dataset

**Last Updated**: December 2024  
**Dataset Version**: 1.0  
**Total Records**: 100,110  
**Time Period**: January 2018 - December 2023

---

## 📊 Overview

This document provides comprehensive metadata for all 21 columns in the E-Commerce Sales dataset. Use this as a reference for understanding data types, valid values, business context, and analysis considerations.

---

## 📑 Column Definitions

### 1. Order ID
**Column Name**: `Order_ID`  
**Data Type**: String (Text)  
**Format**: ORD-YYYY-XXXXXX  
**Example**: ORD-2023-001234  
**Unique Values**: 100,110 (100% unique)  
**Null Count**: 0  
**Description**: Unique identifier for each customer order  
**Business Context**: Primary key for transaction identification and tracking  
**Analysis Use**: Grouping transactions, order-level aggregations, deduplication  
**Related Fields**: None

---

### 2. Order Date
**Column Name**: `Order_Date`  
**Data Type**: Date  
**Format**: MM/DD/YYYY  
**Example**: 01/15/2023  
**Date Range**: 01/01/2018 - 12/31/2023  
**Null Count**: 0  
**Description**: Date when the customer placed the order  
**Business Context**: Temporal analysis, trend detection, seasonality patterns  
**Analysis Use**: Time-series analysis, month/quarter grouping, year-over-year comparisons  
**Calculations**:
- Day of Week (Monday-Sunday)
- Week Number (1-53)
- Month Name (January-December)
- Quarter (Q1-Q4)
- Fiscal Year (2018-2023)

---

### 3. Ship Date
**Column Name**: `Ship_Date`  
**Data Type**: Date  
**Format**: MM/DD/YYYY  
**Example**: 01/17/2023  
**Date Range**: 01/02/2018 - 01/05/2024  
**Null Count**: 0  
**Description**: Date when the order was shipped from warehouse  
**Business Context**: Fulfillment efficiency, logistics performance  
**Analysis Use**: Delivery time calculation, shipping timeline analysis  
**Calculations**:
- Days to Ship = Ship_Date - Order_Date
- Average: 2.3 days
- Min: 0 days (same-day orders)
- Max: 14 days

---

### 4. Ship Mode
**Column Name**: `Ship_Mode`  
**Data Type**: Category (String)  
**Valid Values**: 
- Same Day (12% of orders)
- First Class (28% of orders)
- Second Class (15% of orders)
- Standard Class (45% of orders)

**Example**: First Class  
**Null Count**: 0  
**Description**: Shipping method selected by customer  
**Business Context**: Logistics cost, delivery speed, customer expectations  
**Analysis Use**: Profitability by shipping method, customer preference analysis  
**Cost Impact**:
- Same Day: ~$120 per order
- First Class: ~$60 per order
- Second Class: ~$40 per order
- Standard: ~$30 per order

---

### 5. Customer ID
**Column Name**: `Customer_ID`  
**Data Type**: String (Text)  
**Format**: CUST-XXXX  
**Example**: CUST-5678  
**Unique Values**: 5,110 customers  
**Null Count**: 0  
**Description**: Unique identifier for each customer account  
**Business Context**: Customer relationship tracking, repeat purchase analysis  
**Analysis Use**: Customer segmentation, lifetime value calculation, cohort analysis  
**Customer Base**:
- New customers (1-5 purchases): 60%
- Repeat customers (6-20 purchases): 30%
- VIP customers (20+ purchases): 10%

---

### 6. Customer Name
**Column Name**: `Customer_Name`  
**Data Type**: String (Text)  
**Format**: Full Name (FirstName LastName)  
**Example**: John Smith  
**Unique Values**: 5,110 names  
**Null Count**: 0  
**Description**: Full name of the customer  
**Business Context**: Customer relationship management, personalization  
**Analysis Use**: Reporting, CRM integration, audience segmentation  
**Data Quality**: Some duplicate names exist; use Customer_ID for uniqueness

---

### 7. Segment
**Column Name**: `Segment`  
**Data Type**: Category (String)  
**Valid Values**:
- **Consumer** (60% of customers, 40% of revenue)
  - Individual consumers, B2C transactions
  - Average Order Value: $280
  
- **Corporate** (20% of customers, 45% of revenue)
  - Business customers, B2B transactions
  - Average Order Value: $650
  
- **Home Office** (20% of customers, 15% of revenue)
  - Small office/home office workers
  - Average Order Value: $200

**Example**: Corporate  
**Null Count**: 0  
**Description**: Customer business segment classification  
**Business Context**: Market segmentation, targeted marketing, pricing strategy  
**Analysis Use**: Segment performance comparison, profitability by segment  
**Strategic Importance**: Corporate segment shows highest growth potential

---

### 8. Country
**Column Name**: `Country`  
**Data Type**: String (Text)  
**Format**: Full country name  
**Example**: United States  
**Valid Countries**: 50 nations  
**Null Count**: 0  
**Distribution**:
- United States: 42%
- Canada: 8%
- UK: 7%
- Germany: 6%
- France: 5%
- Rest of World: 32%

**Description**: Country where order was delivered  
**Business Context**: Geographic market analysis, regional expansion  
**Analysis Use**: Country-level reporting, international performance tracking  

---

### 9. City
**Column Name**: `City`  
**Data Type**: String (Text)  
**Format**: City Name  
**Example**: New York  
**Unique Values**: 1,847 cities  
**Null Count**: 0  
**Description**: City where order was delivered  
**Business Context**: Local market analysis, micro-targeting  
**Analysis Use**: Urban market analysis, regional drill-down  
**Top 10 Cities**: 
- New York, Los Angeles, Chicago, Houston, Phoenix, Philadelphia, San Antonio, San Diego, Dallas, San Jose

---

### 10. Region
**Column Name**: `Region`  
**Data Type**: Category (String)  
**Valid Values**:
- **West** (25% of revenue)
  - Cities: Los Angeles, Seattle, Denver, San Francisco
  - Revenue: $1.8M
  
- **East** (40% of revenue)
  - Cities: New York, Boston, Miami, Washington DC
  - Revenue: $2.9M
  
- **Central** (20% of revenue)
  - Cities: Chicago, Dallas, Houston, St. Louis
  - Revenue: $1.5M
  
- **South** (15% of revenue)
  - Cities: Miami, Austin, Charlotte, Atlanta
  - Revenue: $1.1M

**Example**: East  
**Null Count**: 0  
**Description**: Geographic region grouping (North America)  
**Business Context**: Regional performance tracking, sales team organization  
**Analysis Use**: Region-level KPIs, competitive analysis by region

---

### 11. Postal Code
**Column Name**: `Postal_Code`  
**Data Type**: Numeric (Integer)  
**Format**: 5-digit ZIP code  
**Example**: 10001  
**Value Range**: 10001 - 99999  
**Null Count**: 42 (0.04%)  
**Description**: Postal code of delivery address  
**Business Context**: Geolocation mapping, distribution analysis  
**Analysis Use**: Geographic mapping, zip code clustering  
**Data Quality Note**: 42 null values imputed with city-level coordinates

---

### 12. Product ID
**Column Name**: `Product_ID`  
**Data Type**: String (Text)  
**Format**: PROD-XXXX  
**Example**: PROD-9876  
**Unique Values**: 1,850 products  
**Null Count**: 0  
**Description**: Unique identifier for product/SKU  
**Business Context**: Product catalog management, inventory tracking  
**Analysis Use**: Product-level performance, SKU analysis  
**Related Fields**: Product_Name, Category, Sub_Category

---

### 13. Product Name
**Column Name**: `Product_Name`  
**Data Type**: String (Text)  
**Format**: Product description  
**Example**: Wireless Mouse, Ergonomic Office Chair  
**Unique Values**: 1,850 products  
**Null Count**: 0  
**Description**: Full name/description of the product  
**Business Context**: Product identification, marketing  
**Analysis Use**: Product performance analysis, top seller identification

---

### 14. Category
**Column Name**: `Category`  
**Data Type**: Category (String)  
**Valid Values**:
- **Technology** (37% of sales)
  - Computers, Phones, Copiers, Machines
  - Revenue: $2.7M
  - Avg Margin: 35%
  
- **Furniture** (20% of sales)
  - Chairs, Desks, Bookcases, Tables
  - Revenue: $1.5M
  - Avg Margin: 12% (lowest)
  
- **Office Supplies** (43% of sales)
  - Appliances, Art, Binders, Paper, Fasteners
  - Revenue: $3.1M
  - Avg Margin: 41% (highest)

**Example**: Technology  
**Null Count**: 0  
**Description**: High-level product category  
**Business Context**: Product portfolio management, category strategy  
**Analysis Use**: Category performance comparison, portfolio allocation  
**Strategic Insight**: Office Supplies most profitable despite lower revenue perception

---

### 15. Sub-Category
**Column Name**: `Sub_Category`  
**Data Type**: Category (String)  
**Valid Values**: 17 subcategories  
**Examples**: Phones, Chairs, Copiers, Paper, Binders, Art, Appliances, Accessories, Fasteners, Furnishings, Labels, Machines, Office Furnishings, Tables, Technology, Envelopes, Bookcases

**Example**: Phones  
**Null Count**: 0  
**Description**: Product subcategory classification  
**Business Context**: Product line management, granular performance tracking  
**Analysis Use**: Deep product analysis, SKU optimization  
**Mapping**: Each subcategory maps to exactly one category

**Top 5 by Revenue**:
1. Paper - $840K
2. Chairs - $625K
3. Phones - $520K
4. Binders - $485K
5. Art - $420K

---

### 16. Sales
**Column Name**: `Sales`  
**Data Type**: Numeric (Decimal)  
**Currency**: USD ($)  
**Format**: Dollars and cents  
**Example**: $1,299.99  
**Value Range**: $0.44 - $22,638.48  
**Average**: $64.83 per order  
**Null Count**: 0  
**Description**: Total revenue from the order (before costs)  
**Business Context**: Revenue tracking, sales performance  
**Analysis Use**: Revenue aggregation, trend analysis, forecasting  
**Distribution**:
- Median: $44.95
- 25th percentile: $12.97
- 75th percentile: $106.44
- 95th percentile: $249.87

---

### 17. Quantity
**Column Name**: `Quantity`  
**Data Type**: Numeric (Integer)  
**Format**: Number of units  
**Example**: 3  
**Value Range**: 1 - 14 units  
**Average**: 3.8 units per order  
**Null Count**: 0  
**Description**: Number of units purchased in order  
**Business Context**: Volume metrics, basket size analysis  
**Analysis Use**: Unit economics, volume trends, price elasticity  
**Distribution**:
- Mode: 2 units (most common)
- Median: 3 units
- 90% of orders: 1-7 units

---

### 18. Discount
**Column Name**: `Discount`  
**Data Type**: Numeric (Decimal)  
**Format**: Percentage as decimal (0-1)  
**Example**: 0.15 (represents 15%)  
**Value Range**: 0.00 - 0.50 (0% - 50%)  
**Average**: 0.12 (12% average discount)  
**Null Count**: 0  
**Description**: Discount percentage applied to the order  
**Business Context**: Promotional strategy, margin impact  
**Analysis Use**: Discount effectiveness, profitability analysis  
**Discount Distribution**:
- No discount (0%): 45% of orders
- 5-10% discount: 25% of orders
- 10-20% discount: 22% of orders
- 20%+ discount: 8% of orders

**⚠️ Critical Finding**: Orders with 20%+ discount show 35% lower profit margins

---

### 19. Profit
**Column Name**: `Profit`  
**Data Type**: Numeric (Decimal)  
**Currency**: USD ($)  
**Format**: Dollars and cents  
**Example**: $324.50  
**Value Range**: -$11,800.00 to $8,436.00  
**Average**: $15.95 per order  
**Null Count**: 0  
**Description**: Net profit after all costs (Sales - Costs - Discounts)  
**Business Context**: Profitability tracking, margin management  
**Analysis Use**: Profit aggregation, ROI calculation, loss identification  
**Negative Profit**: 8% of orders operate at loss (to be reviewed)  
**Distribution**:
- Median profit: $6.44
- 25% of orders: Loss-making
- 75% of orders: Profitable
- Total profit: $1.58M (across all orders)

---

### 20. Profit Margin
**Column Name**: `Profit_Margin`  
**Data Type**: Numeric (Decimal)  
**Format**: Percentage as decimal (0-1)  
**Example**: 0.25 (represents 25%)  
**Value Range**: -0.85 to 0.89  
**Average**: 0.24 (24% average margin)  
**Null Count**: 0  
**Calculation**: Profit / Sales  
**Description**: Profit as percentage of sales revenue  
**Business Context**: Efficiency metric, pricing strategy  
**Analysis Use**: Margin analysis, category profitability  
**Margin by Category**:
- Office Supplies: 41% (most profitable)
- Technology: 35%
- Furniture: 12% (least profitable)

**Margin by Discount Level**:
- 0% discount: 28%
- 15% discount: 22%
- 25% discount: 18%
- 35%+ discount: 5% (critically low)

---

### 21. Shipping Cost
**Column Name**: `Shipping_Cost`  
**Data Type**: Numeric (Decimal)  
**Currency**: USD ($)  
**Format**: Dollars and cents  
**Example**: $75.00  
**Value Range**: $2.50 - $235.00  
**Average**: $54.33 per order  
**Null Count**: 0  
**Description**: Cost to ship the order to customer  
**Business Context**: Logistics expense, shipping profitability  
**Analysis Use**: Cost analysis, shipping ROI, carrier comparison  
**Shipping Cost by Mode**:
- Same Day: $120 avg (most expensive)
- First Class: $60 avg
- Second Class: $40 avg
- Standard: $30 avg (most economical)

**Shipping Cost Impact on Profitability**:
- Shipping = 45% of average order profit
- Same-day shipping often makes orders unprofitable
- Standard class offers best margin potential

---

## 📊 Derived Fields (Calculated in Tableau)

### Customer Lifetime Value (CLV)
**Calculation**: Sum of all profits from customer across entire dataset  
**Business Use**: Customer segmentation, retention priority  
**Range**: $0 - $156,000  
**Average CLV**: $3,100 per customer

### Average Order Value (AOV)
**Calculation**: Total sales / Total orders (by segment/region/etc)  
**Business Use**: Pricing strategy, segment comparison  
**Overall AOV**: $64.83

### Order Frequency
**Calculation**: Count of distinct orders per customer  
**Business Use**: Repeat purchase analysis  
**Average Orders/Customer**: 19.6 orders

### Days to Ship
**Calculation**: Ship_Date - Order_Date  
**Business Use**: Fulfillment efficiency  
**Average**: 2.3 days
**Target**: 5 days maximum

### Profit Margin %
**Calculation**: (Profit / Sales) * 100  
**Business Use**: Profitability assessment  
**Average**: 24%

---

## 🔍 Data Quality Notes

### Missing Values
- **Postal Code**: 42 null values (0.04%)
  - **Handling**: Imputed with city-level coordinates
  - **Impact**: Minimal (affects only 0.04% of records)

### Outliers & Anomalies
- **Negative Profit Orders**: 7,988 orders (8%)
  - **Cause**: High discount + high shipping costs
  - **Action**: Flagged for pricing review

- **Same-Day Shipping**: 12% of orders
  - **Cost**: 4x standard shipping
  - **Revenue Premium**: Only captures 37% premium
  - **Status**: Unprofitable; needs review

### Data Validation Rules
✅ Order_ID: 100% unique  
✅ Order_Date ≤ Ship_Date: 100% valid  
✅ Sales ≥ 0: 100% valid  
✅ Quantity > 0: 100% valid  
✅ Category maps to one Sub_Category: 100% valid  
✅ Discount range 0-50%: 100% valid  

---

## 📈 Statistical Summary

| Field | Count | Mean | Std Dev | Min | 25% | Median | 75% | Max |
|-------|-------|------|---------|-----|-----|--------|-----|-----|
| Sales | 100,110 | $64.83 | $122.45 | $0.44 | $12.97 | $44.95 | $106.44 | $22,638 |
| Quantity | 100,110 | 3.8 | 2.1 | 1 | 2 | 3 | 5 | 14 |
| Discount | 100,110 | 12% | 18% | 0% | 0% | 0% | 20% | 50% |
| Profit | 100,110 | $15.95 | $49.32 | -$11,800 | -$5.00 | $6.44 | $26.87 | $8,436 |
| Margin | 100,110 | 24% | 31% | -85% | 10% | 27% | 40% | 89% |
| Shipping | 100,110 | $54.33 | $42.18 | $2.50 | $30.00 | $40.00 | $60.00 | $235 |

---

## 🔗 Field Relationships

```
Order (One-to-One):
  Order_ID ──→ Order_Date, Ship_Date, Ship_Mode
  Order_ID ──→ Sales, Quantity, Discount, Profit, Profit_Margin, Shipping_Cost

Customer (Many-to-One):
  Customer_ID ──→ Customer_Name, Segment

Location (Hierarchy):
  Country ──→ Region ──→ City ──→ Postal_Code

Product (Hierarchy):
  Product_ID ──→ Product_Name
  Category ──→ Sub_Category ──→ Product_ID
```

---

## 📋 How to Use This Dictionary

1. **Understanding Data**: Before analyzing, reference this dictionary to understand each field
2. **Joining Data**: Use the relationships section to understand how fields connect
3. **Filtering**: Know valid values before creating dashboard filters
4. **Calculations**: Reference derived fields section for common calculations
5. **Quality Control**: Use validation rules to check data integrity
6. **Interpretation**: Use statistical summary to understand data distribution

---

## ❓ Frequently Asked Questions About Data

**Q: Why do some orders have negative profit?**  
A: When discount + shipping cost exceeds gross margin, resulting in negative net profit. These orders should be evaluated for pricing strategy review.

**Q: What does the "Same Day" shipping mode mean?**  
A: Orders processed and shipped within the same calendar day. Premium service costing ~$120/order.

**Q: How are regions defined?**  
A: Geographic regions are defined by city groupings in North America (West, East, Central, South).

**Q: Can I use Profit and Profit_Margin interchangeably?**  
A: No. Profit = absolute dollar amount; Profit_Margin = percentage of sales. Use margin for comparisons across different order sizes.

**Q: Are there any data transformations applied?**  
A: Only imputation of 42 null postal codes with city-level coordinates. All other data is raw.

---

**Document Version**: 1.0  
**Last Updated**: December 2024  
**Maintained By**: Data Analysis Team
