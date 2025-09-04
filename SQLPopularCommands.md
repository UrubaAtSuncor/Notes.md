## SQL Commands I Might Need Later

Organizations often need to create aggregate functions for measures like averages, counts, maximums, and minimums. For example, if your business needs to answer questions about total weekly sales, you could create a materialized view called weekly_sales that preaggregates this data so analysts and others don't need to recreate frequently used materialized views.

CREATE OR REPLACE MATERIALIZED VIEW weekly_sales AS
SELECT week,
       prod_id,
       region,
       SUM(units) AS total_units,
       SUM(units * rate) AS total_sales
FROM orders
GROUP BY week, prod_id, region
