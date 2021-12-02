# uso-servidor-VIC-SMN

## Buenas prácticas para el uso del Servidor VIC del Servicio Meteorológico Nacional (SMN)
El Servidor VIC es un procesador para la generación de productos y servicios de la Dirección de Servicios Sectoriales del SMN. Se encuentra instalado en un entorno Linux, distribución Ubuntu. El mismo cuenta con dos lugares de almacenado principales: */home* y */data*.

### /home
En el */home* se almacenan las carpetas de los distintos usuarios que se encuentran en el servidor, por ejemplo: **agro**, **hidro**, **ebontempi**, **cbolzi**, **lferreira**, etc. Debido a que el espacio en */home* es muy limitado, cuenta con un total de espacio de 9.8GB, el objetivo de este lugar es que NO almacene archivos muy pesados. Por lo tanto, está pensado para almacenar cosas livianas, como por ejemplo: scripts de lenguajes de programación, algún pequeño archivo de metadatos, etc.
