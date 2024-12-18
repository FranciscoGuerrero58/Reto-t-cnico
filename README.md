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
| ├── `retoetl.exe`                      | Ejecutable del script en python.                                                                      |
| ├── `dashboard.pbix`                   | Dashboard creado en PowerBI para la interpretación de los datos.                                      |
| **/data**                              | Carpeta que contiene las bases de datos originales y procesados.                                      |
| ├── `BD_OPORTUNIDADES_23_24.cvs/`      | Datos originales sin procesar.                                                                        |
| ├── `OPORTUNIDADES_PROCESADO.xlsx/`    | Datos procesados y listos para análisis.                                                              |
| **/img**                               | Carpeta que contiene las bases de datos originales y procesados.                                      |
| ├── `Diagrama de Flujo.jpg/`           | Datos originales sin procesar.                                                                        |
| ├── `Diagrama de Modelo de Datos.jpg/` | Datos procesados y listos para análisis.                                                              |
| **/docs**                              | Carpeta documentación y archivos relacionados al proyecto.                                            |
| ├── `Dashboard.pdf/`                   | Dashboard con la interpretación de los datos                                                          |
| **README.md**                          | Archivo principal con la documentación.                                                               |



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


### Pandas

Pandas es una librería de Python ampliamente utilizada para la manipulación, análisis y limpieza de datos. Proporciona estructuras de datos de alto rendimiento, como DataFrame y Series, que permiten manejar grandes volúmenes de información de manera eficiente. Es ideal para tareas como la lectura y escritura de archivos (CSV, Excel, SQL, etc.), filtrado, transformación y agrupación de datos.

**Instalación individual:**


```bash
pip install pandas
```


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
### Os

La librería `os` es un módulo incorporado en Python que proporciona una interfaz para interactuar con el sistema operativo subyacente. Permite realizar operaciones como navegar entre directorios, manejar rutas de archivos y ejecutar comandos del sistema operativo. Es útil para la automatización y gestión de archivos y carpetas.

### Re

La librería `re` es el módulo de Python para trabajar con expresiones regulares. Las expresiones regulares son patrones que se utilizan para buscar, reemplazar, dividir o validar cadenas de texto.

### WorkBook

Se utiliza para crear un nuevo archivo de Excel (libro de trabajo). Este objeto representa el libro en blanco que puedes modificar, guardar y personalizar según sea necesario.


### Table

Representa una tabla en Excel, que es un rango de celdas con formato especial. Las tablas tienen encabezados, pueden tener filas totales, y soportan filtros y estilos.

### TableStyleInfo

Permite personalizar el estilo visual de una tabla, como colores, bordes y opciones de diseño. Se aplica al objeto Table.


