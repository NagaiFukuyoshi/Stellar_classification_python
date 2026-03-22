# 🌌 Stellar Classification Dataset - Análisis Exploratorio con Python

## 📋 Descripción del Proyecto
Este repositorio contiene un análisis exploratorio del dataset de clasificación estelar del **Sloan Digital Sky Survey (SDSS)**. El objetivo es demostrar mis habilidades en limpieza, transformación y análisis de datos con Python, así como mi capacidad para justificar decisiones técnicas y comunicar hallazgos de forma clara y profesional.

El dataset contiene más de **100,000 observaciones** de objetos celestes clasificados en tres categorías:
- **STAR** (estrellas)
- **GALAXY** (galaxias)
- **QSO** (quásars)

---

## 🎯 Objetivo del Ejercicio

- Explorar la distribución de objetos por clase
- Analizar el **redshift** como indicador de distancia
- Identificar patrones temporales en las observaciones
- Detectar objetos extremos (más brillantes, más lejanos, más fríos/calientes)
- Analizar el uso de equipamiento (placas, cámaras, fibras ópticas)
- Documentar cada decisión técnica para garantizar reproducibilidad

## 🛠️ Tecnologías Utilizadas
- **Python 3** 
- **Pandas** - Limpieza y transformación de datos
- **NumPy** - Operaciones numéricas
- **Matplotlib / Seaborn** - Visualizaciones
- **Jupyter Notebooks** - Análisis interactivo
- **Git / GitHub** - Control de versiones

## 📁 Estructura del Proyecto

```
Stellar_classification_python/
│
├── 📁 data/
│   ├── raw/
│   │   └── stellar_classification.csv
│   └── processed/
│       └── stellar_classification_processed.csv
│
├── 📁 notebooks/
│   └── Stellar_Classification_Python.ipynb
│
├── 📁 docs/
│   └── Stellar_Classification_justificacion.md
│
├── 📁 outputs/
│   └── 📁 graficos/
│       ├── Cámaras_mas_usadas.png
│       ├── Cantidad_de_objetos_por_clase.png
│       ├── Cantidad_objetos_por_plate.png
│       └── Clases_observadas_por_plate.png
│       ├── RCrecimiento_de_observaciones_anual.png
│       └── Fibras_opticas_mas_usadas_top_5.png
│       ├── Objetos_mas_observados_por_año_top_10.png
│       └── objetos_observados_por_año.png
│       ├── Promedio_de_objetos_por_clase.png
│       └── Promedio_redshift_por_clase.png
│       └── Total_objetos_observados_por_mes_top_10.png
│
└── README.md
```

## 🔍 Problemas Encontrados y Soluciones Aplicadas

| Problema | Decisión | Justificación |
|----------|----------|---------------|
| Normalización de nombres de las columnas | Convertir los títulos de las columnas en minúsculas y reemplazar " " y "-" por "_" | Evita problemas con los nombres de las columnas en futuros análisis |
| Falta del promedio de magnitudes | Se crea la columna `magnitud_prom` | Permite identificar objetos más brillantes y más tenues |
| Lectura de fechas en formato MJD | Se crean las columnas `fecha`, `año` y `mes` | Facilita el análisis temporal (años y meses con más observaciones) |

## 📊 Principales Hallazgos

### 1. Distribución de objetos 

Las **GALAXY** son la clase predominante con el **59.44%** de los objetos, seguidas por las **STAR** con cerca del **21.54%**, mientras que los **QSO** (quásars) representan solo el **18.96%** restante. Este desbalance es esperado en astronomía, ya que las galaxias son mucho más abundantes en el universo observable que los quásars, que son objetos extremadamente energéticos y más raros. Para futuros modelos de clasificación, será importante considerar este desbalance para no sesgar las predicciones hacia la clase mayoritaria.

### 2. Redshift por clase

