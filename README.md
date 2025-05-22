 # **Analisis de datos (productos de Amazon)**

 ## **Descripción**

Este proyecto analiza un dataset de productos tecnológicos de Amazon, fue desarrollado como parte del portfolio personal de Leonardo Jeremías Polidori para practicar limpieza y normalización de datos, análisis exploratorio, visualización de estadísticas y consultas SQL.

 ## **Aproximación **

Se solicitó a CHAT GPT que plantee una serie de objetivos a cumplir recreando el rol de "jefe de proyecto" en base a un dataset público de Kaggle.
 
- Los objetivos planteados por la IA fueron los siguentes:

**1.Limpieza y transformación de datos**
	Convertí discounted_price, actual_price, discount_percentage, rating, rating_count a tipos numéricos adecuados (quitando símbolos como ₹, %, ,, etc.).
	Separá correctamente los registros de user_id, user_name, review_id, review_title, y review_content (están unidos por comas pero deberían estar normalizados o contados).
	Verificá duplicados y registros incompletos.
**2.Análisis exploratorio**
	¿Cuál es el promedio de descuento en los productos?
	¿Qué categorías son más frecuentes?
	¿Cuántos productos tienen una calificación mayor a 4?
	¿Cuáles son los 5 productos más caros (precio real, no con descuento)?
	¿Cuál es la relación entre precio y calificación?
**3.Visualizaciones sugeridas (usando Python)**
	Gráfico de barras con las categorías más frecuentes.
	Diagrama de dispersión: precio vs. calificación.
	Histograma de ratings.
	Pie chart con el porcentaje de productos por rango de descuento (0-25%, 26-50%, etc.).

 ## **Objetivos**

- Limpiar y transformar los datos crudos del archivo _`amazon.csv`_
- Explorar patrones en precios, calificaciones y categorías
- Visualizar la distribución de productos y su relación precio/calidad
- Simular un entorno de trabajo con entregas realistas

 ## **Dataset**

- Fuente: archivo `amazon.csv` (https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset/data)
- Registros: 1.465 productos y reseñas
- Variables: nombre del producto, precio, descuento, calificación, reseña, etc.

 ## **Herramientas**

- Python 3, Visual Studio Code
- Pandas, Matplotlib, SQLite
- CHAT GPT / Google Gemini

 ## **Análisis realizado**

- Limpieza de datos: conversión de precios, normalización de texto
- División de tablas hasta la NF3 (debido a la naturaleza de los datos no se siguió normalizando)
- Estadísticas descriptivas
- Visualización por categoría, precio y calificación

 ## **Dificultades y decisiones**
- Durante el proceso de normalización, se dividió la información en distintas tablas para evitar dependencias parciales y redundancias. Sin embargo, al analizar los campos `review_id`, `user_id`, `review_title`, `review_content` y similares, se detectó que contenían múltiples entradas agrupadas en un mismo campo, sin un delimitador claro ni consistente.
- Debido a esta estructura ambigua, se optó por **no dividir estos registros en filas individuales**, ya que una separación automática podría generar **incoherencias en los datos** y afectar negativamente el rendimiento y la calidad del análisis. 
- Se recomienda que, en caso de necesitar una división más precisa de estos campos, se realice un proceso de limpieza **manual o semiautomática**, previa validación del contenido.

- Se detectó una sobrecarga de información a la hora de graficar las categorías más vendidas para su análisis práctico:
	Se creó un archivo CSV _`:database\\most_sold_categorys_short_names.csv`_ para graficarlas cómodamente sin alterar la db principal

 ## **Resultados destacados**

- El descuento promedio de los productos es de 47,69%
- Las 5 categorías más vendidas son:
	1-_USB CABLES_ 233 productos
	2-_SmartWatches_ 76 productos
	3-_Smartphones_ 68 productos
	4-_SmartTVs_ 63 productos
	5-_In-Ear Headphones_ 52 productos
- 930 productos tienen un rating superior a 4, un total del **63.48%** de los productos totales
- Los 5 productos más caros son:
	1-_Fire-Boltt Phoenix Smart Watch with Bluetooth Calling 1.3",120+ Sports Modes, 240*240 PX High Res with SpO2, Heart Rate Monitoring & IP67 Rating_
	2-_Fire-Boltt India's No_ ...
	3-_Fire-Boltt Phoenix Smart Wa_...
	4-_Fire-Boltt Gladiator_ ...
	5-_Fire-Boltt Ring 3 Smart Wa_...
	(Y no es hasta el Nº9: 	_MI REDMI 9i Sport_ ..." 
	Que aparece una marca nueva en la lista, 
	seguido por el Nº14: _"Boult Audio Omeg_...")
- Los 50 productos más caros tienen un ranking promedio de 4.19, lo que indica buena percepción del valor premium
- Dentro de _`figures`_ pueden encontrarse:
	1- _`Figure_1_most_sold_categorys.webp`_ muestra de las categorías más vendidas dentro de las seleccionadas en nuestra db.
	2- _`Figure_2_scatter_rating_rated.webp"_ un gráfico de dispersión precio/calidad de los 20 productos mejor valorados de la db.
	3- _`Figure_3_scatter_rating_expensive.webp`_ un segundo gráfico de dispersión, donde se muestran la misma relación del punto anterior, pero aplicada a los 50 productos más caros de la db.
		_*Cabe destacar en este punto que muchos de los productos más caros son artículos de la misma marca y modelos con el mismo precio que sus homónimos, se recomienda un examen por marca y una revisión de los precios.*_
	4- _`Figure_4_rating_distribution.webp`_ distribución gráfica de los ratings de los productos de la db.
		_*comienza desde el rating "2", ya que no hay productos rankeados por debajo*_
	5- _`Figure_5_discount_percentages.webp`_ gráfica de barras con la distribución de la cantidad de porcentaje realizado en los productos de la db.

## Conclusión final

- La data base requiere saneamiento manual o semiasistido para una correcta normalización de los datos recogidos.
- Se recomienda revisar los precios de los productos más caros de la lista, ya que, se observa una regularidad llamativa entre artículos de modelos similares.
- Los descuentos y ratings analizados muestran una gráfica coherente.
- Más del %60 de las reviews son valores encima del 4, lo que habla de una clara satisfacción general de los consumidores.

--- 

## Notas

- Sirva este proyecto, desarrollado entre el 21 y el 22 de mayo de 2025, como parte de mi formación como analista de datos.
- Adjunto mi Curriculum Vitae: _`Leonardo_Polidori_CV.docx`_ dentro de la carpeta del proyecto.
