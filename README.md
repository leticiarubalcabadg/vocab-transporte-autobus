# Vocabulario autobús

Este vocabulario está siendo desarrollado en el contexto de la actuación sobre datos abiertos del proyecto [Plataforma de Gobierno Abierto, Colaborativa e Interoperable](http://www.red.es/redes/es/que-hacemos/ciudades-inteligentes/proyectos-en-ciudades), de la [II Convocatoria de Ciudades Inteligentes](https://perfilcontratante.red.es/perfilcontratante/busqueda/DetalleLicitacionesDefault.action?idLicitacion=6707&visualizar=0) del [Ministerio de Economía](http://www.mineco.gob.es/) y Empresa lanzada a través de la [Entidad Pública Empresarial Red.es](http://www.red.es/) adscrita a la [Secretaría de Estado de Avance Digital de dicho Ministerio](http://www.mineco.gob.es/portal/site/mineco/avancedigital).


## Propósito y alcance del vocabulario

El propósito de este vocabulario es describir de forma semántica los servicios públicos de transporte terrestre regular de personas por carretera que se realizan con autobuses y que son prestados por las corporaciones municipales de tal manera que la propia institución, el ayuntamiento, la ciudadanía o terceras partes puedan conocer de forma estándar, abierta y sencilla las cuestiones esenciales de su funcionamiento, tal como quedó fijado en el alcance del vocabulario.

En ese mismo acuerdo acotamos trabajar con información referente a los sistemas de transporte público de autobuses, “autobuses urbanos”, por lo que dejamos fuera a otros sistemas de transporte público urbano como pueden ser el tranvía, el metro, el funicular, la góndola, el trolebús o cualquier otro medio de transporte público o privado de la ciudad o que tiene paradas en la ciudad pero que tiene un componente extra urbano como pueden ser los autobuses interurbanos o privado.

De los sistemas de transporte público de autobuses nos centraremos en la información de dos tipos: estática y dinámica.
* Información estática, referida a líneas, paradas, recorridos de las líneas, horarios e incidencias planificadas.
* Información dinámica, referida a tiempo de llegada del bus a parada e incidencias no planificadas.

Contar con los datos del transporte de personas que se produce en las ciudades es un elemento muy valioso para ayuntamientos, ciudadanía y terceras partes, ya sea para la gestión de los servicios, la utilización de los servicios o la prestación de servicios de terceros en diferentes ámbitos como la gestión del tráfico, el diseño de la infraestructura viaria, el cumplimiento de los Objetivos de Desarrollo Sostenible, la calidad del aire, la movilidad urbana, MaaS o cualquier otro ámbito relacionado.

También se ha propuesto un modelo relacional tipo, que está  documentado *[aquí](/relational model/)*, que ha sido utilizado para la generación de  una API REST relacionada con este vocabulario, en el contexto del  proyecto Ciudades Abiertas. Este modelo relacional no está  completamente normalizado, para facilitar algunos procesos de  Extracción, Transformación y Carga (ETLs, por sus siglas en inglés),  habituales en muchos portales de datos abiertos, y no es normativo,  por lo que cualquier organización que adopte este vocabulario para la  publicación de sus datos abiertos puede proponer variaciones siempre  que se respete la forma de exportación a RDF de los datos  correspondientes


## Desarrollo del vocabulario

El material generado en las diferentes actividades ejecutadas durante el desarrollo del vocabulario, casos de uso, historias de usuario, glosario de términos, etc., se encuentra disponible en la [Wiki del Vocabulario](https://github.com/CiudadesAbiertas/vocab-transporte-autobus/wiki)

## Mantenimiento

Para gestionar aquellas incidencias o mejoras sugeridas con respecto al vocabulario te recomendamos seguir las guías proporcionadas en [Gestión de Issues](https://github.com/CiudadesAbiertas/vocab-transporte-autobus/wiki/Gesti%C3%B3n-de-issues)

## Ejemplos
Algunas [consultas](https://github.com/CiudadesAbiertas/vocab-transporte-autobus/blob/master/examples/queries.md) a realizar en un SPARQL endpoint de pruebas se han habilitado para ejemplificar su funcionamiento.
