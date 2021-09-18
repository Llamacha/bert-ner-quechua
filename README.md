# NER_Quechua
NER Quechua es un modelo entrenado especificamente para reconocer entidades en oraciones en el lenguaje quechua sureño. El modelo Ner quechua fue pre entranado con bert-quechua en la cual esta basado en RoBERTa: A Robustly Optimized BERT Pretraining Approach.

## Acerca del modelo
El dataset utilizado fue de la investigación 
[Cross-lingual Name Tagging and Linking for 282 Languages](https://aclanthology.org/P17-1178.pdf)
y tambien hemos creado nuestro porpio dataset desarrollado manualmente.

El modelo Ner quechua desarrollado utiliza el etiquetado en formato BIO
- O, No es una entidad Nombrada.
- B-PER, Comienzo del nombre de una persona justo después del nombre de otra persona.
- B-PER, Comienzo del nombre de una persona justo después del nombre de otra persona.
- I-PER, Nombre de la persona.
- B-ORG, Comienzo del nombre de una organización justo después del nombre de otra organización.
- I-ORG, Organización.
- B-LOC, Comienzo del nombre de una locación justo después del nombre de otra locación.
- I-LOC, Locación.

Utilizamos la libreria Simple Transformers donde nos permitira desarrollar el modelo Ner, la documentacion se puede ver [aqui](https://simpletransformers.ai/docs/ner-model/).

## Usabilidad
Utilizamos la libreria `Simple Transformers` donde nos permitira desarrollar el modelo Ner, la documentacion se puede ver [aqui](https://simpletransformers.ai/docs/ner-model/).

Es este caso para importar el modelo ner entrenado , los archivos necesario lo adjunte en la carpeta `NerModel`.

```python
from simpletransformers.ner import NERModel,NERArgs

model = NERModel(
    "roberta", "./NerModel"
)
```
Ahora inferimos las entidades.

```python
#Aquel es el río Rímac.
prediction, model_output = model.predict(["Wakqa Rimaq mayum."]) 
prediction
```
```
[[{'Wakqa': 'B-LOC'}, {'Rimaq': 'B-LOC'}, {'mayum.': 'O'}]]
```
```python
#Silvia está esperando a Pedro en la puerta del cementerio.
prediction, model_output = model.predict(["Silviam Pedrota pantiyun punkupi suyachkan."]) 
prediction
```
```
[[{'Silviam': 'I-PER'},
  {'Pedrota': 'B-PER'},
  {'pantiyun': 'O'},
  {'punkupi': 'O'},
  {'suyachkan.': 'I-PER'}]]
  ```



