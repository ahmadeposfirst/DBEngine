# DBEngine is a CURD wrapper for SQLAlchemy

By using this wrapper one can easily implement all 
curd operations by simply passing the SQL queries on Data Modals,
In insert you need to pass a dictionary of column names as keys and 
their value to insert as value of dictionary.

# Usage

Initializing the DBEngine
```engine = DBEngine()```

Note: This instance should only be created once and after that you can access the engine functionalioty by using ```_engine``` object of ```DBEngine```

For example using DBEngine to insert values
```
	#insert query
    flag = DBEngine._engine.insert(
        [
            {
                'id': 1, 
                'desc': 'desc of item', 
                'status': 'not updated'
            },
            {
                'id': 2, 
                'desc': 'desc of item', 
                'status': 'not updated'
            },
            {
                'id': 3, 
                'desc': 'desc of item', 
                'status': 'not updated'
            }
        ], 
        'tsettable'
    )
```

Similary for the select query
```
    #select query
    data = DBEngine._engine.select(
        {
            'tablename': 'tsettable',
            'query': 'select * from tsettable'
        }
    )
```

As you can see it's barely an abstraction of an ORM. For the update query
```
    #update query
    DBEngine._engine.set(
        {
            'tablename': 'name',
            'cond': 'OR',
            'new_values':{
                'colname0': 'new_value0',
                'colname1': 'new_value1',
                'colname3': 'new_value3',
                'colname2': 'new_value2'
            },
            'where':{
                'colname1': 'value22',
                'colname2': 'value33',
                'colname3': 'value44'
            }
        }
    )
```

And finally for delete query use it as
```
    #delete query    
    DBEngine._engine.delete(
        {
            'tablename': 'tsettable',
            'query': 'DELETE from tsettable where id=1'
        }
    )
``` 

Note: DBEngine uses logger.py to log for system operations.
