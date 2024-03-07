Se suele utilizar entornos virtuales donde las dependencias en python, pip  y lo demas se encuentra encapsulado. 

Para instalarlo seria `pip install virtualenv`

Para poder crear el espacio virtual seria `virtualenv venv`

Luego para iniciarlo ejecutar el `./venv/Scrips/activate`

En Pycharm se puede configurar el uso de ese entorno virtual , como dice este tutorial : ``Set-ExecutionPolicy RemoteSigned -Scope CurrentUser``


## Instalar django

Se instala con ``pip install django``
Para ver la version `django-admin --version`

## Crear proyecto Django
Para crearlo, en la carpeta virtual se hace `django-admin startproject NOMBRE_PROYECTO`

Si queremos no cree una nueva carpeta,  sino que coloque  los archivos en el mismo lugar donde se ejecuta el comando, se puede jacer lo siguiente:
`django-admin startproject NOMBRE:PROYECTO .`


##  Correr el primer proyecto
Dentro del archivo `manage.py` tenemos algunos comandos para operar con el proyecto. Uno es para correr el proyecto.

Correr el proyecto: `python ./manage.py runserver`
Se puede cambiar el puerto con: `python ./manage.py runserve PUERTO`

## Otros comandos
Se pueden ver con `python ./manage.py --help`


