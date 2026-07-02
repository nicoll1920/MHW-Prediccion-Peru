# 🌊 Proyecto Integrador: Predicción e Identificación de Olas de Calor Marinas (MHW) en la Costa del Perú (1990-2025)

##  Curso: Ciencia de Datos Ambientales (CDA)
**Universidad de Ingeniería y Tecnología (UTEC)** ---

##  1. Descripción del Problema Ambiental e Indicadores

### Contexto Territorial y Relevancia
Las **Olas de Calor Marinas (MHW)** son anomalías térmicas prolongadas en el océano que causan graves impactos en los ecosistemas marinos y la pesca. Este proyecto aborda la problemática analizando y prediciendo estas anomalías en tres zonas oceanográficas clave de la costa peruana: **Norte, Centro y Sur**.

### Indicadores Ambientales Clave
1. **Temperatura Superficial del Mar (SST):** Datos diarios en grados Celsius (°C).
2. **Anomalía de la SST:** Desviación térmica respecto a la climatología.
3. **Métricas de Eventos MHW:** Duración e intensidad según la metodología internacional de Hobday et al. (2016).

---

##  2. Arquitectura y Flujo de Datos

1. **Ingesta:** Uso de datos satelitales de la **NOAA OISST**, integrados con el Índice Costero El Niño (**ICEN**) y variables de reanálisis **ERA5**.
2. **Pipeline de Preparación:** Carga de datos $\rightarrow$ Limpieza $\rightarrow$ Cálculo de climatología (Hobday) $\rightarrow$ Construcción de variables predictoras (rezagos temporales / lags).

---

##  3. Análisis Descriptivo (EDA)
Se realizó una inspección exhaustiva de la serie temporal (1990-2025), tratamiento de valores atípicos, validación de hipótesis sobre la influencia de variables meteorológicas en la SST y división del análisis para las zonas Norte, Centro y Sur.

---

##  4. Modelado Analítico y Predictivo (Regresión)

A diferencia de enfoques tradicionales de clasificación, este proyecto implementa una metodología en dos fases:
1. **Predicción de la Temperatura:** Entrenamiento de modelos **Random Forest Regressor** para estimar la Temperatura Superficial del Mar (SST) basándose en valores rezagados e índices climáticos.
2. **Identificación de MHW:** Aplicación de la metodología de Hobday sobre las predicciones de SST para detectar los eventos de Olas de Calor Marinas.

**Evaluación:**
* Se realizó una división cronológica de los datos: **70% para entrenamiento y 30% para prueba**, evitando fuga de información futura.
* El desempeño del modelo se comparó usando métricas de regresión como **MAE, RMSE y R²**.

---

##  5. Dashboard Interactivo (GitHub Pages)

Se ha desarrollado un dashboard en Python, publicado en GitHub Pages, que permite explorar visualmente los resultados:
* Mapa interactivo (Folium) de las zonas de estudio.
* Gráficos dinámicos (Plotly) de la SST y sus anomalías.
* Tablas comparativas entre MHW observadas vs. predichas.

**🔗 [https://github.com/nicoll1920/MHW-Prediccion-Peru]**

---

## 💡 6. Contribuciones Ambientales
1. **Pronóstico Cuantitativo:** Capacidad de predecir la magnitud exacta de la SST antes de clasificar el evento.
2. **Línea de Base Histórica:** Catálogo de MHW desde 1990 al 2025 bajo un estándar científico riguroso.
3. **Gestión Regionalizada:** Modelos ajustados de forma independiente para el Norte, Centro y Sur del Perú.
4. **Alerta Temprana:** Herramienta clave para anticipar impactos en la pesca y ecosistemas costeros.
