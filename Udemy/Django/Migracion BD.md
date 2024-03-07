Django administra la BD

Para generar las migraciones se hace con el comando, esto se hace luego de los cambios en los modelos. 

```
python manage.py makemigrations
```

Luego para impactarlos en la BD se realiza con:

```
python manager.py migrate
```


## Shell
La idea es no tocar la BD a mano, sino por medio de un shell

Para ello se invoca al shell de la siguiente forma: `python manager.py shell`

Algunos comandos:
- `from myapp.models import Project, Task` aqui importamos lo modelos a utilizar en las siguientes consultas.
- `p = Project(name = "aplication movil")`: Se crea un nuevo proyecto con ese  nombre.  Se lo almacena en `p`
- `p.save`: Guarda la instancia p en la BBDD
- `Proyect.object.all()` Nos devuelve todos los elementos
- `Proyect.object.get(id=1)` Nos debuelve todos los Proyect que tiene como id = 1
- `Proyect.object.get(name = "ALGO")` Nos debuelve todos los Proyect que tiene como name = "ALGO". *Si no devuelve nada explota*
- `p.task_set.all()` Dado un proyect p, nos debuelve el set de tareas en forma de task_set, y en particular todas con .all().
- `p.task_set.create(title="Descargar IDE")` Eso hace que se cree una task para un proyecto p.
- `p.task_set.filter(name == "abs)"` filtra todos los que tiene name == abs, s*i falla debuelbe lista vacia*
- `p.task_set.filter(name__startswitch == "abs)"` filta todos los que *comienzan* con "abs"