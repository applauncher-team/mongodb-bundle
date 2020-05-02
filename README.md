# Installing
```
pip install mongodb_bundle
```

# Configuring
In config/config.yml just provide the influxdb server parameters
```
mongodb:
  uri: mongodb://localhost
```

# Using
Just inject MongoClient and use it!

```python
from pymongo import MongoClient
import inject

client = inject.instance(MongoClient)
client.my_database.my_collection.insert({"hello": "world"})

```