El análisis del **redshift** promedio por clase revela un patrón coherente con el conocimiento astronómico. Las **estrellas** presentan un **redshift** de **-0.000115**, un valor prácticamente nulo que confirma que todas pertenecen a nuestra galaxia. Las **galaxias**, en cambio, muestran un **redshift** promedio de **0.421596**, evidenciando que se encuentran fuera de nuestra galaxia, a distancias que abarcan desde millones hasta miles de millones de años luz. Finalmente, los **quásars** registran el **redshift** más alto, con un valor de **1.719676**, lo que los posiciona como los objetos más lejanos del dataset. Estos núcleos galácticos activos extremadamente energéticos se encuentran tan distantes que su luz ha viajado miles de millones de años antes de ser detectada por los telescopios.

### 3. Observaciones por placas (plates)

El análisis de las placas revela que, en promedio, cada placa contiene aproximadamente **16 objetos** astronómicos. Sin embargo, existe una alta variabilidad: las cinco placas con mayor número de objetos —**6301**, **7699**, **7407**, **7147** y **6516**— superan los **94 objetos cada una**, lo que sugiere que estas regiones del cielo fueron observadas con mayor densidad o corresponden a campos de estudio más extensos.

Al desglosar por tipo de objeto, se observa que las **estrellas (STAR)** son las más frecuentes en estas placas, especialmente en la placa **7147**, donde concentran su mayor número de avistamientos.

### 4. Años con mayor actividad
Los años con mayor número de objetos observados fueron:
- **2012**: 11,044 objetos
- **2011**: 10,813 objetos  
- **2013**: 9,843 objetos
- **2010**: 8,190 objetos
- **2018**: 6,705 objetos

### 5. Crecimiento anual
Los incrementos más notables en observaciones ocurrieron en:
- **2010**: aumento del **296%** respecto al año anterior
- **2001**: aumento del **143.6%** respecto al año anterior

Por el contrario, los años con menor actividad fueron **2019** y **2020**, con una caída del **84%** y **86%** en las observaciones.

### 6. Estrellas: las protagonistas
El análisis por tipo de objeto muestra que las **estrellas (STAR)** fueron los objetos más observados durante todo el período. Los picos de observación se concentraron en:
- **Abril de 2012**: 1,175 STAR
- **Marzo de 2011**: 1,060 STAR
- **Abril de 2013**: 1,021 STAR
- **Marzo de 2012**: 1,014 StAR

Se identifica una **tendencia estacional**: los meses de **marzo y abril** concentran la mayor cantidad de observaciones de estrellas, lo que podría estar relacionado con condiciones atmosféricas favorables o con la disponibilidad del telescopio en esos períodos.

### 7. Top 10 objetos más distantes (mayor redshift)
Los objetos con mayor redshift son **todos quásars (QSO)** , con valores que superan **3.51**. 
Estos se encuentran entre los objetos más lejanos del universo observable registrados en el catálogo.

| ID del objeto | Redshift |
|---------------|----------|
| 1.237663e+18 | 7.011245 |
| 1.237679e+18 | 7.011245 |
| 1.237659e+18 | 7.011245 |
| ... | ... |

### 8. Objetos más brillantes (menor magnitud)
Las **estrellas (STAR)** dominan el ranking de objetos más brillantes, con magnitudes promedio por debajo de **12.05**. 
El quásar más brillante registra una magnitud de **12.19** y la galaxia más brillante de **12.23**.

| Tipo | ID del objeto | Magnitud promedio |
|------|---------------|-------------------|
| STAR | 1.237664e+18 | 12.05 |
| QSO  | 1.237665e+18 | 12.19 |
| GALAXY | 1.237662e+18 | 12.23 |

### 9. Objetos menos brillantes (mayor magnitud)
Los objetos más tenues del dataset incluyen una estrella, una galaxia y un quásar:

| Tipo | ID del objeto | Magnitud promedio |
|------|---------------|-------------------|
| STAR | 1.237664e+18 | 27.54 |
| GALAXY | 1.237655e+18 | 24.60 |
| QSO | 1.237667e+18 | 24.41 |

### 10. Índice de temperatura (u - g)
El índice **u - g** (ultravioleta menos verde) indica temperatura: valores **negativos** = objetos calientes, valores **positivos** = objetos fríos.

