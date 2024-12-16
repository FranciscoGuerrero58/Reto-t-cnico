# Reto-técnico
Reto técnico de programación en python 

# Proyecto de Transformación y Limpieza de Datos (ETL)

## Descripción

El reto técnico consiste en realizar un script en Python que gestione bases de datos, realice la transformación y limpieza de datos, y que genere un Dashboard para visualizar de manera efectiva la información contenida en la base de datos. Este proceso sigue el enfoque de extracción, transformación y carga de datos (ETL), optimizando la calidad de los datos y preparándolos para su análisis.

## Objetivos

El objetivo principal es automatizar y optimizar el proceso de extracción, transformación y visualización de datos. Esto incluye:

- **Extracción de datos** de una base de datos.
- **Transformación y limpieza** de los datos, eliminando valores nulos, duplicados, estandarizando los datos.
- **Visualización** de los resultados a través de un Dashboard interactivo y dinámico, utilizando Power BI.
- **Automatización** de estos procesos para ahorrar tiempo y reducir errores manuales.

## Resultados Esperados

Al finalizar este proyecto, se espera obtener los siguientes resultados:

- Un proceso automatizado y eficiente para la limpieza y transformación de los datos provenientes de la base de datos.
- El sistema eliminará filas con valores nulos y duplicados, y regularizará los datos.
- Los resultados procesados se almacenarán en un archivo Excel con una estructura organizada y lista para su análisis.
- Se utilizarán herramientas como Power BI para crear gráficos interactivos y dinámicos que ayudarán a responder preguntas clave sobre los datos.
- Ahorro de tiempo y reducción de errores manuales en la manipulación de datos.

## Organización de las Carpetas

El repositorio está organizado de la siguiente manera:

- **/src**: Contiene los scripts de Python para la extracción, transformación y limpieza de los datos.
- **/data**: Carpeta con los archivos de datos originales y los datos procesados (Excel).
- **/dashboard**: Archivos relacionados con el Dashboard en Power BI.
- **/docs**: Documentación del proyecto, incluyendo instrucciones y guías.


# Estructura del Proyecto

| Carpeta/Archivo                        | Descripción                                                                                           |
|----------------------------------------|-------------------------------------------------------------------------------------------------------|
| **/src**                               | Carpeta que contiene los archivos Python para el proceso ETL.                                         |
| ├── `retoetl.py`                       | Script que realiza la extracción, transformación y visualización de datos a partir de un archivo CSV. |
| ├── `dashboard.pbix`                   | Dashboard creado en PowerBI para la interpretación de los datos.                                      |
| **/data**                              | Carpeta que contiene las bases de datos originales y procesados.                                      |
| ├── `BD_OPORTUNIDADES_23_24.cvs/`      | Datos originales sin procesar.                                                                        |
| ├── `OPORTUNIDADES_PROCESADO.xlsx/`    | Datos procesados y listos para análisis.                                                              |
| **/img**                               | Carpeta que contiene las bases de datos originales y procesados.                                      |
| ├── `Diagrama de Flujo.jpg/`           | Datos originales sin procesar.                                                                        |
| ├── `Diagrama de Modelo de Datos.jpg/` | Datos procesados y listos para análisis.                                                              |
| **README.md**                          | Archivo principal con la documentación.                                                               |
| **/docs**                              | Carpeta documentación y archivos relacionados al proyecto.                                            |
| ├── `ManualInstalación.pdf/`           | Datos originales sin procesar.                                                                        |
| ├── `Documentación.pdf/`               | Datos procesados y listos para análisis.                                                              |



# Herramientas Utilizadas

## IDE

**Visual Studio Code**

Se estará utilizando el IDE "Visual Studio Code" para el desarrollo del código y la organización del proyecto.

## Visualización de Datos

**PowerBI**

Para la visualización de los datos se utilizará PowerBI.

## Librerías Necesarias


Para ejecutar este proyecto, necesitarás tener instalados los siguientes paquetes:

- `pandas`
- `openpyxl` 
- `word2number`

Puedes instalar los requisitos mediante `pip`:

```bash
pip install pandas openpyxl word2number
```

### Pandas

Pandas es una librería de Python ampliamente utilizada para la manipulación, análisis y limpieza de datos. Proporciona estructuras de datos de alto rendimiento, como DataFrame y Series, que permiten manejar grandes volúmenes de información de manera eficiente. Es ideal para tareas como la lectura y escritura de archivos (CSV, Excel, SQL, etc.), filtrado, transformación y agrupación de datos.

**Instalación individual:**


```bash
pip install pandas
```

### Os

La librería `os` es un módulo incorporado en Python que proporciona una interfaz para interactuar con el sistema operativo subyacente. Permite realizar operaciones como navegar entre directorios, manejar rutas de archivos y ejecutar comandos del sistema operativo. Es útil para la automatización y gestión de archivos y carpetas.

### Openpyxl

Openpyxl es una librería de Python que permite leer y escribir archivos de Microsoft Excel (formato `.xlsx`). Es especialmente útil para automatizar tareas relacionadas con la manipulación de hojas de cálculo, como crear nuevas hojas, escribir datos en celdas y aplicar formatos.

**Instalación individual:**

```bash
pip install openpyxl
```

### Word2number

La librería `word2number` convierte números escritos en palabras (como "dos mil" o "ciento veinte") a su formato numérico equivalente (como `2000` o `120`). Es útil en procesos de limpieza y transformación de datos donde las cifras no están representadas de manera estándar.

**Instalación individual:**

```bash
pip install word2number
```

### Re

La librería `re` es el módulo de Python para trabajar con expresiones regulares. Las expresiones regulares son patrones que se utilizan para buscar, reemplazar, dividir o validar cadenas de texto.

### WorkBook

Se utiliza para crear un nuevo archivo de Excel (libro de trabajo). Este objeto representa el libro en blanco que puedes modificar, guardar y personalizar según sea necesario.


### Table

Representa una tabla en Excel, que es un rango de celdas con formato especial. Las tablas tienen encabezados, pueden tener filas totales, y soportan filtros y estilos.

### TableStyleInfo

Permite personalizar el estilo visual de una tabla, como colores, bordes y opciones de diseño. Se aplica al objeto Table.


# Diagrama de flujo

# Código


Funciones explicadas: 

Flujo del script

Instalación de librerías

Instrucciones paso a paso de como ejecutar los scripts

# Visualizaciones

Detallar como visualizar los graficos y dashboards generados 
