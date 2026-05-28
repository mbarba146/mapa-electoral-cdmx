# Data Sources

Este documento registra las fuentes de datos planeadas para el proyecto **Mapa Electoral CDMX**.

El MVP podrá iniciar con datos simulados para validar estructura, experiencia de usuario y arquitectura. Sin embargo, la versión real deberá conectarse a fuentes oficiales y trazables.

---

## 1. Fuente electoral principal: IECM

**Nombre:** Instituto Electoral de la Ciudad de México  
**Uso:** Resultados electorales locales por alcaldía.  
**Datos esperados:**

- Año electoral
- Alcaldía
- Partido o coalición
- Votos
- Porcentaje de votación
- Partido ganador
- Participación ciudadana
- Margen de victoria

**Justificación:**

El IECM es la fuente más adecuada para elecciones locales de la Ciudad de México. Su historial electoral concentra sistemas y documentos de consulta para procesos electorales locales, incluyendo 2018, 2021 y 2024.

**Uso en el MVP:**

La primera versión puede usar datos simulados con la misma estructura esperada. Posteriormente se reemplazarán por datos oficiales normalizados.

**Prioridad:** Alta  
**Estado:** Fuente identificada  
**Riesgo:** Los datos pueden estar distribuidos en sistemas web, PDFs o archivos con formatos distintos por año.

---

## 2. Fuente electoral secundaria: INE / SICEE

**Nombre:** Instituto Nacional Electoral  
**Uso:** Fuente de respaldo para estadística electoral y validación histórica.  
**Datos esperados:**

- Resultados electorales
- Participación ciudadana
- Ganadores
- Alternancia
- Datos por sección o casilla, si aplica

**Justificación:**

El INE cuenta con portales de datos abiertos y sistemas de consulta de estadística electoral. Puede servir como respaldo o ampliación, especialmente si se decide extender el análisis fuera del nivel alcaldía.

**Prioridad:** Media  
**Estado:** Fuente identificada  
**Riesgo:** Puede estar más orientada a elecciones federales; para alcaldías CDMX se prioriza IECM.

---

## 3. Fuente sociodemográfica: INEGI

**Nombre:** Instituto Nacional de Estadística y Geografía  
**Uso:** Contexto sociodemográfico por alcaldía.  
**Datos esperados:**

- Población
- Densidad poblacional
- Escolaridad promedio
- Edad
- Indicadores económicos o sociales
- Claves geográficas

**Justificación:**

INEGI permite consultar indicadores sociodemográficos y económicos por área geográfica, incluyendo demarcaciones territoriales.

**Uso en el MVP:**

Puede iniciar como datos mock para validar el diseño. La integración real puede quedar en fase posterior.

**Prioridad:** Media / Alta  
**Estado:** Fuente identificada  
**Riesgo:** Requiere homologar nombres y claves de alcaldías con los datos electorales.

---

## 4. Fuente geoespacial: Datos Abiertos CDMX / INEGI

**Nombre:** Límite de Alcaldías de la Ciudad de México  
**Uso:** Mapa geoespacial de alcaldías.  
**Datos esperados:**

- Polígonos de alcaldías
- Nombre de alcaldía
- Clave geográfica
- Geometría

**Justificación:**

El Portal de Datos Abiertos de la CDMX cuenta con un conjunto de polígonos de las 16 alcaldías basado en el Marco Geoestadístico de INEGI.

**Uso en el MVP:**

Idealmente se usará GeoJSON. Si la fuente viene en SHP, se convertirá a GeoJSON.

**Prioridad:** Alta  
**Estado:** Fuente identificada  
**Riesgo:** Puede requerir conversión de formato para integrarse al frontend.

---

## 5. Fuente de noticias: GDELT

**Nombre:** GDELT Project  
**Uso:** Portal de noticias políticas por año.  
**Datos esperados:**

- Fecha
- Título
- Medio
- URL
- Idioma
- País fuente
- Resumen o snippet
- Keyword de búsqueda
- Año electoral relacionado

**Justificación:**

GDELT es una base abierta para consultar cobertura mediática global. Puede reemplazar la idea inicial de X/Twitter sin costos de API y sin depender de una plataforma cerrada.

**Uso en el MVP:**

Se puede crear una página de noticias simuladas y documentar la futura integración. Si hay tiempo, se puede hacer una consulta básica a GDELT.

**Prioridad:** Media  
**Estado:** Fuente identificada  
**Riesgo:** Puede devolver resultados ruidosos; debe presentarse solo como contexto, no como explicación causal del voto.

---

## Estrategia del MVP

Para reducir riesgo, el MVP usará datos simulados con la estructura esperada de producción.

Orden de implementación:

1. Crear estructura mock de datos electorales.
2. Construir dashboard con filtros y descarga CSV.
3. Integrar mapa conceptual o GeoJSON de alcaldías.
4. Documentar fuentes oficiales.
5. Reemplazar datos mock por datos reales si el tiempo lo permite.
6. Dejar GDELT como página contextual o integración futura.

---

## Nota metodológica

Los datos simulados del prototipo no representan resultados oficiales.

La aplicación no busca predecir elecciones ni explicar causalidad entre variables sociales, noticias y voto. Su objetivo es explorar patrones territoriales de votación y mostrar una arquitectura de aplicación web reproducible.
