# CSS
Durante el desarrollo, utiliza un preprocesador como SASS o LESS. Para producción, compilan todos los archivos de SCSS, SASS o LESS dentro de un solo archivo de CSS minificado.

### Estructura de código y archivos 
Es recomendable crear un archivo de variables generales, que definen los estilos que se repiten a lo largo del sitio, para utilizar dentro de los componentes las mismas variables y que el sitio sea fácilmente editable a través de un solo archivo.

Para cada componente o vista, dentro de la carpeta del mismo, se utiliza un archivo de estilos, que tiene el mismo nombre que el componente. Manteniendo esta estructura se mantiene el proyectos modular, lo que hace muy flexible para agregar, editar o eliminar un componente al sitio.

```
vistas/
    index.html
    index.js
    index.scss
```

Dentro del archivo de estilos se organizan las secciones de código por elementos que contenga el componente o vista. En CSS, LESS o SCSS agregar sangrías o no, no rompe el código en sí, pero es importante, por lectura al menos, mantener la sangría. Sin embargo, en SASS, que no utiliza corchetes ni punto y coma al final de cada atributo, se debe tener especial cuidado en el espaciado de elementos, atributos, pseudo-elementos y pseudo-clases.

```
.contenedor {
    // estilo del contenedor
}

.tarjeta {
    // estilos de la tarjeta
    &::after {
        // estilo pseudo elemento
    }
    &::hover {
        // estilo pseudo clase
    }
}
```



### Sintaxis
Cuando se agrupan selectores por tener los mismos estilos, es recomendable escribir cada selector en una línea diferente. 

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
Incluir un espacio antes del corchete de apertura `{` y cerrar en una línea nueva `}`.

```
NO
.selector{atributo:valor;
atributo:valor}

SI
.selector {
    atributo: valor;
    atributo: valor;
}
```

Siempre poner espacios después del nombre de la propiedad `:` y terminar cada propiedad con punto y coma `;`
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

Separar con espacio cuando se pueden especificar múltiples atributos compuestos como el `box-shadow`
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

No se especifican unidades cuando se utiliza `0`. 

```
// NO
border: 0px;

// MEJOR
border: 0;
```

Cuando se utilizan decimales, es mejor no poner el cero
```
// NO
opacity: 0.1;

// MEJOR
opacity: .1;
```

### Media queries
Siempre pensar en el estilo para el celular primero.
Es mejor escribir las *media queries* cerca del bloque de clases que dan estilo a un componente que en archivos separados o por cada clase que se requiera modificar.
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
Casi por convención se utilizan minúsculas y se separan con guiones medios. Se deben poner los nombres relacionados al elemento que deben formatear, no al estilo que van a tener al final, porque éste, siempre puede cambiar y terminas teniendo una clase `.roja` de color `color: blue`.

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

### Evita los @imports en el archivo final de producción
Cuando el navegador está leyendo un archivo CSS y se encuentra con un @import deja de leer el archivo CSS original y empieza a descargar y leer el archivo importado y recién cuando termina sigue con el original.

Debido a que la carga de CSS es una operación bloqueante el estar haciendo esto ralentiza el renderizado de nuestra aplicación por lo que es mejor evitar el uso de `@import` en los archivos CSS, en lugar de eso es mejor combinar los archivos o al menos usar dos etiquetas `<link>`.


### Elimina el CSS innecesario
Al usar algún framework de CSS es muy común no usar todos los estilos que este trae. Es mejor cargar solo los módulos que se están utilizando. También es bastante común que durante el desarrollo queden clases que ya no se utilizan y se dejan “por las dudas” y que el usuario está descargando al bajar el CSS aunque no los necesite.


### Minifica el CSS
Esto a pesar de ser una gran mejora de rendimiento y velocidad es algo que todavía no se realiza en muchos sitios o aplicaciones web. El minificar el CSS, al igual que con el HTML, reduce el peso del archivo y elimina los comentarios, permitiendo una carga más rápida del archivo y terminar el renderizado antes.
