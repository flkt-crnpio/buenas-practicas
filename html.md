# HTML

### Estructura en HTML5
Modo estándar para iniciar un documento en HTML5
```
<!doctype html>
```

Agregar siempre el atributo de lenguaje
```
<html lang="es">
    <!-- ... -->
</html>
```

Agregar el metadato de la codificación de caracteres
```
<head>
    <meta charset="utf-8">
</head>
```

De preferencia, incluir archivos de CSS en la cabecera
```
<!doctype html>
<html lang="es">
<head>
    <!-- Archivo de CSS -->
    <link rel="stylesheet" href="code-guide.css">
</head>
</html>
```

Siempre que se pueda, de preferencia incluir los archivos de JavaScript al final del cuerpo
```
<!doctype html>
<html lang="es">
<head>
    <!-- ... -->
</head>
<body>
    <!-- JavaScript -->
    <script src="code-guide.js"></script>
</body>
</html>
```


### Utiliza la web semántica
Con las etiquetas semánticas mejoramos la definición de nuestro contenido, es más entendible tanto para humanos como para máquinas(algoritmos de buscadores) [html5 semantic elements](https://www.w3schools.com/html/html5_semantic_elements.asp)

Son muy importantes para la semántica las nuevas etiquetas incorporadas en HTML5, es necesario aprenderlas a utilizar. Por ejemplo, si se está agregando una lista utiliza `ol` o `ul`, que para eso fueron creadas en lugar de hacer una hilera de `div`s. 

Para todas las páginas web se deben utilizar primero las etiquetas de HTML para dar formato, antes de empezar a agregar estilos en CSS.


### Reduce el uso de etiquetas
```
<!-- Utilizar etiquetas para encerrar estilos no tiene sentido -->
<span class="avatar">
    <img src="...">
</span>

<!-- Mejor -->
<img class="avatar" src="...">
```


### Utiliza picture para imagenes responsivas
Utilizar `<picture>` con multiples imágenes para mejorarla carga o visualización de imágenes
```
<picture>
    <source media="(min-width: 721px)" srcset="./img/proyectos-480w.jpg" />
    <source media="(min-width: 361px)" srcset="./img/proyectos-720w.jpg" />
    <img src="./img/proyectos-360w.jpg" alt="enlace a proyectos" />
</picture>
```


### Especifíca el tamaño en las imagenes
De ser posible define el atributo `width` y `height` de una imagen. Esto ayudará a evitar repaints y reflows durante el renderizado. Pero manteniendo en mente que el tamaño real de la imágen es el que pesa en el render.


### Elementos con acciones
Se utiliza un link cuando necesitemos enviar al usuario a un lugar en especifico, independientemente de cómo se deba ver en diseño
```
// NO 
<button onclick="window.location.href='/alguna/pagina'">
    liga a alguna página
</button>

// NOO
<a href="/alguna/pagina">
    <button>liga a alguna página</button>
</a>


// SI
<a href="/alguna/pagina" class="button">
    liga a alguna página
</a>
```

De igual manera, si se requiere que algun elemento haga una acción NO se utiliz un link, porque después se tiene que bloquear su acción primaria con JavaScript
```
// NOOO
// e.preventDefault(); 
<a href="#" onclick="hacerAlgo(e)">Acción</a>


// SI
<button onclick="hacerAlgo(e)" class="link">
    Acción
</button>
```
