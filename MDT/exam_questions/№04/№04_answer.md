# №04 Торговая система

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

### 1. Вывести список товаров, отсортированный по возрастанию количествазаказов с ними

```sql
SELECT 
    T1.ItemId,
    T1.Name,
    T1.Price,
    COUNT(DISTINCT T3.OrderId) AS TotalOrderCount
FROM T1
LEFT JOIN T3 ON T1.ItemId = T3.ItemId
GROUP BY T1.ItemId, T1.Name, T1.Price
ORDER BY TotalOrderCount ASC;
```

### 2. Вывести список заказов, где есть только одна позиция (один товар) в количестве не более двух штук

```sql
SELECT
    T3.OrderId,
    COUNT(T3.ItemId) AS ItemCount,
    MAX(T3.Qty) AS MaxQty
FROM T3
GROUP BY T3.OrderId
HAVING 
    COUNT(T3.ItemId) = 1
    AND MAX(T3.Qty) <= 2;
```

### 3. Вывести суммарную стоимость заказов (выручка = Σ Qty × Price), где количество позиций (разных товаров) в заказе больше 5

```sql
SELECT
    T3.OrderId,
    SUM(T3.Qty * T1.Price) AS TotalRevenue    
FROM T3
INNER JOIN T1 ON T3.ItemId = T1.ItemId
GROUP BY T3.OrderId
HAVING COUNT(DISTINCT T3.ItemId) > 5;
```