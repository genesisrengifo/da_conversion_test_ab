# 🛒 Análisis de conversión y prueba A/B para sistema de recomendaciones

Este proyecto se centra en analizar el impacto de un sistema de recomendaciones mejorado en una tienda online, evaluando si puede aumentar al menos un 10% la conversión en las etapas clave del embudo: vista de producto, agregado al carrito y compra. Se utiliza una prueba A/B para comparar el rendimiento entre usuarios con y sin el sistema mejorado.

## 🧪 Metodología

### 1. Preparación de datos
- Conversión de columnas de fecha a formato `datetime` en los datasets `usuarios`, `marketing` y `eventos`
- Identificación y justificación de valores nulos en la columna `details`, presentes solo en eventos de tipo `purchase`
- Verificación de duplicados y discrepancias entre fechas oficiales y fechas reales en los datos

### 2. Filtrado y unión de tablas
- Selección de usuarios inscritos antes del 21/12/2020 en la prueba `recommender_system_test`
- Filtrado por región `EU` y período de observación entre el 07/12/2020 y el 01/01/2021
- Unión de las tablas `usuarios`, `participantes` y `eventos` para formar el dataframe final `df`
- Aseguramiento de que todos los usuarios tengan al menos 14 días de observación

### 3. Análisis exploratorio
- Cálculo de eventos y tasas de conversión por grupo:

#### Grupo A
- Eventos totales: 17
- Login: 7 | Página de producto: 5 | Carrito: 2 | Compra: 3
- Conversiones:
  - Login → Página: 71.43%
  - Página → Carrito: 40.00%
  - Carrito → Compra: 150.00%
  - Página → Compra: 60.00%

#### Grupo B
- Eventos totales: 13
- Login: 8 | Página de producto: 3 | Carrito: 1 | Compra: 1
- Conversiones:
  - Login → Página: 37.50%
  - Página → Carrito: 33.33%
  - Carrito → Compra: 100.00%
  - Página → Compra: 33.33%

- Distribución de eventos por usuario: Grupo A muestra mayor dispersión y un outlier; Grupo B es más compacto
- Verificación de contaminación entre muestras: no se encontraron usuarios duplicados
- Análisis temporal: baja actividad en días festivos, pico el 29/12

### 4. Consideraciones previas a la prueba A/B
- Discrepancias entre fechas oficiales y fechas reales en los datos
- Campañas de marketing activas durante la prueba en regiones `NA` y `CIS`
- Tamaños de grupo similares: A (7 usuarios), B (8 usuarios)

### 5. Evaluación de resultados
- Grupo A muestra mejor rendimiento en todas las etapas del embudo
- Tasa de conversión de carrito a compra superior al 100% en Grupo A (compra directa sin carrito)
- Grupo B tiene más logins pero menor interacción posterior, lo que podría indicar problemas de retención

## 🧰 Tecnologías usadas

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-Data%20Analysis-blueviolet?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-orange?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-yellow?logo=matplotlib&logoColor=black)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-teal?logo=python&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-Statistical%20Tests-darkgreen?logo=scipy&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Hypothesis%20Testing-darkred?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-Documentation-lightgrey?logo=markdown&logoColor=black)

---
Aquí tienes la sección “Cómo ejecutarlo” en formato Markdown, lista para incluir en tu README.md:

## ▶️ Cómo ejecutar el proyecto

1. **Clona este repositorio** en tu máquina local:
   ```bash
   git clone https://github.com/tu-usuario/archivo.git

2. Instala las dependencias necesarias: Asegúrate de tener Python 3.10+ y luego instala los paquetes requeridos:
     ```bash
     pip install pandas numpy matplotlib seaborn scipy statsmodels
3. Ubica los archivos de datos: Coloca los siguientes archivos en la carpeta /datasets/:
- users.csv
- events.csv
- marketing.csv
- participants.csv
4. Abre el notebook principal:
- test_corregifo.ipynb en Jupyter Notebook o VS Code.
5. Ejecuta las celdas en orden para reproducir el análisis completo:
6. Conversión de fechas y limpieza de datos
7. Unión de tablas y filtrado por condiciones del experimento
8. Cálculo de tasas de conversión por grupo
9. Análisis exploratorio y visualizaciones
10. Prueba Z para proporciones y conclusiones



