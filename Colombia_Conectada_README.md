# Colombia Conectada - Infraestructura Nacional de Fibra Optica

> Analisis de datos del Proyecto Nacional de Fibra Optica para el Desarrollo Regional y la Inclusion Digital en Colombia.

**Curso:** Analisis de Datos — Transicion Energetica y Tecnologias de Informacion
**Fecha:** Marzo 2026

---

## Equipo de Trabajo

| Integrante | Rol |
|---|---|
| Camilo Gomez Rendon | Analista de Datos |
| Maria Dilia Gomez Montoya | Analista de Datos |
| Mariana Sanchez Castaneda | Analista de Datos |
| Jefferson Patino Hincapie | Analista de Datos |
| Juan Jose Sanchez Quiroz | Analista de Datos |
| Damian Gutierrez Gaviria | Analista de Datos |

---

## Resumen del Proyecto

Colombia Conectada es un proyecto de analisis de datos que examina la infraestructura nacional de fibra optica desplegada a traves del Proyecto Nacional de Fibra Optica (MINTIC / Fondo Unique de TIC). A partir de un dataset oficial que registra **788 municipios beneficiados** distribuidos en **27 departamentos** y **6 regiones geograficas**, se desarrollo un proceso integral de integracion, analisis y visualizacion de datos orientado a identificar patrones de inversion, distribucion geografica y posibles falencias en la cobertura actual del servicio.

### Problematica

La brecha digital en Colombia representa uno de los desafios mas significativos para el desarrollo socioeconomico equitativo del pais. A pesar de los avances en conectividad, persisten disparidades profundas entre zonas urbanas metropolitanas y areas rurales/perifericas donde el acceso a internet de alta velocidad sigue siendo limitado o inexistente. Sin herramientas robustas de analisis, la toma de decisiones sobre expansion de cobertura, renovacion de contratos y priorizacion de zonas se ve limitada por la falta de informacion consolidada y accesible.

---

## Objetivos

- Identificar y cuantificar brechas de cobertura en fibra optica entre regiones y departamentos.
- Disenar e implementar una base de datos relacional (MySQL) para consulta y analisis eficiente.
- Desarrollar consultas SQL avanzadas y scripts en Python para extraccion de insights.
- Construir dashboards interactivos con Streamlit para visualizacion efectiva.
- Crear una landing page accesible al publico general.
- Proponer recomendaciones estrategicas basadas en evidencia para fortalecer la politica publica de conectividad.

---

## Metodologia

El proyecto sigue un enfoque estructurado de cinco etapas:

```
1. Recoleccion y Limpieza de Datos
       |
2. Diseno de Base de Datos (MySQL)
       |
3. Consultas SQL + Analisis con Python (pandas, matplotlib)
       |
4. Visualizacion Interactiva (Streamlit)
       |
5. Comunicacion de Resultados (Landing Page)
```

1. **Recoleccion y Limpieza:** Dataset oficial con 788 registros y 14 variables (geograficas, financieras, temporales). Validacion de calidad con deteccion de nulos e inconsistencias.
2. **Base de Datos:** Esquema relacional en MySQL normalizado hasta 3NF con 5 tablas y restricciones de integridad referencial.
3. **Consultas y Analisis:** Mas de 20 consultas SQL especializadas + scripts en Python para procesamiento avanzado y generacion de graficos.
4. **Visualizacion:** Dashboards interactivos en Streamlit con graficos Plotly Express, filtros dinamicos y tablas resumen.
5. **Comunicacion:** Landing page responsiva presentando hallazgos, metodologia y recomendaciones.

---

## Base de Datos

### Estructura Relacional (MySQL - 3NF)

```
  region ──1:N──> departamento ──1:N──> municipio
                                           |
                                           | N:1
                                           v
                                    proyecto_fibra ──N:1──> indicador
```

| Tabla | Tipo | Clave Primaria | Descripcion |
|---|---|---|---|
| `region` | Catalogo | `id_region` (AUTO) | 6 macro-regiones geograficas |
| `departamento` | Catalogo | `cod_departamento` | 27 departamentos cubiertos |
| `municipio` | Catalogo | `cod_municipio` | 788 municipios beneficiados (cod. DANE) |
| `indicador` | Catalogo | `id_indicador` | Indicadores de seguimiento |
| `proyecto_fibra` | Hechos | `id_proyecto` (AUTO) | Fechas, estados, inversiones, vigencias |

### Vistas Implementadas

- **`v_inversion_por_departamento`**: Inversion total, MINTIC y contrapartida por departamento, con conteo de municipios y region.
- **`v_inversion_por_region`**: Cobertura e inversion total agrupada por las 6 regiones geograficas del pais.

---

## Indicadores Clave

