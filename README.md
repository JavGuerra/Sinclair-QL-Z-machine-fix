# Parche de español para la Máquina-Z de Infocom

_Spanish patch for the Z-machine of Infocom_

**Última revisión**: noviembre 2026  
**Por**: Javier Guerra

El programa en SuperBASIC [zipfix_bas](./zipfix_bas) parchea el intérprete de la [Máquina-Z](https://es.wikipedia.org/wiki/M%C3%A1quina-Z) de aventuras Infocom para Sinclair QL llamado `zip` (_Z-machine Interpreter Program_, no confundir con el compresor de ficheros). El parche permite que se muestren correctamente los caracteres acentuados, la ñ y otros signos de puntuación al leer los ficheros de aventuras conversacionales que soporta.

El programa `zip` es un port de ZIP 2.0 de Mark Howell a QDOS realizado por Luke Roberts en noviembre de 1994, que entiende las versiones .z1 a .z5 de estas aventuras.

Puedes descargar el [fichero comprimido original](https://sinclairql.net/djw/games/adventures/infocom.zip) con el programa `zip` y algunas utilidades desde: [la página de Dilwyn Jones](https://sinclairql.net/djw/games/adventures/index.html).

## El problema

El intérprete para QL no reconoce los caracteres y símbolos propios del idioma español, ya que sólo usa caracteres del inglés, por ello, las aventuras creadas en nuestro idioma muestran esos caracteres con símbolos extraños o con una interrogación. Lamentablemente, el código fuente del programa no está disponible, y se distribuye compilado.

Para poder obtener un resultado correcto en pantalla es necesario modificar el programa, y para ello, existen varias vías. Descastada la posibilidad de contactar con el autor, tras consultarlo en la comunidad de QL, el programa se podría desensamblar, no obstante se optó por encontrar alguna solución intermedia mediante el uso de la IA.

El problema a salvar comprende tres pasos: mostrar los mensajes del programa en castellano, mostrar los caracteres especiales correctamente y entender los caracteres especiales que se introducen por el teclado durante la ejecución del juego.

## La solución: zipfix_bas

El programa `zipfix_bas` toma el ejecutable del intérprete, lo copia, y lleva a cabo las modificaciones necesarias sobre esta copia, realizando algunas comprobaciones. Ha sido creado con la ayuda de la IA [Claude](https://claude.ai/) de Antrophic en su versión gratuita.

Para su elaboración, a la IA se le ha facilitado:

- El fichero `aventuras.zip` (disponible [aquí](https://sinclairql.es/utilidades/aventuras.zip), un compendio de aventuras .z5 en español que contiene también un menú de arranque, el interprete original renombrado a `zip_exe` e información sobre los cinco juegos que incluye.
- La tabla de conversión `chr.csv` que fue generada mediante la utilidad [Tabla de caracteres del QL](https://sinclairql.speccy.org/articulos/comunicaciones/charset.html) creada por Juanjo Ruiz. Esta tabla ayuda a la IA a buscar las equivalencias del juego de caracteres del QL con la tabla ZSCII de la Máquina-Z que usan los juegos.

La IA ha realizado numerosas pruebas y versiones previas, incluyendo la aventura [chrtest_z5](./chrtest_z5) que se incluye en este repositorio, y que espera que se introduzcan caracteres especiales y entonces devuelve su código equivalente en la tabla de caracteres ZSCII para comprobar que la conversión de los caracteres del QL es correcta. Ver el fichero [ZSCII.md](./ZSCII.md).

### Qué hace el programa

| Parte | Resultado |
| --- | --- |
| Salida | Los acentos la ñ y los caracteres especiales se ven bien en pantalla. |
| Entrada | Lo que se teclea llega al juego con los códigos correctos, y las mayúsculas con acento pasan a minúscula. |
| Mensajes | 30 mensajes del intérprete en castellano, más el cambio de la tecla S en el aviso de confirmación. |
| Ejecutable | El tamaño no cambia, y el programa verifica cada paso antes de escribir. |

### Qué no hace el programa

- Á, Í, Ó y Ú mayúsculas salen sin acento, porque el juego de caracteres del QL no tiene esas letras.
- Las teclas sueltas (los "pulsa una tecla") no se convierten. No hace falta.

## Descargas e información

**Importante**: Lee el fichero [leeme.txt](./leeme_txt) para ejecutar las aventuras en el Sinclair QL.

- Imagen de disquete para QL con el programa ejecutable ya parcheado: [aventuras_es.img](./aventuras_es.img)
- Fichero comprimido para QL con el programa ejecutable ya parcheado: [aventuras_es_zip](./aventuras_es_zip)
- Fichero SuperBASIC usado para aplicar el parche: [zipfix_bas](./zipfix_bas)
- Sobre este parche: Artículo en el blog de Sinclair QL en castellano

## Licencia

El programa `zipfix_bas` está bajo licencia GPL. Las aventuras conversacionales y el programa zip están bajo las licencias indicadas por sus propios autores.
