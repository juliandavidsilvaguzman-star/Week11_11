# Week11_11

Integrantes: DIEGO ALEJANDRO RUIZ ALFONSO - ppmurcia@ucundinamarca.edu.co PEDRO PASCUAL MURCIA VARGAS - ppmurcia@ucundinamarca.edu.co JHON EDUARD TINJACA CRUZ - jetinjaca@ucundinamarca.edu.co JULIAN DAVID SILVA GUZMAN - jdsilva@ucundinamarca.edu.co

# Predicción de Series de Tiempo con Redes Neuronales Recurrentes (RNN)
# Descripción
Este notebook demuestra la implementación de un modelo de Red Neuronal Recurrente (RNN) simple para la predicción de series de tiempo. El proceso incluye la generación de una serie de tiempo sintética, su preprocesamiento (normalización, creación de secuencias y división en conjuntos de entrenamiento y prueba), la construcción y entrenamiento del modelo RNN, y finalmente la evaluación y visualización de sus predicciones.

# Pasos Clave:
Generación de Datos Sintéticos: Se crea una serie de tiempo sintética que simula datos reales, utilizando una función sinusoidal con ruido gaussiano añadido mediante numpy. Esto permite un entorno controlado para probar el modelo RNN.

# Preprocesamiento de Datos:
Normalización: La serie se escala a un rango de 0 a 1 utilizando MinMaxScaler de sklearn, lo cual es esencial para el entrenamiento de redes neuronales, asegurando que todas las características tengan el mismo rango.
Creación de Secuencias: Se transforman los datos normalizados en secuencias de entrada (X) y sus correspondientes valores a predecir (y), utilizando una ventana temporal definida. Esto prepara los datos en el formato secuencial requerido por las RNNs.

# División de Datos: Los datos se dividen en conjuntos de entrenamiento y prueba (X_train, X_test, y_train, y_test) utilizando train_test_split con shuffle=False para preservar el orden temporal de la serie, lo cual es crucial en el análisis de series de tiempo.
Construcción del Modelo RNN: Se define un modelo de red neuronal secuencial con tensorflow.keras.models.Sequential. Incluye una capa SimpleRNN con activación tanh para capturar patrones temporales y dependencias, seguida de una capa Dense de salida con una única neurona para la predicción del siguiente valor en la serie.

# Entrenamiento del Modelo: 
El modelo se compila con el optimizador Adam, que ajusta los pesos de la red de manera eficiente, y la función de pérdida mean_squared_error (MSE), que se minimiza durante el entrenamiento. Se entrena utilizando los datos de entrenamiento y se monitorea su rendimiento con los datos de validación a lo largo de varias épocas para observar la convergencia y detectar el sobreajuste.

# Evaluación y Visualización: 
Se generan predicciones sobre el conjunto de prueba (X_test), y tanto las predicciones como los valores reales (y_test) se desnormalizan a su escala original para una interpretación significativa. Finalmente, se visualizan las series real y predicha para una comparación directa, y se calcula el MSE final para cuantificar el error promedio del modelo.

# Tecnologías Utilizadas:

# numpy: 
Para operaciones numéricas y manipulación de arrays.

# pandas: 
Para manipulación y análisis de datos (uso mínimo en este notebook).

# matplotlib.pyplot: 
Para la visualización de series de tiempo y resultados.

# sklearn.preprocessing.MinMaxScaler: 
Para la normalización de datos.

# sklearn.model_selection.train_test_split: 
Para dividir los datos.

# tensorflow.keras.models.Sequential: 
Para construir el modelo de red neuronal.
tensorflow.keras.layers.SimpleRNN, tensorflow.keras.layers.Dense: Para las capas del modelo RNN.

# Resultados y Conclusiones
El modelo de Red Neuronal Recurrente (RNN) simple demostró la capacidad de aprender patrones en la serie de tiempo sintética generada. Tras 30 épocas de entrenamiento, el Error Cuadrático Medio (MSE) final del modelo en el conjunto de prueba fue de 0.01705.

# Observaciones Clave:
# Rendimiento en Entrenamiento y Validación: 
Los gráficos de MSE durante el entrenamiento mostraron una disminución constante tanto en el conjunto de entrenamiento como en el de validación, indicando que el modelo está aprendiendo y generalizando bien, sin signos evidentes de sobreajuste en las épocas entrenadas.

# Precisión Visual: 
La visualización de las predicciones frente a los valores reales en el conjunto de prueba mostró una buena alineación, sugiriendo que el modelo es capaz de capturar la tendencia sinusoidal subyacente de la serie de tiempo.
Limitaciones del Modelo Simple: Aunque el SimpleRNN es un buen punto de partida, para series de tiempo más complejas o con dependencias a largo plazo, modelos como LSTM o GRU (Long Short-Term Memory o Gated Recurrent Unit) suelen ofrecer un rendimiento superior debido a su arquitectura que les permite manejar mejor las dependencias a largo plazo.

