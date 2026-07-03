# Project 2: Exploratory Data Analysis (EDA)
DecodeLabs Data Analytics Internship Batch 2026

## Overview
This project is the discovery phase of my Data Analytics internship at DecodeLabs:
exploring a 1,200-row sales dataset to uncover patterns, distributions, and
relationships, without changing any of the underlying data. The goal was to move
from "is this data clean?" (Project 1) to "what is this data actually telling us?"

## Dataset
- 1,200 rows × 14 columns
- E-commerce order dataset: OrderID, Date, CustomerID, Product, Quantity, UnitPrice,
  ShippingAddress, PaymentMethod, OrderStatus, TrackingNumber, ItemsInCart,
  CouponCode, ReferralSource, TotalPrice

## Process
### Central Tendency
Calculated mean, median, mode, and the five-number summary (min, Q1, median, Q3, max)
for all numeric columns using =AVERAGE(), =MEDIAN(), =MODE.SNGL(), and
=QUARTILE.INC().

**Key finding:** TotalPrice's mean (1,053.97) sits well above its median (823.62),
a sign of right-skewed data, meaning a handful of large orders are pulling the average
upward.

### Outlier Detection (IQR Method)
Used the interquartile range method:
- Lower Bound = Q1 − 1.5×IQR
- Upper Bound = Q3 + 1.5×IQR
- Formula used: =COUNTIF(range,"<"&LowerBound)+COUNTIF(range,">"&UpperBound)

Then filtered the dataset to visually inspect each flagged row rather than
just counting them.

**Key finding:** 8 orders were flagged as statistical outliers in TotalPrice.
On inspection, every one had Quantity = 5 (the maximum) paired with a higher-priced
item, legitimate large purchases, not data errors. This is the difference between
signal (a real pattern worth investigating) and noise (an error to be corrected).

### Categorical Breakdown
Built PivotTables to count frequency across Product, PaymentMethod,
OrderStatus, and ReferralSource.

**Key finding:** Cancelled orders (250) outnumbered Delivered orders (231), 
a flag worth further business investigation.

## Tools Used
Microsoft Excel: AVERAGE, MEDIAN, MODE.SNGL, QUARTILE.INC, COUNTIF,
SUMPRODUCT, CORREL, Analysis ToolPak (Correlation), PivotTables, Filters

## Key Takeaways
1. compare mean vs. median before trusting an average, skew can
   be hiding in plain sight.
2. Statistical outliers are not automatically errors. Inspect them before
   deciding whether to investigate or discard.
3. A balanced category distribution can be just as informative as an
   imbalanced one, both tell you something about the business.

## Files in This Repository
- dataset for data analytics - Dataset used for analysis.
- cleaned data project 2 - Excel workbook with all EDA formulas and PivotTables.

## What I Learned
EDA is not about running every formula you know, it is about asking "so what?"
after every number. A statistic on its own is just a number; the value comes from
translating it into something a business decision could actually use.
