Por defecto en un proyecto DJANGO no tenemos aplicaciones, el proyecto es un gran contenedor vacio.  

Se pueden ir agrupando funcionalidades en distintas apps.


#### Crear app
Para crear una App se utiliza el siguiente comando
```
	python manager.py startapp NOMBRE_APP
```


#### Simple hello world
Se puede añadir en el archivo `views.py` de la app algunas funciones que haran de view. 

Por ejemplo:

```python
from django.http import HttpResponse  
  
def helloWorld(request):  
return HttpResponse("<h1>Hello world S</h1>")  
  
def abour(request):  
return HttpResponse("About")
```

Luego en la carpeta del *proyecto* (no la app) , tenemos el archivo `urls.py` el cual adentro tenemos la lista `urlpatterns` donde podemos añadir las url y quien responde ante ella:

```python
from django.contrib import admin  
from django.urls import path  
from myapp import views  
  
urlpatterns = [  
path('admin/', admin.site.urls),  
path('', views.helloWorld),  
path('about/', views.abour)  
]
```

#### Delegar manejo de URLS a las Apps
Para no sobrecargar el archivo urls.py del proyecto, se puede hacer que cada app maneje su propias urls..

Para ello creamos el archivo ``urls.py`` dentro de la app

Ahi adentro va lo siguiente:

```python
from django.urls import path  
  
from . import views  
  
urlpatterns = [  
path('', views.helloWorld),  
path('about/', views.about)  
]
```

Y tambien hay que añadir el `include` en la urlpatterns del `url.py` del proyecto. 

Notar que para eso, dentro del metodo `path` se puede añadir un prefijo para las url de esta app.

``` python
from django.contrib import admin  
from django.urls import path, include  
  
urlpatterns = [  
path('admin/', admin.site.urls),  
path('home/', include('myapp.urls'))  
]
```


## Añadir la App al proyecto

Hay que ir al archivo `settings.py` del proyecto y añadir en la lista de `INSTALLED_APPS` la nueva app. 