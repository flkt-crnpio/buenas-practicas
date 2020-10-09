# Buenas prácticas para código en general

### Evita los caracteres especiales del español
El lenguaje estándar de programación no contiene dichos caracteres, solo los que son parte de la arquitectura básica [Código ASCII — American Standard Code for Information Interchange](https://ascii.cl/es/). Utilizar cualquier tipo de tilde, como ñ ü ú û, puede ocasionar errores.

### Evita mezclar tecnologías
Por ejemplo, escribir estilos en JavaScript puede hacer que se crea que las clases de CSS no están funcionando y hace más complicado mantener el código. Lo mismo para cualquier tecnología, es preferible mantener la organización de los archivos únicamente con código del nombre de la extensión de su archivo, en la medida de lo posible.

### Utiliza una sangría consistente
En cualquier lenguaje, se necesita estandarizar un estilo de espaciado y utilizarlo en todo el proyecto. Hay muchos estilos y ninguno es 'el bueno' pero utilizar el mismo en todos lados ayuda a mejorar la lectura. Lo más común es la sangría con dos espacios o un tabulador (cuatro espacios), esta característica se debe configurar en el IDE de cada desarrollador.

Se pueden utilizar espacios 2 o 4 espacios; o un tabulador, pero siempre se debe identar. También es importante observar y homologar el espacio entre cada elemento, o si las llaves van pegadas o separadas de una declaración, si los parámetros se separan con espacio... etc.

```
// HTML
<ol>
    <li>elementos dentro de la lista</li>
    <li>siempre identados</li>
</ol>
<div>
    cada que entras a un elemento
    <div>
        debes agregar una sangria
        <div>
            asi sabes quien contiene a quien
            <div>
                y cuantas veces tienes que cerrar
                <div>
                    para regresar al origen
                    <div>
                        porque todos los elementos de html
                        <div>
                            son como nodos
                            <div>
                                y si no los cierras
                                <div>
                                    se puede romper toda la estructura
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

// JS
var algo = 9;
for(let i = 0; i < algo; i ++) {
    // identar para saber si estoy dentro de un ciclo o función
    llamarOtraFuncion(parametro1, parametro2, parametro3);
    // separar los parámetros para saber cuantos estoy enviando a simple vista
}

```

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

### Comenta el código
Los comentarios dentro del código deben utilizar comentarios en línea. Si se agrega la documentación de una clase o función, se debe agregar antes del inicio de la clase con comentario de bloque.
```
/*
 * aqui poner la descripción
 * las variables que necesita
 * lo que retorna
 */
function nombreDeFuncion() {
    // aca un comentario en línea
}
```

### Nombres obvios y simplificados
No siempre es necesario agregar documentación, sobre todo si los nombres de variables y funciones describen el código que se está ejecutando. Una buena nomenclatura es la mejor documentación.

Evitar escribir código como:
```
function r_c(r){
    Object.keys(r).forEach(c => {
        if (c != o.f1) {
            r[c] = isNaN(r[c]) || r[c] == "" ? null : (parseFloat(r[c]) < 0 ? null : (parseFloat(r[c])))
        }
    })
}
```

### Simplifica y reutiliza

Escribir fragmentos de código reutilizables. Hacer una sola tarea por función mejora la lectura, reutilización, factorización y pruebas.

### Haz pruebas

Cuando se hacen pruebas de FrontEnd es buena idea separar las pruebas de UI de las de funcionalidad. De ser posible las pruebas se deben parecer lo más posible a la realidad a la que se enfrentarán.