**Objetos más fríos (u - g positivo elevado):**
- Estrellas: 1.237655e+18, 1.237663e+18, 1.237665e+18
- Galaxias: 1.237666e+18, 1.237664e+18, 1.237671e+18
- QSO: 1.237661e+18

**Objetos más calientes (u - g negativo):**
- Galaxias: 1.237665e+18, 1.237667e+18, 1.237679e+18
- Estrellas: 1.237662e+18, 1.237664e+18
- QSO: 1.237667e+18

### 11. Fibras ópticas mas usadas

Después de analizar la cantidad de veces que se utilizaron las fibras ópticas en las observaciones, se destaca que las fibras **637**, **105**, **597**, **321** y **611** son las más utilizadas, cada una con más de **150 observaciones**.

Estas fibras corresponden a los canales de captación de luz del espectrógrafo del SDSS. Su alta frecuencia de uso sugiere que podrían estar asociadas a regiones del cielo particularmente estudiadas o a configuraciones preferentes durante las campañas de observación.

| Ranking | ID de fibra | Cantidad de observaciones |
|---------|-------------|---------------------------|
| 1 | 637 | 159 |
| 2 | 105 | 158 |
| 3 | 597 | 158 |
| 4 | 321 | 154 |
| 5 | 611 | 154 |

### 12. Cámaras mas usadas en la observación de objetos celestes

Después de analizar la cantidad de veces que se utilizaron las distintas cámaras en las observaciones, se obtuvo el rango de uso de las cámaras de la siguiente manera

| Ranking | Cámara | Cantidad de observaciones |
|---------|-------------|---------------------------|
| 1 | 4 | 19,573 |
| 2 | 3 | 18,851 |
| 3 | 5 | 18,537 |
| 4 | 2 | 17,117 |
| 5 | 1 | 13,227 |
| 6 | 6 | 12,695 |

**Observaciones clave:**
- Las cámaras **4, 3 y 5** concentran la mayor cantidad de observaciones, con más de **18,500 cada una**
- La cámara **6** es la menos utilizada, con **12,695** observaciones
- La diferencia entre la cámara más usada (4) y la menos usada (6) es de **6,878 observaciones**, lo que representa un **35% menos** de actividad

En el contexto del SDSS, las cámaras están dispuestas en una configuración específica. Este patrón de uso puede reflejar preferencias operativas o diferencias en la calidad de los datos capturados por cada una.

## 📈 Visualizaciones

*Las visualizaciones generadas durante el análisis están disponibles en la carpeta outputs/graficos/ del repositorio.*

## 🚀 Cómo Reproducir el Análisis

### Requisitos previos
- Python 3.8 o superior
- pip (gestor de paquetes)

### Pasos
1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/NagaiFukuyoshi/Stellar_classification_python.git
   cd Stellar_classification_python
   
### Instalar dependencias

- bash
pip install pandas numpy matplotlib seaborn jupyter
Ejecutar Jupyter Notebook

- bash
jupyter notebook
Abrir y ejecutar el archivo notebooks/Stellar_Classification_Python.ipynb

### 💡 Decisiones Clave

- Normalización de nombres de columnas	para evita errores por mayúsculas/minúsculas en análisis posteriores

- Creación de la columna **magnitud_prom** para poder identificar objetos más brillantes y más tenues

- Conversión de MJD a fecha habilitando el análisis temporal (años, meses, estacionalidad)

- Función **graficar** reutilizable	para centralizar la configuración de gráficos, ahorrar código y mantener consistencia

### 📬 Contacto

- **Nombre:** Kevin Andres Arango

- **LinkedIn:** www.linkedin.com/in/kevin-vasquez-73547a29b

- **GitHub:** https://github.com/NagaiFukuyoshi

- **Correo:** vaskev1116@gmail.com

### 📝 Nota Final
Este proyecto fue desarrollado como parte de mi portafolio como aspirante a Data Analyst. Los datos fueron obtenidos de Kaggle y corresponden al dataset Stellar Classification.

⭐ Si te parece interesante, no olvides darle estrella al repositorio