---
layout: post
current: post
cover:  assets/images/pg-csv-pg.png
navigation: True
title: Copiando datos de un servidor Postgres a otro
date: 2020-01-28 10:00:00
tags: [Blog]
class: post-template
subclass: 'post'
---

Una de las tareas con las que tuve que lidiar hoy, fue intentar analizar porque ciertos procesos estaban demorando más de lo esperado. Estos procesos generan eventos a medida que van completando distintas etapas.

Los eventos están almacenados en una base de datos [Postgres](https://www.postgresql.org/), y hay más de 50 millones de registros. 

El problema que tuve fue que por cuestiones técnicas y de seguridad, acceder desde "afuera" a la base de datos que contiene todos estos registros no era posible, así que comencé a pensar de que manera podia extraer ciertas tablas y poder procesarlas en otro servidor con herramientas cómo [Airflow](https://airflow.apache.org/) y [Metabase](https://www.metabase.com/). Acceder a un backup tampoco era una opción. 

Fue entonces cuando recordé que hay una utilidad en Postgres que permite generar archivos de texto basado en consultas o tablas directamente. El meta comando `\copy`.

La sintaxis del meta comando es la siguiente: 
```
\copy { table | ( query ) } { from | to } { ‘filename’ } [ [ with ] ( option [, …] ) ]
```

Asumiendo de que tienes acceso a la base de datos, veamos como puedes generar los archivos de texto utilizando este comando: 

```
COPY tu_tabla to '/tmp/tu_tabla.csv' WITH DELIMITER '|' CSV HEADER;
```

Si en cambio estas intentando exportar una query, podrías cambiarlo por 

```
COPY (select * from tu_tabla where algo=‘completado') to '/tmp/tu_tabla.csv' WITH DELIMITER '|' CSV HEADER;
```

Puedes cambiar el delimitador a lo que quieras, dependerá de qué es lo que contienen tus datos. En mi caso estos eventos, poseen `,` dentro y me estaban generando algunos problemas de parseo. 

Si editas por alguna razón estos archivos de forma manual, asegurate de que no contienen una linea en blanco al final del archivo, o tendrás problemas a la hora de importar los datos nuevamente.

Una vez que tienes todos los datos generados, para importarlos en otra base de datos ejecuta lo siguiente:

```
\COPY tu_tabla FROM '/home/tu_tabla.csv' DELIMITER '|' CSV HEADER;
```

Si lo que intentas es copiar estas filas sobre una base de datos vacía, puedes encontrarte con problemas de claves. Por ejemplo en mi caso los eventos dependen de otras tablas, asi que tienes un par de alternativas para resolver esto:

1. Borras las referencias, por ejemplo `ALTER TABLE tu_tabla DROP CONSTRAINT nombre_constraint;`
2. Deshabitar las relaciones/referencias e importas:

  ```
  ALTER TABLE tu_tabla DISABLE TRIGGER ALL;
  \COPY tu_tabla FROM '/home/tu_tabla.csv' DELIMITER '|' CSV HEADER;
  ALTER TABLE tu_tabla ENABLE TRIGGER ALL;
  ```
3. Importar primero todas las relaciones y luego finalmente la tabla principal. 

Espero te haya servido :)


Cya!
