# Evaluación Final - Módulo 3

Este proyecto forma parte de la evaluación final del Módulo 3 de Data Analytics. El objetivo es analizar el comportamiento de clientes dentro de un programa de fidelización de una aerolínea a partir de dos conjuntos de datos: uno centrado en la actividad de vuelo y otro en el perfil e historial de membresía de los clientes.

## Datasets utilizados

Se han utilizado los siguientes archivos:

- `Customer Flight Activity.csv`: contiene información sobre la actividad mensual de vuelo de los clientes, como vuelos reservados, distancia recorrida, puntos acumulados y puntos redimidos.
- `Customer Loyalty History.csv`: contiene información del perfil del cliente, como país, provincia, ciudad, género, nivel educativo, salario, estado civil, tipo de tarjeta de fidelidad, CLV y datos de inscripción o cancelación en el programa.

## Fase 1: Exploración y limpieza de datos

En la primera fase del proyecto se realizó una exploración inicial de ambos datasets para revisar su estructura, dimensiones, tipos de datos, valores nulos, duplicados y estadísticas descriptivas básicas.

Después, ambos conjuntos de datos se unieron mediante la columna `Loyalty Number`, utilizando un `left join` para conservar todos los registros de actividad de vuelo y añadir la información del perfil de cliente.

Durante la limpieza de datos se realizaron las siguientes tareas:

- eliminación de registros duplicados
- revisión y tratamiento de valores nulos
- detección de valores incoherentes en la variable `Salary`
- transformación de salarios negativos en valores nulos
- comprobación de coherencia entre variables numéricas
- ajuste de tipos de datos
- creación de la variable `Cancelled` para identificar si un cliente canceló su membresía

Tras esta fase, se obtuvo un dataframe limpio y preparado para continuar con el análisis.

## Fase 2: Análisis estadístico

En la segunda fase se llevó a cabo un análisis estadístico de variables numéricas y categóricas.

### Variables numéricas
Se calcularon estadísticas descriptivas como media, mediana, moda, desviación estándar, mínimo y máximo. Este análisis permitió observar que muchas variables relacionadas con la actividad de vuelo presentan distribuciones asimétricas, con muchos valores bajos y algunos registros altos.

### Valores atípicos
Se identificaron valores atípicos mediante el método del rango intercuartílico (IQR) en variables como `Flights Booked`, `Total Flights`, `Distance`, `Points Accumulated`, `Salary` y `CLV`. Los resultados muestran que existen perfiles de clientes bastante alejados del comportamiento medio.

### Correlación entre variables numéricas
También se analizó la correlación entre variables numéricas. Se observaron relaciones fuertes entre `Distance` y `Points Accumulated`, entre `Flights Booked` y `Total Flights`, y entre `Points Redeemed` y `Dollar Cost Points Redeemed`, lo que resulta coherente con la lógica del programa de fidelización.

### Variables categóricas
Se calcularon frecuencias y porcentajes de variables categóricas relevantes como `Gender`, `Education`, `Marital Status`, `Loyalty Card`, `Province` y `Enrollment Type`. Este análisis permitió identificar categorías predominantes dentro de la base de datos.

## Fase 3: Visualización

En esta fase se realizaron distintas visualizaciones con `matplotlib` y `seaborn` para responder de forma gráfica a las preguntas planteadas en el enunciado.

Se analizaron los siguientes aspectos:

- la distribución de la cantidad total de vuelos reservados por mes
- la relación entre la distancia de los vuelos y los puntos acumulados
- la distribución de clientes por provincia
- la comparación del salario promedio según el nivel educativo
- la proporción de clientes según el tipo de tarjeta de fidelidad
- la distribución de clientes según estado civil y género

Para estas visualizaciones se utilizaron gráficos de barras, diagramas de dispersión, gráficos circulares y gráficos categóricos. En los casos en los que el análisis requería representar clientes y no registros mensuales, se trabajó con una tabla de clientes únicos para evitar contar varias veces a la misma persona.

Los resultados muestran que la actividad de reserva presenta cierta estacionalidad, con mayor volumen en meses como julio y diciembre. También se observa una relación positiva clara entre la distancia recorrida y los puntos acumulados. A nivel geográfico, la mayor parte de los clientes se concentra en Ontario, British Columbia y Quebec.

Además, el salario promedio tiende a ser más alto en niveles educativos superiores, la tarjeta `Star` es la más frecuente dentro del programa de fidelización y la categoría `Married` concentra el mayor número de clientes.

## Fase 4: Evaluación de diferencias en reservas de vuelos por nivel educativo

En esta última fase se analizó si existían diferencias en el número de vuelos reservados según el nivel educativo de los clientes.

Para ello, se filtró el conjunto de datos y se trabajó únicamente con las variables `Flights Booked` y `Education`. A continuación, se agruparon los registros por nivel educativo y se calcularon estadísticas descriptivas básicas, como la media, la mediana, la desviación estándar y el número de observaciones en cada grupo.

Además, se utilizaron visualizaciones para comparar tanto la distribución como el promedio de vuelos reservados entre los distintos niveles educativos. En concreto, se emplearon un boxplot para observar la dispersión y los posibles valores atípicos, y un gráfico de barras para comparar las medias.

Los resultados muestran que el número de vuelos reservados es bastante similar entre los distintos niveles educativos. Aunque se observan pequeñas variaciones entre grupos, las diferencias en las medias no son grandes y las distribuciones presentan patrones muy parecidos. En general, a nivel descriptivo, no se aprecian diferencias muy marcadas en el comportamiento de reserva según la educación de los clientes.

## Herramientas utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Estructura del proyecto

- `data/`: archivos de datos originales y dataframe limpio
- `notebooks/`: notebook con el desarrollo del análisis
- `README.md`: descripción general del proyecto

## Estado del proyecto

Hasta este punto se han completado:

- la exploración inicial de los datos
- la limpieza del dataset resultante
- el análisis estadístico de variables numéricas y categóricas
- la fase de visualización

El siguiente paso será desarrollar la fase final del ejercicio, centrada en evaluar las diferencias en el número de vuelos reservados según el nivel educativo de los clientes.