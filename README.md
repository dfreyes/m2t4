# Taller: Adquisición, Procesamiento y Visualización de Datos (Modulo 2 - Taller 2)

## Descripción del Proyecto
Este repositorio contiene un análisis de datos de las transacciones históricas de comercio electrónico obtenidos de **Online Retail II**.
El análisis abarca desde la ingesta y limpieza profunda de más de 1 millón de registros hasta la implementación de modelos avanzados de Machine Learning para clasificación, segmentación y predicción de ventas futuras.

---

* **Autor:** Ing. Diego F. Reyes Y.
* **Fecha:** Octubre 2026
* **Fuente de Datos:** [UCI Machine Learning Repository - Online Retail II](https://uci.edu)

---

## Estructura del Proyecto

---

### Parte 0: Preparación
* **Ingesta y Concatenación:** Carga y unión de las hojas correspondientes a los períodos 2009-2010 y 2010-2011, consolidando un dataset unificado.
* **Exploración y limpieza de Datos:**
  * Remoción de transacciones canceladas (códigos de factura que inician con 'C').
  * Eliminación de registros duplicados idénticos y tratamiento de valores nulos en el identificador de cliente (`Customer ID`).
  * Filtrado avanzado de anomalías estructurales en códigos de producto (`StockCode`) mediante expresiones regulares (Regex).
  * Purga de registros analíticos inconsistentes (precios unitarios menores o iguales a cero).
* **Análisis Exploratorio de Datos:** Análisis de distribución de variables clave (`Quantity`, `Price`, `Total_Amount`), identificación del Top 5 de productos más vendidos y mapeo de tendencias temporales y estacionalidad.

---

### Parte 1: Clasificación de Clientes (Machine Learning Supervisado)
* **Segmentación de clientes:** Aplicación de la **Ley de Pareto (80/20)** sobre el volumen de gasto acumulado. Los clientes responsables del 80% de la facturación global son etiquetados como `Clientes Premium`, mientras que el resto se clasifica como `Clientes Normales`.
* **Modelado Supervisado:** Entrenamiento de un clasificador binario (**Random Forest**) optimizado con balanceo de pesos para predecir el estatus de un cliente basándose en su volumen y frecuencia de compra.

### Parte 2: Segmentación de Clientes (Machine Learning No Supervisado)
* **Clustering K-Means:** Agrupamiento espacial tridimensional de clientes buscando estructuras de comportamiento homogéneas. Determinación del hiperparámetro óptimo \(K\) mediante el Método del Codo.
* **Clustering Mean Shift:** Segmentación automática basada en densidad de puntos para contrastar contra el enfoque de K-Means.
* **Análisis Comparativo:** Evaluación del nivel de granularidad, operabilidad y distribución de clientes en ambos algoritmos.

---

### Parte 3: Predicción de Ventas Futuras (Regresión)
* **Modelado Predictivo:** Construcción de series temporales de ingresos mensuales.
* **Ingeniería de Características:** Inclusión de componentes estacionales mediante variables dummy mensuales y desfases (*lags*) de inventarios por macro-categorías.
* **Entrenamientos Cruzados:** Implementación de modelos lineales y no lineales (Regresión Lineal, Árboles de Decisión y Random Forest Regressor).
* **Evaluación:** Validación de modelos a través de métricas de rendimiento como \(R^2\) Score y Error Absoluto Medio (MAE).

---

## Librerías Utilizadas
* **Python 3**
* **Pandas** Procesamiento y manipulación de datos
* **NumPy** Operaciones numéricas de alta eficiencia
* **Matplotlib** & **Seaborn** Visualización estática de datos
* **Scikit-Learn** Algoritmos de Machine Learning y preprocesamiento

---

| Variable Name | Role | Type | Description | Units | Missing Values |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **InvoiceNo** | ID | Categorical | a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicates a cancellation | | no |
| **StockCode** | ID | Categorical | a 5-digit integral number uniquely assigned to each distinct product | | no |
| **Description** | Feature | Categorical | product name | | no |
| **Quantity** | Feature | Integer | the quantities of each product (item) per transaction | | no |
| **InvoiceDate** | Feature | Date | the day and time when each transaction was generated | | no |
| **UnitPrice** | Feature | Continuous | product price per unit | sterling | no |
| **CustomerID** | Feature | Categorical | a 5-digit integral number uniquely assigned to each customer | | no |
| **Country** | Feature | Categorical | the name of the country where each customer resides | | no |


---
## Cómo Ejecutar el Proyecto
1. Clona este repositorio:
2. Descarga el archivo de datos `online_retail_II.xlsx` desde la fuente de la UCI y colócalo en la raíz del proyecto.
3. Ejecuta el entorno de Jupyter Notebook o Google Colab y abre el archivo correspondiente.
