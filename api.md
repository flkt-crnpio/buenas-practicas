# API
Application Programming Interface, es un conjunto de comandos, funciones, protocolos y objetos que los programadores pueden usar para interactuar con un sistema externo.

## Escribe URLs que describan recursos y sus colecciones
Un recurso es un objeto que es suficientemente importante en nuestra API para utilizarlo solo. Este objeto contiene información, relaciones con otros recursos y métodos para manipularlo. 

Una colección es un conjunto de ese recurso.

Un Uniform Resource Locator (URL) identifica la localización exacta de ese recurso. La forma de la URL consiste en el nombre la colección que puede ir seguida de un recurso específico

```
# url colección
/users

# url recurso
/users/username
```

## Utiliza sustantivos autodescriptivos para los nombres de tus recursos y colecciones
Es importante utilizar nombres que describan al objeto que se va a recibir, lo más recomendado para ello es utilizar sustantivos para nombrar a recursos y colecciones.

No existe una regla para mantener los nombre de los recursos en singular o plural, pero para las colecciones se recomienda utilizar siempre el nombre en plural. 

Una vez que se definan las reglas de la API, mantener el mismo estilo para todos los recursos y colecciones es una buena práctica. 

```
# describir una buena seleccion de nombre de recursos y colecciones debe sonar redundante de lo obvia que es

/usuarios: pues se espera que mande una lista de usuarios
/estados: lista de estados

```

## No utilices verbos en las llamadas
Algunas APIs no RESTful pueden utilizar verbos en las llamadas como 
`` GET: /articles/:slug/generateBanner/ ``
pero el método de HTTP que se utiliza es suficiente para describir la accion. 

Para las RESTful APIs es requerido utiliar las URIs sin verbos
`` GET: /articles/:slug/banner/ ``

```
# No hagas esto
POST: /articles/createNewArticle/

# Es mejor
POST: /articles/

```

## Utiliza los métodos de HTTP para definir las acciones
Todos los recursos en una api tienen un conjunto estandar de acciones: obtener, editar, crear y eliminar. Para ejecutar éstas acciones todas las RESTful APIs utilizan los métodos de HTTP que tienen acciones únicas bien definidas como GET, POST, PATCH, PUT y DELETE

| Método | Acción |
|--------|--------|
| GET    | para obtener un recurso o colección
| POST   | para crear un recurso
| PUT    | para reemplazar un recurso
| PATCH  | para editar un recurso
| DELETE | para eliminar un recurso o colección

Muchas APIs no utilizan PATCH y utilizan PUT para editar, no para reemplazar, lo que lo hace un poco confuso. Pero dentro de la iniciativa para estandarizar las REST APIs (OpenAPI) se nombran todos los métodos, así que próximamente será más comun ver todos los métodos en acción.

```
var express = require('express');
var employeeRoute = express.Router();

employeeRoute
  .all((req, res, next) => {
    res.statusCode = 200;
    next();
  })
  .get('/', (req, res) => {
    res.send('get all employees');
  })
  .post('/', (req, res) => {
    res.statusCode = 201;
    res.send('add a new employee');
  })
  .put('/', (req, res) => {
    res.statusCode = 405;
    res.send('can not replace an employee information without an id');
  })
  .patch('/', (req, res) => {
    res.statusCode = 405;
    res.send('can not edit an employee information without an id');
  })
  .delete('/', (req, res) => {
    res.send('deleting all employees');
  })
  .get('/:employeeId', (req, res) => {
    res.send(`get employee ${req.params.employeeId} information`);
  })
  .post('/:employeeId', (req, res) => {
    res.statusCode = 405;
    res.send('can not add a new employee with an id');
  })
  .put('/:employeeId', (req, res) => {
    // if employeeId exist
    res.send(`replacing employee ${req.params.employeeId}`);
    // if NOT exist
    res.statusCode = 201;
    res.send('add a new employee');
  })
  .patch('/:employeeId', (req, res) => {
    res.send(`updating employee ${req.params.employeeId}`);
  })
  .delete('/:employeeId', (req, res) => {
    res.send(`deleting employee ${req.params.employeeId}`);
  });

module.exports = employeeRoute;
```

