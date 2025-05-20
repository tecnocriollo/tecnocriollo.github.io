![alt text](/assets/images/plataformas-adhoc.png)

En el data engineering se puede trabajar con plataformas ya establecidas como Databricks, Bigquery o Fabric o de forma ad-hoc adaptando al negocio.

### Usando plataformas:

La curva de aprendizaje es menor, lo que si tienes un equipo con mucha gente es útil ya que se reducen los costos de capacitación. Sin embargo, hay que tener mucho control de costos ya que al ser más fácil de usar, también es más fácil de ejecutar sin medir. Ya hay muchos casos de queries costosas en BigQuery, exceso de clusters en Databricks o sobreutilización de la capacidad en Fabric. Un beneficio adicional es que la seguridad viene en la plataforma, lo que facilita su gestión.

### AD-HOC

Se puede armar una plataforma propia de datos usando Open Source: Hadoop, Spark, minio, Hudi, Iceberg, Flink, etc. Acá las cosas son más controlables, pero la curva de aprendizaje es más alta y requiere tener gente de muy alta expertise. Es una opción muy buena si hablamos de una Startup donde es un grupo reducido de personas con gran talento y capacidades que a la vez quieren mantener a raya el control de costos o llegar a niveles de optimizaciones más potentes. La seguridad también debe ser implementada y esto puede generar dolores de cabeza si no se tiene a personas con consciencia en estos temas.

### Conclusiones

No hay opción mala o buena, pero unas reglas simples: Si tienes mucha gente y necesitas estandarizar la forma de trabajo, mejor optar por una plataforma. En cambio, tienes poca gente, muy talentosa y capaz y el rendimiento es clave para tu empresa, la opción ad-hoc es la mejor.
