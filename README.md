# Cat Hipsterizer
Inspirado por ["Hipsterize Your Dog With Deep Learning"](http://blog.dlib.net/2016/10/hipsterize-your-dog-with-deep-learning.html)
Creador por : kairess
![result.jpg](https://github.com/kairess/cat_hipsterizer/raw/master/result/result.jpg)
![result2.jpg](https://github.com/kairess/cat_hipsterizer/raw/master/result/result2.jpg)

El proyecto contiene:
1. Detección de la cara de un gato  con el modelo prentenado de Mobilenetv2
2. Detección de face landmarks de gatos con el modelo prentenado de Mobilenetv2

Al principio yo solía utilizar [cat frontal face detector of OpenCV](https://www.pyimagesearch.com/2016/06/20/detecting-cats-in-images-with-opencv/),pero el rendimiento no era tan bueno en la mayoria de fotografias de gatos reales.Así que decidí hacer un nuevo modelo con Deep Learning.
El método de regresión se usa tanto para la detección de rostros como para la detección de face landmarks, por lo que el modelo es muy ** ingenuo** para usar en aplicaciones reales. Pero funciona mejor  de lo que esperaba ;)

Se utilizo [Cat dataset on Kaggle](https://www.kaggle.com/crawford/cat-dataset) para entrenar y validar .


### Estructura modelo en cascada
1. Input (Full image 224x224) - **Face detection model** - Output (cuadro delimitador de cara)
2. Input (Face image 224x224) - **Facial landmarks model** - Output (9 punto de  landmarks )


# Requiremientos
- Python
- Keras
- Numpy
- Dlib
- OpenCV
- Pandas

# Uso
### Entrenamiento

```
python preprocess.py
python train.py
python preprocess_lmks.py
python train_lmks.py
```
### Testing
```
python test.py bbs_1.h5 lmks_1.h5
```

# Limitaciones
- Detecta un gato por frame
- Potente para caras frontales (rendimiento un poco bajo para caras laterales)
- No se puede detectar la existencia, este modelo cree que el gato debe estar en la imagen

# TODOs (para ti)
-Detección de varios gatos en una misma fotografia
- Aumento de datos (flip, translation, rotation, noise...)
- YOLO como modelo (mapa de probabilidad de clase)
- Utilice capas de convolución de transposición para la reconstrucción de landmarks (para preservar la información espacial)
- Implementación móvil
- Entrenamiento del modelo de predicción de forma "dlib"
