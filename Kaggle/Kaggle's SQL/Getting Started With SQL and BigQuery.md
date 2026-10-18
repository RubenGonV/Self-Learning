```table-of-contents
maxLevel:1
```
---
# Introducción a BigQuery y SQL

SQL es el lenguaje estándar para trabajar con bases de datos, y BigQuery permite usarlo en datasets enormes desde la nube. En esta lección se aprende cómo conectarse, explorar datasets públicos y entender sus estructuras.

## 🚀 Primeros pasos con BigQuery

1. **Importar la librería**
```python
from google.cloud import bigquery
```

2. **Crear un cliente**
```python
client = bigquery.Client()
```

Este objeto será la interfaz para consultar BigQuery.


## Client, project, dataset, table

![[Pasted image 20251125181409.png]]

Ejemplo con el dataset **hacker_news** dentro del proyecto público `bigquery-public-data`.

- Referenciar el dataset:
```python
dataset_ref = client.dataset("hacker_news", project="bigquery-public-data")
dataset = client.get_dataset(dataset_ref)
```

- Listar tablas disponibles:
```python
# list of references
tables = list(client.list_tables(dataset))

# or, if you want to print
list_of_tables = [table.table_id for table in list(client.list_tables(dataset))] 
print(list_of_tables)
```

- Obtener una tabla específica:
```python
table_ref = dataset_ref.table("full")
table = client.get_table(table_ref)
```


---

## Table schema

Cada columna tiene metadatos como:
- nombre
- tipo (`STRING`, `INTEGER`, `BOOLEAN`, etc.)
- si acepta `NULL`
- descripción

```python
# Print information on all the columns 
table.schema
```

Ejemplo de un campo (`SchemaField`): 

```
SchemaField('by', 'STRING', 'NULLABLE', "The username of the item's author.")
```

##  Vista previa de datos

- Ver primeras 5 filas:
```python
client.list_rows(table, max_results=5).to_dataframe()
```

- Ver valores de una columna específica:
```python
client.list_rows(table, selected_fields=table.schema[:1], max_results=5).to_dataframe()
```

---

# Primeras consultas SQL

Ya sabes cómo acceder a BigQuery. Ahora toca hacer lo interesante: sacar información con **SQL** sin morir entre millones de filas.

## Conceptos básicos: SELECT, FROM

Una consulta SQL mínima sigue esta estructura:

```sql
SELECT columna
FROM `proyecto.dataset.tabla`
````

- Usas **SELECT** para elegir columnas.
- Usas **FROM** para indicar la tabla.
- 👀: Las tablas van entre **backticks** (\`), no comillas normales.

El campo **FROM** puede resultar un poco complicado hasta que te acostumbras a él. 
El formato es el siguiente:
- Un backtick (el símbolo \`).
- El nombre del proyecto
- Un punto.
- El nombre del conjunto de datos
- Un punto.
- El nombre de la tabla
- Un backtick (el símbolo \`).

---
## Filtrar con WHERE

Si quieres solo algunas filas, añade `WHERE`.

Ejemplo:

```sql
SELECT Name
FROM `bigquery-public-data.pet_records.pets`
WHERE Animal = 'Cat'
```

Esto devuelve solo los nombres donde el animal es un gato. 

## LIKE

Una cláusula `WHERE` puede limitar los resultados a filas con un texto determinado utilizando la función `LIKE`. 

También puede utilizar `%` como «comodín» para cualquier número de caracteres:
```sql
SELECT *
FROM `bigquery-public-data.pet_records.pets`
WHERE Name LIKE '%ipl%'
```
## Seleccionar más columnas

- Varias columnas:
```sql
SELECT city, country
FROM `bigquery-public-data.openaq.global_air_quality`
```

- Todas las columnas:
```sql
SELECT *
FROM `bigquery-public-data.openaq.global_air_quality`
```

## 💰 Cuida tu cuota

Cada usuario tiene **5TB al mes gratis**. Puede parecer infinito… hasta que ejecutas dos consultas mal hechas.

Puedes:
-  **Estimar el coste antes**
```python
dry_run_config = bigquery.QueryJobConfig(dry_run=True)
job = client.query(query, job_config=dry_run_config)
print(job.total_bytes_processed)
```

- **Limitar el tamaño permitido**
```python
limit = bigquery.QueryJobConfig(maximum_bytes_billed=1_000_000)
job = client.query(query, job_config=limit)
# print(job.to_dataframe().head())
```

Si la consulta excede el límite → BigQuery la cancela y te salva de arruinarte.

---

# GROUP BY, HAVING and COUNT()

## Agregaciones: COUNT, SUM, AVG, MIN, MAX

`COUNT()` devuelve cuántas filas hay. Es una **función de agregación**: toma muchas filas y devuelve un solo valor.

Ejemplo:

```sql
SELECT COUNT(ID)
FROM `dataset.pets`
````

