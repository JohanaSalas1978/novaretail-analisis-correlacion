# NovaRetail+ – Análisis de correlación del comportamiento de clientes

Este repositorio contiene un análisis exploratorio de correlación sobre el comportamiento de los clientes de NovaRetail+, una plataforma de comercio electrónico en Latinoamérica con millones de usuarios.

El proyecto analiza una muestra de 15.000 clientes durante 2024 para responder una pregunta del equipo de Crecimiento y Retención: **¿qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?** El análisis es correlacional y exploratorio; no establece relaciones de causa y efecto.

> Proyecto del Sprint 8 del programa de Análisis de Datos de TripleTen. NovaRetail+ es una empresa ficticia y los datos son simulados.

## 📂 Contenido del repositorio

- `novaretail-analisis-correlacion.ipynb`: notebook principal con la exploración, preparación de datos, visualizaciones, cálculo de correlaciones, interpretación para el negocio, limitaciones y próximos pasos.
- `novaretail_comportamiento_clientes_2024.csv`: archivo CSV original del proyecto.

## 📊 Dataset utilizado

El análisis se basa en un único archivo con 15.000 clientes y 12 columnas:

- **Identificación:** `id_cliente`.
- **Perfil:** `edad`, `nivel_ingreso` (ingreso anual estimado del cliente), `region` y `tipo_dispositivo`.
- **Comportamiento:** `visitas_mes`, `compras_mes` y `gasto_publicidad_dirigida`.
- **Satisfacción y relación con la plataforma:** `satisfaccion` (escala de 1 a 5), `miembro_premium` y `abandono`.
- **Variable foco:** `ingreso_anual`, el ingreso que cada cliente genera para la empresa.

## 🎯 Objetivos del análisis

- Explorar y validar la estructura, los tipos de datos y la calidad del dataset.
- Documentar los supuestos y las decisiones de preparación de los datos.
- Visualizar las relaciones entre variables mediante un heatmap y scatterplots.
- Calcular el coeficiente de correlación adecuado según el tipo de variables.
- Detectar relaciones engañosas, como la colinealidad y la posible causalidad inversa.
- Convertir los hallazgos en recomendaciones de negocio y señalar claramente lo que no se puede concluir.

## 🛠️ Herramientas utilizadas

- **Python**: procesamiento y análisis de datos.
- **Pandas**: carga, exploración, limpieza y agrupación de datos.
- **NumPy**: operaciones numéricas y cálculo de la V de Cramér.
- **Matplotlib**: elaboración de gráficos.
- **Seaborn**: heatmaps y scatterplots con líneas de tendencia.
- **SciPy**: coeficientes de correlación (Pearson, Spearman, punto biserial) y prueba chi-cuadrado.
- **Jupyter Notebook**: desarrollo y documentación del proyecto.

## 🔄 Etapas del análisis

1. **Carga y exploración:** lectura del CSV, revisión de las primeras filas, dimensiones, tipos de datos, valores faltantes y rangos.
2. **Preparación y supuestos:** corrección de tipos (`edad` a entero; `tipo_dispositivo` y `region` a categoría), verificación de variables binarias y categóricas, y documentación de los supuestos del análisis.
3. **Visualización de relaciones:** heatmap de correlación de Pearson, scatterplots de las relaciones moderadas y un scatterplot general de todas las variables numéricas contra `ingreso_anual`.
4. **Cálculo de correlaciones:** Pearson y Spearman para variables numéricas, punto biserial para variables binarias frente al ingreso y V de Cramér para variables categóricas.
5. **Interpretación para el negocio:** cada hallazgo incluye la evidencia visual, la evidencia numérica, una interpretación no causal, lo que no se puede afirmar y su implicación de negocio.
6. **Limitaciones y próximos pasos:** alcance del análisis y propuestas para profundizarlo.

## 🔎 Principales hallazgos

