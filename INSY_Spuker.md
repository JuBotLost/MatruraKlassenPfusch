# 1. Numpy
``

```
import numpy as np

print("Version: ", np.___version___)
np.show_config()

array = np.zeros(shape=10) // 0 Verktor 

len(array)   //memory size

array[4] = 1;

vector = np.arange(10, 50) // von 10 - 49

reversed_vector = vector[::-1] 

array = np.arange(9) // von 0 - 8
matrix = array.reshape(3, 3) // um bauen in eine 3mal3 matrix 

non_zero = np.nonzero(array) // nur Elemente die nicht 0 sind

identity_matrix = np.eye(3) // 3mal3 Einheitsmatrix

randome = np.random.random((3, 3)) //3x3x3 array mit ZufÃ¤lligen Werten

print(np.min(random))
print(np.max(random))

print(np.mean(random)) // mittelwert 

// Grenze mit 1sern 
array[0, :] = 1 Â  Â  Â  Â  Â 
array[-1, :] = 1 Â  Â  Â  Â 
array[:, 0] = 1 Â  Â  Â  Â  Â 
array[:, -1] = 1 Â  Â  Â  Â 

//Was ist die Ausgabe ?
0 * np.nan // not a Numer mal 0 
// Ausgabe: false
np.nan == np.nan // not a Number = not a Number ?
// Ausgabe: false 
np.inf > np.nan // Jeder verleich mit nan ist false
// Ausgabe: false
np.nan - np.nan // Jede Operation mit Nan => Nan 
// Ausgabe: nan
np.nan in set([np.nan]) // Hash vergleichen 
// True
0.3 == 3 * 0.1 // Gleitkommer Darstellung
// False (nicht genau 0.3)


np.fill_diagonal(matrix[1:], [1, 2, 3, 4]) // genau under der Diogonalen 
[[0. 0. 0. 0. 0.] 
[1. 0. 0. 0. 0.] 
[0. 2. 0. 0. 0.] 
[0. 0. 3. 0. 0.] 
[0. 0. 0. 4. 0.]]

//what is the index (x,y,z) of the 100th element?
index = np.unravel_index(99, array.shape)


print(array)

```

## Slicing 

array [start:stop:step]

start => ab wann wird geschnitten (mit dem Index)
stop => bis zu welchem (ohne den Index)
step => schrittweite (negativ = umkehren)

- Grenze von 1sern 
array[0, :] = 1          # Setzt die gesamte erste Zeile auf 1 
(0 => 1. Zeile vom Array)
(: => die gesamte Zeile)

array[-1, :] = 1         # Setzt die gesamte letzte Zeile auf 1
(-1 => letzte Zeile)

array[:, 0] = 1          # Setzt die gesamte erste Spalte auf 1
(: => gesamte Spalte)
(0 => 1. Spalte)

array[:, -1] = 1         # Setzt die gesamte letzte Spalte auf 1

## Einheitsmatrix

3 mal 3
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]

# 2. Pandas
```
// Inhalt der Datei: A|B|C|D#1|2|3|4#5|6|7|8#9|10|11|12#13|14|15|16#
Â with open("./eine_Zeile.csv", "r") as file:

Â  Â  Â  Â  content = file.read().strip()

Â  Â  rows = [row.split('|') for row in content.split('#') if row  

Â  Â  df_new = pd.DataFrame(rows[1:], columns=rows[0])

Â  Â  print(df_new) Â # Ausgabe des neuen DataFrames

// Ausgabe:
A  B  C  D
0  1  2  3  4
1  5  6  7  8
2  9 10 11 12
3 13 14 15 16

// Temperatur stuff

df = pd.read_csv("./GlobalLandTemperaturesByMajorCity.csv")
df.head()

df_spain = df[df['Country'] == 'Spain'] // Filtern
num_records_spain = spain_records.shape[0] // zÃ¤hlen 

min_temp_germany = df_spain['AverageTemperature'].min()

max_temp_germany = df_spain['AverageTemperature'].max()

df_germany = df[df['Country'] == 'Germany']


ungemuetlich_berlin = df_germany[(df_germany['City'] == 'Berlin') &

Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  ((df_germany['AverageTemperature'] < -9) |

Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â  Â (df_germany['AverageTemperature']>22))].shape[0]

// shape[0] => Anzahl der Zeilen, | => oder

tiefste_temp_china = df.loc[df['Country'] == 'China', 'AverageTemperature'].min()

// .loc => ganue die Zeile 



```