Otros ejemplos de agregaciones:

| Función | Qué hace     |
| ------- | ------------ |
| `SUM()` | Suma valores |
| `AVG()` | Promedio     |
| `MIN()` | Mínimo       |
| `MAX()` | Máximo       |

## GROUP BY

Sirve para **agrupar filas con un mismo valor** y aplicar funciones como `COUNT()` a cada grupo.

Ejemplo: contar cuántos animales hay por tipo:
```sql
SELECT Animal, COUNT(ID)
FROM `dataset.pets`
GROUP BY Animal
```

## GROUP BY + HAVING

`HAVING` filtra **grupos**, no filas individuales. Es como un `WHERE`, pero aplicado después del agrupamiento.

Ejemplo: solo mostrar tipos de animales con más de 1 registro:

```sql
SELECT Animal, COUNT(ID)
FROM `dataset.pets`
GROUP BY Animal
HAVING COUNT(ID) > 1
```

## Alias (AS)

Los nombres automáticos tipo `f0__` son feos. Arregla eso con `AS`.

```sql
SELECT parent, COUNT(1) AS NumPosts
FROM `bigquery-public-data.hacker_news.full`
GROUP BY parent
HAVING COUNT(1) > 10
```

Mucho más legible.

> Tip: Usa `COUNT(1)` si no sabes qué columna contar.

---

## Regla importante del GROUP BY

Si usas `GROUP BY`, **todas las columnas del SELECT deben estar:**
* en el `GROUP BY`, **o**
* dentro de una función de agregación.

Ejemplo válido:

```sql
SELECT parent, COUNT(id)
FROM table
GROUP BY parent
```

Ejemplo NO válido:

```sql
SELECT parent, `by`, COUNT(id)
FROM table
GROUP BY parent
```

Porque `by` no está ni agrupado ni agregado.

Es posible que observes que la columna `by` de esta consulta está rodeada de comillas invertidas. Esto se debe a que BY es una palabra clave reservada que se utiliza en cláusulas como GROUP BY.

---
# ORDER BY

## ORDER BY

Sirve para **ordenar** los resultados de una consulta. Se coloca al final del `SELECT`.

Ejemplos:
- Orden ascendente (por defecto):
```sql
  SELECT * FROM pets ORDER BY ID;
```

- Orden alfabético:
```sql
SELECT * FROM pets ORDER BY Animal;
```

- Orden descendente:
```sql
SELECT * FROM pets ORDER BY Animal DESC;
```

## Fechas en BigQuery: DATE, DATETIME

Hay dos formatos comunes:

| Tipo       | Incluye      |
| ---------- | ------------ |
| `DATE`     | YYYY-MM-DD   |
| `DATETIME` | Fecha + hora |

## EXTRACT()

Permite obtener partes específicas de una fecha.

Ejemplos:

```sql
SELECT EXTRACT(DAY FROM Date) FROM pets_with_date;
SELECT EXTRACT(WEEK FROM Date) FROM pets_with_date;
```

