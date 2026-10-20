# Credit-Card-Financial-Dashboard

An interactive Power BI report that analyzes credit card transactions together with customer demographics. It shows where revenue comes from by card type, spending category, transaction channel, customer segment and time period.

## Project Objective

- Measure overall performance: revenue, transaction amount, transaction volume and interest earned
- Understand how revenue is distributed across card categories, expense types and payment channels (swipe, chip, online)
- Profile customers by gender, age, income, education, job, marital status and state
- Track weekly and quarterly trends across 2023
- Compare customer acquisition cost across card categories

## Report Pages

### 1. Transaction Report
| Visual | What it shows |
|---|---|
| KPI cards | Revenue, Transaction Amt, Transaction Volume, Interest Earned |
| Card Category table | Revenue, transaction amount and interest earned per card type |
| Revenue by Use Chip | Swipe vs. Chip vs. Online |
| Revenue by Exp Type | Bills, Entertainment, Fuel, Grocery, Food, Travel, etc. |
| Revenue by Education_Level | Revenue by customer education |
| Revenue by Customer_Job | Revenue by occupation |
| Customer Acq Cost by Card Category | Acquisition cost per card type |
| Revenue & Total Volume by Quarter | Combo chart: revenue (columns) and transaction volume (line) |
| Treemaps | Clients by gender, income level and quarter |
| Date slicer | Filters the page by `Week_Start_Date` |

### 2. Customer Report
| Visual | What it shows |
|---|---|
| KPI cards | Revenue, Income, Customer Satisfaction Score (CSS), Interest Earned |
| Revenue by Year, Month, Day & Gender | Line chart of weekly revenue for male vs. female clients |
| Revenue by Income Group / Age Group / Marital_Status / state_cd | Stacked bars split by gender |
| Revenue by Gender | Treemap |
| Count of Clients by Income Level | Treemap |
| Customer_Job table | Revenue, income and interest earned per job |
| Date slicer | Filters the page by `Week_Start_Date` |

## Data Model

Two tables, joined one-to-one on `Client_Num`:

| Table | File | Rows | Content |
|---|---|---|---|
| `credit_card` | `credit_card.csv` | 10,108 | Card category, expense type, chip usage, transaction amount and volume, interest earned, annual fees, acquisition cost, quarter, week start date |
| `customer` | `customer.csv` | 10,108 | Gender, age, education, marital status, job, income, state, satisfaction score |

### Calculated columns
| Column | Definition |
|---|---|
| `Revenue` | `Annual_Fees + Total_Trans_Amt + Interest_Earned` |
| `Income Group` | Low (up to 35K), Medium (35K to 70K), High (above 70K) |
| `Age Group` | 20-30, 30-40, 40-50, 50-60, 60+ |

## Data Preparation (Power Query)

- Imported both CSV files and joined them on `Client_Num`
- Set correct data types, including converting `Week_Start_Date` to a date type
- Trimmed text fields such as `Use Chip`
- Created the `Revenue`, `Income Group` and `Age Group` columns
- Standardized field names for use in visuals and slicers

## Key Findings

| Metric | Value |
|---|---|
| Total revenue | **55.32M** |
| Transaction amount | **44.52M** |
| Transaction volume | **655.7K** |
| Interest earned | **7.84M** |
| Clients | **10,108** (5.88K female, 4.23K male) |

- **Blue** cards generate about **83%** of revenue (46.14M) and account for most of the acquisition cost (0.89M).
- **Swipe** is the top channel at about **63%** of revenue (34.91M), followed by Chip (16.97M) and Online (3.44M).
- **Bills** is the top expense type (13.78M), followed by Entertainment and Fuel.
- **High-income** clients produce about **53%** of revenue, despite being the smallest income group by client count.
- **Male** clients bring about **55%** of revenue (30.22M) although they are 42% of clients.
- **Businessman** is the top job group (17.39M); **Graduate** is the top education level (22.3M).
- **TX, NY and CA** are the top states, each at roughly 12.6M to 12.8M.
- **Q3** has the highest revenue (14.2M) and transaction volume (166.6K); **Q4** is the lowest (13.3M, 161.6K).


## Tools Used

Power BI Desktop, Power Query, DAX
