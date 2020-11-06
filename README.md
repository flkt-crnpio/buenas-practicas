# DAI Guía de desarrollo 



## Código fuente
### [En general](generales.md)
* [Lee proyectos de código abierto](generales.md#leer-proyectos-de-código-abierto)
* [Evita los caracteres especiales del español](generales.md#evita-los-caracteres-especiales-del-español)
* [Evita mezclar tecnologías](generales.md#evita-mezclar-tecnologías)
* [Evita la anidación profunda](generales.md#evita-la-anidación-profunda)
* [Utiliza una sangría consistente](generales.md#utiliza-una-sangría-consistente)
* [Agrupa el código en segmentos](generales.md#agrupa-el-código-en-segmentos)
* [Comenta el código](generales.md#comenta-el-código)
* [Utiliza nombres obvios para funciones y variables](generales.md#utiliza-nombres-obvios-y-simplificados-para-funciones-y-variables)
* [Simplifica y reutiliza](generales.md#simplifica-el-código-en-fragmentos-reutilizables)
* [Haz pruebas](generales.md#haz-pruebas)
 
### [HTML](./html.md)
    * Estructura en HTML5
    * Utiliza la web semántica
    * Reduce el uso de etiquetas
    * Utiliza picture para imágenes responsivas
    * Especifica el tamaño en las imágenes
    * Elementos con acciones

### [CSS](./css.md)
    * Estructura de código y archivos
    * Sintaxis
    * Media queries
    * Nombres de variables descriptivas de uso no de forma
    * Evita los @imports
    * Elimina el CSS innecesario
    * Minifica el CSS

### [JavaScript](./javascript.md)
    * Nomenclatura consistente
    * Declaración de variables
    * Utiliza nombres de variables obvias
    * Comparaciones en JavaScript
    * Utilizar defaults para los parámetros en las funciones
    * Elimina los console.logs en producción

## Bases de datos
### Diseño de la base de datos
    * Selecciona adecuadamente entre Relacional o No Relacional
    * Normaliza los datos. Reduce la redundancia, elimina los atributos con valores multiples y los atributos repetidos que comiencen con subclaves
    * Escribe estructuras transparentes. Los nombres utilizados en una base de datos no son para sus creadores, son para sus usuarios, elimina el uso de abreviaturas que no son comunes
    * Estandariza los nombres de tablas, relaciones y atributos
    * Documenta, escribe un diccionario de datos
    * Una tabla debe representar un objecto único
    * Utiliza stored procedures
    * Definir restricciones para mantener la integridad de los datos. Utiliza las propiedades de las tablas para guardar las reglas que no cambian en el diseño de tu base de datos. Como el largo del contenido, las llaves foraneas, si un contenido puedo o no ser nulo, si es de un dato en particular...
    * Optimiza para mejorar la velocidad. Crea índices para consultas que se utilizarán con regularidad. Utiliza un analizador de bases de datos para determinar si es necesario un índice o un índice agrupado. 
    * Considera la posibilidad de incorporar herramientas como Elastisearch para acelerar las búsquedas.
    * De ser posible, poner la base de datos en su propio servidor para reducir el uso de la CPU. Además de liberar recursos informáticos, también ayuda a mantener la base de datos fuera del alcance de usuarios no autorizados.

### SQL convencion de nombres
    * escribe en minusculas_separado_por_guiones_bajos
    * no utilices data types como nombres como `text` o `timestamp``
    * los nombres de los objetos deben ser nombres completos 'full english words'. La mayoría de las bases de datos soportan hasta 30 caracteres para los nombres. Es mejor usar `middle_name` en lugar de `mid_nm`
    * si se escribe en español es necesario evitar todo tipo de tilde y caracter especial del idioma
    * utiliza abreviaturas comunes como `i18n` en lugar de `internacionalización` o `l10n` en lugar de `localizacion` 
    * no utilices palabras reservadas como `user` o `table`
    * utiliza nombres en singular. tablas y vistas deben llamarse `team` no `teams`
    * las llaves primarias deben ser únicas y llamarse `id` 
    * las llaves foraneas deben comenzar con la referencia de la tabla y el nombre del campo al que referencian `foo_id`
    * no utilizar prefijos ni sufijos en los nombres de tablas ni campos

### Seguridad
    * Proteje el acceso a la base de datos con un firewall para denegar el tráfico por default y solo dejar acceder desde páginas específicas o servidores conocidos ( no estoy segura si eso sea bueno para datos públicos )
    * Cifra los datos, sobre todo los datos sensibles
    * Reduce al mínimo los accesos directos a la base de datos
    * Nunca otorgues todos los privilegios a todos los usuarios
    * Accesos temporales con constraseñas fuertes
    * Crear los accesos con privilegios específicos por usuario
    * Bloquea los usuarios en caso de accesos fallidos por tres ocaciones consecutivas
    * Se debe establecer un procedimiento para que las cuentas se desactiven cuando un usuario cambie de rol
    * Monitorea la actividad de la base de datos
    * Hacer copias de seguridad frecuentes
    * Realiza auditorias
    * Manten el software actualizado

### Conexiones seguras
    * Utiliza HTTPS
    * Las contraseñas deben tener un hash para proteger el sistema
    * Nunca expongas información sensible en la URL
    * Considera utilizar [OAuth](https://oauth.net/2/)
    * Agrega timestamps en las solicitudes
    * Valida los parámetros de entrada


## APIs
Application Programming Interface, es un conjunto de comandos, funciones, protocolos y objetos que los programadores pueden usar para interactuar con un sistema externo.

### [Diseño de API](api.md)
* [Escribe URLs que describan recursos y sus colecciones](api.md#escribe-urls-que-describan-recursos-y-sus-colecciones)
* [Utiliza sustantivos autodescriptivos para los nombres de tus recursos y colecciones](api.md#utiliza-sustantivos-autodescriptivos-para-los-nombres-de-tus-recursos-y-colecciones)
* [No utilices verbos en las llamadas](api.md#no-utilices-verbos-en-las-llamadas)
* [Utiliza los métodos de HTTP para definir las acciones](api.md#utiliza-los-métodos-de-http-para-definir-las-acciones)
* [Devuelve el correcto código de error y complementa con mensajes](api.md#devuelve-el-correcto-código-de-error-y-complementa-con-mensajes)
* [Escribe ejemplos para todas las repuestas de las llamadas de la API](api.md#escribe-ejemplos-para-todas-las-repuestas-de-las-llamadas-de-la-api)
* [No mezcles recursos](api.md#no-mezcles-recursos)
* [Utiliza querystring para filtrar, ordenar y paginar](api.md#utiliza-querystring-para-filtrar-ordenar-y-paginar)

## [A11y]
Hacer la web accesible para todas las personas


    Diseño
    * Asegurate que el color no sea la única manera de comunicar algo
    * Utiliza un diseño simple y consistente
    * Revisa el contraste para el texto
    * Revisa el contraste para los iconos
    * Utilizar altos contrastes entre el color de fondo y el texto
    * Utilizar texturas como complemento cuando los colores referencían algo
    * Utiliza un label para cada input en un formulario
    * Los errores y mensajes en los formularios no deben ser solo diferencias de color
    * Los videos deben contener subtitulos
    * El audio debe tener transcripciones
    * Asegurate que exite (sobre todo para celulares) el espacio suficiente entre elementos interactivos


    Programacion
    * Agrega el atributo de lenguaje en la cabecera
    * Escribir HTML semántico y [landmarks](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/HTML5.html)
    * Siempre debe existir uno y solo un H1
    * No brincar los headings entre niveles
    * No desabilites el zoom
    * Asegurate que el zoom no cambia el interlineado del texto
    * Siempre que se pueda interactuar con un elemento, utilizar link, botón o input
    * Asegurate que las descripciones para links, botones y labels sea única y descriptiva
    * No eliminar del CSS la propiedad outline de los elementos en la pseudoclase :focus
    * Intenta no utilizar el autofocus
    * Verifica que el focus de los elementos esté en el orden en el que estan distribuidos en la vista
    * Escribe el atributo alt para todas las imágenes que no son decorativas
    * Escribe un texto alternativo para describir imágenes complejas como mapas y gráficas
    * Tablas con th scope y caption
    * Utiliza fieldset y legend en los formularios 
    * Cada input debe tener un label
    * Asegurate que audio y video no tienen autoplay y todos sus controles funcionen correctamente


    En celulares
    * Revisa que se pueda rotar el contenido
    * Elimina el scroll horizontal
    * Asegurate que links y botones se pueden utilizar fácilmente
    * Asegurate que existe espacio suficiente entre elementos interactivos


    Pruebas
    * Navega únicamente con el teclado
    * Escucha tu página
    * Incrementa el texto al 200%
    * Revisa la página en navegadores especializados


    Guías
    https://a11y-style-guide.com/style-guide/section-navigation.html
    https://developer.chrome.com/apps/a11y
    https://github.com/Stephs15/accessibility-resources



## Librerías utilizadas en la DAI
### Visualizacion de datos
* [amcharts](https://www.amcharts.com/) gráficas en JavaScript 
* [OpenLayers](https://openlayers.org/) mapas en JavaScript

### Estilos en páginas web
* [bulma](bulma.io/) CSS y SASS

### Frameworks para crear páginas web
* [jekyll](https://jekyllrb.com/) páginas estáticas
* [Vue](https://vuejs.org/) componentes con JavaScript

## Ligas útiles
* [Para ver áreas de mejora en rendimiento](https://developers.google.com/speed/pagespeed/insights/?hl=es)
* [Para reducir el peso de las imágenes](https://squoosh.app/)
