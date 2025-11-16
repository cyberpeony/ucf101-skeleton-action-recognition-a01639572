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
- validation accuracy: 0.53  
- test accuracy: 0.38  

### Mejorado
- validation accuracy: 0.65  
- test accuracy: ~0.55  

El modelo mejorado reduce el error aprox. un 27% a comparación del baseline.

## Conclusión

- las secuencias de los esqueletos tienen suficiente info. para reconocer las acciones
- un LSTM simple ya supera bastante en resultados al azar
- aumentar la capacidad del modelo + regularización, mejora evidentemente la generalización

## Autora
- Fernanda Díaz Gutiérrez A01639572