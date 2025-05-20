
Basandome en [este artículo](https://blog.min.io/a-developers-introduction-to-apache-iceberg-using-minio/) de la documentación oficial de Minio, voy a intentar probar tener un Datalake usando Minio y Iceberg.

Pero primero algunos conceptos.

### ¿Qué es Iceberg?

Iceberg es un formato de tabla que usa storage y la propia estructura de directorios para armar el catálogo. Digamos que tenemos un data lake storage s3 o adls con la siguiente carpeta:

 `/warehouse/database/table`

donde *warehouse* sería la ruta del catálogo definido en configuración spark, equivalente a como si fuera un servidor de base de datos, *database* la base de datos y *table* la tabla de la base de datos. Si quiera consultar en el catálogo podría usar simple spark SQL de la siguiente forma:

```sql
SELECT col1, col2 FROM database.table
```

en este sentido es un esquema autoorganizado. Pero hay más, Iceberg ofrece versionamiento, evolución de esquema y no es necesario definir índices ya que los crea el mismo. Esto es gracias 

![alt text](/assets/images/iceberg-metadata.png)


### ¿Qué es Minio?

Minio es un object storage compatible con el API de Amazon S3, se puede usar la misma api para la creación, actualización, modificación y eliminación de objetos y al ser open este permite tener su propio storage. Provee una interfaz web donde se pueden ver los objetos así como usar las mismas tools de las apis compatibles S3 y por lo tanto es compatible también con Spark.

### Ejecución y revisión de datalake

Procedemos a importar el docker compose del artículo al equipo local y desde la ruta que lo guardamos lo ejecutamos con `docker-compose up`:

![Importando docker-compose](/assets/images/2025-05-20_importando_imagenes-con-compose.png)

al ejecutar aparece una URL local al notebook jupyter:
![Accediendo a notebook](/assets/images/2025-05-20_acceso_a_notebook.png)

vamos al notebook y se ve que este viene con varios ejemplos:
![Vista notebook](/assets/images/2025-05-20_vista_del_notebook.png)

nos vamos al notebook Getting Started y ejecutamos hasta el SQL que crea una base de datos, una tabla y carga datos de un parquet a la tabla:

![Getting started](/assets/images/2025-05-20_ejemplo_getting_started.png)

luego nos vamos a la interfaz de Minio, esta se entra en http://localhost:9001/, el usuario y password se ve en el archivo docker-compose.

![Inicio minio](/assets/images/2025-05-20_inicio_minio.png)

entramos a la ruta warehouse y podemos ver que se crea la carpeta de la base de datos *nyc* y la tabla *taxis*, finalmente al entrar están las dos carpetas de metadata y data.

![Vista archivos de la tabla](/assets/images/2025-05-20_vista_archivos_de_la_tabla.png)

en la carpeta data se puede ver archivos parquet de la tabla, como se insertó una vez solo se ve uno, pero a medida que se agreguen aparecerán más.

![Datos de la tabla](/assets/images/2025-05-20_datos_de_la_tabla.png)

y en la carpeta metadata está el log de la tabla en que mezcla archivos json y avro

![Metadata de la tabla](/assets/images/2025-05-20_metadata_tabla.png)

finalmente revisamos el archivo json con la metadata

![alt text](/assets/images/2025-05-20_091119_json_metadata.png)

El notebook getting started tiene harta información sobre como ingestar datos, modificar tablas. También en los mismos notebooks hay ejemplo para consultar via DuckDB con PyIceberg y también escribir tablas sin necesidad de tener PySpark.

Espero que esta info les sea muy útil. Nos leemos!!