# Análisis de Emisiones de Gases de Efecto Invernadero en Brasil

## Descripción del Proyecto
Este proyecto tiene como objetivo analizar los datos históricos de emisiones de gases de efecto invernadero (GEI) en Brasil. Utilizando el conjunto de datos proporcionado por el Sistema de Estimación de Emisiones y Remociones de Gases de Efecto Invernadero (SEEG), buscamos comprender las tendencias de emisión a lo largo del tiempo, identificar los sectores económicos y los tipos de gases que más contribuyen a estas emisiones, y evaluar las emisiones per cápita por estado.

El análisis comienza con el reconocimiento del problema de negocio y la preparación de los datos, pasando por la limpieza y transformación, hasta la generación de insights y visualizaciones clave. Tal como se enfatizó en la clase, la comprensión del problema y la correcta preparación de los datos son pasos fundamentales antes de aplicar cualquier técnica de programación.

## Fuentes de Datos
*   **Emisiones de GEI:** Datos extraídos del SEEG - Sistema de Estimativa de Emissões e Remoções de Gases de Efeito Estufa.
    *   **URL:** [http://seeg.eco.br/download](http://seeg.eco.br/download)
*   **Población por Estado:** Censo del IBGE 2022.
    *   **URL:** [https://www.ibge.gov.br/estatisticas/sociais/saude/22827-censo-demografico-2022.html?=&t=resultados](https://www.ibge.gov.br/estatisticas/sociais/saude/22827-censo-demografico-2022.html?=&t=resultados)

## Análisis y Metodología

El proyecto se estructura en las siguientes fases:

### 1. Conocimiento y Ajuste de Datos
*   **Carga Inicial:** Importación de los datos de emisiones de GEI desde un archivo Excel usando `pandas.read_excel()`. Se realizó una primera exploración con `df.sample()` y `df.info()` para entender la estructura.
*   **Limpieza de Datos:** Identificación y exclusión de datos de 'Remoção NCI', 'Remoção' y 'Bunker', centrándonos únicamente en las emisiones (`Emissão`). Se verificó que los valores de remoción fueran negativos para asegurar la correcta clasificación.
*   **Transformación de Formato:** El DataFrame fue transformado de un formato 'wide' (donde los años eran columnas) a un formato 'long' utilizando la función `pandas.melt()`. Esto permitió un análisis más eficiente de las emisiones a lo largo del tiempo.

### 2. Agrupamiento y Análisis de Emisiones
*   **Emisiones por Tipo de Gas:** Se calculó y visualizó la suma total de emisiones para cada tipo de gas, identificando los gases predominantes. Se confirmó que los gases relacionados con CO2e constituyen la mayor parte de las emisiones totales.
*   **Análisis Multi-Índice (Gas por Sector y Sector por Gas):** Se utilizó el agrupamiento multi-índice para:
    *   Determinar el sector más contaminante para cada tipo de gas específico.
    *   Identificar el gas que más contribuye a las emisiones dentro de cada sector económico (`Nível 1 - Setor`).
*   **Tendencias Temporales:** Se analizó el promedio de emisiones anuales por gas y por sector, utilizando `groupby()` y `pivot_table()` para visualizar cómo evolucionan las emisiones a lo largo de los años.

### 3. Emisiones Per Cápita por Estado
*   **Integración de Datos de Población:** Se importaron y procesaron datos de población del censo de 2022 para cada estado brasileño. Se realizó una limpieza de la columna 'POPULAÇÃO' para asegurar su formato numérico correcto.
*   **Cálculo Per Cápita:** Se unieron los datos de emisiones de 2021 con los datos de población para calcular la emisión per cápita por estado.
*   **Visualización:** Se generaron gráficos de dispersión y de barras para explorar la relación entre población y emisiones, y para visualizar las emisiones per cápita, destacando los estados con mayor huella de carbono por habitante.

## Conclusiones Clave
*   La preparación de datos, incluyendo la transformación de formatos, fue crucial para el análisis efectivo.
*   Los gases relacionados con el **CO2e** son, con diferencia, los principales contribuyentes a las emisiones de GEI en Brasil.
*   Se identificaron claramente los **sectores económicos y los estados** que presentan las mayores emisiones, tanto en términos absolutos como per cápita.

## Tecnologías Utilizadas
*   **Python**
*   **Pandas:** Para manipulación y análisis de datos.
*   **Matplotlib:** Para la creación de gráficos estáticos.
*   **Plotly Express:** Para visualizaciones interactivas.
