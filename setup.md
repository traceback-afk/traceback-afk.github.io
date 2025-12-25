# Project Setup


### requirements.txt
```txt
Django
django-ninja
```

### app/api.py
```python
from ninja import NinjaAPI
from core.api import router as core_router


api = NinjaAPI(version="v0.1", urls_namespace="api")


api.add_router("/core/", core_router)
```

### app/urls.py
```python
from django.contrib import admin
from django.urls import path
from .api import api

urlpatterns = [
    path("admin/", admin.site.urls), 
    path("api/", api.urls)
]
```

### core/api.py
```python
from ninja import Router

router = Router(tags=["Core"])

@router.get("/health")
def health_check(request):
    """
    This endpoint is used to check if the app is fully started
    and accepting connections.
    """
    return 200, {"status": "ok"}

```
