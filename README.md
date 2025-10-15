## Fundamentos de Ciencia de datos 2025-2

## 🩺 Análisis de señales ECG, SpO₂ y flujo respiratorio para la detección de apnea del sueño

### Autores: 
**Nataly Rodriguez Atehortua**  
Correo: [nataly.rodriguez@udea.edu.co](mailto:nataly.rodriguez@udea.edu.co)

---

### 🎯 Objetivo del proyecto
El objetivo de este proyecto es analizar las características temporales y frecuenciales derivadas de señales fisiológicas —electrocardiograma (ECG), saturación de oxígeno (SpO₂) y flujo respiratorio— para identificar patrones asociados a la apnea del sueño.  

A partir de la base de datos **Apnea-ECG**, se desarrollaron procesos de extracción de características, detección de valores atípicos y análisis bivariado, con el propósito de comprender las alteraciones fisiológicas asociadas a los eventos de apnea.  

Este trabajo se enmarca dentro del **proyecto del aula de Algoritmos para Big Data**, y complementa las línea de investigación orientada al desarrollo de algoritmos de detección de eventos respiratorios.

---

### 🧠 Descripción general del repositorio

El repositorio se organiza en las siguientes carpetas principales:

📁 Fundamentos-de-Ciencia-de-datos/
<br> ├── 📁 datos/
<br> │   ├── features_with_metaData.csv  -  Datos utilizados en el desarrollo del proyecto (.csv)
<br> │
<br> ├── 📁 proyecto_aula/
<br> │   ├── py_Nataly_Rodriguez_Atehortua.ipynb -  Avance del proyecto de aula: análisis exploratorio, detección y análisis de atípicos
<br> │
<br> ├── 📁 sesiones_practicas/
<br> │   ├── FD_U2_a_ciclo_de_vida.ipynb
<br> │   ├── sp_1_Nataly_Rodriguez_Atehortua.ipynb
<br> │   └── sp_2_Nataly_Rodriguez_Atehortua.ipynb
<br> │   └── sp_3_Nataly_Rodriguez_Atehortua.ipynb
<br> │   └── sp_4_Nataly_Rodriguez_Atehortua.ipynb
<br> │
<br> ├── 📁 recursos/
<br> │   └── artículos_referencia -  Artículos y material de apoyo utilizados en el primer avance del proyecto
<br> │
<br> └── README.md

### 📊 Conclusiones

El análisis de la base de datos Apnea-ECG evidenció que las métricas temporales y frecuenciales derivadas de las señales de ECG, saturación de oxígeno (SpO₂) y flujo respiratorio reflejan adecuadamente los patrones fisiológicos asociados a la apnea del sueño.
Las épocas con eventos respiratorios mostraron desaturaciones transitorias de oxígeno, evidenciadas por disminuciones en SpO₂_min y SpO₂_mean, junto con incrementos en SpO₂_std y SpO₂_var. Además, la señal de flujo respiratorio presentó medianas cercanas a cero y mayor variabilidad, confirmando la capacidad de las métricas extraídas para diferenciar entre épocas con y sin apnea.

Asimismo, se identificaron valores atípicos compartidos en diversas métricas, tanto en épocas con como sin apnea, que exceden los rangos fisiológicos esperables. Entre ellos, algunas características derivadas de los intervalos RR y de la variabilidad cardíaca (RMSSD, std_rr, var_rr) superan los límites típicos, mientras que ciertos registros de SpO₂ muestran desaturaciones inferiores al 70%, fuera del rango confiable de medición.
Estos valores representan artefactos o mediciones no fisiológicas, por lo que deben ser considerados en procesos posteriores de depuración. También se observó alta correlación entre variables relacionadas (por ejemplo, RMSSD y std_rr: ρ = 0.98; airflow_mean y airflow_median: ρ = 0.90; SpO₂_std y SpO₂_var: ρ = 1.0), lo que sugiere redundancia y la necesidad de seleccionar las características más representativas.

Finalmente, aunque los resultados reflejan patrones fisiológicos consistentes, la muestra presenta un sesgo de género (7 hombres y 1 mujer), lo cual limita la generalización de los hallazgos a poblaciones más amplias y heterogéneas.

