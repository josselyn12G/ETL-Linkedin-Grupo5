# ETL Global: Mercado laboral de Data Analysts en LinkedIn

Proceso ETL en Python que consolida ofertas de empleo de LinkedIn de **Estados Unidos, Canadá y África** para comparar el mercado laboral de *Data Analyst* entre continentes.

Proyecto de la materia **Análisis y Visualización de Datos** (UDLA).

## Archivos

| Archivo | Descripción |
|---|---|
| `ETL_LinkedIn_Global.ipynb` | Notebook con todo el proceso, el código comentado y el análisis |
| `linkedin-jobs-usa.csv` | Ofertas de Estados Unidos (2 845 filas) |
| `linkedin-jobs-canada.csv` | Ofertas de Canadá (2 773 filas) |
| `linkedin-jobs-africa.csv` | Ofertas de África (2 872 filas) |
| `linkedin_jobs_analisis_global.csv` | Dataset final limpio (resultado de la Fase 4) |

## Proceso

1. **Extracción y consolidación:** carga de los tres CSV, columna `continent` y unión en `df_global`.
2. **Diagnóstico y limpieza:**
   - Revisión de tipos, nulos y nulos disfrazados (`"Nan"`).
   - Eliminación de duplicados mediante el ID de la oferta extraído del `link`.
   - Conversión de `salary` a `salary_numeric` (punto medio del rango).
   - Análisis de asimetría y curtosis.
   - Filtro `salary_numeric > 18 000`.
3. **Análisis:** salario promedio por continente, importancia de SQL, tamaño de empresa y día de publicación.
4. **Carga y conclusiones:** exportación del dataset limpio.

## Hallazgos principales

- **Duplicados ocultos:** las 8 490 filas corresponden a solo **524 ofertas únicas**. `duplicated()` no detectaba las copias porque cada link incluye parámetros de rastreo distintos.
- **Salario:** Norteamérica tiene un promedio de **≈ 94 135 USD/año** (mediana 90 000). **África no publica ningún salario**, por lo que la comparación salarial entre continentes no es posible.
- **SQL:** aparece en **≈ 75 %** de las ofertas de *Data Analyst* en ambos continentes.
- **Empresas:** ninguna oferta proviene de Amazon, Apple, Google, Microsoft o Meta.
- **Publicación:** el **martes** es el día con más ofertas en ambos continentes; África publica además el 11 % de sus ofertas en sábado.

## Requisitos

```
pandas
numpy
matplotlib
scipy
```

Para ejecutarlo, abre el notebook en Google Colab o Jupyter, sube los tres CSV a la misma carpeta y ejecuta todas las celdas en orden.
