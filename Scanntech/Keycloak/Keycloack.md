 
CAP-452- Modificar el KeycloakCoreSvc para que le pege a la api nueva

- LoginWebContoller (proyecto: be-apis-login)


 
CAP-452
Usar la bibloteca RestTemplate, 
La API es 1.  [https://test-be-minoristas.scanntech.com/be-wrapper-keycloak/swagger-ui/index.html](https://test-be-minoristas.scanntech.com/be-wrapper-keycloak/swagger-ui/index.html "https://test-be-minoristas.scanntech.com/be-wrapper-keycloak/swagger-ui/index.html")



APi keyckoce : 1.  [https://sso-dev.scanntech.com/auth/admin/analytics/console/#/realms/analytics](https://sso-dev.scanntech.com/auth/admin/analytics/console/#/realms/analytics "https://sso-dev.scanntech.com/auth/admin/analytics/console/#/realms/analytics")

Los clientes que tiene el rol BE-TEST-WRAPPER

EL cliente solo puede consultar usuarios que comprata algumentos un rol. EN este caso BE-FUNCIONARIO. 
Hay que añadir los usuarios al grupo (en testing) al grupo `be-test-group`. El cual les da autometicamente el grupo 
Vamos a tener que tener en el property a cual grupo vamos a añadir el usuario. Lo que importa es el ID. 



DUDAS: 
- Cual es la diferencia entre /login y /funcionarios/{username}/iniciar-validacion



#### Usuario creado: 
##### Request
```json
{
  "id": null,
  "email": "dpadron2@scanntech.com",
  "password": "123",
  "nombre": "Daniel2",
  "apellido": "Padron2"
}
```

###### Headers
```json 
1.  accept:application/json
    
2.  Accept-Encoding:gzip, deflate, br
    
3.  Accept-Language:es-419,es;q=0.9
    
4.  Authorization: Bearer TOKEN
    
5.  Connection:keep-alive
    
6.  Content-Length:122
    
7.  Content-Type:application/json
    
8.  Cookie:_ga=GA1.2.608089024.1675186245; _gcl_au=1.1.1044306467.1675186245
    
9.  Host:test-be-minoristas.scanntech.com
    
10.  Origin: https://test-be-minoristas.scanntech.com
    
11.  Referer: https://test-be-minoristas.scanntech.com/be-wrapper-keycloak/swagger-ui/index.html
    
12.  sec-ch-ua: "Not?A_Brand";v="8", "Chromium";v="108", "Google Chrome";v="108"
    
13.  sec-ch-ua-mobile:?0
    
14.  sec-ch-ua-platform:"Linux"
    
15.  Sec-Fetch-Dest: empty
    
16.  Sec-Fetch-Mode: cors
    
17.  Sec-Fetch-Site:same-origin
    
18.  User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36
```

##### Responce
```json
{
  "id": "e4527879-58bf-4aec-b2dd-5096dffaea28",
  "email": "dpadron2@scanntech.com",
  "password": "123",
  "nombre": "Daniel2",
  "apellido": "Padron2"
}
```