Como se puede apreciar en el código de ejemplo. 

Un `PUT request` crea un nuevo recurso o actualiza uno existente. Por lo que el `body` de la llamada debe contener una representación completa del recurso. Si el recurso no existe, creará uno; mientras que si el recurso ya había sido creado, lo modificará.

Un `PATCH request` puede editar parcialmente un recurso existente. El `body`, para éste caso, debe contener la lista de cambios que se quieren editar en el recurso.


## Devuelve el correcto código de error y complementa con mensajes
Para ayudar a las personas a comprender que está pasando con la API, es necesario mandar un código estándar de HTTP para especificar si la respuesta es satisfactoria o contiene un error.

El estatus de cada respuesta debe especificarse con su código de estatus *1xx* para información *2xx* si es satisfactorio *3xx* para redirecciones *4xx* para errores de cliente y *5xx* para errores de servidor. Para información más específica, acá esta la lista completa de [Status Code](https://www.restapitutorial.com/httpstatuscodes.html)

```
GET: 200 OK
POST: 201 Created
PUT: 200 OK
PATCH: 200 OK
DELETE: 204 No Content
```

También es de gran ayuda, y una buena práctica, enviar mensajes para ayudar a las personas a corregir si tienen algun error, sobre todo si contienen detalles específicos de exactamente que estamos haciendo mal, es super valioso y puede ahorrar hoooooras de testing.

```
{
  "error": "Invalid payoad.",
  "detail": {
    "surname": "This field is required."
  }
}

```

## Escribe ejemplos para todas las repuestas de las llamadas de la API
Una API bien diseñada incluye una muestra del tipo de respuesta que se puede esperar cuando la llamada es satisfactoria. Debe ser algo tan breve que un desarrollador pueda comprender en no mas de cinco seg.

Si una persona llama la API con éxito al método GET, debe obtener los datos junto con un código de respuesta 200 para validar el uso correcto. Del mismo modo, una llamada incorrecta debe producir un código de respuesta apropiado de 400 o 500 con información relevante para ayudar a las personas a operar mejor la colección.

```

    responses:
    200:
    description: Successfully returned information about users
    schema:
    type: array
    items:
    type: object
    properties:
    username:
    type: "string"
    example: "kesh92"
    created_time:
    type: "dateTime"
    example: "2010-01-12T05:23:19+0000"


GET /users

{
    “data”:[
        {
            “Username”: “example_user1”,
            “created_time": “2013-12-23T05:51:14+0000 ”
        },
        {
            “username”: “example_user2”,
            “created_time": “2015-3-19T17:51:15+0000 ”
        }...
    ]
}

```

## No mezcles recursos
Las APIs manejan recursos y sus relaciones por lo que en ocaciones se pueden ver URLs con información de dos colecciones, lo que lo hace confuso. Es mejor utilizar como query el id como filtro de la relacion entre las colecciones.

```
# No agregar las colecciones anidadas
GET: /authors/12/articles/

# Mejor utilizar el id como filtro
GET: /articles/?author_id=12

```

## Utiliza querystring para filtrar, ordenar y paginar
Para manejar filtros, ordenar, paginar y buscar, lo mejor es utilizar `querystring`.

Puede haber numerosas relaciones y propiedades, no es una buena práctica definir un recurso para cada una de ellas.  Por otro lado, un buen diseño de API debe proporcionar toda la información, los datos y los recursos necesarios para ayudar a las personas a utilizarlos. Además debe tenerse en cuenta la cantidad de datos que expone el recurso. Si está tratando de exponer mucho, puede haber implicaciones negativas en el servidor, especialmente en lo que respecta a la carga y el rendimiento. 

Todos los casos y relaciones que son consideraciones importantes para la API, se deben manejar utilizando los parámetros de consulta `querystring`.

```
# Publisehd ni siquiera es una colección, es un atributo de los artículos
GET: /articles/published/

# Es mas obvio filtrar de ésta manera
GET: /articles/?published=true
```