# Diagrama de flujo
![diagrama_flujo](https://github.com/user-attachments/assets/0cd3dd9f-fcfb-48a5-bf9e-1e4080f89e98)

# Código

Este script procesa un archivo CSV con datos de oportunidades, realiza transformaciones en las columnas, y guarda los resultados en un archivo Excel con formato de tabla.


## Propósito

El objetivo principal es transformar y limpiar datos en un formato útil para análisis. El flujo abarca:
1. **Extracción**: Leer datos desde un archivo CSV.
2. **Transformación**: Aplicar limpieza, formateo, y cálculos adicionales.
3. **Carga**: Exportar los resultados a un archivo Excel con formato tabular.

## Código y Explicación

### Importación de Bibliotecas

El script utiliza bibliotecas como `pandas` para la manipulación de datos, `os` para manejar rutas, y `openpyxl` para trabajar con archivos Excel.

```python
import pandas as pd
import os
import re
from word2number import w2n
from openpyxl import Workbook, load_workbook
from openpyxl.worksheet.table import Table, TableStyleInfo
```
Puedes instalar los requisitos mediante `pip`:

```bash
pip install pandas openpyxl word2number
```

### `palabras_a_numeros`

Esta función convierte cadenas numéricas escritas en palabras (como "uno", "diez") a valores enteros.

- **Input:** Texto (str)
- **Output:** Número (int) o texto original si no es convertible.

```python
# Función para estandarizar los valores alfabéticos a numéricos
def palabras_a_numeros(texto):
    try:
        texto = texto.lower().strip()
        if texto == "cero":
            return 0
        return w2n.word_to_num(texto)
    except ValueError:
        return texto  # Retorna sin cambios si no es procesable
```

### `configurar_tabla_excel`

Aplica formato de tabla a los datos exportados en Excel. Define un rango basado en el tamaño de los datos y aplica un estilo predeterminado.

- **Input:** Ruta del archivo Excel.
- **Output:** Archivo Excel con formato tabular.

```python
# Función para configurar en modo de tabla los datos procesados
def configurar_tabla_excel(output_file, nombre_tabla="DatosProcesados"):
    wb = load_workbook(output_file)
    ws = wb.active

    # Definir el rango de la tabla
    num_filas = ws.max_row
    num_columnas = ws.max_column
    rango = f"A1:{chr(64 + num_columnas)}{num_filas}"

    # Configurar la tabla
    tabla = Table(displayName=nombre_tabla, ref=rango)
    estilo = TableStyleInfo(
        name="TableStyleMedium9", showFirstColumn=False,
        showLastColumn=False, showRowStripes=True, showColumnStripes=True
    )
    tabla.tableStyleInfo = estilo
    ws.add_table(tabla)
    wb.save(output_file)
```

### `process_csv_to_excel`

Esta es la función principal del script, donde se ejecuta todo el flujo ETL (Extracción, Transformación y Carga).

#### **Extracción**

Se define la ruta de entrada del archivo CSV y se verifica su existencia.

```python
def process_csv_to_excel():
    # Obtiene la ruta del escritorio del usuario
    desktop = os.path.join(os.path.expanduser("~"), r"Desktop\Tec MTY\data")

    # Define la ruta de entrada y salida
    input_file = os.path.join(desktop, "BD_OPORTUNIDADES_23_24.csv")
    output_file = os.path.join(desktop, "OPORTUNIDADES_PROCESADO.xlsx")

    try:
        # Lee el archivo CSV
        data = pd.read_csv(input_file)

        # Identifica las columnas
        columnas = data.columns
        print(f"Columnas detectadas: {columnas}")
```

#### **Transformación**

Se realizan las siguientes tareas:

1. **Limpieza de datos:**
   - Se eliminan filas duplicadas.
   - Se eliminan registros sin valores en la columna `Zona`.

```python
        # Limpieza de datos
        data = data.drop_duplicates()  # Elimina filas duplicadas
        data = data.dropna(subset=['Zona'])  # Elimina registros sin 'Zona'
```

2. **Formateo de columnas:**
   - Convierte IDs a mayúsculas.
   - Transforma la columna `Importe` de texto a números.

```python
        # Transformar a mayúsculas las columnas de IDs
        for col in ['IdOportunidad', 'IdEmpresa', 'IdPropietario']:
            if col in data.columns:
                data[col] = data[col].astype(str).str.upper()

        if 'Importe' in data.columns:
            data['Importe'] = data['Importe'].apply(
                lambda x: palabras_a_numeros(x) if isinstance(x, str) else x
            )
            data['Importe'] = pd.to_numeric(data['Importe'], errors='coerce')  # Asegura valores numéricos
```

3. **Procesamiento de fechas:**
   - Convierte la columna `FechaCierre` a formato de fecha.
   - Extrae el año y el mes de cierre en columnas separadas.

```python
        if 'FechaCierre' in data.columns:
            data['FechaCierre'] = pd.to_datetime(data['FechaCierre'], errors='coerce', dayfirst=True)
            data['Año de Cierre'] = data['FechaCierre'].dt.year  # Extraer año
            data['Mes de Cierre'] = data['FechaCierre'].dt.month  # Extraer mes
            data['FechaCierre'] = data['FechaCierre'].dt.strftime('%d/%m/%Y')
```

4. **Generación de nuevas columnas:**
   - Clasifica importes en rangos (`Bajo`, `Medio`, `Alto`, `Muy Alto`).
   - Calcula el estado de los participantes (`Activo`, `Inactivo`, `Desconocido`).

```python
        if 'Importe' in data.columns:
            data['Rango Importe'] = pd.cut(data['Importe'], bins=[0, 10000, 50000, 100000, float('inf')],
                                           labels=['Bajo', 'Medio', 'Alto', 'Muy Alto'])

        if 'Participantes' in data.columns:
            data['Estado Participantes'] = data['Participantes'].apply(
                lambda x: 'Activo' if pd.to_numeric(x, errors='coerce') > 0 else 'Inactivo' if pd.to_numeric(x, errors='coerce') == 0 else 'Desconocido'
            )
        else:
            data['Estado Participantes'] = 'Desconocido'
```

#### **Carga**

Se exportan los datos transformados a un archivo Excel con formato tabular.

```python
        # Guarda los datos en un archivo Excel
        data.to_excel(output_file, index=False, engine='openpyxl')

        # Configura el formato de tabla en Excel
        configurar_tabla_excel(output_file)

        print(f"Archivo procesado y guardado en: {output_file}")
    except FileNotFoundError:
        print(f"El archivo '{input_file}' no se encontró en la ruta especificada.")
    except Exception as e:
        print(f"Ocurrió un error: {e}")
```

### Ejecución del Script

El script se ejecuta automáticamente cuando se llama directamente, procesando los datos según el flujo definido.

```python
# Ejecuta la función
if __name__ == "__main__":
    process_csv_to_excel()
```


## Flujo General del Script ETL

Este script sigue las etapas del proceso ETL (Extracción, Transformación y Carga) para procesar un archivo CSV y generar un archivo Excel listo para análisis.

### 1. Extracción
La fase de extracción consiste en cargar los datos originales desde un archivo CSV ubicado en una ruta especificada. El archivo fuente contiene información bruta con posibles inconsistencias:

- Se utiliza la biblioteca `pandas` para leer el archivo CSV.
- El script verifica la existencia del archivo en el directorio proporcionado.
- Si el archivo no se encuentra, se lanza un error que finaliza el proceso.

**Resultado de esta etapa:** Un `DataFrame` con los datos cargados del archivo CSV.

---

### 2. Transformación
La fase de transformación incluye una serie de pasos para limpiar y enriquecer los datos. Los principales procesos son:

#### a) Limpieza de Datos
- Eliminación de filas duplicadas.
- Remoción de registros con valores nulos en columnas clave, como `Zona`.

#### b) Formateo de Datos
- Conversión de columnas de identificadores (`IdOportunidad`, `IdEmpresa`, `IdPropietario`) a mayúsculas.
- Conversión de la columna `Importe`:
  - Transformación de valores textuales (como "mil") a numéricos utilizando la función `palabras_a_numeros`.
  - Clasificación en rangos de importe: `Bajo`, `Medio`, `Alto` y `Muy Alto`.

#### c) Procesamiento de Fechas
- Transformación de la columna `FechaCierre` a formato de fecha.
- Extracción del año y mes de cierre en columnas separadas (`Año de Cierre` y `Mes de Cierre`).

#### d) Generación de Nuevas Columnas
- **Rango Importe**: Segmenta los valores en categorías (`Bajo`, `Medio`, `Alto`, `Muy Alto`).
- **Estado Participantes**: Determina el estado en función del número de participantes:
  - `Activo` si es mayor a 0.
  - `Inactivo` si es igual a 0.
  - `Desconocido` si el valor es inválido o la columna no existe.

**Resultado de esta etapa:** Datos limpios y enriquecidos listos para exportar.

---

### 3. Carga
En esta fase, los datos transformados se exportan a un archivo Excel con un formato tabular.

- Se utiliza `pandas` para escribir el archivo Excel.
- La función `configurar_tabla_excel` aplica formato tabular al archivo generado.

**Resultado de esta etapa:** Un archivo Excel listo para su uso en análisis o presentación.

# FALTA ESTA SECCIÓN
Instrucciones paso a paso de como ejecutar los scripts

# Visualizaciones

Detallar como visualizar los graficos y dashboards generados 
