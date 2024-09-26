# Hidro-DISPAC
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.dates as mdates
import seaborn as sns
import pandas as pd
import os
import itertools
import gspread
#from oauth2client.service_account import ServiceAccountCredentials
#from google.colab import drive
from scipy.interpolate import interp1d
import math
from tkinter import Tk
from tkinter.filedialog import askopenfilename

# ENTRADA DE INFORMACIÓN
## Abre el cuadro de diálogo para seleccionar un archivo
Tk().withdraw() ### Evita que aparezca la ventana principal de Tkinter
file_path = askopenfilename(title="Selecciona un archivo", filetypes=[("Data files", "*.data")])

## Carga el archivo CSV con delimitadores de espacio y '|'
#df = pd.read_csv(file_path, delimiter=r'\s+\|\s+', engine='python', decimal='.')
df = pd.read_csv(file_path, delimiter='|', decimal='.')

## Muestra las primeras filas del DataFrame
print(df.head())

# INFORMACIÓN DE CAUDAL


