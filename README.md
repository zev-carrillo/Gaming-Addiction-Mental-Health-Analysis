# Gaming Addiction & Mental Health Analysis

Análisis exploratorio y estadístico sobre la relación entre el tiempo de juego (videojuegos) y distintos indicadores de salud mental: estrés, ansiedad, depresión, soledad, riesgo de salud mental, calidad del sueño y rendimiento académico/laboral.

Proyecto realizado como práctica de análisis de datos, con énfasis en pruebas de correlación, significancia estadística y comparación entre subgrupos poblacionales.

## Objetivo

Explorar si existe asociación entre el tiempo diario de juego y distintas variables de bienestar psicológico, y si esa relación varía según género, edad o tipo de juego.

### Preguntas de investigación

1. ¿Más horas de juego se asocian con más ansiedad, depresión o estrés?
2. ¿Cómo se relacionan las horas de juego con el sueño y el rendimiento académico o laboral?
3. ¿Difiere el impacto según edad o género?

## Dataset

- **Fuente:** https://www.kaggle.com/datasets/ajitashwath/gaming-addiction-dataset 
- **Tamaño:** 250 registros
- **Variables principales:**
  - `daily_playtime_hours`: horas de juego diarias
  - `stress_score`: puntaje de estrés
  - `anxiety_level`: nivel de ansiedad
  - `depression_indicator`: indicador de depresión
  - `loneliness_score`: puntaje de soledad
  - `mental_health_risk_score`: riesgo general de salud mental
  - `sleep_hours`: horas de sueño
  - `gpa_or_performance_score`: rendimiento académico/laboral
  - `gender`: genero
  - `age`: edad

## Metodología

- **Análisis exploratorio de datos (EDA):** distribución de variables, valores nulos, outliers.
- **Pruebas de correlación:** Spearman (`scipy.stats.spearmanr`), elegida por la naturaleza ordinal/no necesariamente lineal de varias variables.
- **Umbral de significancia:** p < 0.05
- **Interpretación de magnitud (convención de Cohen):**
  - < 0.10: trivial
  - 0.10–0.29: débil
  - 0.30–0.49: moderada
  - ≥ 0.50: fuerte
- **Análisis por subgrupos:** segmentación por género y grupo de edad, con cálculo de correlaciones independientes por grupo.
- **Control de calidad:** verificación de tamaño de muestra (`n`) por subgrupo para evitar sobreinterpretar resultados con muestras insuficientes.

## Herramientas

- Python 3.14
- pandas
- scipy (stats)
- seaborn 
- statsmodels.stats.proportion (proportions_ztest)
- Jupyter Notebook

## Estructura del repositorio

```
├── gaming_addiction.ipynb     # Notebook principal con el análisis completo
└── README.md
```

## Principales hallazgos

- **Sueño:** relación negativa y moderada entre horas de juego y horas de sueño (ρ ≈ -0.39, p < 0.001), consistente en todos los subgrupos analizados — el hallazgo más robusto del estudio.
- **Estrés:** asociación positiva y moderada con las horas de juego (ρ ≈ 0.30, p < 0.001).
- **Ansiedad y riesgo de salud mental:** asociaciones positivas pero débiles (ρ entre 0.14 y 0.16), estadísticamente significativas.
- **Soledad:** sin evidencia de relación en la muestra general.
- **Rendimiento académico/laboral:** sin relación directa significativa con las horas de juego.
- **Diferencias por género:** las asociaciones con estrés, depresión y riesgo de salud mental son significativas solo en el grupo masculino; la relación con el sueño es significativa en ambos géneros.
- **Diferencias por edad:** el grupo de 26-50 años muestra el patrón más consistente de asociación con todas las variables de salud mental; curiosamente, en ese grupo la soledad se asocia negativamente con las horas de juego (posible función social del juego en adultos).

> Resultados detallados y gráficos en el notebook `gaming_addiction.ipynb`.

## Limitaciones

- Datos transversales: las correlaciones indican asociación, **no causalidad**.
- Algunos subgrupos (ej. identidades de género minoritarias, rangos de edad extremos) tienen tamaños de muestra insuficientes para conclusiones robustas.
- El dataset es sintético, los hallazgos son ilustrativos del método, no generalizables a la población real.
- No se controlaron variables de confusión mediante modelos multivariados (próximo paso sugerido).

## Próximos pasos

- Regresión múltiple controlando por variables demográficas.
- Análisis de mediación (sueño como posible mediador entre horas de juego y rendimiento).
- Visualizaciones adicionales (loess/lowess) para explorar relaciones no lineales.

## Autor

[Zev Carrillo]
