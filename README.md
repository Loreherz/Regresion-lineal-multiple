# Regresion-lineal-multiple

Un modelo de regresión lineal múltiple es un modelo estadístico versátil para evaluar las relaciones entre un destino continuo y los predictores.

Los predictores pueden ser campos continuos, categóricos o derivados, de modo que las relaciones no lineales también estén soportadas. El modelo es lineal porque consiste en términos de aditivos en los que cada término es un predictor que se multiplica por un coeficiente estimado. El término de constante (intercepción) también se añade normalmente al modelo.

La regresión lineal se utiliza para generar conocimientos para los gráficos que contienen al menos dos campos continuos con uno identificado como el destino y el otro como un predictor. Además, se puede especificar un predictor categórico y dos campos continuos auxiliares en un gráfico y se pueden utilizar para generar un modelo de regresión adecuado. Para cada modelo candidato, IBM®Cognos Analytics lleva a cabo una prueba F de significancia de modelo.

Aprobar y probar el modelo
Múltiples modelos lineales están equipados con los pasos siguientes:

1. Construya una matriz de diseño que contenga una fila por cada fila de datos y una columna por cada parámetro en el modelo de regresión. Las columnas corresponden a los predictores o a las categorías de predictores.

2. Calcule los coeficientes de regresión.

a) Multiplique la matriz de diseño transpuesta consigo misma.

b) Multiplique la matriz de diseño transpuesta con el vector de valores de destino.

c) Multiplique la inversa de la matriz del paso a por la matriz del paso b.

Utilizando los coeficientes de regresión obtenidos, se calculan los valores de destino pronosticados para cada fila de datos. Las diferencias entre los valores de objetivo pronosticados y observados se denominan residuos. A continuación, el modelo se prueba para que sea significativo con la prueba F tal como se indica a continuación.

1. Calcule el cuadrado medio para el origen de error (la varianza no explicada).

a) Calcule la suma de cuadrados de los residuos.

        Tome el cuadrado de cada residuo y añádalos.

b) Divida la suma de cuadrados para la fuente de error por los grados de libertad apropiados.



2. Calcule el cuadrado medio para el modelo de regresión (la varianza explicada).

a) Calcule la suma de cuadrados para el modelo.

     -Para cada fila, reste la media global del valor de destino previsto.

     -Tome el cuadrado de cada uno de estos resultados y añádalos.
     

b) Divida la suma de cuadrados para el modelo de regresión por los grados de libertad apropiados.

3. Divida el cuadrado medio para el modelo de regresión por el cuadrado medio de la fuente de error. En otras palabras, calcule la proporción de la varianza explicada a la varianza no explicada. Esta proporción es el valor F.

El valor F se compara con una distribución de F teórica para determinar la probabilidad de obtener el valor F por casualidad.

-Este es el valor de significación.
-Si el valor de significación es menor que el nivel de significación, los medios son significativamente diferentes.


Se utiliza R2 ajustado para estimar la fuerza predictiva del modelo de regresión. El nivel de significación se establece en 5 % y la potencia predictiva del modelo debe ser mayor que 10 % para indicar una relación de predicción fiable entre el destino y un campo de entrada.



Selección de modelo


El procedimiento de selección de modelos depende de si un predictor categórico está presente o no. Cuando sólo se especifica un predictor continuo, se tienen en cuenta los tres modelos siguientes.

1. Un modelo constante que siempre predice la media general.
2. El modelo lineal con el predictor único se ha añadido a la constante.
3. Modelo cuadrático en el que se añade el predictor cuadrado al modelo lineal.


El modelo cuadrático se selecciona si es significativo y proporciona una mejora relativa en la potencia predictiva de al menos un 10 % sobre el modelo lineal. Si se selecciona, la línea de ajuste cuadrático se notifica junto con la fuerza predictiva del modelo.

De lo contrario, se selecciona el modelo lineal si cumple las mismas condiciones cuando se compara con el modelo constante. Si se selecciona, la línea de ajuste lineal se notifica junto con la fuerza predictiva del modelo.

No se ha seleccionado en ninguno de los modelos anteriores. Se informa de la media global y no se informa de ninguna relación de predicción entre el destino y la entrada.

Cuando está presente un predictor categórico, el proceso de selección es más complejo debido a que se tienen en cuenta hasta ocho modelos diferentes. Los pasos de selección son similares a los pasos anteriores como el modelo más complejo que es significativo y proporciona una mejora relativa suficiente sobre el primer modelo anidado seleccionado.

Se informa de la fuerza predictiva para el modelo seleccionado, así como las líneas de ajuste adecuadas en función del modelo y del número de categorías en el predictor categórico que se selecciona, si existe. El número de categorías en el predictor categórico se limita a 3 para reducir el número de líneas de ajuste visualizadas.

Fuente : https://www.ibm.com/docs/es/cognos-analytics/11.1.0?topic=tests-multiple-linear-regression






