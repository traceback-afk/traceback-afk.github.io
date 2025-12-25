# Testing

```python
def test_ok_endpoint(self):
    response = client.get("/ok")
    self.assertEqual(response.status_code, 200)
    self.assertEqual(response.json(), {"detail": "ok"})
```

### tests/test_book_api.py
```python
from django.test import TestCase
from ninja.testing import TestClient
from book.api import router
from core.models import Book

class BookAPITest(TestCase):

    def setUp(self):
        self.client = TestClient(router)
        self.book = Book.objects.create(
            name="1984",
            author="George Orwell"
        )

    def test_create_book(self):
        response = self.client.post("/books", json={
            "name": "Dune",
            "author": "Frank Herbert"
        })
        self.assertEqual(response.status_code, 200)
        self.assertEqual(Book.objects.count(), 2)
        self.assertEqual(response.json()["name"], "Dune")

    def test_list_books(self):
        response = self.client.get("/books")
        self.assertEqual(response.status_code(), 200)
        self.assertEqual(len(response.json()), 1)

    def test_get_book(self):
        response = self.client.get(f"/books/{self.book.id}")
        self.assertEqual(response.status_code, 200)
        self.assertEqual(response.json()["name"], "1984")

    def test_get_book_not_found(self):
        response = self.client.get("/books/999")
        self.assertEqual(response.status_code, 404)

    def test_update_book(self):
        response = self.client.put(f"/books/{self.book.id}", json={
            "name": "Animal Farm",
            "author": "George Orwell"
        })
        self.assertEqual(response.status_code, 200)
        self.book.refresh_from_db()
        self.assertEqual(self.book.name, "Animal Farm")

    def test_delete_book(self):
        response = self.client.delete(f"/books/{self.book.id}")
        self.assertEqual(response.status_code, 200)
        self.assertEqual(Book.objects.count(), 0)

    def test_delete_book_not_found(self):
        response = self.client.delete("/books/999")
        self.assertEqual(response.status_code, 404)


```