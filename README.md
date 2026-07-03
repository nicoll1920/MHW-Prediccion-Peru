# 🌊 Predicción de Temperatura Superficial del Mar e Identificación de Olas de Calor Marinas (MHW) en la Costa del Perú (1990-2025)

[cite_start]**Proyecto Integrador - Ciencia de Datos Ambientales** [cite: 135]  
[cite_start]**Universidad de Ingeniería y Tecnología - UTEC** [cite: 136]

---

## 3.1. Descripción del Problema Ambiental
[cite_start]Las olas de calor marinas (Marine Heatwaves, MHW) son periodos prolongados de temperatura superficial del mar anormalmente alta[cite: 149]. [cite_start]En la costa peruana, estos eventos extremos alteran fuertemente los ecosistemas marinos, disminuyen la eficiencia de los procesos de afloramiento (surgencia) y modifican drásticamente la disponibilidad de recursos pesqueros clave, teniendo impactos ecológicos y económicos importantes[cite: 150]. 

## 3.2. Indicadores Ambientales Clave e Hipótesis
[cite_start]Para abordar este problema y verificar su comportamiento [cite: 153][cite_start], se utilizaron los siguientes indicadores ambientales[cite: 151, 152]:
* **SST promedio regional/zonal (°C):** Temperatura superficial del mar (variable objetivo).
* **Anomalía climatológica de SST (°C):** Desviación frente al comportamiento normal esperado.
* **Días bajo condición MHW:** Frecuencia de los eventos.
* **Duración e Intensidad Acumulada:** Persistencia de la ola de calor y severidad térmica total.

[cite_start]**Hipótesis del proyecto:** [cite: 153]
1. La SST puede ser estimada a partir de su comportamiento previo (lags), variables estacionales y variables climáticas complementarias (como ICEN y viento).
2. El desempeño del modelo Random Forest variará entre las zonas Norte, Centro y Sur debido a sus marcadas diferencias oceanográficas y de dinámica local.

## 3.3. Arquitectura y Flujo de Datos
[cite_start]El proyecto procesa datos históricos mediante el siguiente flujo[cite: 154, 155, 158]:
1. [cite_start]**Fuentes utilizadas:** Datos de Temperatura Superficial del Mar de **NOAA OISST v2.1** (NetCDF), variables explicativas del Índice Costero El Niño **ICEN** (CSV) y componentes de viento u10/v10 de **ERA5** (NetCDF)[cite: 156, 157].
2. [cite_start]**Pipeline de procesamiento:** Carga de datos → Limpieza y conversión a Celsius → Filtrado latitudinal → Promedio zonal → Cálculo de climatología y umbral P90 → Modelado y validación[cite: 158].

## 3.4. Análisis Descriptivo (EDA)
[cite_start]Se realizó una inspección de la serie temporal entre 1990 y 2025/2026[cite: 159, 161]:
* Se identificaron zonas con rangos latitudinales precisos: Norte (0° a 6° S), Centro (6° S a 13° S) y Sur (13° S a 20° S).
* [cite_start]Se trataron valores faltantes y outliers estacionales, calculando la climatología base de la región para aislar la anomalía térmica[cite: 162].
* [cite_start]Se graficó la distribución histórica de la SST por zonas y se identificaron picos correlacionados con eventos El Niño conocidos[cite: 163, 164].

## 3.5. Desarrollo del Modelo Analítico o Predictivo
[cite_start]Se entrenó un modelo **Random Forest Regressor** para predecir la temperatura superficial de cada zona[cite: 165, 167]. 
[cite_start]Se realizó una división cronológica estricta de **70% para entrenamiento (histórico)** y **30% para validación (futuro)**, evitando así el *data leakage* en la serie temporal[cite: 166]. Tras obtener las predicciones de SST, se aplicó la metodología de Hobday et al. (2016) [cite_start]sobre dicha predicción para detectar olas de calor[cite: 166].

## 3.6. Selección del Mejor Modelo
[cite_start]Se entrenaron modelos independientes por zona geográfica, evaluados con las métricas **MAE, RMSE y R²**[cite: 168, 169]. [cite_start]Se comparó el desempeño predictivo frente a la base observacional (NOAA), confirmando que las predicciones termales lograban capturar la varianza lo suficiente como para detectar los picos de las MHW en el set de prueba[cite: 170].

## 3.7. Contribuciones Esperadas
1. [cite_start]**Detección Anticipada:** Establecer una metodología predictiva capaz de estimar anomalías térmicas en la costa, facilitando sistemas de alerta temprana[cite: 171, 172].
2. [cite_start]**Segmentación Regional:** Demostrar cómo las diferencias oceanográficas entre las zonas Norte, Centro y Sur exigen modelos adaptados localmente para mayor precisión[cite: 172, 173].
3. [cite_start]**Visibilidad Pública:** Proveer una herramienta interactiva abierta para la visualización del monitoreo de SST y las olas de calor históricas en el mar peruano[cite: 172, 173].

## 3.8. Dashboard Interactivo
[cite_start]El proyecto incluye un dashboard interactivo diseñado con mapas (Folium/Leaflet) y gráficos dinámicos que muestran la serie de tiempo de la SST por zonas geográficas[cite: 174, 177, 179].
🔗 **Puedes acceder al dashboard del equipo aquí:**
[cite_start]👉 [https://nicoll1920.github.io/Grupo5-MHW-Prediccion-Peru/](https://nicoll1920.github.io/Grupo5-MHW-Prediccion-Peru/) [cite: 175, 186]

## 3.9. Conclusiones
[cite_start]El pipeline implementado permitió predecir la SST de forma robusta e identificar olas de calor marinas simuladas en base a predicciones[cite: 187, 188]. Las variables estacionales y la historia reciente mostraron alto poder explicativo. [cite_start]Como limitación, la exactitud extrema de los umbrales de detección MHW requiere un ajuste fino continuo y mayor integración de covariables oceanográficas para las dinámicas abruptas (outliers climáticos)[cite: 189].
