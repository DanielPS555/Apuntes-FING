
Dentro de una aplicacion, se pueen crear modelos, estos modelos se crean dentro del archivo ``models.py``

Un ejemplo basico seria:

```python
from django.db import models  
  
  
class Project(models.Model):  
name = models.CharField(max_length=200)
```

Para que las migraciones noten el cambio hay que garantizar que en `settings.py`, en particular en la lista `INSTALLED_APPS` se encuentre nuestra aplicacion. 