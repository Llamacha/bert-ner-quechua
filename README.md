# Llama-NER
Es un modelo entrenado especificamente para reconocer entidades en oraciones en el lenguaje quechua sureño. Se realizó el fine-tuning con [LlamaRoBERTa](https://github.com/Llamacha/LlamaRoBERTa) el cual es un modelo de lenguaje para el quechua sureño basado en RoBERTa.

## Acerca del modelo
El dataset utilizado fue de la investigación 
[Cross-lingual Name Tagging and Linking for 282 Languages](https://aclanthology.org/P17-1178.pdf)
y tambien hemos creado nuestro porpio dataset desarrollado manualmente.

El modelo Llama-NER utiliza el etiquetado en formato BIO
- O, No es una entidad Nombrada.
- B-PER, Comienzo del nombre de una persona justo después del nombre de otra persona.
- B-PER, Comienzo del nombre de una persona justo después del nombre de otra persona.
- I-PER, Nombre de la persona.
- B-ORG, Comienzo del nombre de una organización justo después del nombre de otra organización.
- I-ORG, Organización.
- B-LOC, Comienzo del nombre de una locación justo después del nombre de otra locación.
- I-LOC, Locación.

Ademas comparamos con distintos modelos pre-entrenados para el fine-tuning. A continuación mostramos los resultados:

| Modelos | Wikiann | Llama-NER dataset |             
|---------|:---------:|:-------------------:|
| mBERT   | 53.65   | 54.72             | 
| XML-RoBERTa  | 74.15      | 75.3      | 
| MetaXL  | 77.06      | 77.85        |
| MAD-X  | **87.10**      | 79.63        | 
| LlamaBERT  |   -   | 49.53        | 
| LlamaRoBERTa  |  -     | **82.21**        | 

## Usabilidad
Utilizamos la libreria `Simple Transformers` donde nos permitira desarrollar el modelo NER, la documentacion se puede ver [aqui](https://simpletransformers.ai/docs/ner-model/).

```python
from simpletransformers.ner import NERModel,NERArgs

model = NERModel(
    "roberta", "./Llama-NER"
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



