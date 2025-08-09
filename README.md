# Challenge_2-Telecom_FM
# 📊 Análisis de Evasión de Clientes (Churn) en Telecomunicaciones

## 🧭 Introducción

Este análisis explora una base de datos de una empresa de telecomunicaciones con el objetivo de comprender los factores asociados a la **evasión de clientes (churn)**. Se aplican procesos de limpieza, exploración, análisis estadístico y visualización para detectar patrones que ayuden a generar recomendaciones estratégicas enfocadas en la retención de clientes.

---

## 🧹 Limpieza y Normalización de Datos

### 🔽 Origen de los datos
Los datos fueron obtenidos desde una API en formato `.json` y transformados en un DataFrame de Pandas.

```python
datos=requests.get("https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json")
resultado=json.loads(datos.text)
df=pd.DataFrame(resultado)
![Datos json raw](https://raw.githubusercontent.com/fmonteci/Challenge_2-Telecom_FM/main/001%20Ch2.png)


🔧 Proceso de normalización
El archivo contenía varias columnas con estructuras anidadas (customer, phone, internet, account), por lo cual se aplicó json_normalize para aplanar los datos y luego se concatenaron.

### 🧼 Etapas de limpieza
Eliminación de duplicados

Transformación de datos tipo string a valores numéricos binarios

Conversión de columnas a tipos adecuados (float, int, etc.)

Estándar en los textos: minúsculas, sin espacios extra, sin valores vacíos

Creación de nuevas variables como Cuentas_Diarias (gasto mensual dividido por 30)

### 📌 Proceso de Transformacion
Antes:
📷 <img width="1802" height="198" alt="image" src="https://github.com/user-attachments/assets/93cc45d6-e809-4cc0-83b1-60b506d0f93d" />

Después: 
<img width="1355" height="258" alt="image" src="https://github.com/user-attachments/assets/f892c7ea-a2a1-4a0f-9374-464eb3837e2f" />


## 🔍 Análisis Exploratorio (EDA)
📊 Estadísticas generales
El 49.42% de los clientes son mujeres.

El 26.53% del total se ha dado de baja (churn).

El tiempo promedio de permanencia es de 32.34 meses.

El gasto mensual promedio es de USD $64.72, mientras que el gasto diario es de aproximadamente $2.15.

🎯 Coeficiente de variación
Alta dispersión en: SeniorCitizen, Churn, Dependents

📷 Baja dispersión en: Charges.Monthly, PhoneService, Cuentas_Diarias
<img width="375" height="494" alt="image" src="https://github.com/user-attachments/assets/431a45aa-6e89-40a1-997a-6f8a93e21320" />

📈 Boxplot: en busqueda de outliers
<img width="552" height="435" alt="image" src="https://github.com/user-attachments/assets/ed5e6dec-189f-46ed-8759-d3629305102a" />
<img width="543" height="435" alt="image" src="https://github.com/user-attachments/assets/aa737611-14eb-48e7-8597-3111282a9d6d" />


📈 Histograma de Charges.Monthly
<img width="560" height="435" alt="image" src="https://github.com/user-attachments/assets/37dfd67b-93b5-4969-ada7-bb03f88a3d27" />

📈 Distribución de clientes según estatus en la compañia (clientes retenidos vs. dados de baja)
<img width="1722" height="430" alt="image" src="https://github.com/user-attachments/assets/73c28df6-0f7a-4cd5-af90-b097ba2edbd4" />

📈 Heatmap de correlación entre variables numéricas


## 📌 Insights Relevantes **complementar**
Clientes nuevos tienen más probabilidad de irse: Se observa una correlación negativa entre tenure y Churn (-0.35).
Alrededor del 55% de los clientes que se dan de bajan se encuentran en 2 segmentos:
   :star: El primer segmento: Hombres, con contrato mes a mes y facturacion electronica
   :star: El segundo segmento: Mujeres, con contrato mes a mes y facturación electrónica
de lo anterior se desprende que el churn no se relaciona fuertemente con el gasto mensual, pero sí con la permanenciay los clientes con menor compromiso (contratos mensuales, sin servicios múltiples) tienden a abandonar más.

<img width="571" height="660" alt="image" src="https://github.com/user-attachments/assets/eae8d567-015f-4766-82e6-7c5bba1151c3" />


## 📑 Recomendaciones Estratégicas
Basadas en los análisis y visualizaciones, se sugiere:

✅ 1. Fortalecer programas de fidelización para nuevos clientes
Intervenir activamente en los primeros 12 meses de permanencia.

Ofrecer bonos o descuentos progresivos para contratos largos.

✅ 2. Incentivar contratos anuales o bianuales
El churn es considerablemente menor entre quienes tienen contratos largos.

Agregar beneficios exclusivos a clientes con mayor tenure.El costo de traer un nuevo cliente es aprox entre 5 a 7 veces el costo de retener a un cliente

✅ 3. Evaluar medios de pago vinculados con mayor churn
Clientes que pagan con cheques electronicos presentan mayor abandono.


📊 Tablas y gráficos complementarios sugeridos
** agregar Tabla de evasión por género, contrato y método de pago (df_sql_recuento)**

**Agregar Gráfico de pastel con % de churn total**

** agregar Heatmap de correlación (sns.heatmap)**

🧾 Conclusión
El análisis de churn revela patrones claves sobre el comportamiento de los clientes que abandonan el servicio. Aunque no hay una única variable predictora fuerte, la combinación de permanencia, tipo de contrato y medio de pago permite identificar segmentos con alto riesgo de evasión. Estos resultados pueden guiar estrategias de retención enfocadas y medibles.

