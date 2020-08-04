# Buenas prácticas para código en general

### Evita los caracteres especiales del español
El lenguaje estándar de programación no contiene dichos caracteres, solo los que son parte de la arquitectura básica [Código ASCII — American Standard Code for Information Interchange](https://ascii.cl/es/). Utilizar cualquier tipo de tilde, como ñ ü ú û, puede ocacionar errores.

### Evita mezclar tecnologías
Por ejemplo escribir estilos en javascritp hace que se crea que las clases de CSS no estan funcionando y hace que sea más complicado de mantener el código.

### Utiliza una sangría consistente
Tanto en HTML, CSS ó JavaSctipt, se necesita estandarizar un estilo de espaciado y utilizarlo en todo el proyecto. Hay muchos estilos y ninguno es 'el bueno' pero utilizar el mismo en todos lados ayuda a mejorar la lectura. 

Se pueden utilizar espacios 2 o 4 espacios; o un tabulador, pero siempre se debe identar. Y el espacio entre cada elemento o si las llaves van pegadas o separadas de una declaracion, si los parametros se separan con espacio

### Agrupa el código en segmentos
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

### Comenta el codigo
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

### Simplifica y reutiliza

Escribir fragmentos de código reutilizables.

Hacer una sola tarea por funcion para mantenerlo lo más modular posible, mejora la lectura, reutilizacion, factorizacion y pruebas.

### Haz pruebas

Cuando se hacen pruebas de FrontEnd es buena idea separar las pruebas de UI de las de funcionalidad. De ser posible las pruebas se deben parecer lo mas posible a la realidad a la que se enfrentaran.
