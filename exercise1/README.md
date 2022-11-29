# EJERCICIO 1 

La idea del siguiente ejercicio es formular una solucion con airflow armando data pipelines siguiendo las buenas prácticas de desarrollo.
El script consiste en extraer noticias de Google News sobre un cierto tópico (en el caso de ejemplo usamos la keyword `messi`) para obtener algunos campos para cada articulo. Luego, una vez curado el dataframe insertamos los datos a la base de datos.

Entre los items a considerar:
1. Hypermodern Tooling de python: Ver el hilo de posts de Claudio Jolowicz https://cjolowicz.github.io/posts/hypermodern-python-01-setup/ y https://medium.com/@gonzaloandres.diaz/fundamentos-y-automatizacion-codigo-de-alta-calidad-en-python-2020-671706a7f09b.
   1. Template Cookie cutter.
   2. Poetry.
   3. Linters.
   4. Formatters.
   5. Pre-commit hooks.
   6. Pytest.
2. Dockerizacion + integracion con poetry.
3. Armado de data pipelines con Airflow/Prefect/Kedro/etc. Los DAGs deben cumplir algunos criterios:
   
    a. Idempotencia y atomicidad

       * https://towardsdatascience.com/how-to-design-better-dags-in-apache-airflow-494f5cb0c9ab
       * https://docs.astronomer.io/learn/dag-best-practices
       * https://www.manning.com/books/data-pipelines-with-apache-airflow
  
    b. Data validation with pandera/Great expectations/Pydantic (https://github.com/NatanMish/data_validation):
       * https://docs.astronomer.io/learn/data-quality
       * https://docs.astronomer.io/learn/airflow-sql-data-quality
       * https://www.astronomer.io/blog/how-to-keep-data-quality-in-check-with-airflow/
    
    c. Uso de algunas features de Airflow tales como TaskGroup, Factorias, Features nuevas de Airflow, etc.

    d. Integracion de Airflow con los distintos servicios: MLFlow, PostgreSQL, MinIO, etc.

4. Logging.
5. Buen manejo de try-except.
6. Configuracion correcta de variables de entorno/secrets.
7. Opcional: Armado de pipelines CI/CD. Algunos ejemplos:
   1. Crear CI para correr tests
   2. Crear CI para correr linters y formatters.
8. Opcional: Armado de ML pipeline e integracion con MLFlow.
9.  Opcional: Armado de sistema de monitorizacion de Airflow.
10. Opcional: Setup de plataforma de BI para generar dashboards.

## PASOS PARA REPRODUCIR LA SOLUCION
Pasos para reproducir el script `main.py`:

1. Correr `pip3 install -r requirements.txt` para instalar las librerias necesarias.
2. Correr `docker-compose up` para levantar los servicios
3. Correr `main.py` para ejecutar el script end to end.
4. Correr `pgcli -h 0.0.0.0 -U postgres -p 5432 -d postgresdb` para acceder a la base de datos
5. Ejecutar la siguiente query:

```sql
select * from news limit 1;
```

