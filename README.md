# 📊 Análisis de clientes y patrones de uso — ConnectaTel

## 🎯 Objetivo del proyecto

Analizar el comportamiento de los clientes de **ConnectaTel** a partir de su información demográfica y sus patrones de uso, con el fin de identificar segmentos de clientes, detectar problemas de calidad de datos y obtener hallazgos que ayuden a mejorar la oferta de planes.

El análisis se enfoca principalmente en:

- Edad de los clientes.
- Cantidad de mensajes y llamadas.
- Minutos de llamadas.
- Distribución de los clientes por plan.
- Segmentación por edad y nivel de uso.
- Identificación y revisión de valores faltantes, sentinels y outliers.

---

## 📁 Datasets utilizados

### `users.csv`

Contiene información de los clientes, incluyendo:

- `user_id`
- `first_name`
- `last_name`
- `age`
- `city`
- `reg_date`
- `plan`
- `churn_date`

### `usage.csv`

Contiene los registros de uso:

- `id`
- `user_id`
- `type`
- `date`
- `duration`
- `length`

### `plans.csv`

Contiene la información relacionada con los planes disponibles.

---

## 🔎 Etapas del análisis realizadas

### 1. Carga e inspección de datos

- Lectura de los datasets con `pandas`.
- Revisión de las primeras filas con `.head()`.
- Inspección de estructura y tipos de datos con `.info()`.
- Resumen estadístico con `.describe()`.

### 2. Calidad de datos

- Identificación de valores faltantes y cálculo de su proporción.
- Detección de valores inválidos o **sentinels**.
- Identificación del sentinel `-999` en `age`.
- Revisión de valores extremos en variables de uso.
- Conversión de columnas de fecha a formato `datetime`.
- Revisión de fechas fuera de rango.

### 3. Tratamiento de datos

- Reemplazo de `-999` en `age` por la mediana.
- Reemplazo de `?` en `city` por valores nulos.
- Tratamiento de fechas fuera de rango.
- Conservación de nulos en `duration` y `length` cuando se consideraron potencialmente MAR.

### 4. Agregación y construcción del perfil de usuario

Se agregaron los datos de uso por `user_id` para obtener:

- `cant_mensajes`
- `cant_llamadas`
- `cant_minutos_llamada`

Después se combinaron con `users` para construir `user_profile`.

### 5. Análisis exploratorio y visualización

Se utilizaron:

- Histogramas.
- Boxplots.
- Distribuciones por plan.
- Conteos de categorías.

Variables principales:

- `age`
- `cant_mensajes`
- `cant_llamadas`
- `cant_minutos_llamada`

### 6. Detección de outliers

Se utilizaron boxplots y el método del **IQR** para identificar valores extremos.

Se observaron posibles outliers principalmente en:

- `cant_mensajes`
- `cant_llamadas`
- `cant_minutos_llamada`

Estos valores se conservaron para su revisión porque pueden representar usuarios reales de alto consumo.

### 7. Segmentación de clientes

#### Por edad

- `Joven`
- `Adulto`
- `Adulto Mayor`

#### Por nivel de uso

- `Bajo uso`
- `Uso medio`
- `Alto uso`

Estas segmentaciones permiten relacionar características demográficas con patrones de consumo.

---

## ▶️ Cómo ejecutar el notebook

### Google Colab

1. Sube el notebook `.ipynb` a GitHub.
2. Abre el notebook desde GitHub o desde [Google Colab](https://colab.research.google.com/).
3. Sube los archivos `users.csv`, `usage.csv` y `plans.csv` a la sesión de Colab.
4. Verifica las rutas utilizadas en el código.
5. Ejecuta las celdas en orden.

### Jupyter Notebook

1. Clona o descarga este repositorio.
2. Instala las librerías utilizadas.
3. Abre el archivo `.ipynb` con Jupyter Notebook o JupyterLab.
4. Verifica que los datasets estén disponibles.
5. Ejecuta las celdas de principio a fin.

---

## 🔁 Guía breve de reproducción

1. Cargar los datasets.
2. Revisar estructura y estadísticas descriptivas.
3. Identificar valores faltantes y sentinels.
4. Corregir valores inválidos y fechas fuera de rango.
5. Convertir las fechas a `datetime`.
6. Analizar los nulos de `duration` y `length`.
7. Agregar los datos de uso por `user_id`.
8. Combinar la tabla agregada con `users`.
9. Crear histogramas y boxplots.
10. Detectar outliers mediante IQR.
11. Crear los segmentos `grupo_edad` y `grupo_uso`.
12. Revisar resultados y elaborar conclusiones.

---

## 📌 Resultado esperado

Obtener un perfil consolidado de los usuarios que permita:

- Analizar sus patrones de consumo.
- Identificar segmentos por edad y nivel de uso.
- Detectar casos extremos.
- Generar recomendaciones para mejorar la oferta comercial de ConnectaTel.

---

## 🛠️ Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

Jupyter Notebook / Google Colab
