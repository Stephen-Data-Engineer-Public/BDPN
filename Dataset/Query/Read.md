## Insert a blacklisted customer with no ID​
Insert a record into the customers table where the customer_id is NULL and the blacklisted flag is set to
TRUE.​

## Find percentage of free deliveries per customer​
For each customer, calculate the percentage of their orders that were delivered for free.​
Assume free delivery applies when the order total is at least $150.​

## List pending deliveries (excluding blacklisted customers)​
The result should include: order_id, customer_address, & carrier​
Find the second highest purchase per customer​

## For each customer, return the order with the second highest total_amount.​
If a customer has fewer than 2 orders, exclude them.

```sql
WITH CTE AS (

SELECT O.[order_id]
      ,O.[store_location]
      ,O.[customer_id]
      ,O.[order_date]
      ,O.[total_amount]
      ,O.[payment_method], 
	   D.[delivery_id]
      ,D.[order_id] AS [order_id_D]
      ,D.[customer_id] AS [customer_id_D]
      ,D.[store_location] AS [store_location_D]
      ,D.[delivery_date]
      ,D.[status]
      ,D.[carrier],
		CASE WHEN	O.[total_amount] > 150 THEN 1 ELSE NULL END AS Order_qlf_free_Dl

FROM		[SCHOOL].[dbo].[orders] O
LEFT JOIN	[SCHOOL].[dbo].[deliveries] D		ON O.customer_id = D.customer_id
												AND O.store_location = D.store_location
												AND O.order_id = D.order_id
												AND D.status = 'Delivered'
)
SELECT [customer_id], CAST((COUNT(Order_qlf_free_Dl) * 100) / COUNT(*)AS DECIMAL(5,2)) AS perc_order
FROM CTE
GROUP BY [customer_id]
```

```sql
WITH CTE AS (
SELECT [order_id]
      ,[store_location]
      ,[customer_id]
      ,[order_date]
	  ,[total_amount]
      ,SUM([total_amount]) OVER (PARTITION BY NULL )   AS Total_All_location 
	  ,SUM([total_amount]) OVER (PARTITION BY [store_location] )  total_per_location
      ,[payment_method]
  FROM [orders]
)
SELECT *
FROM CTE

-- If you don't use partition for the Total_All_location you will have to use GROUP BY
```
