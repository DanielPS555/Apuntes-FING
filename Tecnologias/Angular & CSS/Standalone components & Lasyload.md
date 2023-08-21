Para generar una *standalone component* se puede hacer con el siguiente comando: 

```
ng g c NOMBRE --standalone
```

Es importante tambien añadir este componente en el `app-routing.modules.ts`

```js
const = routes : Routes = [
	{path: '', pathMatch : 'full' . redirectTo: 'list'},
	{path: 'list', components: NOMBRE_COMPONENTE}


]