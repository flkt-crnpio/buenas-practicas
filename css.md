# CSS
Para desarrollo, utiliza un preprocesador como SASS o LESS. 
Para producción, compila los CSS dentro de un archivo y minificalo para reducir su peso y tamaño.

### Estructura de códifo y archivos 
Organiza las secciones de código por elementos y los archivos por copmonentes.
Se puede mantener un archivo de variables para poder utlizarla a lo largo de los componentes.


### Sintaxis
Cuando se agrupen selectores, manten cada selector en una linea diferente.
Incluir un espacio antes del `{` de apertura y cerrar con `}` en una línea nueva.
```
// NO
.selector, .selector-secondary, .selector[type=text] {

}


// SI
.selector,
.selector-secondary,
.selector[type="text"] {

}
```

Siempre poner espacios después del nombre de la propiedad `: ` y terminar cada propiedad con punto y coma `;`
```
// NO
.clase {
    propiedad:valor
}


// SI
.clase {
    propiedad: valor;
}
```

Separar con espacio cuando se pueden especificar multiples atributos compuestos como el `box-shadow`
```
// NO
box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF

// SI
box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
```
Pero evitar los espacios en propiedades que requieren los atributos separados con coma como `rgb()` `rgba()` `rec()`
```
// NO
background-color:rgba(0, 0, 0, 0.5);

// SI
background-color: rgba(0,0,0,.5);
```

Es mejor utilizar el código hexadecimal en minúsculas y abreviado
```
// FUNCIONA
#FFFFFF

// MEJOR
#fff
```

No se especifican unidades cuando se utiliza `0`. Y cuando se utlizan decimales, es mejor no poner el cero
`e.g., .5 instead of 0.5 and -.5px instead of -0.5px`


### Media queries
Siempre pensar en el estilo para el celular primero.
Es mejor escribir las media queries cerca del bloque de clases que dan estilo a un componente que en archivos separados o por cada clase que se requiera modificar.
```
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
    .element { ...}
    .element-avatar { ... }
    .element-selected { ... }
}
```

### Nombres de variables descriptivas de uso no de forma
Casi por convencion se utlizan minúsculas y se separa con guiones medios. Se deben poner los nombres relacionados al elemento que deben formatear, no al estilo que van a tener al final, porque éste, siempre puede cambiar y terminas teniendo una clase `.roja` de color `color: blue`.

```
// NO
.t { ... }
.red { ... }
.header { ... }

// SI
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

### Evita los @imports
Cuando el navegador esta leyendo un archivo CSS y se encuentra con un @import deja de leer el archivo CSS original y empieza a descargar y leer el archivo importado y recién cuando termina sigue con el original.

Debido a que la carga de CSS es una operación bloqueante el estar haciendo esto ralentiza el renderizado de nuestra aplicación por lo que es mejor evitar el uso de `@import` en los archivos CSS, en lugar de eso es mejor combinar los archivos o al menos usar dos etiquetas `<link>`.


### Elimina el CSS innecesario
Al usar algun framework de CSS es muy común no usar todos los estilos que este trae. Es mejor cargar solo los módulos que se están utilizando. También es bastante común que durante el desarrollo queden clases que ya no se utilizan y se dejan “por las dudas” y que el usuario esta descargando al bajar el CSS aunque no los necesite.


### Minifica el CSS
Esto a pesar de ser una gran mejora de rendimiento y velocidad es algo que todavía no se realiza en muchos sitios o aplicaciones web. El minificar el CSS, al igual que con el HTML, reduce el peso del archivo y elimina los comentarios, permitiendo una carga más rápido del archivo y terminar el renderizado antes.
