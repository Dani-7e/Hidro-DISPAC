# Hidro-DISPAC
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.dates as mdates
import seaborn as sns
import pandas as pd
import os
import itertools
import gspread
from oauth2client.service_account import ServiceAccountCredentials
from google.colab import drive
from scipy.interpolate import interp1d
import math

# Carga el archivo CSV con dos delimitadores (espacio y |)
df = pd.read_csv("Q_MEDIA_D@11035020.data", delimiter=r'\s+\|\s+', engine='python',decimal='.')
# Muestra las primeras filas del DataFrame
df.head()
