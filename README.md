# Implementación de un modelo de deep learning para la detección de acciones humanas en videos del dataset UCF101

Este momento de retroalimentación implementa un modelo de deep learning para clasificar acciones del dataset UCF101, utilizando exclusivamente las anotaciones en formato pkl de esqueletos 2D (encontradas en el file dado, ucf101_2d.pkl).  


## Contenido del archivo del modelo

- File: UCF101_Skeleton_DL.ipynb
  - carga de los datos y preprocesamiento
  - construcción del dataset, dataloaders
  - modelo base
  - modelo mejorado
  - train y validation
  - evaluación en test
  - las predicciones finales
  - el análisis de resultados y la documentación de las decisiones tomadas para el modelo


## Dataset

Como fue mencionado previamente, el proyecto usa los datos del archivo ucf101_2d.pkl

El archivo contiene (para cada video):
- coordenadas 2D de 17 joints por frame
- secuencias temporales por video
- etiquetas de las acciones
- splits: train1/train2/train3 y test1/test2/test3  

Para el modelo, utilicé:
- train1 para train/val
- test1 para test  
- subset de 8 clases



## Para ejecutar

1. Subir el file de los datos (ucf101_2d.pkl) a la ruta /content/ucf101_2d.pkl
2. Abrir el notebook en Google Colab
3. Ejecutar



## Modelos

### Baseline
- LSTM (1 layer, 64 unidades)
- sin dropout
- sin regularización
- in: 34 features, 17 joints x 2 coords

### Modelo mejorado
- LSTM (2 layers y 128 unidades)
- dropout de 0.5 
- weight decay de 1e-4


## Resultados (aprox)

### Baseline
- Validation accuracy: ~0.46  
- Test accuracy: ~0.38  

### Mejorado
- Validation accuracy: ~0.59  
- Test accuracy: ~0.52  

El modelo mejorado reduce el error en aprox. 24% respecto al baseline, mostrando mejor generalización.

## Conclusión

- Las secuencias de esqueletos contienen suficiente información temporal para reconocer acciones  
- Un LSTM simple ya supera claramente el desempeño al azar (12.5% en 8 clases)
- Aumentar la capacidad del modelo + añadir regularización mejora de forma evidente la generalización y el desempeño final

## Autora
- Fernanda Díaz Gutiérrez — A01639572