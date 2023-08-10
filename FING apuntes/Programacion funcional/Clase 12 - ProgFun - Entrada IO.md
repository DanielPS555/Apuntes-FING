
- En haskell las funciones **no** tienen *efectos laterales*. Los resultados son puros

- Haskell introduce el tipo *(IO a)*, es una ventana al mundo real
	- Representa una *accion de entrada/salida*
	- Es un tipo un *tipo abstracto*, que tiene una interface con un *mini lengaje imperativo*
	- *separar lo puro de lo impuro*

La función *getLine* tiene el siguiente tipo: 
```
getLine :: IO String
```
	
Lee una lineal y la retorna como String

- Tenemos la notación *do-notation* 

Ejemplo: 
 ```
 prefijoIn :: String → IO String 
 prefijoIn str = do pre ← getLine 
 						return (pre ++ str)
 ```

- Eso sigue la regla del *off-side rule*, los componentes de un bloque *do* identados al mismo nivel. 
- Un bloque lo que define es una *secuencia* de acciones IO
- La operación $a \leftarrow getLine$ se le asigna a $a$ el resultado de evaluar $getLine$ si falla, todo falla. 
- Con el $return$ transformamos un valor puro en uno impuro.


Otra funcion es la *putStrLn* que inserta un texto en la salida. 
```
putStrLn :: String -> IO()
```

La funcion *main* consiste en una secuencia de acciones IO. Eso le da *comienzo al programa.* 
```
 main :: IO ()
```

**Importante** Se pueden uitulizar if y else dentro de un bloque do-notation, pero si dentro hay mas de una linea, entonces hay que abrir con *do*

```
	getInts = do i ← getInt 
				 if i == 0 
					 then return [ ] 
					 else do is ← getInts 
							 return (i : is)
```

El uso de *let* es para declarar variables *puras* dentro de un bloque *do-notation*

### Ejemplo de uso de evaluación perezosa 
![[Pasted image 20230613220650.png]]


### Manejo de archivos
Algunas un tipo que es : 

```
type FilePath = String
```

```
readFile :: FilePath → IO String 
writeFile :: FilePath → String → IO () 
appendFile :: FilePath → String → IO ()
```


### Variables mutable (Data.IORef)
Aca se pueden crear variables *mutables*, a las cuales le podemos cambiar el valor, las funciones parta hacer esto son: 

```
newIORef :: a → IO (IORef a) 
readIORef :: IORef a → IO a 
writeIORef :: IORef a → a → IO () 
modifyIORef :: IORef a → (a → a) → IO ()
```

Un ejemplo es: 

```
main = do v ← newIORef 10 
		  modifyIORef v (+5) 
		  x ← readIORef v 
		  print x
```
