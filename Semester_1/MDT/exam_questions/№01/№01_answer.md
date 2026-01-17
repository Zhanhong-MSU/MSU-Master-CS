# №01 Торговая система

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

### 1. Вывести список товаров, отсортированный по убыванию суммы продаж в штуках

```sql
SELECT 
    T1.ItemId,
    T1.Name,
    T1.Price,
    SUM(T3.Qty) AS TotalQty
FROM T1
LEFT JOIN T3 ON T1.ItemId = T3.ItemId
GROUP BY T1.ItemId, T1.Name, T1.Price
ORDER BY TotalQty DESC;
```

### 2. Вывести список заказов, где количество позиций (разных товаров) в заказе больше 5

```sql
SELECT
    T2.OrderId,
    T2.Dt
    COUNT(DISTINCT t3.ItemId) AS CountQty
FROM T2
JOIN T3 ON T2.OrderId = T3.OrderId
GROUP BY T2.OrderId, T2.dt
HAVING CountQty > 5
ORDER BY T2.OrderId


```

### 3. Вывести список суммарной стоимости заказов (выручка = Σ Qty × Price) для часовых интервалов в течение одних суток (распределение выручки по часам)

```sql
SELECT
    DATEPART(hour, T2.Dt) AS HourTime,
    SUM(T3.Qty * T1.price) AS TotalRevenue
FROM T2
INNER JOIN 
    T3 ON T3.OrderId = T2.OrderId
GROUP BY 
    DATEPART(hour, T2.Dt)
ORDER BY 
    HourTime ASC;

```