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

