# 📱 ConnectaTel: Análisis de Comportamiento y Retención de Clientes

## 🎯 Objetivo / Pregunta de Negocio
¿Qué patrones de uso tienen los clientes de ConnectaTel y qué segmentos representan mayor valor comercial?  
Este proyecto analiza el comportamiento de ~4,000 clientes de telecomunicaciones en Latinoamérica para identificar oportunidades de segmentación, upselling y retención basadas en datos.

---

## 📂 Datos
| Dataset | Fuente | Contenido |
|---|---|---|
| `plans.csv` | TripleTen / Practicum | 2 planes disponibles (Básico y Premium) con precios, minutos, GB y costos por excedente |
| `users_latam.csv` | TripleTen / Practicum | ~4,000 usuarios con edad, ciudad, plan contratado y fecha de registro |
| `usage.csv` | TripleTen / Practicum | Registro de actividad por usuario: mensajes de texto, llamadas y duración en minutos (año 2024) |

---

## ⚙️ Proceso

### 1. Carga y Exploración Inicial (Python - Pandas)
- Carga de los 3 datasets y revisión de estructura, tipos de datos y dimensiones
- Identificación de columnas relevantes por dataset

### 2. Calidad de Datos
- **Valores nulos detectados y tratados:**
  - `city` (~12%): impacto bajo, no se usa para segmentación → se deja como nulo
  - `churn_date` (~88%): consistente con usuarios activos → se deja como nulo
  - `duration` (55%) y `length` (48%): dependientes del tipo de evento (MAR — Missing At Random) → se dejan como nulos sin imputar
- **Valores erróneos:** columna `age` con valores -999 → reemplazados por la mediana de la distribución real
- **Fechas imposibles:** 40 registros con año 2026 en `reg_date` → eliminados (< 1% del total)
- **Valores sentinel:** caracteres "?" en `city` → reemplazados por NA

### 3. Análisis de Uso por Usuario (Python - Pandas)
- Creación de columnas auxiliares `is_text` e `is_call` para conteo por tipo
- Agregación por `user_id`: total de mensajes, llamadas y minutos
- Merge con dataset de usuarios para crear perfil completo (`user_profile`)

### 4. Análisis Estadístico y Visualización (Matplotlib - Seaborn)
- Histogramas por tipo de plan para: edad, mensajes, llamadas y minutos
- Boxplots para detección de outliers en variables de uso
- Cálculo de límites IQR para cuantificar outliers por variable

### 5. Segmentación de Clientes
- **Por nivel de uso:** Bajo uso / Uso medio / Alto uso (basado en llamadas y mensajes)
- **Por edad:** Joven (< 30) / Adulto (30–60) / Adulto Mayor (> 60)

---

## 📊 Insights Clave

1. **El segmento adulto domina y es el más valioso:** El grupo de 31–60 años representa ~50% del total. Los adultos mayores (60+) concentran el mayor consumo de plan Premium, especialmente en llamadas de larga duración — un segmento de alto valor comercial desatendido.

2. **La mayoría de clientes tiene uso moderado con oportunidad de upselling:** El 74% de usuarios cae en "Uso medio". Este segmento es el principal candidato para campañas de conversión hacia el plan Premium, ya que su consumo está cerca del límite del plan Básico.

3. **Los outliers son usuarios de alto valor, no errores:** Se detectaron 109 outliers en minutos de llamada, 46 en mensajes y 30 en llamadas. Estos usuarios intensivos tienden a consumir plan Premium y representan oportunidades de fidelización, no anomalías a eliminar.

---

## 💡 Recomendación / Siguiente Paso
Si esto fuera una tarea laboral real:
- **Campaña de upselling dirigida al segmento "Uso medio":** Ofrecer prueba gratuita de plan Premium a usuarios cuyo consumo supera el 80% del límite del plan Básico.
- **Plan especial para adultos mayores intensivos:** Este segmento muestra alta fidelidad y mayor disposición al plan Premium — un paquete de llamadas ilimitadas podría aumentar su retención.
- **Monitoreo de churn:** Cruzar los datos de `churn_date` con segmentos de uso para identificar qué perfil cancela más y diseñar intervenciones preventivas.

---

## 🔗 Enlaces
- 📓 [Notebook del proyecto](./S7_Version-Estudiante-Project-ConnectaTel.ipynb)

---

## 🛠️ Herramientas Utilizadas
`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `Jupyter Notebook`

---

## 👩‍💻 Sobre mí
Soy Yetlanezzi Robles, Data Analyst con más de 7 años de experiencia en operaciones retail. Actualmente completando mi certificación en Análisis de Datos en TripleTen.

📩 yetlanezziroblescano@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/yetlanezzi-analyst)
