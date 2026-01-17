# №10 Торговая система

Есть однотипные товары, они комплектуются в заказы, каждый заказ содержит один или несколько товаров в заданном количестве. Необходимо написать запросы (отчеты) по указанным ниже спецификациям.

## Схема БД (таблицы):

**Т1** - список товаров. Товары - однотипные (единицы измерения - одинаковые, штуки). Есть код товара, наименование и цена.

```sql
T1 (
    ItemId int primary key,
    Name varchar(80),
    Price decimal(5,2)
)
```

**Т2** - журнал заказов. Есть код заказа и время, когда он был отгружен. В таблице представлены данные для 24-х часового интервала.

```sql
T2 (
    OrderId int primary key,
    Dt datetime
)
```

**Т3** - заказы. Есть код заказа, код товара в заказе и его количество.

```sql
T3 (
    OrderId int,
    ItemId int,
    Qty int,
    primary key (OrderId, ItemId)
)
```

## Задачи:

### 1. Вывести список товаров, которые присутствуют ровно в двух заказах

```sql
SELECT 
    T1.ItemId,
    T1.Name,
    T1.Price,
    COUNT(DISTINCT T3.OrderId) AS OrderCount
FROM T1
LEFT JOIN T3 ON T1.ItemId = T3.ItemId
GROUP BY T1.ItemId, T1.Name, T1.Price
HAVING COUNT(DISTINCT T3.OrderId) = 2;
```

### 2. Вывести список заказов, где отсутствует самый дорогой из проданных товаров
```sql
SELECT
    T3.OrderId
FROM T3
JOIN T1 ON T3.ItemId = T1.ItemId
GROUP BY T3.OrderId
HAVING MAX(T1.Price) < (
    SELECT MAX(T1.Price) 
    FROM T3
    JOIN T1 ON T3.ItemId = T1.ItemId
);
```

```sql
SELECT
    DISTINCT T3.OrderId
FROM T3
WHERE T3.OrderId NOT IN (
    SELECT T3.OrderId
    FROM T3
    JOIN T1 ON T3.ItemId = T1.ItemId
    WHERE T1.Price = (
        SELECT MAX(Price) FROM T1
        JOIN T3 ON T1.ItemId = T3.ItemId
    )
);
```


### 3. Вывести среднюю стоимость для заказов (выручка = Σ Qty × Price), где сумма отгруженных товаров (в штуках) больше 6

```sql
SELECT
    AVG(OrderValue) AS AvgOrderValue
FROM (
    SELECT
        SUM(T3.Qty * T1.Price) AS OrderValue
    FROM T3
    JOIN T1 ON T3.ItemId = T1.ItemId
    GROUP BY T3.OrderId
    HAVING SUM(T3.Qty) > 6
) AS OrderValues;
```