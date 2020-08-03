# Buenas prácticas

## Evita mezclar tecnologías
Por ejemplo escribir estilos en javascritp hace que se crea que las clases de CSS no estan funcionando y hace que sea más complicado de mantener el código.

## Sangría consistente
Tanto en HTML, CSS ó JavaSctipt, se necesita estandarizar un estilo de espaciado y utilizarlo en todo el proyecto. Hay muchos estilos y ninguno es 'el bueno' pero utilizar el mismo en todos lados ayuda a mejorar la lectura. 

Se pueden utilizar espacios 2 o 4 espacios; o un tabulador, pero siempre se debe identar. Y el espacio entre cada elemento o si las llaves van pegadas o separadas de una declaracion, si los parametros se separan con espacio

### En HTML
Siempre identar, siempre siempre
```
<p>
    Contenido acá
    <ul>
        <li>siempre identar</li>
        <li>siempre</li>
    </ul>
</p>
```

### En CSS
```
.clase {
    propiedad: .4; // float
    propiedad: 1; // int
    &::after { // pseudo element
        propiedad: "valor"; //string
    }
    &:hover { // pseudo class
        propiedad: #aaa; // hexadecimal
    }
}

@media (max-width: 600px) {
    // poner acá todas las clases que se modifican
    // pero solo las propiedades que se modifican
    .classe {
        propuedad: .3;
    }
}
```

### En JavaScript
Utilizar espacios entre los parametros o variables.
```
// no sean asi, no cobran por espacio
let variable='algo'
function nombrefuncioin(p1,p2,p3,p4,p5,p6){
//y aca otra cosa
}



// Esto se lee más fácil

let variable = 'algo';
function nombreFuncion( parametro1, parametro2 ) {
    // codigo aqui
}
```

## Agrupación de código
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

## Nomenclatura consistente
Existen varios estilos de escribir nombres de variables, funciones, clases. No existe 'el mejor método para combinar estilos' pero siempre a lo largo de la aplicación se debe mantener el mismo estilo para las mismas cosas.

* camelCase
* PascalCase
* snake_case
* SNAKE_CASE_CAPS
* kebab-case


## Simplifica y reutiliza

Escribir fragmentos de código reutilizables.

Hacer una sola tarea por funcion para mantenerlo lo más modular posible, mejora la lectura, reutilizacion, factorizacion y pruebas.


## Comenta el codigo
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

## Declaración de variables 

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


## Utiliza nombres de variables obvias
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

## Comparaciones en JavaScript
Utilizar `===` en JavaScript en lugar de `==`. El primero hace una comparación contra el tipo de variable y el valor de la variable, mientras que el segundo solo verifica el valo y pueden existir comparaciones que no se esperan. 

Por ejemplo
```
alert("" == false); // true
alert(0 == false); // true


// mientras que

alert(0 === false); // false, porque son de diferentes tipos
```

## Utilizar defaults para los parametros en las funciones
```

function logNumber(num = 25) {
    console.log(num);
}
logNumber();
```
