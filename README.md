##### **Análisis exploratorio de la salinidad del agua subterránea en pozos del acuífero costero de Olón**

###### **Descripción del proyecto**



En este Proyecto se realize un análisis exploratorio de datos aplicado a la red de pozos de la comuna de Olón. El objetivo principal es caracterizar el comportamiento de la salinidad del agua subterránea durante el periodo 2020–2025, a partir de una base integrada que contiene registros hidráulicos, físico-químicos, climáticos y espaciales.



El análisis se desarrolló en Python mediante un notebook de Jupyter llamado **'Proyecto.ipynb'**. En este cuaderno se realizó la carga de datos, limpieza, revisión de calidad, tratamiento de valores nulos, análisis descriptivo y generación de visualizaciones para interpretar el comportamiento de la salinidad en los pozos.



###### **Elección del conjunto de datos**



El conjunto de datos utilizado contiene información histórica de los 14 pozos que componen la red de pozos de la comunda. La salinidad del agua subterránea es una variable importante en este contexto, debido a que permite evaluar posibles cambios en la calidad del agua y diferencias entre pozos.



***La base principal utilizada en el notebook se llama:base\_final\_pozos.csv***



Esta base integra información proveniente de registros de campo y archivos .csv que contienen valores de rasters (NDVI, Lluvia mensual, Evapotranspiracion, elevacion) por cada pozo obtenidos de Google Engine. Estos documentos utilizados para formar la base de datos se adjuntan en este repositorio, las variables restantes fueron obtenidas desde ArcMap 10.5 mediante el respectivo tratamiento de rasters y extracción de valores por pozo.

Este proyecto integra información proveniente de distintas fuentes ambientales y satelitales:



\- \*\*CHIRPS\*\*: datos de precipitación mensual.

\- \*\*MOD16\*\*: datos de evapotranspiración.

\- \*\*Copernicus\*\*: datos de elevación.

\- \*\*NDVI\*\*: índice de vegetación calculado a partir de imágenes satelitales.

README.md: descripción general del proyecto.



**Nota:** en el notebook, la base se carga con el nombre base\_final\_pozos.csv, por lo que este archivo debe estar en la misma carpeta que Proyecto.ipynb, a menos que se modifique la ruta en el código.



La base de datos contiene variables agrupadas según su función dentro del análisis:



***Variables de identificación***

**id:** identificador del pozo

**estado:** estado operativo registrado del pozo

**estado\_corregido:** estado corregido después de revisar la consistencia con el nivel dinámico

***Variables de ubicación***

**x:** coordenada X del pozo (UTM 17S)

**y:** coordenada Y del pozo (UTM 17S)

***Variables físicas del pozo***

**brocal:** altura o referencia del brocal

**elev:** elevación del pozo

**prof\_pozo:** profundidad del pozo

***Variables espaciales***

p**endiente:** pendiente del terreno

**flow\_ac:** acumulación de flujo

**densidad\_drenaje:** densidad de drenaje

**twi:** índice topográfico de humedad

**dist\_cost:** distancia a la costa

**dist\_rio\_m:** distancia al río Olón

**ndvi:** índice de vegetación de diferencia normalizada

***Variables temporales y climáticas***

**anio:** año de registro

**mes:** mes de registro

**lluviamensual\_mm:** lluvia mensual en mm

**et\_mensual:** evapotranspiración mensual.

***Variables hidráulicas***

**nivel\_est:** nivel estático

**nivel\_din:** nivel dinámico

***Variables físico-químicas***

**ce:** conductividad eléctrica

**ph:** potencial de hidrógeno

**temperatura:** temperatura del agua.

**salinidad:** salinidad medida en UPS.

**resistividad:** resistividad ohm

**tds:** sólidos disueltos totales

**do:** oxígeno disuelto

***Variable categórica creada***

**categoria\_salinidad:** clasificación de la salinidad según rangos de referencia TULSMA, diferenciando registros como agua dulce, agua salobre y agua salina.



###### **Metodología**

El código se desarrolló mediante un flujo de análisis secuencial:



Carga de la base de datos.

Revisión inicial de columnas, tipos de datos y estructura.

Normalización de nombres de columnas.

Clasificación de variables por grupo.

Conversión de variables numéricas.

Revisión de valores nulos y registros duplicados.

Validación de rangos temporales.

Revisión de consistencia entre estado operativo y nivel dinámico.

Corrección de inconsistencias en la variable estado.

Tratamiento inicial de valores nulos.

Justificación de nulos conservados.

Estadística descriptiva.

Análisis exploratorio de salinidad.

Elaboración de visualizaciones.

Interpretación de resultados, conclusiones y recomendaciones.

Tratamiento de datos





No se imputaron automáticamente variables como:salinidad, porque es la variable principal del análisis.

do, porque empezó a registrarse desde 2024.

nivel\_din, cuando el pozo no estuvo operativo.



En el notebook se generaron diferentes gráficos para interpretar los datos:



Histograma de salinidad.

Diagrama de caja de salinidad por pozo.

Gráfico de salinidad promedio por pozo.

Gráfico de salinidad promedio anual.

Gráfico de salinidad promedio mensual por año.

Conteo de categorías de salinidad por año.

Clasificación de pozos según salinidad promedio.

Mapa de calor de correlación de variables físico-químicas.

Gráfico de dispersión entre conductividad eléctrica y salinidad.

Gráfico espacial de salinidad promedio por pozo.



El proyecto fue desarrollado en un ambiente virtual de Python. El entorno virtual se llama proyectoad. Ademas, se incluye el archivo requirements.txt, donde se registran las librerías necesarias.



###### **Librerías utilizadas**



Las principales librerías utilizadas fueron:



numpy

pandas

matplotlib

seaborn

.gitignore: archivo que evita subir elementos innecesarios como el entorno virtual.





