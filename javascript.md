# JavaScript

### Nomenclatura consistente
Existen varios estilos de escribir nombres de variables, funciones, clases. No existe 'el mejor método para combinar estilos' pero siempre a lo largo de la aplicación se debe mantener el mismo estilo para las mismas cosas.

* camelCase
* PascalCase
* snake_case
* SNAKE_CASE_CAPS
* kebab-case

### Declaración de variables 
Aunque en JavaScript una variable puede ser declarada después de utilizarse es una buena práctica declarar las variables al inicio del código, excepto las que se utilizan solo en un bloque.

Elegir el tipo de variable dependiendo de los requerimientos 
* `const` // scope de bloque
* `let` // scope de bloque
* `var` 

```
{
  var x = 2;
}
// con VAR x PUEDE seguirse utilizando después del bloque
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
// esto es difícil de descifrar, pues tienes que leer todo lo que está alrededor para enterarte para que se necesita

let iu = []; 


// mientras que describir con el nombre de variable para lo que se utilizará, además de descriptivo reduce los comentarios

let informacionUsuario = [];
```
Y utilizar prefijos `has` `is` para variables booleanas
```
let isAdmin = true;

ó

let hasDescription = false;
```

### Comparaciones en JavaScript
Utilizar `===` en JavaScript en lugar de `==`. El primero hace una comparación contra el tipo de variable y el valor de la variable, mientras que el segundo solo verifica el valor y pueden existir comparaciones que no se esperan. 

Por ejemplo
```
alert("" == false); // true
alert(0 == false); // true


// mientras que

alert(0 === false); // false, porque son de diferentes tipos
```

### Utilizar defaults para los parámetros en las funciones
```
function logNumber(num = 25) {
    console.log(num);
}
logNumber();
```

### Elimina los console.logs en producción
En general no está bien que se vean los mensajes de prueba a la hora de abrir la consola, pero el problema también es que cuando se ejecutan llevan un proceso y se suman a la lista de tareas que debe hacer el navegador para mostrar el contenido.
