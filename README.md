## Consumer Finance Stress Analysis

A datathon project analyzing how U.S. macroeconomic stressors, especially interest rates and inflation, relate to consumer complaints across major financial products.

## Overview

Macroeconomic conditions shape everyday financial life in the United States. Changes in interest rates and inflation can affect borrowing costs, repayment pressure, and household financial decision-making across products such as credit cards, mortgages, student loans, vehicle loans, and checking or savings accounts.

This project uses public data from the Consumer Financial Protection Bureau (CFPB) and the Federal Reserve Economic Data (FRED) platform to study whether complaint activity changes as economic conditions tighten. We focus on identifying which financial products appear most responsive to macroeconomic stress and whether those effects appear immediately or with a time lag.

## Research Question

How do changes in inflation and interest rates relate to complaint activity across major consumer financial products?

More specifically:
- Which products appear most responsive to macroeconomic stress?
- Are complaints more strongly associated with interest rates or inflation?
- Do these relationships appear immediately or after a lag?

## Hypothesis

We expect complaint patterns to vary across product categories rather than move uniformly.

Our hypothesis is that:
- complaint activity will be more strongly associated with interest rates than with inflation
- debt-related products such as credit cards, student loans, and vehicle loans will be more sensitive to macroeconomic stress than other categories
- some effects will appear with a lag rather than in the same month

## Datasets

### 1. CFPB Consumer Complaint Database
Public complaint records related to consumer financial products and services. 

Used fields include:
- Date received
- Product
- Issue
- Company
- State

Source: CFPB
**Note: I did not include the csv file for this dataset as it exceeded 25MB.** 

### 2. CPIAUCSL
Consumer Price Index for All Urban Consumers: All Items.

This dataset is used to measure inflation over time.

Source: FRED

### 3. FEDFUNDS
Effective Federal Funds Rate.

This dataset is used as a measure of U.S. interest-rate conditions.

Source: FRED

## Methodology

### Data Preparation
- Filtered data to the period from January 2019 to December 2025
- Cleaned complaint product categories
- Aggregated complaints by month and product
- Built a complete month-by-product panel so zero-complaint months were preserved
- Merged complaint data with monthly macroeconomic variables

### Feature Engineering
- Created inflation measures from CPI data
- Used the federal funds rate as the interest-rate variable
- Generated lagged macroeconomic variables to test delayed effects

### Analysis
- Exploratory data analysis on complaint trends by product
- Lagged Pearson correlation analysis between complaints and macro variables
- OLS regression models by product category
- Random Forest models as an optional predictive benchmark

## Key Findings

- Complaint activity appears more strongly associated with the Federal Funds Rate than with CPI inflation.
- Credit card complaints show the strongest positive relationship with interest-rate conditions in our analysis.
- Student loans and vehicle loans also appear highly rate-sensitive.
- Relationships differ across financial products, suggesting that macroeconomic stress is not experienced uniformly across markets.
- Some complaint responses appear with a lag rather than immediately.
- The machine learning model did not outperform simpler statistical analysis, suggesting that the signal in this dataset is better captured through interpretation-focused methods than through predictive modeling alone.

## Interpretation

One of the main conclusions of this project is that interest rates may be a more direct and useful macroeconomic stress indicator for consumer complaint behavior than headline inflation.

For example:
- higher rates directly affect borrowing costs for revolving debt
- they may increase repayment pressure on interest-sensitive products
- they may also reduce market activity in some areas, such as mortgages, which can complicate the interpretation of raw complaint counts

Because of this, results should be interpreted as statistical associations rather than causal effects.

## Limitations

This project has several important limitations:

- **Correlation is not causation**  
  The analysis identifies relationships, not definitive causal effects.

- **Complaint counts are an imperfect proxy for financial stress**  
  Complaint behavior depends on reporting awareness, consumer choice, and regulatory context.

- **Raw complaint counts are not normalized by market size**  
  For example, mortgage complaints may fall when rates rise because mortgage activity itself falls.

- **Limited macroeconomic controls**  
  Other factors such as unemployment, lending volume, consumer sentiment, and policy changes were not fully incorporated.

- **The 2019 to 2025 period is unusual**  
  The sample includes the pandemic, stimulus programs, inflation surges, and aggressive rate hikes.

- **Broad product categories may mask differences within products**  
  A single product category can include several complaint types and consumer experiences.

