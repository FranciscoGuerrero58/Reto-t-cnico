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
- **/docs**: Documentación del proyecto, incluyendo instrucciones y guías.


# Estructura del Proyecto

| Carpeta/Archivo                        | Descripción                                                                                           |
|----------------------------------------|-------------------------------------------------------------------------------------------------------|
| **/src**                               | Carpeta que contiene los archivos Python y PowerBI del proceso ETL.                                   |
| ├── `retoetl.py`                       | Script que realiza la extracción, transformación y visualización de datos a partir de un archivo CSV. |
| ├── `dashboard.pbix`                   | Dashboard creado en PowerBI para la interpretación de los datos.                                      |
| **/data**                              | Carpeta que contiene las bases de datos originales y procesados.                                      |
| ├── `BD_OPORTUNIDADES_23_24.cvs/`      | Datos originales sin procesar.                                                                        |
| ├── `OPORTUNIDADES_PROCESADO.xlsx/`    | Datos procesados y listos para análisis.                                                              |
| **/docs**                              | Carpeta documentación y archivos relacionados al proyecto.                                            |
| ├── `Dashboard.pdf/`                   | Documento con la interpretación de los datos                                                          |
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

# Guía de Instalación

## Descargar el Repositorio
1. Accede al repositorio de GitHub: `git@github.com:FranciscoGuerrero58/Reto-t-cnico.git`.
2. Haz clic en el botón “Code” y selecciona “Download ZIP”.
   
![Descargagit](https://github.com/user-attachments/assets/d8da3fd1-af7d-41f6-a35e-1a70922dcca5)


## Preparación de los Archivos
1. Descomprime los archivos descargados.
2. Dirígete a la carpeta `src` y localiza el archivo `retoetl.py`.
   ![explorador de archivos1](https://github.com/user-attachments/assets/d340b6eb-f9ed-4694-a17b-64d1958fb179)
   ![explorador de archivos2](https://github.com/user-attachments/assets/a516529f-40ed-4f1e-a993-25d0ca205aa4)

3. Abre el archivo en el IDE o editor de texto de tu preferencia.
![script](https://github.com/user-attachments/assets/2cdc1620-0c6d-4ad2-b729-722a10cd61ca)

## Instalación de Librerías Necesarias
Las siguientes librerías deben estar instaladas:
- `pandas`
- `word2number`
- `openpyxl`

Para instalarlas, utiliza el siguiente comando en la terminal:
```bash
pip install pandas openpyxl word2number
```
![terminal](https://github.com/user-attachments/assets/bd8c9840-3203-4138-8bda-144497eea32e)


4. Cambiar la ruta del archivo en la función `process_csv_to_excel` por la ruta de la carpeta descargada de GitHub.

![función](https://github.com/user-attachments/assets/b2ca15cd-8be1-4a5c-9b9e-51f51073e610)


## Ejecución del Proyecto
1. Una vez instaladas las librerías, se deberá ejecutar el script `retoetl.py`.
2. Al ejecutar el archivo:
   - Se mostrará en la terminal la identificación de las columnas del archivo sin procesar.
   - Aparecerá una confirmación de que las transformaciones se han aplicado correctamente.
   - Se generará el archivo `OPORTUNIDADES_PROCESADO.xlsx` en la carpeta `data`.

**Nota:** Asegúrate de que los archivos `BD_OPORTUNIDADES_23_24.csv` (sin procesar) y `OPORTUNIDADES_PROCESADO.xlsx` (procesado) no estén abiertos durante la ejecución del script. De lo contrario, se generará un error de permisos.

## Archivos Generados
En la carpeta `data` encontrarás:
- `BD_OPORTUNIDADES_23_24.csv`: Archivo sin procesar.
- `OPORTUNIDADES_PROCESADO.xlsx`: Archivo procesado generado por el script.
![docs](https://github.com/user-attachments/assets/19c402f5-b363-42b7-a353-73758217f975)

Verifica que el archivo procesado exista y se haya creado con éxito.

---

# Visualización de los Datos

## Requisitos
Es necesario tener Power BI instalado. Puedes descargarlo desde la Microsoft Store si no lo tienes instalado.

![PowerBIdw](https://github.com/user-attachments/assets/315b62b3-2d1e-4ea6-960a-48002547a724)

## Abrir el Dashboard
1. En la carpeta `src`, localiza el archivo `Dashboard.pbix`.
   
![explorador de archivos2](https://github.com/user-attachments/assets/cddd3ea7-f1f8-48f7-ae8e-f6bee237fd3a)

3. Haz doble clic para abrirlo en Power BI.
4. Dentro del archivo encontrarás un informe de ventas anuales con diversos filtros interactivos.

![dashboard](https://github.com/user-attachments/assets/ea58d2e2-4502-4496-98ad-13602217012b)


## Descripción de los Filtros
- **Zona:** Permite visualizar el top 3 de empresas y asesores en crecimiento comparando 2023 con 2024, así como un recuento de los registros en esa zona.

![zona](https://github.com/user-attachments/assets/5d892ea0-af70-415f-83a2-36b883aaa3ac)

- **Rango de Importe:**
  - Rango de valores: `0`, `10000`, `50000`, `100000`.
  - Clasificaciones: Bajo, Medio, Alto y Muy Alto.
  - Ayuda a identificar la tendencia de ventas según el valor filtrado.
  
![rango](https://github.com/user-attachments/assets/7c36cb72-4517-4616-98b9-99aa5a6b6fca)

- **Estado de Participantes:** Muestra las tendencias en ventas cuando:
  - Hay más de un participante por oportunidad.
  - No hay participantes (0).
  - Se desconoce el número de participantes.

![status](https://github.com/user-attachments/assets/94dbd57b-e32d-4f71-aa48-22ece85de696)

- **Divisa:** Permite analizar las tendencias de ventas según la moneda utilizada (Euros, Pesos Mexicanos o Dólares Estadounidenses).

![divisa](https://github.com/user-attachments/assets/671ae3c4-7eba-4f72-bd1b-fe1db963e87d)

- **Mes de Cierre:** Ayuda a visualizar mes a mes:
  - La empresa, zona o asesor con mayor porcentaje de crecimiento.
  - El número de registros para ese mes.

![mes](https://github.com/user-attachments/assets/c73fe0ba-3562-4855-921b-ba3b4617b2ff)

---
