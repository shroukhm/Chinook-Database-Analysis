# Chinook Database Analysis Project

## Project Overview
This project involves analyzing the Chinook database, a sample SQLite database representing a digital media store. The goal is to practice advanced SQL techniques, including complex joins, Common Table Expressions (CTEs), window functions, and query optimization through indexing. The project is divided into three main requirements:

1. **Complex Joins and CTEs**: Combine data from multiple tables to calculate the total spending of customers and identify the top 10 spenders.
2. **Window Functions for Ranking**: Use window functions to rank products based on total sales and identify top-selling products.
3. **Indexing and Performance Optimization**: Optimize query performance by creating indexes on frequently queried columns and comparing execution times.

The project deliverables include SQL queries, a Jupyter Notebook with code and results, and a PDF report summarizing the findings.

## Repository Structure
- **Analysis_chinook_database.ipynb**: Jupyter Notebook containing the SQL queries, Python code, and analysis results.
- **results.pdf**: PDF report with screenshots of query results for all requirements.
- **Chinook_Sqlite.sqlite**: The Chinook database file (not included in the repository; download from [here](https://github.com/lerocha/chinook-database)).
- **README.md**: This file, providing an overview of the project.

## Tools and Technologies
- **SQLite**: The database management system used for storing and querying the Chinook database.
- **Python**:
  - **sqlite3**: Python library for interacting with the SQLite database.
  - **pandas**: Used for handling and displaying query results in DataFrames.
  - **time**: Used to measure query execution times for performance comparison.
- **Jupyter Notebook**: For writing and executing SQL queries and Python code, and for documenting the analysis process.

## Requirements and Implementation

### Requirement 1: Complex Joins and CTEs
**Objective**: Calculate the total amount spent by each customer and identify the top 10 spenders using INNER JOIN, LEFT JOIN, and a CTE.

- **Implementation**:
  - Used INNER JOIN to connect the `Customer` and `Invoice` tables, and LEFT JOIN to include `InvoiceLine` data.
  - Created a CTE (`CustomerTotalSpending`) to compute the total spending (`UnitPrice * Quantity`) for each customer.
  - Sorted results by total spending in descending order and limited to the top 10 customers.
- **Results**:
  - Top spender: Helena Holý with $49.62.
  - The query successfully retrieved customer IDs, names, and total spending amounts.
  - Results are displayed in the Jupyter Notebook and included in `results.pdf`.

### Requirement 2: Window Functions for Ranking
**Objective**: Rank products by total sales using window functions and identify the top-selling products.

- **Implementation**:
  - Used INNER JOIN to combine the `InvoiceLine` and `Track` tables.
  - Calculated total sales (`SUM(il.Quantity)`) for each product and used the `RANK()` window function to assign ranks based on sales.
  - Limited results to the top 10 products by sales rank.
- **Results**:
  - Top product: "The Trooper" with 5 units sold (Rank 1).
  - Multiple products tied for Rank 2 with 4 units sold (e.g., "Untitled", "The Number Of The Beast").
  - Results are displayed in the Jupyter Notebook and included in `results.pdf`.

### Requirement 3: Indexing and Performance Optimization
**Objective**: Optimize a query listing total sales per customer by creating an index on the `CustomerId` column in the `Invoice` table and comparing performance.

- **Implementation**:
  - Executed a query to calculate total sales per customer without indexing and measured execution time.
  - Created an index (`idx_invoice_customerid`) on the `CustomerId` column in the `Invoice` table.
  - Re-executed the same query and measured execution time with the index.
  - Compared execution times to evaluate performance improvement.
- **Results**:
  - Execution time without indexing: 0.013862 seconds.
  - Execution time with indexing: 0.009097 seconds.
  - The index reduced query execution time by approximately 34%, demonstrating significant performance improvement.
  - Results are displayed in the Jupyter Notebook and partially in `results.pdf` (note: the PDF appears incomplete for this section).

## Conclusions
- **SQL Proficiency**: The project successfully demonstrated the use of advanced SQL techniques, including complex joins, CTEs, window functions, and indexing, to analyze the Chinook database.
- **Performance Optimization**: Indexing the `CustomerId` column significantly improved query performance, highlighting the importance of indexes for frequently queried columns.
- **Data Insights**:
  - The top customers by spending provide insights into high-value clients for potential targeted marketing.
  - The product sales rankings identify popular tracks, which could inform inventory or promotional strategies.
- **Challenges**:
  - Ensuring correct JOIN types (INNER vs. LEFT) was critical to avoid missing data in Requirement 1.
- **Future Improvements**:
  - Add visualizations (e.g., bar charts) in the Jupyter Notebook to better present customer spending and product sales.
  - Explore additional indexing opportunities (e.g., on `InvoiceId` in `InvoiceLine`) to further optimize queries.
  - Fix the PDF generation process to ensure all tables are fully rendered.

## How to Run the Project
1. **Prerequisites**:
   - Install Python 3.11 or higher.
   - Install required Python packages:
     ```bash
     pip install pandas sqlite3
     ```
   - Download the Chinook database (`Chinook_Sqlite.sqlite`) from [here](https://github.com/lerocha/chinook-database) and place it in the project directory.
2. **Steps**:
   - Clone this repository:
     ```bash
     git clone <repository-url>
     ```
   - Open the `Analysis_chinook_database.ipynb` in Jupyter Notebook:
     ```bash
     jupyter notebook Analysis_chinook_database.ipynb
     ```
   - Run all cells to execute the SQL queries and view results.
   - Review `results.pdf` for a summary of query outputs.

## Acknowledgments
- The Chinook database is provided by [Luis Rocha](https://github.com/lerocha/chinook-database).
- This project was completed as part of a SQL and database analysis learning exercise.
