# Contrato SCD tipo 2 de la demo

Se recibe una instantánea completa de entidades existentes, con una clave y
un atributo `region`. Cada ejecución tiene una fecha efectiva. No se
interpretan ausencias como borrado. Una clave puede tener como máximo una
versión vigente. Se usan intervalos `[valid_from, valid_to)` y `None` como
fin abierto. Solo un cambio real de `region`, incluidos cambios con `None`,
cierra la versión vigente y crea otra.

Una instantánea no puede repetir claves ni incluir claves nulas; una fecha
anterior a la versión vigente se rechaza. Si hay un cambio en la misma fecha
que el inicio vigente se rechaza para no generar intervalos vacíos; una
repetición idéntica no cambia la historia. El algoritmo local copia su
entrada y no escribe ficheros ni tablas. No resuelve CDC, borrados,
reprocesamiento retroactivo ni concurrencia: diseñarlos con el cliente antes
de implementar en Delta.
