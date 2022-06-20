# **Trabajo Final Big-Data**
Este repositorio consta de los archivos pertinentes al desarrollo del Trabajo Final de Big Data para el módulo de "Open Data &amp; Big Data".

## Contenido del repositorio
El contenido de este repositorio se divide en:
  1. Código fuente (Componente #1 y #2)
  2. Archivo .csv que almacena los tweets resultantes del Componente #1
  3. Archivo .csv que almacena los tweets y sus respectivos análisis resultantes del Componente #2

A continuación se procede a dar una descripción más profunda de cada uno.

### **Código Fuente** (Archivo en formato .ipynb)

Este archivo corresponde a un Notebook de Jupyter donde encontramos toda la programación realizada en python de este trabajo. La primera división que hayamos en esta Notebook está denotada por los títulos "Componente 1" y "Componente 2".

Para comenzar a utilizar este Jupyter Notebook es necesario abrir el archivo .ipynb (preferiblemente en Google Colab para una mayor compatibilidad con el entorno) y comenzar a ejecutar las celdas en el mismo orden en el que están actualmente dispuestas.

#### **Componente #1**

##### Importación de librerías
En este bloque se realiza la importación de todas las librerías y sublibrerías que serán necesarias a lo largo de la ejecución del resto del código.

##### Credenciales de acceso a la API de Twitter
En este bloque se realizan dos cosas. En primer lugar se encuentra la carga "en duro" de las variables de seguridad otorgadas por Twitter para tener acceso de desarrollador a su API. Estas cuatro variables posteriormente son utilizadas para establecer la conexión con la API misma tras la debida validación de claves.

##### Función para el fetching de tweets
Este espacio alberga a la declaración de la función de scrapeado de Tweets en sí misma. La estructura de dicha función puede desglosarse en: Declaración del nombre de los campos a almacenar, realización de la llamada al fetching de tweets con tweepy.Cursor(), almacenmiento de las variables correspondientes a cada campo y, por último, carga de los valores de cada observación a un DataFrame.

##### Creación del .csv con los datos originales de los tweets
Aquí simplemente se exporta el dataframe que contiene a las observaciones con sus campos a un archivo del formato .csv a ser guardado en el entorno local o bien una dirección específica en caso de ser debidamente indicada en la función .to_csv() de la librearía Pandas.

Con eso concluye la sección correspondiente al Componente #1 del trabajo práctico. Para observar el archivo .csv resultante de la búsqueda se puede ejecutar el código o bien ir al archivo "tweets_scrapeados_original.csv"

#### **Componente #2**
