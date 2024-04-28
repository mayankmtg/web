
---

## Singleton design pattern

There are cases where we require a single instance of an object but we don't want that to be assigned until it is actuall invoked

So for example we need a global variable, which needs to be used everywhere in that file

There are 2 ways of achieving this:

### Assigning it at the import level

```python
mongodb_connector = Mongo()
```

### Using singleton (more elegant and useful while writing unit tests)

```python
mongodb_connector = None

def get_mongodb_connector():
    global mongodb_connector
    if mongodb_connector is None:
        mongodb_connector = Mongo()
    return mongodb_connector
```

With this, wherever we want to use `mongodb_connector.<something>`, we can use `get_mongodb_connector().<something>`

---
