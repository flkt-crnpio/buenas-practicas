# Python
En esta sección se resumen los que se consideran los puntos más importantes en cuanto a la convención de estilo de código en python.

## Importaciones
- La importación de todas las bibliotecas siempre debe ir al inicio del código y después de cualquier comentario
- Las importaciones deben estar en líneas separadas:
        
<font color='blue'> **Correcto** </font>
```
    import os
    import sys
    from subprocess import Popen, PIPE
```
**Incorrecto**
```
    import os, sys
```

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

```
with open('/path/to/some/file/you/want/to/read') as file_1, \

open('/path/to/some/file/being/written', 'w') as file_2: \

file_2.write(file_1.read())

```

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

## Clases

- Al nombrar la clase se debe usar el estilo CamelCase, o si sólo es una palabra para el nombre, ésta debe ir en con la primera letra en mayúscula. 
- No usar más de tres palabras para nombrar la clase
- El nombre debe ser algo entendible y que remita al propósito de la clase
- Colocar los atributos al momento de iniciar la clase
- Al escribir los atributos, éstos deben de ir en minúsculas, en caso de usar múltiples palabras conectarlos por medio de guiones bajos (estilo serpiente/snake case style)  `first_name`

_Ejemplo_
```class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age
```

## Funciones
- Usar minúsculas para nombrar las funciones, las variables y los argumentos. En caso de unar más de una palabra para denominar cualquiera de los elementos anteriores usar guiones bajos para conectarlas (snake case style). Al igual que en los otros casos de estilo **NO** poner un espacio en blanco ante de los dos puntos _(colon)_ _(:)_ que definen el cuerpo de la función. 
- Usar un nivel extra de identación (agregar 4 espacios) para hacer la distinción de los argumentos del resto del código
- Describir lo que hace la función, este comentario debe aparecer después de la línea de definición `def`. Recordar no exceder los 72 caracteres, si esto sucede colocar en dos líneas la descripción
```
def hello_world():
# Descripción de lo que hace la función.
# Segunda línea de descripción para no exceder los caracteres.
    print(var_one)
```
- Siempre usar `self` para el primer argumento en _instance methods_
```
def __init__(self, fruit, color):
self.fruit = fruit
self.color = color
```
- Siempre usar `cls` para el primer argumento en _class methods_
```
def class_method(cls):
        return 'class method called', cls
```
- Si dentro de la función se utiliza un operador _si (if)_ tener en cuenta que o todos los operadores regresan una expresión, o ninguno lo hace.
```
def foo(x):
    if x >= 0:
        return math.sqrt(x)
    else:
        return None

def bar(x):
    if x < 0:
        return None
    return math.sqrt(x)
```
- Si la función tiene más de tres parámetros se recomienda usar *keyword arguments*. En la siguiente función los argumentos `cc` y `bcc` son opcionales y se evaluan con `None` cuando no se les asigna ningún valor.
```
def send(message, to, cc=None, bcc=None):
    print('mensaje enviado')
```
- Si la función requiere un número indeterminado de argumentos, usar la palabra clave _**kwargs_ y en el cuerpo de la función usar un diccionario con todos los argumentos.
```
def myFun(**kwargs):
    for key, value in kwargs.items():
        print ("%s == %s" %(key, value))
 ```

 # Fuentes
 
 - [PEP8](https://www.python.org/dev/peps/pep-0008/)
 - [Advanced Python: 9 Best Practices to Apply When You Define Classes](https://betterprogramming.pub/advanced-python-9-best-practices-to-apply-when-you-define-classes-871a27af658b)
 - [Python’s Instance, Class and Static Methods](https://medium.com/python-features/pythons-instance-class-and-static-methods-e9097f07829b#:~:text='WELCOME'-,Class%20Methods,the%20object%20of%20the%20class%20.)
 - [CodeStyle](https://docs.python-guide.org/writing/style/)
 # Contacto
 
 nadia.neri.vera@gmail.com
 
 joselin.ceronal@gmail.com



 

        


