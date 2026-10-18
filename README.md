# Sales Commercial Analytics | B2B Sales Performance

## Project Overview

This project examines a B2B technology company's sales pipeline to understand how effectively sales opportunities are converted into recorded Won value and where performance differs across products, sales agents, customers and regions.

The analysis combines exploratory data analysis in **Python (Pandas)** with an interactive **Power BI** report. Its purpose is to move beyond headline sales figures and identify practical questions management can investigate to improve pipeline follow-up and commercial decision-making.

> **Core business question:** How effectively is the company converting its sales pipeline into recorded Won value, and what factors are associated with stronger or weaker sales performance?

## Business Objectives

- Assess pipeline health, including open opportunities and the closed-deal win rate.
- Compare product performance by Won opportunities, total Won value, average Won deal value and win rate.
- Evaluate sales agents using multiple measures rather than a single ranking.
- Identify high-value customer accounts and compare customer sectors.
- Examine regional and sales-manager performance.
- Translate descriptive findings into management recommendations, while acknowledging data limitations.

## Dataset

The analysis uses five related CSV files:

| File | Description |
| --- | --- |
| `sales_pipeline.csv` | Opportunity-level sales data, including stage, product, sales agent, account, dates and close value. |
| `sales_teams.csv` | Sales agents, their managers and regional offices. |
| `accounts.csv` | Account characteristics, including sector, employees, revenue and office location. |
| `products.csv` | Product reference information, including series and sales price. |
| `data_dictionary.csv` | Definitions of dataset fields. |

The main pipeline dataset contains **8,800 opportunities**. Its deal stages are Won, Lost, Engaging and Prospecting.

**Data relationships:** The pipeline connects to sales-team information through `sales_agent` and to account information through `account`.

## Tools and Skills

- **Python and Pandas:** data exploration, missing-value investigation, filtering, grouping, aggregation and business metric calculations.
- **Power BI:** data modelling, table relationships, DAX measures, KPI cards, interactive charts and report design.
- **Analytical communication:** interpreting findings, developing recommendations and communicating limitations.

SQL exploration was started but not included as a completed analytical component because the initial MySQL CSV import omitted open opportunities. The Power BI report uses the original CSV data.

## Analytical Approach

1. **Understand the data:** inspect columns, deal stages, row counts and the meanings of missing values.
2. **Check data quality:** distinguish genuinely incomplete records from opportunities that are still open.
3. **Define business metrics:** calculate Won and Lost counts, open opportunities, closed win rate, recorded Won value and average Won deal value.
4. **Compare performance:** analyse products, sales agents, accounts, customer sectors, regional offices and managers.
5. **Build the dashboard:** present the metrics in Power BI and conclude with management insights and recommendations.

The **closed win rate** is defined as:

\[
\text{Closed Win Rate} = \frac{\text{Won Opportunities}}{\text{Won Opportunities + Lost Opportunities}} \times 100
\]

Open opportunities are excluded from this denominator.

## Key Findings

### 1. Pipeline Health

| Metric | Result |
| --- | ---: |
| Total opportunities | 8,800 |
| Won opportunities | 4,238 |
| Lost opportunities | 2,473 |
| Open opportunities | 2,089 |
| Closed win rate | 63.15% |
| Recorded Won value | £10,005,534 |
| Average Won deal value | £2,360.91 |

Of the **2,089 open opportunities**, **1,589** are in the Engaging stage and **500** are in Prospecting. These records warrant follow-up investigation, but the available data does not establish which opportunities are overdue or likely to close.

### 2. Product Performance

**GTXPro** contributed approximately **£3.51 million**, representing **35.1%** of recorded Won value. **GTX Plus Pro** contributed approximately **£2.63 million**, followed by **MG Advanced** at approximately **£2.22 million**.

**GTX Basic** had the highest number of Won opportunities (**915**), illustrating the difference between sales volume and total value. **MG Special** had a relatively high closed win rate (approximately **64.84%**) but contributed only around **£43,768** in Won value. **GTK 500** had the highest average Won deal value (approximately **£26,707**), but this is based on only **15** Won opportunities and should be interpreted cautiously.

### 3. Sales Agent Performance