| Indicador | Valor |
|---|---|
| Total de proyectos | **788 municipios** |
| Departamentos cubiertos | **27** |
| Regiones | **6** |
| Inversion total acumulada | **$1.010.902.595.117 COP** |
| Inversion MINTIC | **$435.166.092.392 COP (43.1%)** |
| Inversion contrapartida | **$575.736.502.725 COP (56.9%)** |
| Inversion promedio por municipio | **$1.282.937.694 COP** |
| Estado predominante | **En Operacion (100%)** |

---

## Distribucion por Region

| Region | Municipios | Inversion Total (COP) | % del Total |
|---|---|---|---|
| Centro Oriente | 316 | $424.700.841.225 | 42.0% |
| Pacifico | 131 | $170.493.636.332 | 16.9% |
| Caribe | 130 | $154.258.584.438 | 15.3% |
| Centro Sur | 95 | $114.355.999.950 | 11.3% |
| Eje Cafetero | 68 | $80.762.533.173 | 8.0% |
| Llano | 48 | $66.330.999.999 | 6.6% |

---

## Top 5 Departamentos por Inversion

| Departamento | Municipios | Inversion Total (COP) | % del Total |
|---|---|---|---|
| Boyaca | 117 | $150.411.857.076 | 14.9% |
| Cundinamarca | 89 | $119.604.060.917 | 11.8% |
| Santander | 78 | $111.222.729.696 | 11.0% |
| Narino | 62 | $82.127.999.982 | 8.1% |
| Bolivar | 41 | $54.192.628.548 | 5.4% |

---

## Hallazgos Principales

### Concentracion regional de la inversion
La Region Centro Oriente concentra el **42% de la inversion total** con 316 municipios cubiertos, generando una asimetria significativa respecto a regiones como Llano (6.6%) y Eje Cafetero (8.0%). Esta distribucion refleja densidad poblacional y prioridades iniciales, pero sugiere la necesidad de evaluar planes de expansion para las regiones menos favorecidas.

### Modelo de financiacion equilibrada
El 43.1% de la inversion proviene de MINTIC y el 56.9% de contrapartidas territoriales, indicando un modelo de corresponsabilidad financiera entre la Nacion y las entidades locales. Sin embargo, existen municipios donde la contrapartida supera significativamente al aporte MINTIC, generando posibles tensiones financieras en jurisdicciones con menor capacidad fiscal.

### Concentracion temporal de la implementacion
El **97.1% de los proyectos iniciaron operaciones entre 2013 y 2014** (452 y 317 proyectos respectivamente), indicando una fase de despliegue masivo seguida de un periodo de menor actividad (solo 2 proyectos en 2023). Esto implica que una proporcion significativa de contratos estara proxima a vencer en los proximos anos.

---

## Recomendaciones Estrategicas

1. **Expansion focalizada en regiones de menor cobertura:** Disenar planes especificos para las regiones Llano y Eje Cafetero, priorizando municipios con mayor potencial de impacto socioeconomico.

2. **Plan de renovacion anticipada de contratos:** Establecer un mecanismo sistematico de seguimiento y renovacion con calendario de al menos 24 meses antes del vencimiento, incluyendo evaluaciones de desempeno del operador.

3. **Equilibrio en el modelo de financiacion:** Revisar la politica de contrapartidas para municipios con menor capacidad fiscal, explorando mecanismos de subsidio cruzado o cofinanciacion diferenciada. Evaluar la creacion de un fondo de nivelacion.

4. **Monitoreo continuo mediante dashboards:** Institucionalizar los dashboards de Streamlit como herramienta de monitoreo permanente, incorporando indicadores adicionales como velocidad efectiva, usuarios conectados y disponibilidad del servicio.

---

## Tecnologias Utilizadas

| Categoria | Herramienta |
|---|---|
| Base de Datos | MySQL |
| Consultas | SQL |
| Analisis de Datos | Python (pandas, matplotlib) |
| Visualizacion Interactiva | Streamlit, Plotly Express |
| Conexion a BD | mysql-connector-python / SQLAlchemy |
| Presentacion | Landing Page (HTML/CSS responsivo) |

---

## Conclusiones

Este proyecto demuestra el valor transformador del analisis de datos como herramienta para la comprension, el monitoreo y la mejora de las politicas publicas de conectividad en Colombia. A traves de la integracion sistematica de MySQL, SQL, Python y Streamlit, se construyo un ecosistema analitico completo que permite extraer conocimiento accionable de los datos del Proyecto Nacional de Fibra Optica.

Los hallazgos confirman tanto los logros significativos del proyecto (cobertura de 788 municipios con inversion superior al billon de pesos), como los desafios pendientes: concentracion geografica, proximidad del vencimiento de contratos y asimetrias en el modelo de financiacion. El enfoque adoptado —integrando multiples capas tecnologicas desde el almacenamiento hasta la visualizacion interactiva— constituye un modelo replicable para otros proyectos de politica publica que requieran un manejo riguroso y accesible de informacion.

---

*Informe generado en el marco del curso de Analisis de Datos — Transicion Energetica y Tecnologias de Informacion. Marzo 2026.*
