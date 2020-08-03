# Guía de buenas prácticas en desarrollo web

Este repositorio es una pequeña guía con una serie de recomendaciones, buenas prácticas, enlaces y recursos para mejorar el desarrollo Web. Primero se abordan las recomendaciones generales se deben seguir para mejorar la lectura y mantenimiento de cualquier aplicación. Para después adentrarse ligeramente en cada tecnoloía individualmente.



## Generales

### 1. Evita mezclar tecnologías
Por ejemplo escribir estilos en javascritp hace que se crea que las clases de CSS no estan funcionando y hace que sea más complicado de mantener el código.

### 2. Utiliza una sangría consistente
Tanto en HTML, CSS ó JavaSctipt, se necesita estandarizar un estilo de espaciado y utilizarlo en todo el proyecto. Hay muchos estilos y ninguno es 'el bueno' pero utilizar el mismo en todos lados ayuda a mejorar la lectura. 

Se pueden utilizar espacios 2 o 4 espacios; o un tabulador, pero siempre se debe identar. Y el espacio entre cada elemento o si las llaves van pegadas o separadas de una declaracion, si los parametros se separan con espacio

### 3. Agrupa el código en segmentos
Esta es la sugerencia más opcional de la vida del código, pero igual siempre me ha parecido que hace más fácil de leer como por párrafos en una novela.

```
function editarAlgo(unaVariable) {
    // una funcion
    // que hace algo especifico
}
// que luego edita acá
// y termina imprimiendo algo
// mantener el bloque sin espacios 
// pa' saber que se trata de lo mismo


// hasta que pasamos otra cosa diferente
// y entonces empieza con un margen de espacio
```

### 4. Comenta el codigo
Cuando se comente dentro del código utilizar comentatios en linea 
y si se hace documentacion de una clase o funcion, 
documentar antes del inicio de la clase con comentario de bloque
```
/*
 * aqui poner la descipcion
 * las variables que necesita
 * lo que retorna
 */
function nombreDeFuncion() {
    // aca un comentario en linea
}
```

### 5. Simplifica y reutiliza

Escribir fragmentos de código reutilizables.

Hacer una sola tarea por funcion para mantenerlo lo más modular posible, mejora la lectura, reutilizacion, factorizacion y pruebas.



## HTML

### 1. Estructura HTML5
Estandar mode doctype
```
<!doctype html>
```

Agregar siempre el atributo de lenguaje
```
<html lang="es">
    <!-- ... -->
</html>
```

Character encoding
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

### 2. Web Semántica
Con las etiquetas semánticas mejoramos la definición de nuestro contenido, es más entendible tanto para humanos como para máquinas(algoritmos de buscadores)

Nuevas etiquetas incorporadas en HTML5
```
<article>
<aside>
<details>
<figcaption>
<figure>
<footer>
<header>
<main>
<mark>
<nav>
<section>
<summary>
<time>
```

* [html5 semantic elements](https://www.w3schools.com/html/html5_semantic_elements.asp)

### 3. Reducción de etiquetas
```
<!-- Utilizar etiquetas para encerrar estilos no tiene sentido -->
<span class="avatar">
    <img src="...">
</span>

<!-- Mejor -->
<img class="avatar" src="...">

```
### 4. Imágenes responsivas
Utilizar `<picture>` con multiples imágenes para mejorarla carga o visualización de imágenes
```

```


## CSS
### 1. Nomenclatura consistente
### 2. Nombres de variables descriptivas de uso no de forma



## JavaScript

### Nomenclatura consistente
Existen varios estilos de escribir nombres de variables, funciones, clases. No existe 'el mejor método para combinar estilos' pero siempre a lo largo de la aplicación se debe mantener el mismo estilo para las mismas cosas.

* camelCase
* PascalCase
* snake_case
* SNAKE_CASE_CAPS
* kebab-case

### Declaración de variables 
Aunque en JavaScript una variable puede ser declarada después de utlizarse es una buena práctica declarar las variables al inicio del código, excepto las que se utilizan solo en un bloque.

Elegir el tipo de variable dependiendo de los requerimientos 
* `const` // scope de bloque
* `let` // scope de bloque
* `var` 

```
{
  var x = 2;
}
// con VAR x PUEDE seguirse utilizando despues del bloque
```
```
{
  let x = 2;
}
// con LET x NO PUEDE usarse fuera de un bloque
```

Es mucho mejor intentar utilizar siempre `let` y `const` porque pueden reducir errores de sobreescritura
```
var x = 10;
// x es 10
{
  var x = 2;
  // aquí x es 2
}
// saliendo x es 2 :(
```
```
var x = 10;
// x es 10
{
  let x = 2;
  // nuevo scope x es 2
}
// Acá volvemos al scope de afuera donde x = 10
```

Una constante no puede ser declarada sin asignarle un valor.
```
var x; // valid
let y; //valid
const z; // error
```

No se puede asignar un nuevo valor a una constante declarada.
```
const z = 3; // valid
z = 4; // error
```

### Utiliza nombres de variables obvias
Por legibilidad y porque el código nunca se debe escribir para uno mismo, es mejor ser descriptivo a la hora de poner el nombre a las variables

```
// esto es difícil de desifrar, pues tienes que leer todo lo que está alrededor para enterarte para que se necesita

let iu = []; 


// mientras que describir con el nombre de variable para lo que se utilizará, además de descriptivo reduce los comentarios

let informacionUsuario = [];
```
Y utlizar prefijos `has` `is` para variables boleanas
```
let isAdmin = true;

ó

let hasDescription = false;
```

### Comparaciones en JavaScript
Utilizar `===` en JavaScript en lugar de `==`. El primero hace una comparación contra el tipo de variable y el valor de la variable, mientras que el segundo solo verifica el valo y pueden existir comparaciones que no se esperan. 

Por ejemplo
```
alert("" == false); // true
alert(0 == false); // true


// mientras que

alert(0 === false); // false, porque son de diferentes tipos
```

### Utilizar defaults para los parametros en las funciones
```
function logNumber(num = 25) {
    console.log(num);
}
logNumber();
```
