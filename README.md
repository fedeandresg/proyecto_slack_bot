![Logo](https://blog.soyhenry.com/content/images/2021/02/HEADER-BLOG-NEGRO-01.jpg)

# DATA SCIENCE - PROYECTO FINAL
# Desarrollo Bot de Inteligencia Artificial

Para este proyecto se trabajó en conjunto con la startup **`Holocruxe`** ante la necesidad de crear el primer motor de inteligencia artificial para la misma.
Luego de varios intentos y deliberaciones se concluyó que un buen MVP sería la construcción de un Bot de Inteligencia Aritificial que pudiese integrarse a diversas plataformas con las que el usuario interactúa día a día.

## Contexto

Se plantea la necesidad de crear un bot que mediante el uso de IA, permita mejorar y aumentar la productividad de los usuarios que utilizan la plataforma **`Slack`**. El bot debe poder ofrecer recomendaciones y/o sugerencias para mejorar la agenda del usuario en cuanto a sus tareas y/o actividades diarias.

## Dataset

Debido a que el trabajo en cuestión requiere de datos reales de usuarios activos, para las pruebas del bot y el entrenamiento del modelo de Machine Learning, se optó por trabajar con datos sintéticos creados mediante la librería `Faker` de **`Python`**.

## Funcionamiento

**`HOLOBOT`** es un bot de slack que recopila datos en base a las respuestas a formularios que brinda el usuario. Su interfaz gráfica es similar a la de un formulario con botones de opción, donde el usuario puede elegir entre 2 ó más respuestas preestablecidas.

Los datos serán recolectados a través de 2 formularios: 

- Un formulario que se completa por la mañana, el cual pregunta acerca de las tareas que se desarrollarán en el día. Las respuestas a dicho formulario serán almacenadas en una colección de **`MongoDb`** denominada initial_questions como un documento por cada día y usuario. La intención es conocer si el usuario tiene agenda planeada o no para el día;

- Un formulario que se completa al finalizar la jornada acerca de las actividades que se desarrollaron en la misma. Las respuestas a dicho formulario serán almacenadas en una colección de **`MongoDb`** denominada final_questions como un documento por cada día y usuario. La intención es conocer cómo el usuario ha desarrollado sus tareas durante el día y si ha cumplido los propósitos que tenía.

Finalmente el HOLOBOT aplica IA para indicar si el usuario estuvo por encima o por debajo de la estimación de productividad para el día (variable objetivo definida en el modelo de Machine Learning).

## Stack tecnológico

Para el proyecto se decidieron utilizar las siguientes tecnologías:

- **`Python`**: desarrollo y programación del bot, integración del bot con slack, integración del bot con MongoDB y almacenamiento del modelo de machine learning;
- **`Slack`**: plataforma de interacción donde el usuario carga las respuestas a formularios y donde recibe las recomendaciones;
- **`MongoDB`**: gestor de base de datos para almacenar las respuestas a los formularios que posteriormente serán utilizados para el modelo de machine learning y dashboard interactivo;
- **`Tensorflow`**: librería de machine learning utilizada para crear un modelo de regresión lineal y predecir la productividad del usuario en función de las respuestas;
- **`Power BI`**: plataforma para crear un dashboard interactivo sobre las respuestas del usuario que le será entregado semanalmente;
- **`Amazon Web Services`**: entorno cloud para el deployment y puesta en producción (próximamente).

## Modelo de Machine Learning

Para el modelo de `Machine Learning` se utilizó un dataset con registros sintéticos el cual permitió el entrenamiento del modelo. Para el mismo se utilizó la librería de Python denominada **`Tensorflow`** con un modelo de `Regresión Lineal`. 
El modelo consistió en predecir para cada usuario y por cada día, en función a los datos ingresados respecto a su agenda, la productividad de la variable conocida como `productividad_hoy` correspondiente de modo de poder constatar con la estimación subjetiva de cada usuario al final de la jornada. 
Para el entrenamiento se utilizó un 70% de los datos y para la evaluación un 30%. 
En esta etapa, el modelo no presenta grandes resultados en cuanto a métricas de evaluación pero se espera que las mismas mejoren a medida que el bot comience a recibir respuestas de usuarios reales y a re-entrenarse en consecuencia.

Se pueden visualizar los códigos realizados en el siguiente
[archivo](https://github.com/fedeandresg/proyecto_slack_bot/blob/main/EDA%20y%20Modelo%20de%20machine-learning/modelo_tensor_flow_holobot.ipynb)

## Deployment

Para el deploy del proyecto, se ha planificado el uso de **`AWS`**.
En esta primer etapa no se ha efectuado el deployment, y el trabajo se ha orientado a entregar un MVP para la evaluación y consideración de la puesta en producción.


