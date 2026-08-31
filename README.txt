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
