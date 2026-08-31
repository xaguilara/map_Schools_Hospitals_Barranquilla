# Health & Education Facilities — Barranquilla

Geospatial analysis and visualization of the **health** (hospitals and clinics) and **education** (schools) facilities of Barranquilla, Colombia. Built end to end with open-source tools: data download and processing in **QGIS**, spatial analysis and visualization in **Python**, and web publishing with **Leaflet** and **GitHub Pages**.

*Read this in [Spanish / Español](README.md).*

## 🌐 Live products

- **🗺️ Interactive map (viewer):** [Open viewer](https://xaguilara.github.io/map_Schools_Hospitals_Barranquilla/)
  Web map with hospitals and schools color-coded by type, pop-ups showing each facility's name, and a layer toggle.

- **📊 Dashboard:** [Open dashboard](https://xaguilara.github.io/map_Schools_Hospitals_Barranquilla/dashboard.html)
  A dashboard combining key figures (counts by type), a distribution chart, and the interactive map, with a reference legend.

## 🎯 Objective

Locate and characterize the health and education facilities of Barranquilla, and answer an urban-accessibility question: **what share of schools has a health service (hospital or clinic) within 500 meters?**

## 🔎 Key finding

**57.4% of schools (136 of 237) have a hospital or clinic within 500 meters.**

The result was computed independently by two methods —geoprocessing in QGIS (*buffer* + select by location) and a spatial SQL query (`ST_Distance`)— and both returned the same value (136), which validates the analysis.

## 🗂️ Data

- **Source:** OpenStreetMap (downloaded with the QuickOSM plugin in QGIS).
- Open data was processed and cleaned locally before publishing.

## ⚙️ Methodology

1. **Download** facilities from OpenStreetMap by category (`amenity = hospital/clinic/school`).
2. **Integration** of features mapped as points and as polygons (converting polygons to their centroid and merging layers) to avoid losing records.
3. **Attribute cleanup**, done non-destructively, keeping only the relevant fields (name, type, address).
4. **Proximity spatial analysis**, solved and validated through three independent paths:
   - Visual geoprocessing in QGIS: reprojection to a metric system (UTM 18N), a 500 m *buffer*, and select by location.
   - **Spatial SQL** over a GeoPackage (`ST_Distance`).
   - **Python** with GeoPandas (`sjoin_nearest`) and a distance histogram.
5. **Web publishing** of the map (Leaflet, exported with qgis2web) and the dashboard (Python), hosted on GitHub Pages.

## 🧰 Tech stack

- **QGIS** — download (QuickOSM), processing, geoprocessing, and web export (qgis2web).
- **Python** — GeoPandas, Folium, and Matplotlib for analysis and the dashboard.
- **Spatial SQL** — GeoPackage / SpatiaLite (`ST_` functions).
- **Leaflet** — interactive web map.
- **GitHub Pages** — hosting.

## 📌 Notes

Portfolio-oriented practice project. Data comes from OpenStreetMap, so its completeness depends on the community that maintains it.

---

**Author:** Ximena Aguilar —  Architect . GIS Analyst Junior


**SPANISH VERSION**

# Ejercicio de Equipamientos de Salud y Educación — Barranquilla

Proyecto de análisis y visualización geoespacial de los equipamientos de **salud** (hospitales y clínicas) y **educación** (colegios) de Barranquilla, Colombia. Construido de punta a punta con herramientas de código abierto: descarga y procesamiento de datos en **QGIS**, análisis espacial y visualización en **Python**, y publicación web con **Leaflet** y **GitHub Pages**.

## 🌐 Productos en vivo

- **🗺️ Mapa interactivo (visor):** [Abrir visor](https://xaguilara.github.io/map_Schools_Hospitals_Barranquilla/)
  Mapa web con hospitales y colegios diferenciados por color, ventanas emergentes con el nombre de cada equipamiento y control para prender/apagar capas.

- **📊 Dashboard:** [Abrir dashboard](https://xaguilara.github.io/map_Schools_Hospitals_Barranquilla/dashboard.html)
  Tablero que combina indicadores (conteo por tipo), un gráfico de distribución y el mapa interactivo, con leyenda de referencia.

## 🎯 Objetivo

Localizar y caracterizar los equipamientos de salud y educación de Barranquilla, y responder una pregunta de accesibilidad urbana: **¿qué proporción de colegios cuenta con un servicio de salud (hospital o clínica) a menos de 500 metros?**

## 🔎 Hallazgo principal

**El 57,4 % de los colegios (136 de 237) tiene un hospital o clínica a menos de 500 metros.**

El resultado se calculó de forma independiente por dos métodos —geoproceso en QGIS (*buffer* + selección por localización) y consulta de SQL espacial (`ST_Distance`)— y ambos arrojaron el mismo valor (136), lo que valida el análisis.

## 🗂️ Datos

- **Fuente:** OpenStreetMap (descargados con el complemento QuickOSM de QGIS).
- Los datos abiertos se procesaron y depuraron localmente antes de publicar.

## ⚙️ Metodología

1. **Descarga** de los equipamientos desde OpenStreetMap por categoría (`amenity = hospital/clinic/school`).
2. **Integración** de las entidades mapeadas como punto y como polígono (conversión de polígonos a su centroide y unión de capas) para no perder registros.
3. **Limpieza de atributos** de forma no destructiva, conservando solo los campos relevantes (nombre, tipo, dirección).
4. **Análisis espacial de proximidad**, resuelto y validado por tres vías independientes:
   - Geoproceso visual en QGIS: reproyección a un sistema métrico (UTM 18N), *buffer* de 500 m y selección por localización.
   - **SQL espacial** sobre un GeoPackage (`ST_Distance`).
   - **Python** con GeoPandas (`sjoin_nearest`) y un histograma de distancias.
5. **Publicación web** del mapa (Leaflet, exportado con qgis2web) y del dashboard (Python), alojados en GitHub Pages.

## 🧰 Tecnologías

- **QGIS** — descarga (QuickOSM), procesamiento, geoproceso y exportación web (qgis2web).
- **Python** — GeoPandas, Folium y Matplotlib para el análisis y el dashboard.
- **SQL espacial** — GeoPackage / SpatiaLite (funciones `ST_`).
- **Leaflet** — mapa web interactivo.
- **GitHub Pages** — alojamiento de los productos.

## 📌 Notas

Proyecto de práctica orientado a portafolio. Los datos provienen de OpenStreetMap, por lo que su completitud depende de la comunidad que los mantiene.

---

**Autora:** Ximena Aguilar — Arquitecta · Analista GIS Junior
