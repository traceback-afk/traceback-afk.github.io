# Path parameters
[Docs](https://django-ninja.dev/guides/input/path-params/)

```python
@api.get("/items/{item_id}")
def read_item(request, item_id):
    return {"item_id": item_id}
```
```python
@api.get("/items/{item_id}")
def read_item(request, item_id: int):
    return {"item_id": item_id}
```

```python
@api.get("/items/{int:item_id}")
def read_item(request, item_id):
    return {"item_id": item_id}
```

```python
@api.get("/events/{year}/{month}/{day}")
def events(request, year: int, month: int, day: int):
    return {"date": [year, month, day]}
```

# Query parameters
[Docs](https://django-ninja.dev/guides/input/query-params/)
```python
@api.get("/weapons")
def list_weapons(request, limit: int = 10, offset: int = 0):
    return weapons[offset : offset + limit]
```
