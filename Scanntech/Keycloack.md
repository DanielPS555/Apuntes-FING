 
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