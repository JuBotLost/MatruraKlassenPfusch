# INSY5 Zusammenfassung
von Moritz Simet und Julian Winkler
___
## numpy
- ``np.zeroes(shape=10) || np.zeroes(10)`` Array with filled with 0 size 10:
- ``np.ones(10)`` -||- with 1 size 10
- ``array.nbytes`` Memory Size
- ``array[4] = 2`` Set indexed
- ``np.arange(10, 20)`` end exclusive
- ``array[::-1]`` Revert array
- ``array.reshape(3, 3) || array.reshape((3, 3))``
- ``np.nonzero([1, 2, 0, 0, 4, 0])`` find indeces where not 0
- ``np.identity(3)`` indentity matrix
- ``np.random.random((3, 3, 3))`` Random Numbers
- ``np.min(array) || array.min()``
- ``np.max(array) || array.max()``
- ``np.mean(array) || array.mean()`` Average 
- ``np.median(array) || array.median()`` 
- ``np.mode(array) || array.mode()``
- ``array[1:-1, 1:-1] = 0`` array with border of 0
- ``array.pad(1, "constant", constant_values=0)`` add border around array
- ``np.fill_diagonal(matrix[1:], [1,2,3,4])``
- ``zero_array[1::2, ::2] = 1`` ``zero_array[::2, 1::2] = 1``
- ``index = np.unravel_index(99, array.shape)``
___
## pandas
- ``df = pd.read_csv("teilnehmer.csv")`` read csv file
- ``df.head()`` 1st five records
- ``df["City"]`` get all City values
- ``df["City"][n]`` get City value of record 'n' 
- ``df["City"][n:m]`` get City values of records 'n' to 'm'
- ``df[["City", "Country"]]`` more columns
- ``df.drop(["City"], axis = 1, inplace = True)``
- ``df["AvgTemp"].min()``
- ``df["AvgTemp"].max()``
- ``df["AvgTemp"].sum()``
- ``df["AvgTemp"].avg()``
- ``df["AvgTemp"].to_numpy()``
- ``df["AvgTemp"].plot().hist()``
- ``df.loc[n]`` get specific record 'n'
- ``df[df["Country"] == "Austria"]`` Search
- ``df[(df["Country"] == "Austria") | (df["Country"] == "Germany")]`` OR
- ``df[(df["Country"] == "Austria") & (df["City"] == "Vienna")]`` AND
- ``df["Planet"] = "World"`` Add new Column or set Columns from all records
- ``df["AvgTemp"] + 5`` add 5 to all records
- ``df.loc[df["AvgTemp"] >= 25, "AvgTemp"] = 25``
- ``rows = [row.split('|') for row in content.split('#') if row]
    df_new = pd.DataFrame(rows[1:], columns=rows[0])``
- ``df.info()`` Overview of DataFrame (DataTypes, Sizes, Count of Not-Null Values)
- ``df.describe()`` Statistics of DataFrame (Avg, Quartils, ...) numeric Columns
___
## Mashine Learning
### Theory
KI->ML->DL
#### Workflow
1. Daten sammeln
    - Quantität / Qualität
    - Daten erhebung muss nicht selbst gemacht werden
    - Daten müssen zur Aufgabe des Modells passen
2. Daten aufbereiten
   - Fehlende Daten fixen
   - Doppelte Datenpunkte löschen
   - Normalisieren 0-1
   - Strings -> Int (encoding) -> Normalisieren
   - Werte randomisieren
   - Daten visualsieren
   - Daten splitten
     - Trainingsdaten (Cross Validation)
       - k-Folds (1 Validierung, rest Training)
     - Testdaten
3. Modell trainieren
    - Supervised Learning
      - Ergebnis bekannt (gut für Predictions wenn fehlt)
    - Unsupervised Learning
      - komplexe Zusammenhänge
    - Reinforcement Learning
      - Agent wird trainiert
4. Modell auswerten
    - Val. Daten für Modell nicht bekannt
    - Cross Validiation: Performance aus allen / Anzahl
5. Parametertuning (Kunst und kein Wissenschaft)
6. Testeinsatz
### Linear Regression
- ``x_axis = data[['Number_of_Stores']]`` ``y_axis = data['Profit']``
- ``model = LinearRegression()`` ``model.fit(x_axis, y_axis)``
- ``model.coef_[0]`` -> k
- ``model.intercept_`` -> d
- ``y_pred = model.predict(x_axis)``
- ``plt.scatter(x_axis, y_axis, color='green', label='Actual Data')``
- ``plt.scatter(x_axis, y_pred, color='blue', label='Fitted Data')``
- ``plt.plot(x_axis, y_pred, color='red', label='Fitted Line')``
- ``plt.xlabel('Number of Stores')``
- ``plt.ylabel('Profit')``
- ``plt.title('Linear Regression: Number of Stores vs Profit')``
- ``plt.legend()``
- ``plt.show()``