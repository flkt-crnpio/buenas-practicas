# CSS
Para desarrollo, utiliza un preprocesador como SASS o LESS. 
Para producción, compila los CSS dentro de un archivo y minificalo para reducir su peso y tamaño.

### Estructura 
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