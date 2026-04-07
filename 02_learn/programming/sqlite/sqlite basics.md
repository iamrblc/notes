# Import

```python
import sqlite3 as sql
```

# Connector and cursor
Connector is needed to connect to the database.

```python
# If working from a file
con = sql.connect('databasename.db')
# If working in memory
con = sql.connect(":memory:")
```

We also need a cursor. This is what will execute stuff. 

```python
c = con.cursor()
```

# Create a table
```python
c.execute("""CREATE TABLE data (
			first text,
			last text,
			pay integer
)""")
con.commit()
con.close( )
```