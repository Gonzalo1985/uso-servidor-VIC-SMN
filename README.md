# uso-servidor-VIC-SMN

# Buenas prácticas para el uso del Servidor VIC del Servicio Meteorológico Nacional (SMN)

## Almacenamiento en VIC
El Servidor VIC es un procesador para la generación de productos y servicios de la Dirección de Servicios Sectoriales (DSS) del SMN. Se encuentra instalado en un entorno Linux, distribución Ubuntu. El mismo cuenta con dos lugares de almacenado principales: */home* y */data*, y dos secundarios: */ms-36* y */ms-270*.

### /home
En el */home* se almacenan las carpetas de los distintos usuarios que se encuentran generados en el servidor, por ejemplo: **agro**, **hidro**, **ebontempi**, **cbolzi**, **lferreira**, etc. Debido a que el espacio en */home* es muy limitado, cuenta con un total de espacio de 9.8GB, el objetivo de este lugar es NO almacenar archivos muy pesados. Por lo tanto, está pensado para almacenar cosas livianas, como por ejemplo: scripts de lenguajes de programación, algún pequeño archivo de metadatos, etc.

### /data
En el */data* se almacenan archivos necesarios para ejecutar los scripts que se encuentren en */home* y debido a que es un lugar con un mayor almacenamiento (pero tampoco tan grande) pueden ubicarse ahí archivos más pesados. Por ejemplo: archivos de datos, archivos de parámetros para modelos, etc. El espacio total de */data* es de 1.5TB.

### /ms-36 y /ms-270
Por otro lado, el Servidor VIC cuenta con acceso a otros lugares de almacenamiento más importantes, como son el */ms-36* y el */ms-270*. Respectivamente, en total, ambos tienen aproximadamente 36TB y 270TB de espacio. Por lo tanto, aquí también podrían almacenarse archivos más grandes. Dentro de */ms-36* se encuentra una carpeta */hidro* en donde también se guardan varios archivos shp para su utilización en gráficos o proyectos. Por lo tanto, además de archivos de datos y de parámetros, también podría utilizarse el */ms-36* como un lugar para almacenar archivos estáticos (contornos de provincias, cuencas, etc.). Inicialmente, el */ms-270* no es utilizado como un lugar de almacenamiento en la DSS.

## Instalación de librerías en R
Entre algunos de los software de lenguaje de programación en VIC, se encuentra R (https://www.r-project.org). Es muy habitual el uso de librerías o paquetes en R que se van instalando a medida de la necesidad del usuario. Debido a que por DEFAULT, cuando uno instala una librería en R, esta es instalada en el */home* del usuario, es necesario indicarle a R que la librería no sea instalada ahí (ya que esto podría producir que colapse el almacenamiento en */home*).

Para llevar a cabo esto, cuando se instala la librería por línea de comando, se debe indicar a través del parámetro **lib**, donde instalar la librería. Un ejemplo para instalar el paquete 'lubridate', por línea de comando, sería el siguiente:

```{r echo = FALSE}
install.packages("lubridate", lib = "/data/R-libs/x86_64-pc-linux-gnu-library/3.4")
```

Notar que, el lugar que debe indicarse para instalar la librería o paquete es en una posición alojada en */data*.

## Levantar librería en R desde */data*
En la sección anterior se abarcó el tema de como instalar una librería o paquete en R en una ruta específica. Ahora, para poder *levantar* o *abrir* una librería previamente instalada en la ruta específica, es cuestión de indicarle esta ruta a través del parámetro **lib.loc** de la función *library*.

Entonces, la forma de levantar la librería "lubridate" desde la ruta ubicada en */data*, sería de la siguiente manera:

```{r echo = FALSE}
library("lubridate", lib.loc = "/data/R-libs/x86_64-pc-linux-gnu-library/3.4")
```
Notar que algunos paquetes específicos de R a veces pueden ser levantados únicamente con la función *require*. Siempre es bueno intentar primero con *library* y si esto no funciona, probar con *require*.
