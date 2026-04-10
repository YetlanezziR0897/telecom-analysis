# telecom-analysis
# Sprint 7 - Análisis estadístico para detectar patrones de uso de clientes

## Descripción del proyecto

Este proyecto corresponde al análisis exploratorio y estadístico de una base de clientes de telecomunicaciones, con el objetivo de identificar patrones de comportamiento, segmentar usuarios y detectar oportunidades de negocio a partir del uso de mensajes, llamadas y minutos consumidos.

A través de este análisis se buscó responder preguntas clave del negocio, como:

- ¿Qué segmentos de clientes muestran mayor o menor uso de llamadas y mensajes?
- ¿Qué usuarios presentan valores atípicos que puedan indicar comportamientos inusuales?
- ¿Cómo varía el uso según la edad y el tipo de plan contratado?
- ¿Qué patrones pueden ayudar a diseñar mejores planes y optimizar la oferta comercial?

---

## Objetivo del análisis

Traducir los hallazgos estadísticos en conclusiones accionables para el negocio, enfocadas en:

- segmentación de clientes,
- patrones de uso,
- detección de valores atípicos,
- identificación de segmentos valiosos,
- oportunidades de mejora en la oferta de planes.

---

## Contenido del repositorio

Este repositorio contiene:

- `Sprint_7_analisis_estadistico.ipynb`  
  Notebook principal con todo el análisis exploratorio, limpieza de datos, visualizaciones, segmentación e insight ejecutivo.

- `README.md`  
  Documento descriptivo del proyecto.

- Archivos de datos utilizados para el análisis, en caso de incluirse en el repositorio.

---

## Tecnologías utilizadas

- Python 3
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook 

---

## Principales hallazgos

### 1. Calidad de datos
Se detectaron valores nulos en distintas columnas, aunque en su mayoría no comprometen el análisis:

- `city`: ~12%
- `churn_date`: ~88%
- `date`: ~0.1%
- `length`: ~48%
- `duration`: ~55%

También se detectaron valores erróneos en la variable `age`, los cuales fueron corregidos usando la mediana.

### 2. Perfil general de usuarios
- Se analizaron aproximadamente **3,999 usuarios**
- Edad promedio: **48 años**
- Rango de edad: **18 a 79 años**

La población es amplia y diversa, con predominio del segmento adulto.

### 3. Segmentación por edad
Se construyeron grupos de edad para facilitar el análisis:

- **Joven:** 18 a 30 años
- **Adulto:** 31 a 60 años
- **Adulto Mayor:** más de 60 años

El grupo con mayor presencia es el de **Adultos**, seguido por **Adultos Mayores**.

### 4. Segmentación por nivel de uso
Se clasificó a los usuarios según su intensidad de consumo:

- **Bajo uso**
- **Uso medio**
- **Alto uso**

El grupo dominante fue **Uso medio**, con aproximadamente **74% del total**, lo que indica que la mayoría de los usuarios consume el servicio de manera moderada.

### 5. Comportamiento de uso
Promedios observados:

- Mensajes: **5.52**
- Llamadas: **4.48**
- Minutos en llamadas: **23.31**

Esto sugiere un comportamiento de uso moderado, con una distribución sesgada hacia la derecha, especialmente en la variable de minutos.

### 6. Valores atípicos detectados
Se identificaron outliers en variables de consumo:

- `cant_mensajes`: **46**
- `cant_llamadas`: **30**
- `cant_minutos_llamada`: **109**

Estos valores no necesariamente representan errores, sino usuarios intensivos que podrían pertenecer a un segmento de alto valor comercial.

### 7. Insight ejecutivo
La mayoría de los clientes pertenece al segmento adulto y presenta un nivel de uso medio. Sin embargo, existe un grupo reducido de usuarios intensivos que concentra consumos atípicos, especialmente en minutos de llamada.

Esto representa una oportunidad para:

- diseñar estrategias de **upselling** hacia planes premium,
- crear ofertas diferenciadas para usuarios intensivos,
- optimizar la propuesta de valor para segmentos adultos, que parecen ser los más rentables.

---

## Recomendaciones de negocio

- Enfocar estrategias comerciales en el segmento **Adulto**, ya que concentra buena parte del consumo.
- Diseñar planes específicos para usuarios de **alto consumo**, especialmente en llamadas y minutos.
- Crear campañas de conversión para mover usuarios de **uso medio** hacia planes de mayor valor.
- Mantener monitoreo sobre usuarios con comportamiento atípico para detectar oportunidades comerciales o posibles anomalías.

---

