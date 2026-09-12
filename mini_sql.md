# SQL Mini Analysis
---

- Data source : Bigquery Public Dataset
- Dataset : The look E-commerce

created by : Ignatia

## Analysis

### 1. Berapa Banyak Item yang Tercatat pada Database?

 **Syntax**

 ```sql
 SELECT
  COUNT(id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items;
```

**Output**

Terdapat sebanyak 181.589 item yang tercatat dalam transaksi di the look e-commerce

### 2. Apa Saja Top 3 Kategori Produk yang Tercatat?
**Syntax**

```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**
Tercatat Pembagian Kategori pada Database The Look Ecommerce sebagai berikut:
- Top 3 : Intimates (13.529), Jeans (12.595), Tops & Tees (11.946)
- Last 3 : Clothing Sets (220), Jumpsuits & Rompers (901), Suits (972)

### 3. Kategori Produk Apa yang Paling Banyak Terjual ?
**Syntax**

```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
WHERE
  oi.status = 'Complete'
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**
Terdapat 3 kategori produk yang paling banyak terjual sebagai berikut:
1. Intimates (3.396)
2. Jeans(3.073)
3. Fashion Hoodies & Sweatshirts (2.891)

### 4. Kategori Produk yang Paling Banyak Dibatalkan ?
**Syntax**

```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
WHERE
  oi.status = 'Cancelled'
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**
Tercatat 3 kategori produk yang paling banyak dibatalkan sebagai berikut:
1. Intimates (1,969)
2. Jeans (1.927)
3. Top & Tees (1.855)

### 5. Kategori Produk yang Paling Banyak Dikembalikan?
**Syntax**
```sql
SELECT
  p.category,
  COUNT(oi.id) AS jumlah_items
FROM
  bigquery-public-data.thelook_ecommerce.order_items AS oi
JOIN
  bigquery-public-data.thelook_ecommerce.products AS p
ON oi.product_id = p.id
WHERE
  oi.status = 'Returned'
GROUP BY p.category
ORDER BY jumlah_items DESC;
```

**Output**
Tercatat 3 kategori yang paling banyak dikembalikan adalah sebagai berikut:
1. Jeans (1.312)
2. Intimates (1.309)
3. Swim (1.192)











