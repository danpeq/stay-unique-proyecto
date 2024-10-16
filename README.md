# stay-unique-proyecto
Proyecto comparación de CSV files y scraping para decisiones estratégicas y mejorar el posicionamiento competitivo de Stay-Unique

# PASO A PASO DESARROLLO DEL PROYECTO

1. Existe un método con Python usando BeautifulSoup, mediante
la inspección de la página y la extracción de las clases del
código HTML de cada título e información en la cuales estamos 
interesados, pero en esta oportunidad quiero presentar una 
manera mas eficiente y rápida de obtener los datos haciendo 
scraping utilizando APIFY.
Utilicé APIFY scraping para extraer los datos de Airbnb	
	- Use la API de Airbnb Scraper.
	- Utilicé la forma regular.
	- Pegué la URL de la página de Airbnb
	- Filtre los datos por Ubicación, fechas de check in 
	y check out y el número de datos (propiedades).
	- Descargué los datos en formato CSV.

2. Limpié los datos del file de scraping descargado en CSV.
	-Eliminación de duplicados.
	-Ordené las columnas.
	- Limpié celdas donde habia información mezclada
	letras y númeroS. Separé las letras de los números.
	- Me quedé solo con las columnas necesarias.

3. Creé un ambiente virtual en VSCode
	A. CREACION AMBIENTE VIRTUAL
	python.exe -m venv airbnbvenv
	
	B. ENTRAR AL AMBIENTE VIRTUAL
	cd .\airbnbvenv\ 

	C. ENTRAMOS A LA CARPETA SCRIPS
	cd .\Scripts\

	D. Activamos
	.\activate

	E. INSTALACIONES DE LIBRERIAS
	pip install pandas
	pip install matplotlib seaborn
	pip install scipy

	F. Por ultimo seleccionar el Kermel enviromente creado
	para trabajar. --> airbnbvenv(Python 3.12.2)

4. Proceso pipeline ETL
   	- El código de limpieza EDA y ETL en python se encuentra en el archivo: 'airbnb_barcelona.ipynb'
	- Decidí no combiar las dos tablas (Booking y Property),
	ya que en la tabla booking me presenta el PropertyId
	de cada propiedad con cada una de las reservas de cada
	PropertyId. Por lo tanto no veo mucho sentido en combinar
	Booking y Property. Ya que un Dataset es mucho mas grande
	que el otro.
	- Importé los dos archivos Booking y Property
	- Procedí con los procesos ETL y EDA.
	- Eliminé filas con datos y valores ausentes.
	- Cambié el tipo de datos de las columnas de 
	de fecha a date
	- Cree files de Booking y Property con formato parquet
	para poder importarlas en Google BigQuery.

   5. BigQuery
 	- Utilicé BigQuery para crear un proyecto nuevo con el 
	nombre vacational-rental e importé los dos archivos 
	(Booking y Property) en formato parquet que cree en 
	VSCode.
	A continuación adjunto el link con los dataset en BigQuery:
	https://console.cloud.google.com/bigquery?ws=!1m4!1m3!3m2!1svacational-rental!2sBooking_Property