Funciona con valores `DATE` o `DATETIME`.


---


Un **CTE** es una tabla temporal dentro de una consulta.  
Solo existe durante esa consulta y hace el código más legible.

Estructura general:

```sql
WITH nombre_temporal AS (
    SELECT ...
    FROM ...
    WHERE ...
)
SELECT *
FROM nombre_temporal;
```

Ventajas:

- Divide una consulta grande en etapas lógicas.
- Evita repetir código.
- Más legibilidad, menos dolor existencial.

## Ejemplo real: transacciones de Bitcoin por fecha

Objetivo: contar cuántas transacciones hubo cada día. 

Se convierte un `DATETIME` a `DATE`, se usa un CTE y luego se agrupa.

```sql
WITH time AS (
    SELECT DATE(block_timestamp) AS trans_date
    FROM `bigquery-public-data.crypto_bitcoin.transactions`
)
SELECT COUNT(1) AS transactions,
       trans_date
FROM time
GROUP BY trans_date
ORDER BY trans_date;
```

---
# JOIN: Joining Data
Combine data sources. Critical for almost all real-world data problems


To get information that applies to a certain pet, we match the `ID` column in the `pets` table to the `Pet_ID` column in the `owners` table.
![[Pasted image 20251203125615.png]]

Using **JOIN**, we can write a query to create a table with just two columns: the name of the pet and the name of the owner.
```sql
SELECT p.Name AS Pet_Name, o.Name AS Owner_Name
FROM `bigquery-public-data.pet_records.pets` AS p
INNER JOIN `bigquery-public-data.pet_records.owners` AS o
	ON p.ID = o.Pet_ID
```

We combine information from both tables by matching rows where the `ID` column in the `pets` table matches the `Pet_ID` column in the `owners` table.

In the query, **ON** determines which column in each table to use to combine the tables. Notice that since the `ID` column exists in both tables, we have to clarify which one to use. We use `p.ID` to refer to the `ID` column from the `pets` table, and `o.Pet_ID` refers to the `Pet_ID` column from the `owners` table.

> In general, when you're joining tables, it's a good habit to specify which table each of your columns comes from. That way, you don't have to pull up the schema every time you go back to read the query.

## INNER JOIN

The type of **JOIN** we're using today is called an **INNER JOIN**. That means that a row will only be put in the final output table if the value in the columns you're using to combine them shows up in both the tables you're joining. 

For example, if Tom's ID number of 4 didn't exist in the `pets` table, we would only get 3 rows back from this query. There are other types of **JOIN**, but an **INNER JOIN** is very widely used, so it's a good one to start with.

## Example

Write a new query that has a single row for each user who answered at least one question with a tag that includes the string "bigquery". Your results should have two columns:

- `user_id` - contains the `owner_user_id` column from the `posts_answers` table
- `number_of_answers` - contains the number of answers the user has written to "bigquery"-related questions

```python
# Your code here
bigquery_experts_query = """
        WITH answers AS(
            WITH q AS (
                SELECT id
                FROM `bigquery-public-data.stackoverflow.posts_questions` 
                WHERE tags LIKE '%bigquery%'
            )
            SELECT a.id, body, owner_user_id
            FROM q
            INNER JOIN `bigquery-public-data.stackoverflow.posts_answers` as a
                ON a.parent_id = q.id
        )
        SELECT owner_user_id AS user_id, COUNT(1) AS number_of_answers
        FROM answers
        GROUP BY user_id
        """

# Set up the query
safe_config = bigquery.QueryJobConfig(maximum_bytes_billed=10**10)
bigquery_experts_query_job = client.query(bigquery_experts_query, job_config=safe_config) # Your code goes here

# API request - run the query, and return a pandas DataFrame
bigquery_experts_results = bigquery_experts_query_job.to_dataframe() # Your code goes here

# Preview results
print(bigquery_experts_results.head())
```

---
