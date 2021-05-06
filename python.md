# Python
En esta sección se resumen los que se consideran los puntos más importantes en cuanto a la convención de estilo de código en python.

## Importaciones
- La importación de todas las bibliotecas siempre debe ir al inicio del código y después de cualquier comentario
- Las importaciones deben estar en líneas separadas:
        
    **Correcto**

    `import os`
    
    `import sys`
    
    `from subprocess import Popen, PIPE`

    **Incorrecto**

    `import os, sys`

- Las importaciones deben agruparse en el siguiente orden:
    - Importaciones de bibliotecas estándar
    - Importaciones de terceros relacionadas
    - Importaciones de aplicaciones locales/bibliotecas específicas
* _Nota: Entre cada grupo de importaciones debe ir un espacio en blanco_
- Se recomiendan las importaciones abosolutas:

    `import mypkg.sibling`
    
    `from mypkg import sibling`
    
    `from mypkg.sibling import example`

- Las importaciones relativas explícitas se recomiendan cuando se trata de diseños de paquetes complejos:

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
- El método más recomendado para “corte” de líneas largas es utilizar la continuación implícita dentro de paréntesis, corchetes o llaves. Las líneas largas pueden dividirse en múltiples líneas entre ( ). Este método es preferible al uso de  barra invertida (`“\”`) para la continuación de la línea:

**incorrecto**

`with open('/path/to/some/file/you/want/to/read') as file_1, open('/path/to/some/file/being/written', 'w') as file_2: file_2.write(file_1.read())`

**correcto**

`with open('/path/to/some/file/you/want/to/read') as file_1, \

open('/path/to/some/file/being/written', 'w') as file_2: \

file_2.write(file_1.read())`

- **Espacios en Blanco**
    - Utiliza espacio para separar los elementos de un arreglo, lista, serie,  etc:

        ```b = [1, 3, 4, 7]```

    - **No** usar espacios alrededor del signo *=* en argumentos o parámetros de funciones.
    - Separar funciones de alto nivel y definiciones de clase con **dos** líneas en blanco.
    - Las definiciones de métodos dentro de una clase deben separarse por una línea en blanco.
    - Las líneas en blanco adicionales pueden utilizarse (escasamente) para separar grupos de funciones relacionadas. Las líneas blancas pueden ser omitidas entre un grupo de funciones relacionadas.
    - Utilizar líneas en blanco en funciones (escasamente), para indicar secciones lógicas. 
    - Python acepta el carácter control-L como espacio en blanco.
    - **Evite usar espacios en blanco en las siguientes situaciones**
        - Inmediatamente dentro de paréntesis, corchetes o llaves:

        **Correcto**
        
        `spam(ham[1], {eggs: 2})`

        **Incorrecto**

        `spam( ham[ 1 ], { eggs: 2 }`

        - Entre una coma al final y un paréntesis de cierre:

        **Correcto**
        
        `foo = (0,)`
        
        **Incorrecto**
        
        `bar = (0, )`

        - Inmediatamente antes de una coma, punto y coma y dos puntos:
        
        **Correcto**

        `if x == 4: print x, y; x, y = y, x`
        
        **Incorrecto**
        
        `if x == 4 : print x , y ; x , y = y , x`

        - Inmediatamente antes del paréntesis abierto que indica la lista de argumentos en la llamada a una función:

        **Correcto**

        `spam(1)`

        **Incorrecto**

        `spam (1)`

        - Inmediatamente antes del paréntesis abierto que inicia una indexación o división:

        **Correcto**

        `dct['key'] = lst[index]`

        **Incorrecto**

        `dct ['key'] = lst [index]`

        - Más de un espacio alrededor de un operador de asignación para alinearlo con otro:

        **Correcto**

        `x = 1`

        `y = 2`

        `long_variable = 3`

        **Incorrecto**

        `x    = __________ 1`

        `y    = _______________ 2`

        `long_variable     = _________________ 3`
        
        * Nota: "____" hace referencia a varios espacios en blanco

 # Fuente
 
 Esta información se obtuvo de
        
 # Contacto
 
 nadia.neri.vera@gmail.com
 
 joselin.ceronal@gmail.com



 

        


