# ExamenTratamientoDatos
Elaborado por: Sandra Gómez
Maestría de Ciberseguridad

Crear un clasificador de tipos de carnes que se utiliza en la industria real.
Se va a generar un dataframe con el resumen de las imagenes por carpeta de la carpeta Train.
Exploramos la base de datos de entrenamiento que nos va a servir, leemos los directorios y luego se toma las dimensiones de las imagenes largo y ancho para conocer como estan distribuidas las imágenes, en este caso sacamos el mínimo, máximo y promedio de como están las imágenes.
Todas las imágenes son del mismo tamaño, la clase mayoritaria es la clase_05 y la clase_01 no tiene imagenes.
Se toma una muestra de las imagenes, para saber cual es la visulización, cada fila es una clase.
En el dataset de testeo tome las dimensiones de las imagenes, la clase 5 es la mayoritaria y existe una imagen en la clase1 por lo que existe un desbalanceo.
El dataset train se dividio 80% para entrenamiento y 20% para validación.
Esto es para mejorar el error a través de la iteración, con esto el modelo va aprendiendo.
En este punto tomamos una nueva imagen que nunca ha visto, esto para ver si el modelo aprendio.
Luego utilizamos el objeto python ImageDataGenerator, para genera un conjunto de imágenes a partir de unas imágenes ya existentes. 
Tenemos 1310  imágenes pertenecientes a 8 clases para entrenamiento y 323 imágenes perteneciente a 8 clases para validación.
Las redes neuronales convolusionales  se definen para poder mejorar el % de aciertos, utilice algunos paramétros de las redes tales como maxpooling2D
Compiló la arquitectura con un optimizador adam, para encontrar el error mínimo.
Con esto voy a verificar que tan preciso es mi modelo o que tan  bien recuerda mi modelo lo que estoy haciendo.
Luego definimos el modelo con 10 epocas por que en dos iteraciones se puede observar el error y saber cuantas epocas son necesarias para determinar como va evaluándose el modelo.
Evaluo y hago el ajuste del modelo, se requeire el dataset de entrenamiento y el validation generator (digo que tiene 8 clases) la salida de la red neuronal es de 8 clases y la entrada es del número que corresponde a las dimensiones de la imagen.
El algoritmo me va dando a través de las epocas cuantas iteraciones tengo que realizar para que el modelo me de un accuracy de validación y veo que tan bien el modelo está respondiendo a la prueba, lo ideal sería llegar a 1, el modelo va evolucionando numéricamente a lo largo de las epocas.
Generamos la matriz de confusión para saber que tan bien estoy acertando, es decir a que clase pertenece la imagen y cual predijo el modelo.
Luego del entrenamiento evaluamos la matriz de test con una nueva arquitectura, se aumento  un parámetro al optimizador, se aumento learning ride, es el número de saltos pequeños para que sea mas exhaustivo el modelo.
Aplicamos la técnica  de transferencia de aprendizaje, se uso la red nueronal RESNET50, con lo que se entreno la red, RESNET50 quiere decir  capa convolusionales  residuales y tiene una profundidad de 50 capas, se redefine los generadores train y test, por que se necesita hacer una readecuación a la imagen por la característica que se usa RESNET50, con los dataset se define el modelo, y congelo las capas de entradas y salidas, en la entrada que sea de la misma dimensión de la imagen, y la salida la redefino a 8 salidas, redefino desde el aplanamiento y defino el optimizador, la perdida y la métrica.
VGG16, red de profundidad de 16 capas con pesos preentrenados de imagenes, la epocas se aumentaron a 25, y se obtuvo el 93% de accuracy con datos de train balanceados.
