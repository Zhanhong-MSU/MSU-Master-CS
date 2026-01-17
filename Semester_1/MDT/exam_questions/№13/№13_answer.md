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

### 1. Вывести список товаров, отсортированный по убыванию выручки (Qty*Price)

```sql
SELECT 
    T1.ItemId,
    T1.Name,
    T1.Price,
    SUM(T3.Qty * T1.Price) AS TotalRevenue
FROM T1
LEFT JOIN T3 ON T1.ItemId = T3.ItemId
GROUP BY T1.ItemId, T1.Name, T1.Price
ORDER BY TotalRevenue DESC;
```

### 2. Вывести список заказов, где сумма отгруженных товаров (в штуках) больше 10, а количество позиций (разных товаров) в заказе меньше 3
```sql
SELECT
    T3.OrderId,
    SUM(T3.Qty) AS TotalQty,
    COUNT(DISTINCT T3.ItemId) AS CountQty
FROM T3
GROUP BY T3.OrderId
HAVING SUM(T3.Qty) > 10 AND COUNT(DISTINCT T3.ItemId) < 3;
```

### 3. Вывести суммарную отгрузку (в штуках) для заказов, в которых нет товара с кодом (itemid) 127, а количество позиций (разных товаров) в заказе равно 5

```sql
SELECT
    T3.OrderId,
    SUM(T3.Qty) AS TotalQty,
    COUNT(DISTINCT T3.ItemId) AS CountQty
FROM T3 
GROUP BY T3.OrderId
HAVING 
    SUM(CASE WHEN T3.ItemId = 127 THEN 1 ELSE 0 END) = 0
    AND COUNT(DISTINCT T3.ItemId) = 5;
```

```sql
SELECT
    T3.OrderId,
    SUM(T3.Qty) AS TotalQty,
    COUNT(DISTINCT T3.ItemId) AS CountQty,
FROM T3 
GROUP BY T3.OrderId
HAVING 
    COUNT(CASE WHEN T3.ItemId = 127 THEN 1 ELSE NULL END) = 0
    AND COUNT(DISTINCT T3.ItemId) = 5;
```