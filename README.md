# Práctica 5. Reconocimiento de matrículas

## Descripción

En esta práctica, se implementó un detector de matrículas usando tanto un modelo entrenado con YOLOv8 como una propuesta usando detección de bordes usando opencv.

El modelo se trata de una red neuronal entrenada con YOLOv8, en nuestro caso se entrenó con la gpu con 100 epochs. El dataset lo conseguimos de roboflow  [Enlace al dataset](https://universe.roboflow.com/samrat-sahoo/license-plates-f8vsn) donde nos dan las imágenes etiquetadas en el formato de YOLOv8. Este fue el resultado obtenido de la red:

![confusion_matrix](https://github.com/EmilioDeniz/VC_P5/assets/72134226/c0b1ac25-13f6-46fd-a454-dd347b2d50f6 =250x250)

## Funcionamiento

El detector de matrículas usando la red neuronal funciona de la siguiente manera:

- Se carga el modelo pre-entrenado para hacer la detección de los coches.
- Se define el input(imagen o video).
- Se detectan los objetos de interés.
- Si el objeto se trata de un vehículo dibujamos el recuadro.
- Si el objeto se trata de una matricula farmamos una nueva imagen de esa region en escala de grises y aplicamos los filtros necesarios para facilitar la lectura.
- Se hace uso de un OCR para leer la imagen generada.
- Ponemos el recuadro alrededor de la matricula y la string obtenida por el OCR cerca de la matrícula.
- Mostramos resultados por la consola.

El detector de matrículas usando la detección de bordes funciona de la siguiente manera:

- Se carga el modelo pre-entrenado para hacer la detección de los coches.
- Se define el input(imagen o video).
- Se detectan los objetos de interés.
- Si el objeto se trata de un vehículo creo una imagen nueva usando esa zona y solo la parte inferior de la imagen.
- Aplicamos los filtros y hago la detección de bordes
- De esos bordes solo me quedo con los que tengan cuatro esquinas usando las funciones cv2.arcLength() y cv2.approxPolyDP()
- Hacemos un pequeño filtro de tamaños mínimos, máximos y miramos el aspect ratio.
- Se hace uso de un OCR para leer la imagen generada.
- Ponemos el recuadro alrededor de la matricula y la string obtenida por el OCR cerca de la matrícula.
- Mostramos resultados por la consola.
  
## Requisitos

- Python 3.x
- OpenCV (para el procesamiento de imágenes)
- pytesseract (OCR)
- easyocr
- ultralytics(YOLO)

## Referencias
https://omes-va.com/reconocimiento-de-matriculas-vehiculares-opencv-pytesseract-ocr-python/



