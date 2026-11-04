# Analyzing Motorcycle Part Sales with SQL

An end-to-end SQL analysis of a motorcycle parts retailer and wholesaler: which product lines earn the most, which payment methods and warehouses carry the business, and where the numbers raise questions that need follow-up. The full analysis, queries and written findings are in [`motorcycle_sales_analysis.ipynb`](motorcycle_sales_analysis.ipynb).

## Business questions

| Stakeholder | Question |
|---|---|
| Board of Directors | What is the wholesale net revenue of each product line, by month and warehouse? |
| Finance | Which payment method earns the most net revenue for each warehouse in each month? |
| Marketing | What are the three most ordered product lines for retail and for wholesale customers? |
| Operations | How is work distributed across warehouses, and is there an anomaly at the West warehouse? |

## Dataset

One table, `sales`, covering June to August 2021: 1,000 orders and 9,395 units across three warehouses (North, Central, West), retail and wholesale clients, and three payment methods (credit card, transfer, cash).

| Column | Description |
|---|---|
| `order_number` | Unique order number |
| `date` | Order date, June to August 2021 |
| `warehouse` | `North`, `Central` or `West` |
| `client_type` | `Retail` or `Wholesale` |
| `product_line` | Type of product ordered |
| `quantity` | Number of products ordered |
| `unit_price` | Price per product (USD) |
| `total` | Total price of the order (USD) |
| `payment` | `Credit card`, `Transfer` or `Cash` |
| `payment_fee` | Fee charged because of the payment method |

**Net revenue** is calculated as `total - payment_fee`.

## Key findings

### 1. Wholesale drives volume

Wholesale is 22.5% of orders but 55% of all units. A wholesale order averages 21 to 24 units, compared with about 5 for retail. Central handles 48% of all units, North 35% and West 17%.

<img width="1440" height="864" alt="image" src="https://github.com/user-attachments/assets/dc3437b9-f52f-4312-a9d8-f19180c6d521" />


### 2. Revenue is concentrated in three product lines

Suspension & traction, Frame & body and Electrical system generate 64% of net revenue (ABC class A). Braking system and Engine are close to each other in revenue, and Engine sits just above the 90% line.

<img width="1440" height="864" alt="image" src="https://github.com/user-attachments/assets/3d6e1a89-6024-4a18-a95d-92fd3f5682b1" />


### 3. Units and revenue tell different stories

Braking system is the second most ordered line (2,130 units) but earns the least per unit (about 18 USD). Engine sells only 627 units yet earns about 60.5 USD per unit, roughly twice the network average of 30.8 USD.

<img width="1440" height="864" alt="image" src="https://github.com/user-attachments/assets/d5b81782-b095-4acc-8492-e24e6cafc448" />


### 4. Transfer leads every warehouse, but West is declining

Transfer is the top payment method by net revenue in all nine warehouse-month combinations. Between June and August, Transfer revenue grew 34% at Central and 38% at North, but fell 25% at West.

<img width="1440" height="864" alt="image" src="https://github.com/user-attachments/assets/691a263d-63c2-4a3c-a90a-358c028f8f28" />


### 5. Most ordered product lines by client type

| Client type | Rank | Product line | Units |
|---|---|---|---|
| Retail | 1 | Suspension & traction | 1,017 |
| Retail | 2 (tie) | Braking system | 862 |
| Retail | 2 (tie) | Electrical system | 862 |
| Wholesale | 1 | Braking system | 1,268 |
| Wholesale | 2 | Suspension & traction | 1,128 |
| Wholesale | 3 | Frame & body | 932 |

### 6. Open question: the West warehouse Engine gap

The West warehouse has no wholesale Engine sales in any month, and its wholesale average unit price (27.49 USD) is 10 to 12% lower than at Central and North. The notebook includes diagnostic queries to tell whether this is a stock or allocation problem or simply low B2B demand for engine parts in that region. Stock and customer records would be needed to settle it.

## Recommendations

1. Protect stock availability of the three class A product lines.
2. Review pricing and bundling for Braking system (high volume, low revenue per unit).
3. Monitor Engine stock closely: low volume, highest revenue per unit, and lumpy wholesale demand.
4. Build campaigns around Suspension & traction and Braking system, the top two in both channels.
5. Plan Central warehouse capacity for peak days and collect capacity data to confirm any bottleneck.
6. Investigate the West warehouse: Engine availability, falling Transfer revenue and lower wholesale pricing.

## SQL techniques used

- Common table expressions (CTEs) for step-by-step logic
- Window functions: `RANK()`, `SUM() OVER`, running totals for the Pareto analysis
- Conditional aggregation with `FILTER`
- Date handling with `EXTRACT` and `TO_CHAR` to order months chronologically
- Data validation queries before analysis

## How to reproduce

1. Open `motorcycle_sales_analysis.ipynb` in a SQL-capable notebook environment (the project was built in DataCamp Workspace) connected to a PostgreSQL database that contains the `sales` table.
2. Run the cells in order. The validation section comes first and checks the data before any analysis.
3. The charts in `images/` were drawn from the query results shown in the notebook.

## Notes and limitations

- **Fee definition:** the data dictionary describes `payment_fee` as a percentage of `total`, while net revenue here subtracts it as an amount. A diagnostic query in the notebook checks which is correct; if the column holds rates, absolute revenue figures would change slightly, though rankings are unlikely to.
- **Short window:** three months of data limit conclusions about trends and seasonality.
- **No cost data:** the analysis is revenue-based, not profit-based.
- **No capacity or inventory data:** warehouse congestion and stock-out questions can only be tested indirectly.

## Author

[kov1cx](https://github.com/kov1cx)
