\# Análisis de Componentes Principales (ACP) y Clustering en Pingüinos de Palmer



Este proyecto corresponde a una tarea académica del Máster en Minería de Datos y Visualización. Se ha aplicado un enfoque estadístico multivariante para explorar la estructura morfológica de pingüinos de la Antártida mediante \*\*Análisis de Componentes Principales (ACP)\*\* y \*\*clustering no supervisado\*\*, con el fin de descubrir patrones naturales en los datos sin utilizar etiquetas de especie durante el agrupamiento.



---



\## 🎯 Objetivo del proyecto



El objetivo es identificar grupos de individuos con morfología similar a partir de variables cuantitativas. Las especies no se utilizan como variable predictora, lo que permite:



\- Sintetizar la información mediante ACP.

\- Visualizar la variabilidad estructural en un espacio de baja dimensión.

\- Determinar el número óptimo de grupos (k).

\- Interpretar y perfilar morfológicamente los clústeres.

\- Comparar resultados con la clasificación taxonómica original.



---



\## 📚 Metodología aplicada



\### 1. Preparación y estandarización de datos

\- Variables utilizadas: `bill\_length\_mm`, `bill\_depth\_mm`, `flipper\_length\_mm`, `body\_mass\_g`.

\- Se eliminaron observaciones con valores nulos.

\- Las variables fueron transformadas con `StandardScaler`.



\### 2. Análisis de Componentes Principales (ACP)

\- Se retuvieron 2 componentes principales que explican el \*\*88.1 % de la varianza total\*\*.

\- Se utilizaron gráficos como:

&nbsp; - Scree Plot (`plot\_varianza\_explicada`)

&nbsp; - Círculo de correlaciones (`plot\_corr\_cos`)

&nbsp; - Proyección de individuos (`plot\_pca\_scatter\_with\_vectors`)



📌 \*\*Ejemplo:\*\*



!\[Círculo de correlaciones](fig/fig\_04\_circulo\_correlaciones.png)



---



\### 3. Clustering jerárquico (Ward)

\- Se utilizó la matriz de distancias euclídeas sobre las componentes principales.

\- Método de Ward aplicado con `scipy.cluster.hierarchy`.

\- El dendrograma sugirió \*\*k = 3\*\* como número natural de grupos.



📌 \*\*Ejemplo:\*\*



!\[Dendrograma Ward](fig/fig\_06\_dendrograma\_ward.png)



---



\### 4. Clustering particional (K-means)

\- Se evaluaron valores de `k` entre 2 y 10.

\- Se utilizaron:

&nbsp; - \*\*Gráfico del codo\*\* (inercia intra-cluster)

&nbsp; - \*\*Coeficiente de silueta media\*\*

\- Se seleccionó \*\*k = 5\*\* como valor óptimo.



📌 \*\*Ejemplos:\*\*



!\[Codo](fig/fig\_07\_kmeans\_codo.png)  

!\[Silueta](fig/fig\_08\_silueta.png)



---



\### 5. Perfilado morfológico de los grupos



Cada grupo fue descrito mediante la media y desviación estándar de sus variables estandarizadas.



📌 \*\*Gráfico radar por grupo:\*\*



!\[Radar](fig/fig\_09\_radar\_clusters.png)



---



\## 🧠 Hallazgos principales



\- El agrupamiento jerárquico refleja bien la separación entre especies, proponiendo \*\*k = 3\*\*.

\- El clustering K-means con \*\*k = 5\*\* permitió descubrir:

&nbsp; - Dos subgrupos dentro de \*\*Gentoo\*\* (grupos 1 y 3).

&nbsp; - Un grupo morfológicamente consistente de \*\*Chinstrap\*\* (grupo 2).

&nbsp; - Dos agrupaciones asociadas a \*\*Adelie\*\*, una de las cuales (grupo 4) incluye también individuos \*\*Chinstrap\*\*.



🔍 \*\*Grupo 4\*\* presenta una combinación intermedia de características, lo que podría indicar:

\- Un caso de \*\*hibridación natural\*\*.

\- Una \*\*diferenciación incipiente\*\* que justifica futuras investigaciones.



---



\## ⚠️ Limitaciones



\- La elección del número de clústeres implica interpretación visual.

\- K-means presupone forma esférica de los clústeres.

\- El ACP es una técnica lineal: no capta relaciones no lineales.

\- No se dispone de validación genética o geográfica externa.

\- El tamaño muestral reducido limita la generalización.



---



\## 📁 Estructura del repositorio

