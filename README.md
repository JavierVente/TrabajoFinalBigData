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

##### Lectura del .csv de entrada (Resultado Componente 1)
Así como lo indican las intrucciones del trabajo, el componente 2 inicia con la importación del archivo .csv resultante del scrapeado del Componente 1. De eso se encarga este bloque de código, el cual lee el archivo del entorno local y lo convierte al tipo DataFrame con la función read_csv() de la librería Pandas.

##### Limpieza de datos
A través de 3 bloques de código, esta sección se encarga de la limpieza de texto del DataFrame que contiene a los tweets originales, específicamente al campo "Texto del Tweet". El DataFrame resultante se almacena en un nuevo objeto llamado "df_tweets_analisis", encargado específicamente de almacenar la información previamente recolectada de los tweets con su respectivos cambios debido a la limpieza.

Cabe mencionar que las limpiezas realizadas al texto en este espacio son de tres tipos: En primer lugar tenemos la limpieza de caracteres especiales, luego la de caracteres del tipo emoji, y finalemente el filtrado de todo tipo de caracter no alfabético.

##### Eliminación de conectores
En este bloque se aplica la función de sustracción de aquellas palabras que no conlleven un valor signifiacmente en un análisis léxico de texto, como lo son en este caso los conectores del idioma siendo utilizado. Para la aplicación de esta limpieza de texto se aplicó la búsqueda y borrado de aquellas palbaras encontradas en la lista de stop_words traída desde una librería con el mismo nombre.

#####Toknization, POS Tagging
Aquí se procede a la tokenización del texto ya previamente limpiado, para así facilitar el análisis de sentimientos que requiere contar con las palabras en forma de lista con elementos separados. A esta lista además se agrega una letra por cada palabra (v para verbos, a para adjetivos, n para sustantivos) con el fin de facilitar el análisis posterior de subjetividad (En este caso sin embargo no fue aplicado para esto)

##### Segmentación usando Sentiwordnet
Es recién en este punto donde encontramos la librería principal de análisis de sentimiento siendo utilizada, en este caso, Sentiwordnet. La razón por la cual se eligió esta librería es por los buenos resultados obtenidos en otros análisis donde se utilizó esta misma, posiblemente debido en gran parte a su ligera percepción superior de los textos con sentimientos negativos, si la comparamos con otras herramientas de análisis de sentimientos.

Dentro de la misma función se procede a la introducción de los textos de cada tweet en formato tokenizado (Realizado en el paso anterior) de tal manera a determinar el balance sentimental que se percibe de ellos, pudiendo resultar en una de tres categorías: Positivo, Neutro, Negativo

También un poco más abajo encontramos un gráfico circular hecho con la librería Matplot que expone la segmentación de los sentimiento en la totalidad de los tweets.

##### Exportación del DataFrame resultante a archivo en formato .csv
Finalmente se encuentra el bloque encargado de la exportación en un archivo del tipo .csv del DataFrame que había estado almacenando los datos de cada tweet en su etapa de análisis. Este archivo constituye además el entregable exigido del Componente #2 del trabajo práctico. El nombre de este archivo es "tweets_scrapeados_analizados.csv"
