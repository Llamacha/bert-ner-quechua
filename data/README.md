# Herramienta para construccion del corpus NER

Para la construcción el corpus NER hemos usado la herramienta basado en web de Código abierto Label studio, la cual nos permitió anotar los textos planos en quechua de forma intuitiva y rapida, nos permitió exportar el corpus NER en formato ConLL2003 muy usado en tareas de NER y estilo de anotación BIO.

El Código fuente de la herramienta de anotación se puede conseguir en su cuenta oficial de github de forma gratuita [Label Studio](https://github.com/heartexlabs/label-studio#run-with-docker-compose)

## Como usar la herramienta

El metodo que hemos usado fue por medio de un contendor de Docker localmente
Como nos menciona en su documentacion:

---

Official Label Studio docker image is [here](https://hub.docker.com/r/heartexlabs/label-studio) and it can be downloaded with `docker pull`. Run Label Studio in a Docker container and access it at `http://localhost:8080`.

```bash
docker pull heartexlabs/label-studio:latest
docker run -it -p 8080:8080 -v `pwd`/mydata:/label-studio/data heartexlabs/label-studio:latest`
```

You can find all the generated assets, including SQLite3 database storage `label_studio.sqlite3` and uploaded files, in the `./mydata` directory.

---

En la herramienta una vez ejecutado localmente por el contenedor de docker.
Lo Primero debemos crear un proyecto
![1-step](https://drive.google.com/uc?id=1qAmuwbUv0vnoay3QfoK6ms3quk7F3A3x)

Una vez creado el proyecto le damos importar un texto plano en quechua
![2-step](https://drive.google.com/uc?id=1LjwaCC-3ENAKLnfDszAOi5zG55dVcfIv)
![3-step](https://drive.google.com/uc?id=1zOiozGTqGaOZ4eXvFGn4HGzHgH7yeEcF)

Nos aparecerá esta lista de tareas de cada sentencia del corpus que hemos importado previamente
![4-step](https://drive.google.com/uc?id=1JJocpAW6M8WFWpHBnvzRbUTVVBeWBmoK)

Antes de comenzar anotar nos pedirá configurar el etiquetado
![5-step](https://drive.google.com/uc?id=1SXz-Ury4z0iZtgpfuWNv_84MLbFCAQDB)
![6-step](https://drive.google.com/uc?id=1k-rZHsOhvpUgu1bQHSQfQnlxBTT1FUO1)
![7-step](https://drive.google.com/uc?id=1uhsG2oNjeZus6fL7qKrhZz-SHK2ViaMR)

Seleccionamos una tarea y comenzamos a etiquetar las entidades
![8-step](https://drive.google.com/uc?id=1XbgwXclgW56CtKDSrBV-jJeAPpMWDUYZ)

En caso que se requiera exportar el corpus del NER elegimos la opción de CONLL2003
![9-step](https://drive.google.com/uc?id=15-Ra7D_DzEURsSvMPZPi92q04wdHNkoF)
![10-step](https://drive.google.com/uc?id=18lK4FETdu3ZWSUoQEe3COxZ7s__QiCYw)
