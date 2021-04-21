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
from applauncher import ServiceContainer
client = ServiceContainer.mongodb.mongo_client()
client.my_database.my_collection.insert({"hello": "world"})
```

Or you can inject it as a dependency of a service 

```python
from pymongo import MongoClient
from dependency_injector import containers, providers
from mongodb_bundle import MongoDBContainer
from applauncher import ServiceContainer

class ApiClient:
    def __init__(self, mongo_client: MongoClient):
        self.client = mongo_client
    def laugh(self):
        return self.client.db.col.insert_one({"jaja": "jeje"})


class MyContainer(containers.DeclarativeContainer):
    api_client = providers.Factory(ApiClient, mongo_client=MongoDBContainer.mongo_client)
```