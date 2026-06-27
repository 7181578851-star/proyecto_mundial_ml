# Proyecto Mundial 2026 - Modelo de Machine Learning

## 1. Descripción del proyecto

Este proyecto desarrolla un modelo de Machine Learning para estimar resultados de partidos del Mundial 2026. El trabajo utiliza datos históricos de partidos, ranking FIFA, calendario del torneo, resultados reales disponibles y variables de rendimiento deportivo.

El objetivo principal es generar predicciones reproducibles que permitan responder las preguntas planteadas en el entregable:

1. ¿Qué países clasificarían a la siguiente fase?
2. ¿Cuál sería el marcador estimado de cada partido?

El modelo no busca afirmar resultados exactos, sino estimar resultados probables a partir de datos y criterios matemáticos.

---

## 2. Objetivo general

Implementar un flujo de análisis predictivo para el Mundial 2026, desde la preparación de datos hasta la generación de predicciones de marcadores y selecciones clasificadas.

---

## 3. Estructura del proyecto

La carpeta del proyecto está organizada de la siguiente manera:

```text
proyecto_mundial_ml/
│
├── Proyecto_Mundial_2026_Modelo_ML.ipynb
├── README.md
├── requirements.txt
│
├── data/
│   ├── matches_1930_2022.csv
│   ├── fifa_ranking_2022-10-06.csv
│   ├── fifa_ranking_2026-06-08.csv
│   ├── schedule_2026.csv
│   ├── world_cup.csv
│   └── resultados_reales_2026.csv
│
└── resultados/
    ├── tabla_posiciones_actualizada_2026.csv
    ├── clasificados_dieciseisavos_32_selecciones.csv
    ├── partidos_dieciseisavos_cuadro_fifa.csv
    ├── respuesta_1_dieciseisavos_resultados_estimados.csv
    ├── respuesta_2_clasificados_a_octavos.csv
    └── respuesta_10_podio_mundial_estimado.csv
```

---

## 4. Datos utilizados

Los datos utilizados se encuentran en la carpeta `data/`.

Archivos principales:

* `matches_1930_2022.csv`: partidos históricos utilizados para el análisis y entrenamiento.
* `fifa_ranking_2022-10-06.csv`: ranking FIFA de referencia para el Mundial 2022.
* `fifa_ranking_2026-06-08.csv`: ranking FIFA de referencia para el Mundial 2026.
* `schedule_2026.csv`: calendario de partidos del Mundial 2026.
* `world_cup.csv`: información histórica de mundiales.
* `resultados_reales_2026.csv`: resultados reales disponibles para actualizar el análisis.

---

## 5. Preparación de datos

Antes de generar las predicciones se realizaron los siguientes procesos:

* Limpieza y estandarización de nombres de selecciones.
* Revisión de valores nulos.
* Integración de ranking FIFA.
* Construcción de variables de rendimiento.
* Cálculo de goles a favor, goles en contra y diferencia de goles.
* Actualización de tablas de posiciones.
* Generación de cruces de fase eliminatoria.

También se evita la fuga de información. Los goles de un partido no se usan como variables predictoras para predecir ese mismo partido, sino como datos históricos o como variable objetivo.

---

## 6. Modelos implementados

En el notebook se implementan modelos de Machine Learning para estimar resultados, entre ellos:

* Regresión logística.
* Random Forest.
* Ridge.
* Lasso.
* Modelo de Poisson calibrado.

Los modelos de clasificación se utilizan para estimar el resultado general del partido. El modelo de Poisson calibrado se utiliza para estimar los goles esperados y obtener marcadores probables.

---

## 7. Justificación del modelo de Poisson calibrado

Los goles son una variable de conteo porque toman valores discretos como 0, 1, 2, 3 o más. Por ello, el modelo de Poisson es adecuado para estimar goles esperados.

En este proyecto se utiliza un Poisson calibrado con variables como:

* Goles a favor.
* Goles en contra.
* Diferencia de goles.
* Puntos por partido.
* Ranking FIFA.
* Rendimiento en fase de grupos.

Esta calibración busca obtener marcadores más realistas y evitar resultados excesivamente repetidos.

---

## 8. Resultados generados

Los resultados principales se guardan en la carpeta `resultados/`.

Archivos principales:

* `tabla_posiciones_actualizada_2026.csv`: tabla de posiciones actualizada.
* `clasificados_dieciseisavos_32_selecciones.csv`: selecciones clasificadas a dieciseisavos.
* `partidos_dieciseisavos_cuadro_fifa.csv`: partidos de dieciseisavos.
* `respuesta_1_dieciseisavos_resultados_estimados.csv`: marcadores estimados de dieciseisavos.
* `respuesta_2_clasificados_a_octavos.csv`: selecciones clasificadas a octavos.
* `respuesta_10_podio_mundial_estimado.csv`: podio estimado como análisis adicional.

---

## 9. Respuesta directa a la consigna

### Pregunta 1: ¿Qué países clasificarían a la siguiente fase?

La respuesta se encuentra en:

```text
resultados/respuesta_2_clasificados_a_octavos.csv
```

Este archivo muestra las selecciones que clasifican a octavos de final.

### Pregunta 2: ¿Cuál sería el marcador estimado de cada partido?

La respuesta se encuentra en:

```text
resultados/respuesta_1_dieciseisavos_resultados_estimados.csv
```

Este archivo contiene los partidos de dieciseisavos de final, el marcador estimado y la selección clasificada.

---

## 10. Instrucciones para ejecutar el proyecto

Para reproducir los resultados:

1. Abrir el notebook `Proyecto_Mundial_2026_Modelo_ML.ipynb`.
2. Verificar que los archivos CSV estén dentro de la carpeta `data/`.
3. Instalar las dependencias con el siguiente comando:

```bash
pip install -r requirements.txt
```

4. Ejecutar todas las celdas del notebook en orden.
5. Revisar las tablas generadas dentro del notebook.
6. Consultar los archivos exportados en la carpeta `resultados/`.

---

## 11. Dependencias

Las librerías necesarias se encuentran en el archivo:

```text
requirements.txt
```

Entre las principales librerías utilizadas están:

* pandas
* numpy
* scikit-learn
* matplotlib
* seaborn
* scipy
* plotly
* nbformat

---

## 12. Limitaciones del modelo

El modelo genera predicciones probabilísticas, no resultados exactos garantizados.

En el fútbol existen factores difíciles de modelar, como lesiones, expulsiones, decisiones arbitrales, penales, clima, cansancio, cambios tácticos y rendimiento individual durante el partido.

Por ello, los resultados deben interpretarse como estimaciones basadas en datos, no como resultados definitivos.

---

## 13. Reproducibilidad

El proyecto incluye:

* Código fuente del modelo en formato notebook.
* Datos utilizados.
* Archivo `requirements.txt` con dependencias.
* Archivo `README.md` con instrucciones.
* Resultados generados en archivos CSV.

Esto permite que otra persona pueda revisar el proyecto y reproducir la ejecución.

---

## 14. Autor

Edgar Heiner Jauregui Epiquien 

Universidad Nacional Toribio Rodríguez de Mendoza de Amazonas
Escuela Profesional de Ingeniería en Ciencia de Datos e Inteligencia Artificial
