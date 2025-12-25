# CRUD
create read update delete


### schemas.py
```python
from ninja import Schema
from datetime import datetime

class BookIn(Schema):
    name: str
    author: str

class BookOut(Schema):
    id: int
    name: str
    author: str
    created_at: datetime
    updated_at: datetime
```

### ModelSchema
```python
from ninja import ModelSchema

class BookInSchema(ModelSchema):
    class Meta:
        model = Book
        fields = ["name", "author"]
        
class BookOutSchema(ModelSchema):
    class Meta:
        model = Book
        fields = ["id", "name", "author", "created_at", "updated_at"]
```

### api.py
```python
from ninja import NinjaAPI
from django.shortcuts import get_object_or_404
from .models import Book
from .schemas import BookIn, BookOut

api = NinjaAPI()

@api.post("/books", response=BookOut)
def create_book(request, data: BookIn):
    book = Book.objects.create(**data.dict())
    return book

@api.get("/books", response=list[BookOut])
def list_books(request):
    return Book.objects.all()

@api.get("/books/{book_id}", response=BookOut)
def get_book(request, book_id: int):
    return get_object_or_404(Book, id=book_id)

@api.put("/books/{book_id}", response=BookOut)
def update_book(request, book_id: int, data: BookIn):
    book = get_object_or_404(Book, id=book_id)
    for attr, value in data.dict().items():
        setattr(book, attr, value)
    book.save()
    return book

@api.delete("/books/{book_id}")
def delete_book(request, book_id: int):
    book = get_object_or_404(Book, id=book_id)
    book.delete()
    return {"success": True}
```

### get_object_or_404

```python
from ninja.errors import HttpError
from .models import Book

@api.get("/books/{book_id}")
def get_book(request, book_id: int):
    try:
        return Book.objects.get(id=book_id)
    except Book.DoesNotExist:
        raise HttpError(404, "Book not found")

```