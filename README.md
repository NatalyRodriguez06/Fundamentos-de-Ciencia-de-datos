## Fundamentos de Ciencia de datos 2025-2

## 🩺 Análisis de señales ECG, SpO₂ y flujo respiratorio para la detección de apnea del sueño

### Autores: 
**Nataly Rodriguez Atehortua**  
Correo: [nataly.rodriguez@udea.edu.co](mailto:nataly.rodriguez@udea.edu.co)

---

### 🎯 Objetivo del proyecto
El objetivo de este proyecto es analizar las características temporales y frecuenciales derivadas de señales fisiológicas —electrocardiograma (ECG), saturación de oxígeno (SpO₂) y flujo respiratorio— para identificar patrones asociados a la apnea del sueño.  

A partir de la base de datos *Apnea-ECG*, se implementaron procesos de extracción de características, análisis exploratorio de los datos, identificación y tratamiento de valores atípicos y análisis de clústeres. 

Este trabajo se enmarca en el **proyecto del aula de Fundamentos de Ciencia de Datos** y contribuye a la línea de investigación dedicada al desarrollo de algoritmos para la detección de eventos respiratorios. Como parte de este proyecto, se presenta el artículo titulado \textit{Detección de patrones de apnea del sueño mediante análisis de señales fisiológicas}.

---

### 🧠 Descripción general del repositorio

El repositorio se organiza en las siguientes carpetas principales:

📁 Fundamentos-de-Ciencia-de-datos/
<br> ├── 📁 datos/
<br> │   ├── features_with_metaData.csv  -  Datos utilizados en el desarrollo del proyecto (.csv)
<br> │
<br> ├── 📁 articulo/
<br> │   ├── 1. Informe_final_Nataly_Rodriguez.pdf
<br> │
<br> ├── 📁 proyecto_aula/
<br> │   ├── 1. Análisis_Exploratorio_de_Datos
<br> │   ├── 2. Detección_y_Análisis_de_Atípicos
<br> │   ├── 3. Tratamiento_de_Atípicos
<br> │   ├── 4. Transformación_de_Datos_y_Análisis_de_Clúster
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

### Cómo ejecutar el proyecto 

Para reproducir el análisis completo, ejecutar los notebooks en el siguiente orden, ya que cada uno genera los archivos necesarios para los pasos posteriores:

1. Análisis_Exploratorio_de_Datos

2. Detección_y_Análisis_de_Atípicos

3. Tratamiento_de_Atípicos

4. Transformación_de_Datos_y_Análisis_de_Clúster


### Jerarquía de carpetas del proyecto de aula 

El proyecto está estructurado en **cuatro notebooks principales**

#### 1. Análisis Exploratorio de los Datos

En este notebook se formula el problema y se presenta la descripción técnica de la base de datos *Apnea-ECG*. Se analizan las variables del archivo **features_with_metaData**, llevando a cabo una exploración inicial de distribuciones, patrones y correlaciones relevantes. 

Como parte del preprocesamiento, se eliminan los registros en los que **SpO₂ = 0**, ya que corresponden a desconexiones o fallos del sensor y no aportan información útil. El dataframe depurado resultante se almacena y constituye la base para las etapas posteriores.


#### 2. Detección y Análisis de Atípicos

En este notebook se examinan las variables del dataset **features_iniciales**, enfocándose en la **identificación de valores atípicos** en las características extraídas de las señales de ECG, flujo respiratorio y SpO₂. Para ello, se aplican y comparan tres metodologías:

- **IQR (rango intercuartílico)**  
- **Z-score** (criterio |Z| > 3)  
- **DBSCAN** (ε = 5, *min_samples* = 5; parámetros ajustados empíricamente)

Las visualizaciones incluyen **boxplots estratificados por etiqueta** (‘A’ y ‘N’) y **gráficos de dispersión bivariados**, que permiten detectar valores atípicos y analizar su posible origen, ya sea debido a artefactos, fallas del sensor o errores en la detección de picos R.

#### 3. Tratamientos de Atipicos

En este notebook se analizan las variables del dataset **features_iniciales**. Algunas de estas variables presentan valores que no se encuentran dentro de los rangos fisiológicos esperados; por esta razón, dichos registros se reemplazan inicialmente por valores `NaN`. Una vez definidos los valores nulos, se realiza un análisis detallado para identificar su distribución y determinar a qué épocas pertenecen según la etiqueta correspondiente.

Posteriormente, se aplica un proceso de imputación utilizando diferentes técnicas: imputación por mediana, imputación aleatoria y KNN. Estas metodologías se implementan de manera separada para las etiquetas de **apnea ('A')** y **normal ('N')**, con el fin de preservar las características propias de cada condición fisiológica.

Finalmente, tras comparar el desempeño de cada método, se selecciona la estrategia más adecuada y se construye el dataframe final con los valores imputados y se almacena. 

#### 4. Transformación de Datos y Análisis de Clúster

En este notebook se emplean las **variables imputadas** almacenadas en el archivo `variables_imputadas.csv` como base para el análisis.

Se aplican transformaciones de los datos, específicamente **Yeo-Johnson** y **logaritmo natural**, con el fin de **normalizar las distribuciones** y facilitar el análisis posterior.

A continuación, se realiza un **balanceo de clases** mediante técnicas como **under-sampling** y **SMOTE**, con el objetivo de corregir posibles desequilibrios en las etiquetas.

Finalmente, las variables transformadas y balanceadas se utilizan en un **análisis de clúster**, permitiendo **explorar la estructura subyacente de los datos** y detectar patrones relevantes.

### Conclusiones

- El análisis integral de las señales ECG, SpO₂ y flujo respiratorio permitió caracterizar de manera consistente las alteraciones fisiológicas asociadas a los eventos de apnea del sueño. Las métricas temporales y frecuenciales extraídas reflejaron patrones entre épocas con y sin apnea, destacándose las desaturaciones transitorias en SpO₂ y las modificaciones en la variabilidad respiratoria y cardíaca durante los eventos obstructivos.

- La identificación de valores atípicos mediante IQR, Z-score y DBSCAN confirmó la presencia de registros no fisiológicos, particularmente en las características derivadas de ECG y SpO₂. Estos atípicos se asociaron principalmente a fallas en la detección de picos R, artefactos y pérdidas de señal, por lo que su depuración resultó necesaria para garantizar la validez del análisis posterior.

- La evaluación posterior del conjunto depurado evidenció que la mayor proporción de datos faltantes se concentra en las características de ECG —especialmente en épocas de apnea—, mientras que SpO₂ y flujo respiratorio presentaron menor afectación. La imputación aleatoria por clase se identificó como la estrategia más adecuada para preservar la variabilidad fisiológica y evitar distorsiones en las distribuciones originales, superando a alternativas como la imputación por mediana.

- La aplicación de transformaciones como Yeo-Johnson permitió corregir la asimetría y el sesgo presentes en variables críticas, lo que mejoró su distribución y aumentó la capacidad de distinguir entre épocas normales y de apnea. Posteriormente, el análisis de clúster, complementado con técnicas de balanceo como SMOTE, reveló agrupamientos consistentes con las diferencias fisiológicas entre ambas clases. En conjunto, estos resultados respaldan la utilidad de las características extraídas y de las técnicas empleadas para describir y diferenciar los patrones respiratorios, cardiovasculares y de oxigenación asociados a la apnea del sueño.
