# Bulk Insert
utilizes bash
```
for counter in {1..10000}; do echo "INSERT INTO table_name (column1, column2, column3) VALUES ($counter, \"12345\", \"someValue\");"; done | mysql --database=db_name
```
