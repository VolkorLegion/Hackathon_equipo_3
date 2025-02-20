# hackathon_equipo_3

### Integrantes 
- Laura
- Gabriel
- Julio
- Leonardo
- Diego 

**El Hackathon de QA organizado por TripleTen presenta un reto emocionante y complejo al colocar al equipo 3 en una situación desconocida. Los 5 integrantes del equipo: Gabriel, Laura, Julio, Leonardo y Diego entran en acción el día 5 de septiembre a las 07:00 PM hora de CDMX con una llamada en discord configurada por Diego, donde pasan a presentarse y exponen sus habilidades.**


**Se determinan los objetivos del reto tras analizar la documentación provista y se toma la decisión de iniciar con el aplicativo “Platzi Fake Store API” en conjunto con el aplicativo “Restful-Booker”.**

**Tras tener buenos avances en ambos campos, se inicia el proceso de organizar los datos obtenidos y determinar el estilo de entrega de la documentación, a su vez, se hace un avance sobre el tercer aplicativo “BugBank” a la vez que se continúan afinando detalles sobre la presentación y se diseñan los informes de errores en JIRA.**


## Documentación:
- Lista de comprobación.
- Clases de equivalencia y valores límite.
- Pruebas de API en POSTMAN.
- Documentación de errores en JIRA.


### Revisión de los aplicativos web bugbank, Platzi Fake Store API y resful-booker
#### Problemas encontrados
#### **Bugbank**
1. Al tocar el botón "cadastral" la aplicación no indica todos que todos los campos sean obligatorios, por lo que no indica que el texto "nome" es obligatorio
2. La aplicación permite volver a registrar un e-mail ya ingresado con anterioridad, por lo que este debe generar un error

#### **Platzi Fake Store API**
En este proyecto decidimos abordar la API "Platzi Fake Store", una API para una tienda en línea en una etapa temprana del desarrollo. Cuenta con la estructura básica con la que un administrador de la página puede agregar y modificar productos en las diferentes categorías que maneja la página. Asimismo, permite crear y administrar usuarios, asignando identificadores de usuario como lo son: nombre y avatar. De igual manera, cuenta con un sistema de autenticación rudimentario y una gestión de contraseñas.

En este punto se utiliza Postman para desarrollar los casos de prueba diseñados de manera exploratoria para comprender el funcionamiento de la API, al mismo tiempo que se buscan errores en las respuestas de la API a las solicitudes HTTP1.1 realizadas por el equipo.

Se utilizan las solicitudes GET, POST y PUT a medida que son requeridas para acceder a los datos registrados, crearlos y modificarlos.

Usuarios
En general el punto de Usuarios funciona bien, no existen muchas restricciones para los campos de creación de Usuarios, y las que existen funcionan como descrito en las respuestas de la API.

El error encontrado por estás pruebas exploratorias se encuentra en el endpoint /api/v1/users/is-available, el cuál confirma si un correo electrónico ya se encuentra registrado en la base de datos de la API. Con la solicitud, la API responde "false", si el correo no está disponible; esto significa que el correo ya está siendo utilizado por un perfil en la base de datos. Por el contrario, la respuesta "true" indica que el correo está disponible, o sea, no se encuentra en uso por ningún perfil en la base de datos.

En teoría se esperan respuestas 200 OK en ambas solicitudes, de estar planteadas de manera correcta, sin embargo, ambas devuelven una respuesta 201 CREATED. Más importante aún, al revisar la disponibilidad de un correo que no se ha introducido a la base de datos, la API responde con un "false".

Este error aparentemente no evita el funcionamiento del aplicativo, sin embargo, de no atenderse, podría degenerar en un error bloqueador al existir la posibilidad de que en una actualización futura la API no permita el registro de nuevos usuarios.

Si bien la severidad es media al momento, la prioridad deberá de ser alta, por el riesgo que presenta un error de este tipo.

Seccion de categorias de API de tienda falsa de Platzi
"Se genero una lista de comprobacion para la seccion de categorias, ya que ayuda a organizar de manera eficiente las tareas a realizar divididos por segmento segun endpoint, el cual da el aplicativo web para realizar pruebas.

En este mismo se puede verificar el codigo de respuesta dado en caso de ser positivo o negativo y el resultado esperado segun cada punto de la lista.

Estos siendo divididos en metodos GET los cuales son el de obtener todas las categorias, en donde se hace una comparativa entre lo que aparece en postman y lo que aparece en la aplicación web siendo esta la visual del cliente.
Tambien esta el obtener una sola categoria y obtener los productos por categoria.

Estando el metodo POST el cual es el crear una categoria, validando si aparece el cambio en la aplicacion web.

Validando el metodo PUT El cual es el actualizar una categoria, haciendo validaciones similares al post 

Finalmente creando un metodo DELETE, para eliminar categorias, las cuales se puedan ver para saber si se ve el cambio dentro del aplicativo WEB

Con todo esto se genero como resultado el total de 22 bug encontrados y reportados, en el cual por medio de la implementación de las APIS nos arroja un resultado el cual no es visible en el aplicativo, generando así errores al momento de que el cliente vaya a revisar cada categoria."

