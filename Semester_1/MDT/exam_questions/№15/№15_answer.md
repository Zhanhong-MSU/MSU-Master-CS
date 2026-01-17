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

### 1. Вывести список товаров, отсортированный по возрастанию количества заказов с ними

```sql
SELECT 
    T1.ItemId,
    T1.Name,
    T1.Price,
    COUNT(DISTINCT T3.OrderId) AS OrderCount    
FROM T1
LEFT JOIN T3 ON T1.ItemId = T3.ItemId
GROUP BY T1.ItemId, T1.Name, T1.Price
ORDER BY OrderCount ASC;
```

### 2. Вывести список заказов, где есть сумма отгруженного (в штуках) меньше 3
```sql
SELECT
    T2.Dt,
    T3.OrderId,
    SUM(T3.Qty) AS TotalQty
FROM T3
INNER JOIN T2 ON T3.OrderId = T2.OrderId
GROUP BY T3.OrderId, T2.Dt
HAVING SUM(T3.Qty) < 3;
```


### 3. Вывести среднюю стоимость заказов (выручка = Σ Qty × Price), где количествопозиций (разных товаров) меньше 3

```sql
SELECT
    AVG(OrderValue) AS AvgOrderValue
FROM (
    SELECT
        SUM(T3.Qty * T1.Price) AS OrderValue
    FROM T3
    JOIN T1 ON T3.ItemId = T1.ItemId
    GROUP BY T3.OrderId
    HAVING COUNT(DISTINCT T3.ItemId) < 3
) AS OrderValues;
```