### AufrÃ¤umen mit Panda
```
laptops = pd.read_csv('./laptops.csv', encoding='latin1')

print(laptops.info())

//Leere List erstellen 
new_columns = []

// Durch die Spaltennamen gehen, strip um leerzeichen zu entfernen und immer and die Liste anhÃ¤ngen
for column in laptops.columns:

Â  Â  new_columns.append(column.strip())
	laptops.columns = new_columns  // Data Frame


// Methode um bestimmet Dinge zu ersetzen, alles klein zu schreiben und AbstÃ¤nde zu entfernen 

def clean_col(col):

Â  Â  col = col.strip()

Â  Â  col = col.replace('Operating System', 'os')

Â  Â  col = col.replace(' ', '_')

Â  Â  col = col.replace('(', '').replace(')', '')

Â  Â  col = col.lower()

Â  Â  return col
laptops.columns = [clean_col(column) for column in laptops.columns]
print(laptops.columns)

// Jede Zahl nur einmal 

unique_ram = laptops['ram'].unique()

//.dtype um den Datentyp auszugeben 

// typcast
laptops['ram'] = laptops['ram'].astype(int)

// Spalteumbennen und gleich anwenden 
laptops.rename(columns={'ram': 'ram_gb'}, inplace=True)



```


# 3. Machine learning 

// Lineare Regression
```
import pandas as pd

import numpy as np

import matplotlib.pyplot as plt



file = pd.read_csv('./stores_profit_data.csv', encoding='latin1')


// Die 2 die ich abhÃ¤ngig machen will
X = file[['Number_of_Stores']]
y = file['Profit']

// In Test und Trainingsdaten
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

//Lineare Regression erstellen
model = LinearRegression()
model.fit(X_train, y_train)


# Vorhersagen treffen
y_pred = model.predict(X_test)

# Modellbewertung
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f'Mean Squared Error: {mse}')
print(f'RÂ² Score: {r2}')

# Visualisierung
plt.figure(figsize=(10, 6))
plt.scatter(X_test, y_test, color='blue', label='Echte Werte', alpha=0.6)
plt.plot(X_test, y_pred, color='red', linewidth=2, label='Regressionslinie')
plt.title('Lineare Regression: Profit und Anzahl der GeschÃ¤fte')
plt.xlabel('Number of Stores')
plt.ylabel('Profit')
plt.legend()

plt.grid(True)

plt.show()
```

// Workflow

1. Daten sammeln: (QualitÃ¤t, QuantitÃ¤t), 
2. Daten Aufbereiten: (lÃ¶schen oder Mittelwert oder Medium), Doppelte entfernen ,Normalisiert (zwischen 0 und 1), Daten mischen, Daten Splitten (Trainings und Testdaten), encoden (Text zu Zahl -> Normalisation)

3. Modell Training: 
Supervised learning (In den Daten ist schon das Ergebnis drin, man kann predictions machen wenn etwas fehlt), 

Unsupervised learning (Datenmenge ZusammenhÃ¤nge bilden) 

Reinforcement Learning (Belohnung und Bestrafung)

4. Model auswerten: Perfomance messen mit Validierungswerten
5.  Parametertuning: Trainingsschritte, Startwerte, Lernarten
6. Testeinsatz: neue Daten 
- Man muss zwischen den Schritten hin und her Springen 
- Varianz: Punkte weiterauseinander => HÃ¶her, brauche mehr Daten

- Modelle: Lineare Regression, Nicht Lineare Regression, Entscheidungsbaum
- Linear: Abstand zur Gerade hoch 2
- Neuronales Netz: Inputlayer, Hiddenlayer, Outputlayer