# Python
En esta sección se resumen los que se consideran los puntos más importantes en cuanto a la convención de estilo de código en python.

## Importaciones
- La importación de todas las bibliotecas siempre debe ir al inicio del código y después de cualquier comentario
- Las importaciones deben estar en líneas separadas:
    - Ejemplo:
        # Correcto
        `import os`
        `import sys`
        `from subprocess import Popen, PIPE`
        # Incorrecto
        `import os, sys`
- Las importaciones deben agruparse en el siguiente orden:
    - Importaciones de bibliotecas estándar
    - Importaciones de terceros relacionadas
    - Importaciones de aplicaciones locales/bibliotecas específicas
* Nota: Entre cada grupo de importaciones debe ir un espacio en blanco
- Se recomiendan las importaciones abosolutas:
    # Ejemplo
    `import mypkg.sibling`
    `from mypkg import sibling`
    `from mypkg.sibling import example`
- Las importaciones relativas explícitas se recomiendan cuando se trata de diseños de paquetes complejos.
    # Ejemplo
    `from . import sibling`
    `from .sibling import example`
- En importaciones de clases de un módulo lo correcto es escribir:
    `from myclass import MyClass`
    `from foo.bar.yourclass import YourClass`
    En caso de tener conflictos por ortografía, escribir:
    `import myclass9`
    `import foo.bar.yourclass`


## Estilo de código
- Limitar las líneas de código a máximo **79 caracteres**
- En bloques de texto (*"docstrings o comentarios"*) la longitud de la línea debe limitarse a 72 caracteres.
- El método más recomendado para “corte” de líneas largas es utilizar la continuación implícita dentro de paréntesis, corchetes o llaves. Las líneas largas pueden dividirse en múltiples líneas entre ( ). Este método es preferible al uso de  barra invertida (`“\”`) para la continuación de la línea.
    # Ejemplo
    `with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())`

- **Espacios en Blanco**
    - Utiliza espacio para separar los elementos de un arreglo, lista, serie,  etc. Ejemplo:
        ```b = [1, 3, 4, 7]```
    - Utiliza espacio inmediatamente después de un símbodo de asignación. Ejemplo:
        ```x = 1```
    - **No** usar espacios alrededor del signo *=* en argumentos o parámetros de funciones.

## Estilo de comentarios
- Limitar las líneas de código a máximo **79 caracteres**
- **Espacios en Blanco**
    - Utiliza espacio para separar los elementos de un arreglo, lista, serie,  etc. Ejemplo:
        ```b = [1, 3, 4, 7]```
    - Utiliza espacio inmediatamente después de un símbodo de asignación. Ejemplo:
        ```x = 1```
    - **No** usar espacios alrededor del signo *=* en argumentos o parámetros de funciones.