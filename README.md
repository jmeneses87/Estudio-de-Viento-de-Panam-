
# PROYECTO: ESTUDIO DEL VIENTO EN PANAMÁ

Este repositorio contiene el desarrollo del proyecto académico correspondiente al curso "Proyecto Integrador I" de la Maestría en Analítica de Datos.

## Objetivo General
Analizar el comportamiento del viento en diferentes niveles de la atmósfera sobre Panamá, utilizando datos reanalizados de ERA5 y generando un dataset limpio con variables meteorológicas relevantes.

## Estructura del Repositorio

```
/data/         # Contiene archivos CSV procesados de 2015 a 2024
/scripts/      # Contiene notebook o scripts de procesamiento
/doc/          # Contiene reportes semanales y descripción de columnas
```

## Dataset Procesado

Se extrajeron las siguientes variables de los archivos GRIB:
- `u_wind`: Componente zonal del viento (m/s)
- `v_wind`: Componente meridional del viento (m/s)
- `speed`: Magnitud del viento (m/s)
- `temperatura`: Temperatura promedio (K)
- `geopotencial`: Geopotencial medio (m²/s²)
- `altura_m`: Altura estimada (m)
- `isobaricInhPa`: Nivel de presión (hPa)
- `time`: Fecha y hora UTC
- `time_local`: Fecha y hora local ajustada a UTC-5 (Panamá)
- `año`: Año del archivo original

### Cálculo de la velocidad del viento (`speed`)
La velocidad del viento se calcula a partir de las componentes zonal (`u_wind`) y meridional (`v_wind`) mediante la fórmula:

```
speed = sqrt(u^2 + v^2)
```

Esta fórmula permite calcular la magnitud del viento a partir de sus dos direcciones horizontales.

## Frecuencia y Resolución

- Frecuencia temporal: Cada 4 horas (00, 04, 08, 12, 16, 20 UTC)
- Niveles de presión: 200, 700, 850, 925, 1000 hPa
- Período: 2015 a 2024

> ⚠️ La columna `time` está en UTC. `time_local` corresponde a la hora de Panamá (UTC-5).

## Casos de Estudio Sugeridos

1. **Agricultura – Vuelco de cultivos por vientos fuertes**  
   Evaluar cómo los vientos intensos afectan cultivos vulnerables como plátano y maíz.  
   Se pretende establecer umbrales críticos de velocidad del viento que causan daño estructural.  
   **Nivel de análisis:** 10–100 m sobre el suelo.

2. **Salud – Enfermedades respiratorias y viento seco**  
   Analizar si el aumento de vientos secos coincide con mayor dispersión de partículas (polvo, contaminantes) y aumento de casos respiratorios.  
   Se recomienda correlacionar con indicadores hospitalarios y humedad relativa.  
   **Nivel de análisis:** 1000 y 925 hPa.

3. **Marítimo – Incidentes en zonas portuarias**  
   Estudiar si vientos racheados afectan la operación segura de embarcaciones en puertos como Balboa y Cristóbal.  
   Aplicable para emitir alertas en combinación con datos de oleaje.  
   **Nivel de análisis:** 1000 hPa.

4. **Terrestre – Tormentas por viento en niveles medios**  
   Evaluar cómo el viento en niveles intermedios (700–850 hPa) está relacionado con el desarrollo de tormentas que causan inundaciones.  
   Útil para modelos meteorológicos e hidrológicos acoplados.

## Autor

- **Joel Meneses**  
Estudiante de Maestría en Analítica de Datos  
Universidad Tecnológica de Panamá

## Profesor

- **Juan Marcos Castillo, PhD**

## Fuente de Datos

- Copernicus Climate Data Store: https://cds.climate.copernicus.eu/

## Licencia

Uso académico exclusivamente. Datos descargados y procesados por el autor.
