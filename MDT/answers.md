# P01
## 3.
```sql
SELECT
    DATEPART(hour, T2.Dt),
    SUM(T3.Qty * T1.price)
FROM T2
INNER JOIN 
    T3 on T3.OrderId = T2.OrderId
INNER JOIN 
    T1 on T1.ItemId = T3.ItemId
GROUP BY 
    DATEPART(hour, T2.Dt)
ORDER BY 
    DATEPART(hour, T2.Dt)

```