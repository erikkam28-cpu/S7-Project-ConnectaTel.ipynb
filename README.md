# S7-Project-ConnectaTel.ipynb
Análisis exploratorio de datos de clientes de una empresa de telecomunicaciones latinoamericana (ConnectaTel). Incluye limpieza de datos, detección de outliers, segmentación por edad y nivel de uso, y recomendaciones comerciales basadas en patrones de consumo

Objetivo
Evaluar el comportamiento de los clientes de ConnectaTel a partir de datos históricos de registro, uso de llamadas y mensajes. El análisis busca:
- Limpiar y preparar los datos para el análisis.
- Identificar patrones de consumo por tipo de plan.
- Segmentar a los clientes por edad y nivel de uso.
- Generar recomendaciones accionables para mejorar la oferta de planes y estrategias de retención.

Datasets utilizados
| Archivo | Descripción | Filas | Columnas |
|--------|-------------|-------|----------|
| `plans.csv` | Información de los planes disponibles (precio, minutos, GB, costos por extra) | 2 | 8 |
| `users_latam.csv` | Datos de los clientes (edad, ciudad, fecha de registro, plan, churn) | 4,000 | 8 |
| `usage.csv` | Detalle del uso real de servicios (llamadas y mensajes) | 40,000 | 6 |

Etapas del análisis
### 1. Carga y exploración inicial
- Importación de librerías (`pandas`, `seaborn`, `matplotlib`).
- Carga de los tres datasets y revisión con `.head()`, `.info()`, `.shape()`.
### 2. Limpieza de datos
- Reemplazo del sentinel `-999` en `age` por la mediana.
- Reemplazo del sentinel `"?"` en `city` por `pd.NA`.
- Corrección de fechas futuras (año 2026) en `reg_date` → marcadas como `pd.NaT`.
- Eliminación de 50 nulos en `usage.date`.
- Confirmación de nulos estructurales MAR en `duration` y `length`.
### 3. Agregación de uso por usuario
- Creación de métricas por usuario: `cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`.
- Merge con el dataset de usuarios para construir `user_profile`.
### 4. Análisis estadístico y visualización
- Resumen estadístico de columnas numéricas.
- Histogramas por plan (`hue='plan'`) para detectar diferencias de comportamiento.
- Boxplots para identificar outliers.
- Cálculo de límites IQR para las variables con valores extremos.
### 5. Segmentación
- Creación de `grupo_uso`: Bajo uso / Uso medio / Alto uso.
- Creación de `grupo_edad`: Joven / Adulto / Adulto Mayor.
- Visualización de distribución de segmentos con `countplot`.
### 6. Análisis ejecutivo
- Conclusiones por segmento.
- Recomendaciones comerciales para ConnectaTel.

