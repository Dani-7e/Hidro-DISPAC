# **Hidro-DISPAC**
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.dates as mdates
import seaborn as sns
import pandas as pd
import os
import itertools
import gspread
from scipy.interpolate import interp1d
import math
from tkinter import Tk
from tkinter.filedialog import askopenfilename

# **ENTRADA DE INFORMACIÓN**
## Abre el cuadro de diálogo para seleccionar un archivo
Tk().withdraw() ## Evita que aparezca la ventana principal de Tkinter
file_path = askopenfilename(title="Selecciona un archivo", filetypes=[("Data files", "*.data")])

## Carga el archivo CSV con delimitadores de '|'
df = pd.read_csv(file_path, delimiter='|', decimal='.')
print(df.head())

# **INFORMACIÓN DE CAUDAL**
try:
    df["Fecha"] = pd.to_datetime(df["Fecha"], format='%Y-%m-%d %H:%M:%S')
except KeyError:
    print("La columna 'Fecha' no existe en el DataFrame")

df['Fecha'] = pd.to_datetime(df['Fecha'], format='%Y-%m-%d %H:%M:%S')
print(df.head())
print(df.dtypes)

## Se crea una nueva columna 'Decade' para agrupar la información por décadas
df['Decade'] = df['Fecha'].dt.year // 10 * 10

## Filtrado de los valores diferentes a 0 y no nulos
filtered_Q = df[(df['Valor'] != 0) & (~df['Valor'].isna())]

## Agrupación y descripción estadística por décadas:
decade_summary = filtered_Q.groupby('Decade')['Valor'].describe()
print(decade_summary)
print(filtered_Q.head())

### Este método calcula las siguientes estadísticas: count: Número de valores, mean: Promedio, std: Desviación estándar, min: Valor mínimo, 25%: Primer cuartil, 50%: Mediana, 75%: Tercer cuartil, max: Valor máximo.

# **ColorPlot** Calidad de la información



# **Interpolar información faltante**