**Darcel Schlecht** led in both Won opportunities (**349**) and recorded Won value (approximately **£1.15 million**). However, rankings differ when comparing win rate, deal volume and average deal size. For example, **Elease Gluck** had the highest average Won deal value (approximately **£3,615**), while **Hayden Neloms** had one of the highest closed win rates (approximately **70.39%**).

These results show why salesperson performance should be assessed using several complementary measures.

### 4. Customer and Sector Performance

**Kan-code** generated the highest recorded Won value among accounts (approximately **£341,455**). The top five accounts contributed approximately **12.1%** of all recorded Won value.

Among customer sectors, **retail** had the highest recorded Won value (approximately **£947,251**), followed by the sector labelled **`technolgy`** in the source data (approximately **£744,937**) and **medical** (approximately **£698,749**). The source-data spelling is retained here for transparency.

### 5. Regional and Manager Performance

| Region | Won opportunities | Recorded Won value | Average Won deal value |
| --- | ---: | ---: | ---: |
| Central | 1,629 | £3,346,293 | £2,054.20 |
| East | 1,171 | £3,090,594 | £2,639.28 |
| West | 1,438 | £3,568,647 | £2,481.67 |

**West** generated the highest recorded Won value, **Central** had the most Won opportunities and **East** had the highest average Won deal value. This suggests that regional comparisons should consider both volume and deal size.

Among managers, **Melvin Marxen** led in Won opportunities and total recorded Won value, while **Rocco Neubert** had the highest average Won deal value.

## Power BI Dashboard

The report contains six pages:

1. **Executive Overview** — headline KPIs, deal-stage distribution, open pipeline, product value and leading sales agents.
2. **Product Performance** — Won volume, recorded Won value, average Won deal value, win rate and customer office-location distribution.
3. **Sales Performance** — comparisons of sales agents by Won volume, value, average deal size and closed win rate.
4. **Account Performance** — customer accounts and sector-level performance.
5. **Regional and Manager Performance** — regional and manager comparisons.
6. **Business Insights & Recommendations** — key findings, recommended next steps and data limitations.

*Dashboard screenshots can be added here when publishing the repository.*

## Management Recommendations

1. **Review the open pipeline:** Prioritise investigation of the 2,089 open opportunities, especially those in Engaging, and identify which need timely follow-up.
2. **Investigate high-value products:** Explore what drives GTXPro's contribution, including product mix, customer demand and sales practices.
3. **Evaluate agents fairly:** Compare closed win rate, Won volume, average deal value and total Won value together instead of relying on one measure.
4. **Understand regional differences:** Investigate product and customer mix before drawing conclusions about regional effectiveness or reallocating resources.
5. **Improve data quality:** Review missing account information and standardise inconsistent category labels to support more reliable reporting.

## Data Limitations

- **Snapshot rather than history:** The data provides current deal stages, not complete stage-transition histories. Stage-to-stage conversion rates and time spent in each stage cannot be established reliably.
- **Open opportunities:** Missing `close_date` and `close_value` for Engaging and Prospecting opportunities are consistent with their open status and should not automatically be treated as errors.
- **Missing account data:** Some opportunities have no account recorded, limiting account-level analysis.
- **Recorded Won value is not necessarily realised revenue:** The dataset does not independently establish invoicing, cash collection or profit.
- **Descriptive analysis:** Observed differences between products, people and regions do not establish causation.
- **SQL import issue:** An attempted MySQL import retained only closed opportunities, so SQL results from that incomplete import were not used as the basis for the final dashboard.

## Project Structure

```text
Sales Commercial Analytics/
├── data/
│   ├── accounts.csv
│   ├── data_dictionary.csv
│   ├── products.csv
│   ├── sales_pipeline.csv
│   └── sales_teams.csv
├── Notebook/
│   └── 01_initial_exploration.ipynb
├── SQL/
│   └── 01_sales_analysis.sql
├── PowerBi/
│   └── Sales_Commercial_Analytics.pbix
└── README.md
```

*Adjust filenames to match the files in your repository before publishing.*

## Conclusion

The project demonstrates how a sales dataset can be used to answer commercial questions through data preparation, KPI development, comparative analysis and dashboard reporting. The main lesson is that commercial performance cannot be judged by a single figure: deal volume, win rate and deal value each provide a different perspective. The resulting report offers a starting point for more targeted investigation and management decisions.
