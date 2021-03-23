

<img src="https://ciudadesabiertas.es/assets/img/cabiertas/logo.svg" alt="LogoCiudadesAbiertas" width="200"/> 

# DESARROLLO API REST DE DATOS REUTILIZABLE. MODELO DE TABLAS: AUTOBÚS

&nbsp;

## **ÍNDICE**   
1. [AUTORES](#id1)
2. [LINKS](#id2)
3. [DIAGRAMA CONCEPTUAL](#id3)
4. [TABLAS](#id4)  
    - [AUTOBUS_AUTHORITY](#id5)  
    - [AUTOBUS_OPERATOR](#id6)  
    - [AUTOBUS_LINEA](#id7)  
    - [AUTOBUS_REL_LINEA_INCIDENCIA](#id8) 
    - [AUTOBUS_ROUTE](#id9) 
    - [AUTOBUS_INCIDENCIA](#id10)  
    - [AUTOBUS_POINTONROUTE](#id11) 
    - [AUTOBUS_JOURNEYPATTERN](#id12)  
    - [AUTOBUS_STOPPOINTINJOURNEYPATTERN](#id13) 
    - [AUTOBUS_PARADA](#id14) 
    - [AUTOBUS_VEHICLEJOURNEY](#id15)  
    - [AUTOBUS_REALTIMEPASSINGTIME](#id16) 
    - [AUTOBUS_HEADWAYJOURNEYGROUP](#id17)    
    - [AUTOBUS_HEADWAYINTERVAL](#id18) 
    - [AUTOBUS_SERVICECALENDAR](#id19) 
    - [AUTOBUS_DAYTYPEASSIGNMENT](#id20)  
    - [AUTOBUS_DAYTYPE](#id21)   



&nbsp;

## AUTORES <a name="id1"></a>
- Adolfo Antón Bravo
- Edna Ruckhaus
- Hugo Lafuente Matesanz
- Leticia Rubalcaba
- Oscar Corcho
- Paola Espinoza Arias

&nbsp;

## LINKS <a name="id2"></a>


Este documento contiene la información detallada del modelo de datos asociado al vocabulario de los convenios. A continuación, se detallan los enlaces de interés asociados a este vocabulario:

- *[Documentación](http://vocab.ciudadesabiertas.es/def/transporte/autobus/index-es.html)*
- *[Repositorio](https://github.com/CiudadesAbiertas/vocab-transporte-autobus)*
- *[Webinar](https://www.youtube.com/watch?v=RcP9dplKb3A&list=PLuvmjKgQP8bXSFG289dUU4I6hOQZhjxUW)*
- *[Requisitos](https://github.com/CiudadesAbiertas/vocab-transporte-autobus/tree/master/Requirements)*
- *[Issues](https://github.com/CiudadesAbiertas/vocab-transporte-autobus/issues)*

&nbsp;

## DIAGRAMA CONCEPTUAL <a name="id3"></a>
&nbsp;
El vocabulario se ha dividido en tres grandes partes: Operador y sus líneas, Rutas y paradas y Viajes.
&nbsp;
### OPERADOR Y SUS LINEAS
Un operador es una empresa que ofrece servicio de transporte público. En GTFS se representa como una TransitAgency. Asimismo para representar una línea del servicio público de transporte de autobuses urbanos se crea una instancia de la clase de nueva creación esautob:Linea. La Figura 1 muestra las clases y propiedades del vocabulario de tráfico.

&nbsp;
![Diagrama conceptual](http://vocab.ciudadesabiertas.es/def/transporte/autobus/resources/images/vocabulario-autobus.png)
Figura 1
&nbsp;

### RUTAS Y PARADAS
Uno de los conceptos más ricos de Transmodel es el de las rutas. Para explicarlo se ha realizado el diagrama de la Figura 2, donde se ve cómo se despliega la representación de la información de una ruta. Esta sección del vocabulario se centra en la secuencia de enlaces, con las subclases ruta y patrón de viaje. 
Una parada del servicio público de transporte de autobuses urbanos es una zona tmcommons:Zone es la superclase de lugar tmcommons:Place y esta a su vez de la clase de nueva creación esautob:Parada. A continuación, en la Figura 3 tenemos un diagrama de Parada, y cómo se relaciona con Place, Dirección postal y línea.

&nbsp;
![Diagrama conceptual](http://vocab.ciudadesabiertas.es/def/transporte/autobus/resources/images/link-sequence.png)
Figura 2
&nbsp;

&nbsp;
![Diagrama conceptual](http://vocab.ciudadesabiertas.es/def/transporte/autobus/resources/images/parada.png)
Figura 3
&nbsp;

### VIAJES
Además de línea, ruta y patrón de viaje, en Transmodel está el concepto viaje del vehículo tmjourney:VehicleJourney que representa el modelo de viaje que realiza el vehículo usando tmjourney:madeUsing patrones de viaje tmjourney:JourneyPattern. La Figura 4 muestra un diagrama con los viajes del vehículo, horarios de cabecera, intervalos, tipos de día, calendarios de servicio y su asignación a día tipo.

&nbsp;
![Diagrama conceptual](http://vocab.ciudadesabiertas.es/def/transporte/autobus/resources/images/vehicle-journey.png)
Figura 4
&nbsp;


## TABLAS <a name="id4"></a>
En principio se considera esta estructura de datos bastante estable y no se estima que sufrirá cambios. Pero puesto que la actuación D2, que es donde se enmarca la definición de estas tablas, aún está en desarrollo, no se puede asegurar al 100% que será la definitiva.     

[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### AUTOBUS_AUTHORITY <a name="id5"></a>
&nbsp;

|     Campo             |     Tipo            |     Ejemplo                                 |     Descripción                                                                |     URL                                                                                                         |
|-----------------------|---------------------|---------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
|     ikey              |     VARCHAR(50)     |     BUSAUTH01                               |     Identificador de la   Tabla (PK).                                          |                                                                                                                 |
|     id                |     VARCHAR(50)     |     CRTM                                    |                                                                                |     http://purl.org/dc/terms/identifier                                                                         |
|     telephone         |     VARCHAR(200)    |     +34 91 406   88 10                      |     Teléfono de   información y contacto con la entidad.                       |     http://schema.org/telephone                                                                                 |
|     email             |     VARCHAR(200)    |     info@crtm.es                            |     Correo   electrónico de información.                                       |     http://schema.org/email                                                                                     |
|     url               |     VARCHAR(400)    |     nfo@crtm.es                             |     Dirección   URL pública donde puedes obtener información de la entidad.    |     http://schema.org/url                                                                                       |
|     street_address    |     VARCHAR(200)    |     Calle Cerro   de la Plata, 4            |     La dirección   de una parada.                                              |     http://schema.org/address                                                                                   |
|     postal_code       |     VARCHAR(10)     |     28007                                   |     Una   dirección postal según el vocabulario esdir.                         |     http://vocab.linkeddata.es/datosabiertos/def/urbanismo-infraestructuras/direccion-postal#DireccionPostal    |
|     legal_name        |     VARCHAR(200)    |     Consorcio de   transportes de Madrid    |     Nombre legal.                                                              |     http://schema.org/legalName                                                                                 |
|     alternate_name    |     VARCHAR(200)    |     CRTM                                    |     Nombre   alternativo, popular o por el que se conoce a algo.               |     http://schema.org/alternateName                                                                             |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### AUTOBUS_OPERATOR <a name="id6"></a>
&nbsp;

|     Campo             |     Tipo            |     Ejemplo                                   |Descripción   |URL|
|-----------------------|---------------------|-------------------------------------------------------------------|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
|ikey|VARCHAR(50)|BUSOPE01|Identificador de la   Tabla (PK).|                                 |
|id|     VARCHAR(50)     |     EMT                                                           |                                                                                         |     http://purl.org/dc/terms/identifier                                                                         |
|serving_pt_for|VARCHAR(50)|CRTM|Esta propiedad indica para qué   Autoridad está trabajando la entidad operadora.|http://w3id.org/transmodel/organisations#servingPTFor|
|telephone|VARCHAR(200)|+34 91 406 88   10|Teléfono de   información y contacto con la entidad.|http://schema.org/telephone |
|email|VARCHAR(200)|https://www.emtmadrid.es/AtencionAlCliente/Agradecimientos    |Correo   electrónico de información.|http://schema.org/email|
|url|VARCHAR(400)|https://www.emtmadrid.es/Servicios/Contactar|Dirección   URL pública donde puedes obtener información de la entidad.|http://schema.org/url  |
|street_address|VARCHAR(200)|Calle Cerro   de la Plata, 4|La dirección   de una parada.|http://schema.org/address|
|postal_code|VARCHAR(10)|28007|Una   dirección postal según el vocabulario esdir.|http://vocab.linkeddata.es/datosabiertos/def/urbanismo-infraestructuras/direccion-postal#DireccionPostal    |
|legal_name|VARCHAR(200)|Empresa Municipal de   Transportes|Nombre legal. |http://schema.org/legalName|
|alternate_name|VARCHAR(200)|EMT|Nombre   alternativo, popular o por el que se conoce a algo.|http://schema.org/alternateName|



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### AUTOBUS_LINEA <a name="id7"></a>
&nbsp;


|Campo             |     Tipo             |     Ejemplo                                                                                |     Descripción                                                                                                                                            |     URL                                                                      |
|-----------------------|----------------------|--------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
|     ikey              |     VARCHAR(50)      |     BUSLIN01                                                                               |     Identificador de la   Tabla (PK).                                                                                                                      |                                                                              |
|     id                |     VARCHAR(50)      |     138                                                                                    |                                                                                                                                                            |     http://purl.org/dc/terms/identifier                                      |
|     description       |     VARCHAR(4000)    |     Línea 138,   comienzo en Cristo Rey y final en San Ignacio de Loyola                   |     Una   descripción del recurso dentro de un contexto dado.                                                                                              |     http://purl.org/dc/terms/description                                     |
|     title             |     VARCHAR(200)     |     Línea   138                                                                            |     Nombre   o título de la línea del autobús.                                                                                                             |     http://purl.org/dc/terms/title                                           |
|     url               |     VARCHAR(400)     |     https://www.emtmadrid.es/Bloques-EMT/EMT-BUS/Mi-linea-(1).aspx?linea=138&lang=es-ES    |     Dirección   URL pública donde puedes obtener información de la entidad.                                                                                |     http://schema.org/url                                                    |
|     short_name        |     VARCHAR(200)     |     138                                                                                    |     Nombre   corto para algo que lo necesite.                                                                                                              |     http://w3id.org/transmodel/commons#shortName                             |
|     cabecera_linea    |     VARCHAR(50)      |     4608                                                                                   |     Indica   cuál es la parada de cabecera de la línea.                                                                                                    |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#cabeceraLinea    |
|     final_linea       |     VARCHAR(50)      |     5481                                                                                   |     Indica   cuál es la parada de final de la línea.                                                                                                       |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#finalLinea       |
|     distancia         |     DOUBLE           |     58                                                                                     |     Distancia   total para una Línea o una Ruta o similares.                                                                                               |     http://w3id.org/transmodel/journeys#distance                             |
|     operating         |     VARCHAR(50)      |     emt                                                                                    |     Esta   propiedad señala qué Líneas están operadas por qué Operador.                                                                                    |     http://w3id.org/transmodel/organisations#operating                       |
|     colour            |     VARCHAR(200)     |     Azul                                                                                   |     Esta   propiedad permite describir el color de algo que va en Presentación de   información, como por ejemplo el color identificativo de una línea.    |     http://w3id.org/transmodel/commons#colour                                |
|     text_colour       |     VARCHAR(200)     |     Negro                                                                                  |     El color que   se usa para representar el texto asociado con una Presentación, por ejemplo   de una línea.                                             |     http://w3id.org/transmodel/commons#textColour                            |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### AUTOBUS_REL_LINEA_INCIDENCIA <a name="id8"></a>
&nbsp;

|     Campo                  |     Tipo           |     Ejemplo                                 |     Descripción                                                      |     URL                                                                              |
|----------------------------|--------------------|---------------------------------------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------------|
|     ikey                   |     VARCHAR(50)    |     BUSLININC01                             |     Identificador de la Tabla (PK).                                  |                                                                                      |
|     id                     |     VARCHAR(50)    |     138                                     |                                                                      |     http://purl.org/dc/terms/identifier                                              |
|     afectada_incidencia    |     VARCHAR(50)    |     29059944-382A-49AA-A068-B55BF2FAC51F    |     Relación de una línea que está afectada   por una incidencia.    |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#afectadaPorIncidencia    |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### AUTOBUS_ROUTE <a name="id9"></a>
&nbsp;

|     Campo             |     Tipo             |     Ejemplo                                                                 |     Descripción                                                                   |     URL                                                  |
|-----------------------|----------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------|
|     ikey              |     VARCHAR(50)      |     BUSROU01                                                                |     Identificador de la Tabla (PK).                                               |                                                          |
|     id                |     VARCHAR(50)      |     138a                                                                    |                                                                                   |     http://purl.org/dc/terms/identifier                  |
|     description       |     VARCHAR(4000)    |     Línea 138, comienzo en Cristo Rey y final en San Ignacio de   Loyola    |     Una descripción del recurso dentro de un contexto dado.                       |     http://purl.org/dc/terms/description                 |
|     direction_type    |     VARCHAR(200)     |     outbound                                                                |     Esta propiedad permite   describir el tipo de dirección para una Ruta.        |     http://w3id.org/transmodel/journeys#directionType    |
|     on                |     VARCHAR(50)      |     138                                                                     |     Esta propiedad conecta el patrón de viaje con la ruta en la que   trabaja.    |     http://w3id.org/transmodel/journeys#on               |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### AUTOBUS_INCIDENCIA <a name="id10"></a>
&nbsp;


|     Campo                 |     Tipo             |     Ejemplo                                                                                   |     Descripción                                                                                                |     URL                                                                                        |
|---------------------------|----------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
|     ikey                  |     VARCHAR(50)      |     BUSINC01                                                                                  |     Identificador de la   Tabla (PK).                                                                          |                                                                                                |
|     id                    |     VARCHAR(50)      |     29059944-382A-49AA-A068-B55BF2FAC51F                                                      |                                                                                                                |     http://purl.org/dc/terms/identifier                                                        |
|     description           |     VARCHAR(4000)    |     Corte de calles   entre el cruce de Alcalá con Gran Vía y la Plaza de la Independencia    |     Una   descripción del recurso dentro de un contexto dado.                                                  |     http://purl.org/dc/terms/description                                                       |
|     tipo_incidencia       |     VARCHAR(50)      |     obras                                                                                     |     Es de tipo   SKOS:     http://vocab.linkeddata.es/datosabiertos/kos/transporte/trafico/tipo-incidencia     |     http://vocab.ciudadesabiertas.es/def/transporte/trafico#tipoIncidencia                     |
|     date_posted           |     DATETIME         |     2020-03-31   08:00:00                                                                     |     La fecha y   hora de publicación de una incidencia (en formato fecha ISO 8601)                             |     http://schema.org/datePosted                                                               |
|     num_sentidos          |     INTEGER          |     2                                                                                         |     Número de   sentidos de circulación                                                                        |     http://vocab.ciudadesabiertas.es/def/transporte/trafico#numSentidos                        |
|     num_carriles          |     INTEGER          |     8                                                                                         |     Número de   carriles de circulación                                                                        |     http://vocab.ciudadesabiertas.es/def/transporte/trafico#numCarriles                        |
|     es_recurrente         |     BIT(1)           |     0                                                                                         |     Esta   propiedad permite describir si la incidencia es recurrente o no.                                    |     http://vocab.ciudadesabiertas.es/def/transporte/trafico#esRecurrente                       |
|     fecha_fin_prevista    |     DATETIME         |     2020-05-03   23:59:00                                                                     |     La fecha y   hora prevista de finalización de una incidencia planificada (en formato fecha   ISO 8601).    |     http://vocab.ciudadesabiertas.es/def/transporte/trafico#fechaFinPrevista                   |
|     x_etrs89              |     DECIMAL(13,5)    |     440124.33000                                                                              |     Coordenada X   en metros (ETRS89).                                                                         |     https://datos.ign.es/def/geo_core#xETRS89                                                  |
|     y_etrs89              |     DECIMAL(13,5)    |     4474637.17000                                                                             |     Coordenada Y   en metros (ETRS89).                                                                         |     https://datos.ign.es/def/geo_core#yETRS89                                                  |
|     incidencia_tramo      |     VARCHAR(50)      |     TRAFTRAM01                                                                                |     Relación de   la Incidencia con el Tramo donde se produce la misma.                                        |     http://vocab.ciudadesabiertas.es/def/transporte/trafico/index-es.html#incidenciaEnTramo    |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### AUTOBUS_POINTONROUTE <a name="id10"></a>
&nbsp;

|     Campo                      |     Tipo           |     Ejemplo        |     Descripción                                                                                                                                                                 |     URL                                                         |
|--------------------------------|--------------------|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
|     ikey                       |     VARCHAR(50)    |     BUSPOIROU01    |     Identificador de la   Tabla (PK).                                                                                                                                           |                                                                 |
|     id                         |     VARCHAR(50)    |     138b-4608      |                                                                                                                                                                                 |     http://purl.org/dc/terms/identifier                         |
|     order                      |     INTEGER        |     1              |     Orden de un   Punto en una Secuencia de Enlaces (Link Sequence) y por tanto de un Punto en   una Ruta o en cualquier otra estructura similar.                               |     http://w3id.org/transmodel/journeys#order                   |
|     distance_from_start        |     DOUBLE         |     0              |     Para   un Punto en una Secuencia de enlaces (o similares), esta propiedad representa   la distancia desde el comienzo del correspondiente Patrón de Viaje o   similares.    |     http://w3id.org/transmodel/journeys#distanceFromStart       |
|     in                         |     VARCHAR(50)    |     138a           |                                                                                                                                                                                 |                                                                 |
|     functional_centroid_for    |     VARCHAR(50)    |     4608           |     Esta   propiedad permite la conexión de un Punto con una Zona.                                                                                                              |     http://w3id.org/transmodel/commons#functionalCentroidFor    |


[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### AUTOBUS_JOURNEYPATTERN <a name="id11"></a>
&nbsp;

|     Campo                      |     Tipo            |     Ejemplo                                 |     Descripción                                                                                                  |     URL                                                                              |
|--------------------------------|---------------------|---------------------------------------------|------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
|     ikey                       |     VARCHAR(50)     |     BUSJOUPAT01                             |     Identificador de la Tabla (PK).                                                                              |                                                                                      |
|     id                         |     VARCHAR(50)     |     138a2                                   |                                                                                                                  |     http://purl.org/dc/terms/identifier                                              |
|     title                      |     VARCHAR(200)    |     138a2                                   |     Nombre o título.                                                                                             |     http://purl.org/dc/terms/title                                                   |
|     distance                   |     DOUBLE          |     11,194                                  |     Distancia total para una Línea o una Ruta o similares.                                                       |     http://w3id.org/transmodel/journeys#distance                                     |
|     on                         |     VARCHAR(50)     |     138a                                    |     Esta propiedad conecta el patrón de viaje con la ruta en la que   trabaja.                                   |     http://w3id.org/transmodel/journeys#on                                           |
|     generado_por_incidencia    |     VARCHAR(50)     |     29059944-382A-49AA-A068-B55BF2FAC51F    |     Relación de un patrón de viaje de una ruta que se ha creado por   una incidencia.                            |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#generadoPorIncidencia    |
|     front_text                 |     VARCHAR(50)     |     San Ignacio de Loyola                   |     Texto que se muestra normalmente en la parte frontal de un   vehículo del servicio público de transporte.    |     http://w3id.org/transmodel/journeys#frontText                                    |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### AUTOBUS_STOPPOINTINJOURNEYPATTERN <a name="id12"></a>
&nbsp;

|     Campo                      |     Tipo            |     Ejemplo         |     Descripción                                                                                                                                      |     URL                                                         |
|--------------------------------|---------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
|     ikey                       |     VARCHAR(50)     |     BUSSTOPOI01     |     Identificador de la   Tabla (PK).                                                                                                                |                                                                 |
|     id                         |     VARCHAR(50)     |     138a1-4608      |                                                                                                                                                      |     http://purl.org/dc/terms/identifier                         |
|     order                      |     INTEGER         |     1               |     Orden de un   Punto en una Secuencia de Enlaces (Link Sequence) y por tanto de un Punto en   una Ruta o en cualquier otra estructura similar.    |     http://w3id.org/transmodel/journeys#order                   |
|     stop_use                   |     VARCHAR(200)    |     pass-through    |     Permite la   descripción del tipo de uso de una parada: acceso, intercambio, de paso, etc.                                                       |     http://w3id.org/transmodel/journeys#stopUse                 |
|     in                         |     VARCHAR(50)     |     138a2           |                                                                                                                                                      |                                                                 |
|     functional_centroid_for    |     VARCHAR(50)     |     4608            |     Esta   propiedad permite la conexión de un Punto con una Zona.                                                                                   |     http://w3id.org/transmodel/commons#functionalCentroidFor    |
|     alighting                  |     BIT(1)          |     1               |     Esta   propiedad indica si la parada se puede usar para bajarse o no.                                                                            |     http://w3id.org/transmodel/journeys#forAlighting            |
|     boarding                   |     BIT(1)          |     0               |     Esta   propiedad indica si se puede montar en la parada.                                                                                         |     http://w3id.org/transmodel/journeys#forBoarding             |
|     title_stop_area            |     VARCHAR(200)    |     Cristo Rey      |     Un grupo de   Paradas que están próximas entre sí.                                                                                               |     http://w3id.org/transmodel/journeys#StopArea                |


&nbsp;
### AUTOBUS_PARADA <a name="id13"></a>
&nbsp;

|     Campo                |     Tipo             |     Ejemplo                           |     Descripción                                                                                                                         |     URL                                                                                                         |
|--------------------------|----------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
|     ikey                 |     VARCHAR(50)      |     BUSPAR1                           |     Identificador de la Tabla (PK).                                                                                                     |                                                                                                                 |
|     id                   |     VARCHAR(50)      |     3086                              |                                                                                                                                         |     http://purl.org/dc/terms/identifier                                                                         |
|     description          |     VARCHAR(4000)    |     Manuel Becerra                    |     Una   descripción del recurso dentro de un contexto dado.                                                                           |     http://purl.org/dc/terms/description                                                                        |
|     title                |     VARCHAR(200)     |     Manuel Becerra                    |     Nombre o título de la parada del   autobús.                                                                                         |     http://purl.org/dc/terms/title                                                                              |
|     url                  |     VARCHAR(400)     |     https://emtmadrid.es/paradas/#    |     Dirección URL pública donde puedes   obtener información de la entidad.                                                             |     http://schema.org/url                                                                                       |
|     wifi                 |     BIT(1)           |     0                                 |     La parada dispone de conexión Wifi   pública.                                                                                       |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#wifi                                                |
|     panel_electronico    |     BIT(1)           |     1                                 |     La   Parada dispone de un Panel Electrónico Informativo que permite dar   información actualizada de tiempos de llegada y otros.    |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#panelElectronico                                    |
|     zona                 |     VARCHAR(10)      |     A                                 |     Zona a la que pertenece la Parada.                                                                                                  |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#zona                                                |
|     x_etrs89             |     DECIMAL(13,5)    |     440124.33000                      |     Coordenada X   en metros (ETRS89).                                                                                                  |     https://datos.ign.es/def/geo_core#xETRS89                                                                   |
|     y_etrs89             |     DECIMAL(13,5)    |     4474637.17000                     |     Coordenada Y   en metros (ETRS89).                                                                                                  |     https://datos.ign.es/def/geo_core#yETRS89                                                                   |
|     portal_id            |     VARCHAR(50)      |     496400                            |                                                                                                                                         |                                                                                                                 |
|     street_address       |     VARCHAR(200)     |     Calle Cerro de la Plata, 4        |     La dirección de una Parada.                                                                                                         |     http://schema.org/address                                                                                   |
|     postal_code          |     VARCHAR(10)      |     28007                             |     Una   dirección postal según el vocabulario esdir.                                                                                  |     http://vocab.linkeddata.es/datosabiertos/def/urbanismo-infraestructuras/direccion-postal#DireccionPostal    |






&nbsp;
### AUTOBUS_VEHICLEJOURNEY <a name="id14"></a>
&nbsp;

|     Campo               |     Tipo           |     Ejemplo            |     Descripción                                                                                                                                  |     URL                                                    |
|-------------------------|--------------------|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
|     ikey                |     VARCHAR(50)    |     BUSVEHJOU01        |     Identificador de la Tabla (PK).                                                                                                              |                                                            |
|     id                  |     VARCHAR(50)    |     110a1              |                                                                                                                                                  |     http://purl.org/dc/terms/identifier                    |
|     journey_duration    |     VARCHAR(50)    |     P1D                |     Duración programada del viaje de un   vehículo.                                                                                              |     http://w3id.org/transmodel/journeys#journeyDuration    |
|     departure_time      |     TIME           |     09:00:00+02:00     |     Hora de salida programada del viaje de   un vehículo.                                                                                        |     http://w3id.org/transmodel/journeys#departureTime      |
|     made_using          |     VARCHAR(50)    |     138a2              |     Esta propiedad conecta algunas clases   con otras que hacen posible su funcionamiento.                                                       |     http://w3id.org/transmodel/journeys#madeUsing          |
|     worked_on           |     VARCHAR(50)    |     laborable          |     Relación entre el Viaje de un Vehículo   y el Día Tipo.                                                                                      |     http://w3id.org/transmodel/journeys#workedOn           |
|     composed_of         |     VARCHAR(50)    |     138a1-laborable    |     Un Viaje de Vehículo compuesto de   indicaciones de viaje en cabecera de línea donde se indican las salidas del   primero y último viaje.    |     http://w3id.org/transmodel/journeys#composedOf         |
|     direction_type      |     VARCHAR(50)    |     outbound           |     Esta propiedad permite describir el   tipo de dirección para una Ruta.                                                                       |     http://w3id.org/transmodel/journeys#directionType      |



&nbsp;
### AUTOBUS_REALTIMEPASSINGTIME <a name="id15"></a>
&nbsp;

|     Campo                      |     Tipo           |     Ejemplo                |     Descripción                                                                                             |     URL                                                                            |
|--------------------------------|--------------------|----------------------------|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
|     ikey                       |     VARCHAR(50)    |     BUSREATIM01            |     Identificador de la Tabla (PK).                                                                         |                                                                                    |
|     id                         |     VARCHAR(50)    |     138a1-4608             |                                                                                                             |     http://purl.org/dc/terms/identifier                                            |
|     result_time                |     DATETIME       |     2020-05-13T12:45:05    |     Esta propiedad establece la fecha/hora   de la observación.                                             |     http://www.w3.org/ns/sosa/resultTime                                           |
|     expected_arrival_bus       |     VARCHAR(50)    |     PT15M                  |     Tiempo de llegada prevista para un   autobús en una parada, duración de esautob:RealTimePassingTime.    |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#expectedArrivalTime    |
|     has_feature_of_interest    |     VARCHAR(50)    |     138a1-4608             |     La   observación esautob: RealTimePassingTime aparece en tmjourney: PointInLinkSequence.                |     http://www.w3.org/ns/sosa/hasFeatureOfInterest                                 |



&nbsp;
### AUTOBUS_HEADWAYJOURNEYGROUP <a name="id16"></a>
&nbsp;

|     Campo                   |     Tipo           |     Ejemplo            |     Descripción                                                                            |     URL                                                       |
|-----------------------------|--------------------|------------------------|--------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|     ikey                    |     VARCHAR(50)    |     BUSHEAJOU01        |     Identificador de la Tabla (PK).                                                        |                                                               |
|     id                      |     VARCHAR(50)    |     138a1-laborable    |                                                                                            |     http://purl.org/dc/terms/identifier                       |
|     first_departure_time    |     TIME           |     06:15:00+02:00     |     La hora de inicio de un Viaje de un   Vehículo.                                        |     http://w3id.org/transmodel/journeys#firstDepartureTime    |
|     last_departure_time     |     TIME           |     23:30:00+02:00     |     La hora de fin de un Viaje de un   Vehículo.                                           |     http://w3id.org/transmodel/journeys#lastDepartureTime     |
|     determined_by           |     VARCHAR(50)    |     138-laborable      |     Un grupo de viajes de cabecera de línea   con un intervalo desde cabecera de línea.    |     http://w3id.org/transmodel/journeys#determinedBy          |




&nbsp;
### AUTOBUS_HEADWAYINTERVAL <a name="id17"></a>
&nbsp;

|     Campo                         |     Tipo            |     Ejemplo             |     Descripción                                             |     URL                                                             |
|-----------------------------------|---------------------|-------------------------|-------------------------------------------------------------|---------------------------------------------------------------------|
|     ikey                          |     VARCHAR(50)     |     BUSHEAINT01         |     Identificador de la Tabla (PK).                         |                                                                     |
|     id                            |     VARCHAR(50)     |     138-laborable       |                                                             |     http://purl.org/dc/terms/identifier                             |
|     minimum_headway_interval      |     VARCHAR(50)     |     P7M                 |     Mínimo intervalo/frecuencia fijada   desde cabecera.    |     http://w3id.org/transmodel/journeys#minimumHeadwayInterval      |
|     maximum_headway_interval      |     VARCHAR(50)     |     P20M                |     Máximo intervalo/frecuencia fijada   desde cabecera.    |     http://w3id.org/transmodel/journeys#maximumHeadwayInterval      |
|     scheduled_headway_interval    |     VARCHAR(200)    |     Cada 7 - 20 min.    |     Intervalo/frecuencia   programada desde cabecera.       |     http://w3id.org/transmodel/journeys#scheduledHeadwayInterval    |





&nbsp;
### AUTOBUS_SERVICECALENDAR <a name="id18"></a>
&nbsp;

|     Campo          |     Tipo             |     Ejemplo                                                |     Descripción                                                                   |     URL                                             |
|--------------------|----------------------|------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------|
|     ikey           |     VARCHAR(50)      |     BUSSERCAL01                                            |     Identificador de la Tabla (PK).                                               |                                                     |
|     id             |     VARCHAR(50)      |     2020                                                   |                                                                                   |     http://purl.org/dc/terms/identifier             |
|     title          |     VARCHAR(200)     |     Calendario de servicio de la EMT Madrid   para 2020    |     Nombre o título del calendario.                                               |     http://purl.org/dc/terms/title                  |
|     description    |     VARCHAR(4000)    |     Calendario de servicio de la EMT Madrid   para 2020    |     Una   descripción del recurso dentro de un contexto dado.                     |     http://purl.org/dc/terms/description            |
|     short_name     |     VARCHAR(200)     |     Calendario Servicio EMT Madrid 2020                    |     Nombre corto para algo que lo necesite.                                       |     http://w3id.org/transmodel/commons#shortName    |
|     from           |     DATETIME         |     2020-01-01                                             |     Esta propiedad permite describir el   inicio de un calendario de servicio.    |     http://w3id.org/transmodel/journeys#from        |
|     to             |     DATETIME         |     2020-12-31                                             |     Esta propiedad permite describir el fin   de un calendario de servicio.       |     http://w3id.org/transmodel/journeys#to          |






&nbsp;
### AUTOBUS_DAYTYPEASSIGNMENT <a name="id19"></a>
&nbsp;


|     Campo                    |     Tipo           |     Ejemplo                     |     Descripción                                                                                                                                 |     URL                                                |
|------------------------------|--------------------|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
|     ikey                     |     VARCHAR(50)    |     BUSDAYASS01                 |     Identificador de la Tabla (PK).                                                                                                             |                                                        |
|     id                       |     VARCHAR(50)    |     20200102-CAL01-laborable    |                                                                                                                                                 |     http://purl.org/dc/terms/identifier                |
|     date                     |     DATETIME       |     2020-01-02                  |     Fecha de una Asignación de Día Tipo.                                                                                                        |     http://w3id.org/transmodel/journeys#date           |
|     is_available             |     BIT(1)         |     1                           |     Propiedad que determina si una   Asignación de Día Tipo está disponible o no.                                                               |     http://w3id.org/transmodel/journeys#isAvailable    |
|     specifying               |     VARCHAR(50)    |     laborable                   |     La   asignación de características operativas expresadas en Día Tipo a un Día   Operativo particular dentro de un Calendario de Servicio    |     http://w3id.org/transmodel/journeys#specifying     |
|     for_the_definition_of    |     VARCHAR(50)    |     2020                        |     Establece la relación entre un   Calendario de Servicio y la Asignación de Día Tipo.                                                        |     http://w3id.org/transmodel/journeys#definedBy      |




&nbsp;
### AUTOBUS_DAYTYPE <a name="id20"></a>
&nbsp;


|     Campo            |     Tipo             |     Ejemplo                                                        |     Descripción                                                              |     URL                                                 |
|----------------------|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------|---------------------------------------------------------|
|     ikey             |     VARCHAR(50)      |     BUSDAYTYP01                                                    |     Identificador de la Tabla (PK).                                          |                                                         |
|     id               |     VARCHAR(50)      |     laborable                                                      |                                                                              |     http://purl.org/dc/terms/identifier                 |
|     title            |     VARCHAR(200)     |     Día laborable                                                  |     Nombre o título del tipo de día.                                         |     http://purl.org/dc/terms/title                      |
|     description      |     VARCHAR(4000)    |     Horario general para el servicio de EMT   en día laborable.    |     Una   descripción del recurso dentro de un contexto dado.                |     http://purl.org/dc/terms/description                |
|     short_name       |     VARCHAR(200)     |     Laborables                                                     |     Nombre corto para algo que lo necesite.                                  |     http://w3id.org/transmodel/commons#shortName        |
|     earliest_time    |     TIME             |     5:30:00                                                        |     Hora más temprana para el inicio de un   servicio un cierto día tipo.    |     http://w3id.org/transmodel/journeys#earliestTime    |



&nbsp;








<p float="right" align="center">
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/gobEspana-logo.svg" alt="Logo Gobierno España" width="200"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/red-logo.svg" alt="Logo red.es" width="150"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ciudadesInteligentes-logo.svg" alt="Logo CiudadesInteligentes" width="150"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/unionEuropea-logo.svg" alt="Logo UnionEuropea" width="200"/>
</p>


<p float="right" align="center">
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntAcoruna-logo.svg" alt="Logo AyuntACoruña" width="200"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntMadrid-logo.svg" alt="Logo Madrid" width="100"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntSantiagoCompostela-logo.svg" alt="Logo Concello Santiago" width="200"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntZaragoza-logo.svg" alt="Logo Ayun.Zaragoza" width="200"/>
</p>