Authentication, Files
Para la autenticacion y files se generaron casos de prueba con el proposito de comprobar los endpoints y que estos a su vez cumplan la con funcionalidad con la que estos fueron diseñados.
Para el corto tiempo con el que contamos, se tomo la decision de realizar prueba funcionales para que la funcionalidad del producto coincida con la forma en que fue diseñado.
De igual manera se trabajaron con pruebas positivas para garantizar que el producto de software cumple al menos con los requisitos clave del cliente.
Y con pruebas negativas que proporciona una garantía de funcionamiento estable del sistema, incluso en casos de condiciones inesperadas. 
La pruebas fueron en su mayoria fueron aprobadas, para "Files" se puede subir un archivo y obetener un archivo, los endpoints funcionan correctamente para lo que fueron diseñados.
Para "Autenticacion" se puede iniciar sesion, obetener el usuario con la autenticacion, sin embargo el unico endpoint que no cumple con su funcionalidad fue el de obtener un nuevo access token mediante el refresh token 
Por lo tanto se tomo la decision de poner como prioridad media los errores encontrados, ya que si bien no afecta a la funcionalidad de las API's son errores que deben ser corregidos.

Platzi Fake Store API - Categoría Producto y Filtrado
"El propósito de las pruebas es verificar la funcionalidad de los endpoints relacionados con el producto y los diferentes tipos de filtrado.

Se busca verificar y validar que las interacciones con los productos tanto para Creación, Obtención, Actualización o Modificación y Eliminación, y las operaciones de filtrado mediante Título, Precio y Categoría así como la paginación funcionen acorde a lo esperado tanto para entradas válidas e inválidas, evaluando y asegurando la integridad de las funciones y la calidad de las respuestas, códigos de estado y mensajes de error correctos."
"Se realizaron pruebas funcionales para validar que la API cumpla con las funcionalidades básicas de manera correcta.

Se emplearon los siguientes metodos en Postman:
GET: Para verificar que la API puede recuperar y mostrar los datos correctos solicitados
POST: Para la creación de nuevos datos (productos)
PUT: Para modificar los datos existentes del producto
DELETE: Para eliminar un registro de un producto"
En el proceso de prueba se encontraron varios errores (7) que afectan la funcionalidad y experiencia del usuario, estos bugs se lo categorizó con severidad y prioridad media, ya que si bien afectan la funcionalidad no bloquean el uso general de la API

1. El aplicativo para obtener una lista de productos se generaron los siguientes errores: No devuelve la lista de productos en formato JSON de más de 200 productos, no es posible filtrar por título del producto, por precio del producto
2. El aplicativo para visualizar la categoría se generaron los siguientes errores: No se puede ver la lista completa de categorías, no se puede acceder a cada categoría, la hace búsqueda de nombres de las categorías no salen, no se puede ver cuantos productos tiene cada una, si se hace un cambio o se crea una categoría no se evidencia en la web y si se elimina esta tampoco desaparece de la web
3. Para el ingreso del usuario se encontró como error: al ponerse los datos los crea en lugar de ingresarlos, es decir, manda un mensaje de 201 en lugar de 200, tampoco hay muchas restricciones para el acceso 
4. Para subir o cargar archivos se encontraron los siguientes errores: En donde no se carga el documento a subir en la web

**Resful-booker**
1. Para el aplicativo restful-booker se encontraron los siguientes errores: Para hacer la reserva acepta datos distintos al esperado y la crea 
2. En general, la API no está validando los tipos de datos esperados.
3. Nos genera duda sobre la duración de la validez del token
Restful Booker
Restful Booker es un formulario de reserva de Node simple para probar servicios web RESTful.
La API permite:
1. Crear token (Ítem importante ya que esta relacionado a la seguridad de la API)
2. Para el Ítem reserva permite:
- Obtener ID de reserva
- Obtener reserva
- Crear reserva
- Actualizar reserva
- Actualización parcial de la reserva
- Eliminar reserva
Para Restful Booker priorizamos la creación de un token ya que para actualizar y eliminar una reserva es obligatorio el token, ademas es un ítem importante referente a la seguridad de la aplicación, también realizamos el caso de prueba de la creación de una reserva, pero nos llama la atención que permite crearla sin utilizar un token.





### Posibles soluciones
**Bugbank**
1. La aplicación debe mostrar mediante un texto de olor rojo que estos son obligatorios, por lo tanto, esta sección debe ser mejorada
2. En el campo se debe generar una marca la cual indique el ya hay un registro de ese e-mail

**Platzi Fake Store API**
1. Se puede generar una biblioteca de búsqueda, que se genere para que se pueda hacer una mejor búsqueda del artículo deseado
2. tenga una barra de visualización en cada categoría, donde se pueda abrir como una carpeta y no sea una imagen estática, al igual que con los productos se pueda generar una mejor búsqueda con una biblioteca, y que se enlace el back-end con el front-end, esto para que se visualicen los cambio
3. Se está entrelazado el crear una cuenta con el iniciar sesión, por lo que genera dicho error, por lo que se debe crear un inicio de sesión para que no cree más cuentas
4. No se evidencia que se suban los documentos, por lo que quiere decir como si interfiriera, por lo que no hay conexión entre el back-end con el   para que se generen los cambios, por lo que hace que el aplicativo se vea como un cascarón.

**Resful-booker**
1. Se deben poner restricciones sobre qué tipo de datos son permitidos para generar una reserva, esto para evitar confusión al momento de validar cada reserva
2. En general, la API no está validando los tipos de datos esperados.
3. Nos genera duda sobre la duración de la validez del token.




### Tecnologías utilizadas 
- Postman
- Visual Studio Code
- git
- github
- Drive de Google para trabajo colaborativo 
- Se crea Server en Discord para la comunicación como equipo







### **Estructura**

```plaintext
hackathon_equipo_3/
|
|--fake_api/
|   |-- test_report
|   |-- postman_captures_api_testing
|
|--bugbank/
|   |-- test_report
|-- |postman_captures_api_testing
|
|--restful_booker/
|   |-- test_report
|-- |postman_captures_api_testing
|
|--README.md
|--presentation.pdf
```