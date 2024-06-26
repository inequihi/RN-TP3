# Trabajo Practico 3  

Notas del progreso

## Primer Modelo
Se agregaron capas convolucionales a la red existente previa sin criterio, tan solo una
con activación relu y una ultima con softmax. El comportamiento de la red
mejoro pero no tan significativamente como se esperaba
Agrego 3 capas Conv2D con MaxPooling2D para downsampling 
Cada capa de convolucional usa activacion ReLU y para normal inicializacion Glorot
Despues de cada bloque convolucional aplico Dropout y BatchNormalization

Result Sin Data Aug --> 0.3718

Result Con Data Aug --> 0.3718

## Segundo Modelo
Se aumento el patience y la cantidad de epochs ya que la cantida de parametros
a definir con cada entrenamiento es mucho mayor qu eocn la red de MPL. 
Se agregan capas y se prueba con una arquitectura con forma triangular, empezando con capas densas con
muchas neuronas y vamos disminuyendo hasta llegar a la ultima capa con 100 neuronas ocn 
activacion softmax. 
Cantidad de neuronas por capas: 10k 10k 5k 2k 1.5k 1k 100
Fueron 206millones de parametros. 
Se edito la paciencia y aumento la cantidad de epochs para llegar a editar todos los parametros. 

Result Sin Data Aug --> 0.49580

Result Con Data Aug --> 0.48620

## Tercer Modelo
Se consideraron las dimensiones de salida de cada etapa de las capas confolucionales y 
se aplicaron filtros para que tenga sentido la morfología elegida de la red. 
Se Hizo una pequeña progresión en la cantidad de filtros, empezando con 256 y luego 512. 
Se dejo de hacer batch normalization y dropout en una misma cada (error gravisimo conceptual)
Se minimizo la cantidad de densee layers despues de la etapa convolucional a solo dos. 
Tambien itere probando distintos epsilon para el batch normalization pero no se vio miuy afectado. 
El learning rate 0.001 y epsilon en 1e-9

Result Sin Data Aug --> 0.60900

Result conData Aug --> 0.60530

Tambien se probo la ResNet50 con los data sets con datos no augmentados. 
Epochs 300 y un batchsize de 120. 

Result Resnet50 --> 0.51180

## Cuarto Modelo
Modifique el test size de 0.2 a 0.4 para disminuir la cantidad de datos con la que entreno a la red ya
que estaba sospechando overfitting en entrenamiento. 
No obstante esto no mejoro el performance.

A la resnet le agreuge epochs para que se entrene mejor, 

Result Resnet50 --> 0.52490

## Quinto Modelo
Editando hiperparametor de learning rate y patience y aumentando epochs llegue a el 
mejor resultado:

Result Sin Data Aug --> 0.64030

Result conData Aug --> 0.63960
El learning rate del caso con data augmentation no afecta mucho, se llega rapido 
al maximo. Fui muy generosa con la patience por eso es que se realizan tantas epochs. 

Result Resnet50 --> 0.51180 