- **Calidad de los datos:** el dataset no tiene valores nulos, duplicados ni valores imposibles. El 30,4 % de los clientes (4.567) tiene 0 compras e ingreso anual igual a 0.
- **Compras:** `compras_mes` es, con diferencia, la variable más asociada con `ingreso_anual` (Pearson y Spearman = 0,97). La relación es casi mecánica: cada compra aporta unas 30 unidades de ingreso.
- **Visitas y publicidad:** `visitas_mes` (0,34) y `gasto_publicidad_dirigida` (0,20) muestran asociaciones moderadas a débiles. El gasto publicitario se correlaciona con las visitas (0,58), por lo que parece dirigirse a los clientes más activos y su relación con el ingreso puede ser engañosa.
- **Membresía premium:** los clientes premium (13,9 % de la base) generan en promedio 44,58 de ingreso frente a 35,30 de los no premium (punto biserial = 0,093), una asociación débil.
- **Variables sin relación relevante:** `edad`, `nivel_ingreso`, `satisfaccion` y `abandono` presentan correlaciones menores a 0,06 con el ingreso. El tipo de dispositivo y la región no se asocian con el ingreso ni con el abandono (V de Cramér entre 0,007 y 0,020).
- **Efecto techo:** `satisfaccion` presenta un pico en 5,0 (420 clientes frente a 157 con 4,9).

Los resultados detallados, las visualizaciones y las decisiones de preparación se encuentran documentados en el notebook.

## 💡 Recomendaciones para el negocio

- Priorizar la conversión de los clientes sin compras (cerca del 30 % de la base) y el aumento de la frecuencia de compra de quienes ya compran.
- Evaluar las visitas junto con su conversión en compras, ya que por sí solas no son un buen indicador de valor.
- Probar la efectividad de la publicidad dirigida mediante un experimento controlado (A/B test) antes de aumentar la inversión.
- Explorar el programa premium con un piloto, ya que la evidencia actual es débil y no demuestra un efecto causal.
- Segmentar por comportamiento (compras y visitas) y no por edad, nivel de ingreso, dispositivo o región, que no explican el ingreso.
- Analizar con mayor detalle el abandono, que no se relaciona con el ingreso anual generado por el cliente.

## ⚠️ Limitaciones

- Correlación no implica causalidad.
- La relación entre compras e ingreso es en parte mecánica.
- La publicidad dirigida no se asigna al azar, por lo que su efecto no puede medirse con estos datos.
- Los datos corresponden a un solo año (2024) y no permiten estudiar la evolución de los clientes.
- Las variables mensuales (visitas y compras) se comparan con un ingreso anual acumulado.

## ▶️ Cómo abrir el notebook en Google Colab

Haz clic en el siguiente botón para abrir el notebook:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JohanaSalas1978/novaretail-analisis-correlacion/blob/main/novaretail-analisis-correlacion.ipynb)

También puedes seguir estos pasos:

1. Abre el notebook `novaretail-analisis-correlacion.ipynb` desde el repositorio de GitHub.
2. Selecciona **Open in Colab** o abre Google Colab y carga el notebook.
3. Asegúrate de tener disponible el archivo CSV.
4. Ejecuta las celdas en orden para reproducir el análisis.

## 📘 Cómo reproducir el análisis

1. Clona o descarga este repositorio.
2. Verifica que `novaretail_comportamiento_clientes_2024.csv` esté en la misma carpeta que el notebook, o ajusta la ruta de lectura.
3. Instala las dependencias necesarias si el entorno no las incluye:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```

4. Abre Jupyter Notebook y ejecuta:

   ```bash
   jupyter notebook
   ```

5. Abre el notebook y ejecuta las celdas en orden.

> **Nota:** el notebook original utiliza la ruta `/datasets/novaretail_comportamiento_clientes_2024.csv`. Para reproducir el análisis fuera del entorno original, esta ruta debe ajustarse a la ubicación real del archivo.

## 📌 Conclusión

El análisis permite identificar qué comportamientos del cliente se asocian con el ingreso anual: las compras son el factor dominante, las visitas y la publicidad dirigida se asocian de forma moderada a débil, y las variables demográficas y de segmentación no aportan. Los resultados son una base para orientar estrategias de conversión, evaluar la publicidad y el programa premium mediante experimentos, y priorizar la segmentación por comportamiento.

## 🔗 Repositorio del proyecto

Enlace del repositorio: <https://github.com/JohanaSalas1978/novaretail-analisis-correlacion>
