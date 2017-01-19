# Python - Intro

version 3.x

ipython sheel
python script (.py)

{{TOC}}

## Variables
- Create a variable : `myVariable = 10`
- Print a variable : `print(myVariable)`
- Type : `type(myVariable)`
- Transtypage : srt(), int(), float() and bool() 

## Listes
- création : `my_list = ["my", "list", a, b]`
- liste de liste : `house = [["hallway", hall],
         ["kitchen", kit],
         ["living room", liv],
         ["bedroom",bed],
         ["bathroom",bath]]`
- sélection d'items de liste : 
	- `fam[0]`renvoie le 1er élément de la liste fam
	- `fam[-1]`renvoie le dernier élément de la liste fam
	- `fam[3:5]`renvoie les éléments d'index compris entre 3 (inclu) et 5 (exclu) de la liste fam
	- `fam[:4]`renvoie les éléments d'index 0 à 3 de la liste fam
- addition d'items de liste : `eat_sleep_area=areas[3]+areas[7]`
- pointer le 2ème élément de la liste de listes house : `house[-1][1]`
- modification d'une liste : `myList[2]=65`
- extension d'une liste : `y = x + ["e", "f"]`
- suppression d'un élément : `del(x[1])`
- duplication de liste : myList2=list(myList1)

## Fonctions
Syntaxe générale : `output = function_name(input)`
- afficher description d'une fonction `?nomFonction` ou `help(nomFonction)`

## Méthodes
Appel de méthodes : `var_up=maVar.upper()` ou `var_count=maVar.count("o")`
- pour connaitre méthodes de str() : `help (str)`
- méthode pour connaitre index de 20.0 dans areas : `areas.index(20.0)`
- méthode pour connaitre nbre de fois ou 14.5 apparait dans areas : `areas.count(14.5)`
- ajouter des éléments : `areas.append(elt1)`
- supprimer élément elt1 : `areas.remove(elt1)`
- inverser éléments : `areas.reverse()`

## Packages
- install package : utilisation de pip
	- download get-pip.py depuis http://pip.readthedocs.org/en/stable/installing/
	- terminal : `python3 get-pip.py
	- **installation** : `pip3 install bumpy`
- **import de packages** (ici : bumpy) : `import numpy` as np
- import d'une fonction d'un package : `from numpy import array` qui permet d'appeler directement array comme ça : `array([1,2,3])` mais pas conseillé car masque le fait que la fonction est une fonction du package numpy

## Numpy
Numeric Python
- **import** : `import numpy as np`
- numpy array permet opérations sur les tableaux
- **création** : `np_tableau=np.array(tableau)`
- ne marche que sur tableaux de même type / numpy arrays contain only one type
- numpy array : new type / just as float, integer, etc
- subsetting : 
	- soit bmi un tableau contenant [2.4,5.6,1.8]
	- bmi>3 renverra le tableau [False,True,False]
	- bmi[bmi>3] renverra le tableau [5.6] !!
- transformation du tableau baseball en Numpy array : `np_baseball = np.array(baseball)`

### Numpy N-dimensional arrays
- Type of numpy arrays : ndarray = N-dimensional array
- Tableaux à 2 dimensions : 
	- `np_2d[0]` : renvoie ligne d'index 0
	- `np_2d[0][2]` : renvoie ligne 0 col 2
	- `np_2d[0,2]` : renvoie aussi  ligne 0 col 2
	- `np_2d[:,1:3]` : renvoie toutes lignes des cols 1 et 2

### Numpy : basic statistics
- Moyenne : `np.mean(np_city[:,0])`
- Médiane : `np.median(np_city[:,0])`
- Coef. de corrélation : `np.corcoef(np_city[:,0], np_city[:,1])`
- Standard : `np.std(np_city[:,0])`
- Autres méthodes : sum(), sort(), ...
- Génération données :
	- np.random.normal(disturb mean,distrib std dev.,nbre samples)
	- ex. height = np.round(np.random.normal(1.75,0.20,5000),2)

# Data Visualisation
Basic plots with matplotlib
- importation pkg : `import matplotlib.pyplot as plt`
- `import matplotlib.pyplot as plt`

## Plots
- graph ligne : `plt.plot(x,y)`
- graph points : `plt.scatter(x,y)`
- afficher graph : `plt.show()`

## Histograms
- histogramme simple : `plt.hist(life_exp,bins=15)`
- plt.clf() cleans it up again so you can start afresh.

## Customization
- label des X : plt.xlabel('Year')
- label des Y : plt.ylabel('Population')
- titre : plt.title('myTitle')
- graduations (valeurs, noms) : plt.yticks([0,2,4,6,8,10],['0','2B','4B','6B','8B','10B'])
- text label : plt.text(x, y, 'monTexte')
- grille : plt.grid(True)

## Dictionnaries
- rappel :
	- pour avoir l'index de l'élt "alb" dans la liste countries : `countries.index("alb")`
	- pour avoir la population correspondante :  `pop[countries.index("alb")]`
- création : world = {"afgh":30.55,"alb":2.77,"alg":39.21}
- utilisation : `world["alb"]` renvoie 2.77
- commande : `dict_name[key]` / result : `value`
- affichage clés d'un dictionnaire : `dict_name.keys()`
- ajout d'une entrée : `dict_name[newKey]= newValue`
- recherche d'une valeur : `valeur in dict_name`
- destruction d'une valeur : `del(dict_name[keyName])`
### Pandas
Pandas = DataFrame with row labels and column labels
Avantage : columns with ≠ types !!
- importation pkg : `import pandas as pd`
- 1ère option : DataFrame from dictionary 
	- `brics = pd.DataFrame(dict)`
	- pour attribuer des noms aux lignes : `bricks.index=["BR","RU","IN","CH","SA"]`
	- créer un dictionnaire d'après 3 listes prédéfinies names, dr, cpc : `my_dict={'country':names,'drives_right':dr,'cars_per_cap':cpc}`
- 2ème option : DataFrame from CSV
	- importation en utilisant la 1ère colonne comme index : `brics = pd.read_csv("path/to/brics.csv",index_col=0)`
- !! différence entre séries et dataframe :
	- `brics["country"] renvoie série (key + valeurs colonne country)
	- `brics[["country"]]` renvoie dataframe (juste valeurs colonne country)
	- `brics[["country","capital]]` renvoie dataframe (valeurs colonnes country et capital)
	- `brics[1:4]` renvoie toutes les colonnes des lignes 1 à 3
- loc and iloc
	- `bricks.loc[["RU"]]`renvoie ligne entière corresp. à key "RU"
	- `bricks.loc[["RU","IN","CH"]]`renvoie ttes les colonnes des lignes "RU","IN","CH"
	- `bricks.loc[["RU","IN","CH"],["country","capital"]`renvoie colonnes "country" et "capital" des lignes "RU","IN","CH" 
	- `bricks.loc[:,["country","capital"]`renvoie colonnes "country" et "capital" de ttes les lignes
- Recap
	- Square brackets
		- column access `brics[["country","capital"]]`
		- row access : only through slicing `brics[1:4]`
	- loc (label-based)
		- row access `brics.loc[["RU","IN","CH"]]`
		- column access `brics.loc[:,["country","capital"]]`
		- row & column access `brics.loc["RU","IN","CH",["country","capital"]]`
	- iloc (index based)

## Logic, Control Flow and Filtering
### Basics
- comparison : `< > >= <=`
- boolean operators : `and, or, not`
- sur np arrays, boolean operators ne marchent pas / à la place :
	- `np.logical_and(), np.logical_or() and np.logical_not()`
### If,then, else
- if, then, else
	- syntaxe :  
`if condition :`    
`expression1`   
`else :`   
`expression2`
- elif
	- syntaxe :  
`if condition :`    
`expression1`   
`elif :`   
`expression2`
`else :`   
`expression3`

### Filtering Pandas DataFrame
- Extract columns : 
	* Faire un test et ne garder que les trues : `sel = cars[cars['drives_right']]`
		cars_per_cap        country drives_right
    US            809  United States         True
    RU            200         Russia         True
    MOR            70        Morocco         True
    EG             45          Egypt         True
- Autre exemple :
- `# Create car_maniac: observations that have a cars_per_cap over 500
cpc=cars['cars_per_cap']
many_cars=cpc>500
car_maniac=cars[many_cars]

### While
Syntaxe : `while condition :   
	expression`
	
### For
- Loop over a list : `for x in areas :`  
	`print(x)`
	- with index info : `for x,y in enumerate(areas) :    
print("index :"+str(x)+": "+str(y))`
- Loop over Data structures
- Loop over dictionary : `for key, value in world.items() :`  
    `print(key + " -- " + str(value))`  
- Loop over Numpy array :
	- pour 1D Numpy array :`for x in my_array :
    ...`
	- pour 2D Numpy array : `for x in np.nditer(my_array) :
    ...`
- Loop over DataFrames
	- `for lab, row in brics.iterrows() :
    ...`
    - idem avec sélection de la colonne à afficher : `for lab, row in brics.iterrows() :
    print(row['country'])`
    - ajout colonne résultante d'une opération sur une autre : `for lab, row in brics.iterrows() :
    brics.loc[lab, "name_length"] = len(row["country"])`
		- autre méthode : `brics["name_length"] = presidents["country"].apply(len)`ou `cars["COUNTRY"] = cars["country"].apply(str.upper)`

## Random
### Random Float
*ne pas oublier de charger le pkg numpy : `import numpy as np`*
- Set the seed : `np.random.seed(123)`
- Generate and print random float : `print(np.random.rand())`
### Random integer
- Simulation d'un dé à 6 faces : `np.random.randint(1, 7)`
### Random walk
- initialisation liste : `random_walk=[0]`
- ajout d'un élément step à liste random_walk : `random_walk.append(step)`
- If you pass max() two arguments, the biggest one gets returned. For example, to make sure that a variable x never goes below 10 when you decrease it, you can use:
`x = max(10, x - 1)`
- pour faire boucler 10 fois : `for i in range(10) :`

# Interactive Data Visualization with Bokeh
## Plotting with Glyphs
- Glyphs are :
	- Visual shapes (circles, rectangles, lines...)
	- with properties attached to data : coordinates, size, color, transparency
	- Typical usage : 
		- `import from bokeh.io import output_file, show`
		- import des pkg nécessaires :     
`from bokeh.plotting import figure`   `from bokeh.io import output_file, show`
		- création du graphe :`plot = figure(plot_width=400, tools='pan,box_zoom')`
		- dessin des données : `p.circle(, female_literacy_latinamerica, color='blue', size=10, alpha=0.8)`  
`p.x(fertility_africa,female_literacy_africa,color='red',size=10,alpha=0.8)`
		- nom du fichier de sortie : `output_file('circle.html')`
		- affichage du graphique : `show(plot)`
	- Glyph properties
		- List, arrays, sequences of values
		- Single fixed values
	- Markers
		- en plus d'une line, ajout d'un cercle blanc sur points : `p.circle(date, price, fill_color='white', size=4)`
	- Selon type données, spécifier format
		- ici, 'date' est une liste d'objets de type `datetime` / le préciser au moment de l'appel : `p = figure(x_axis_type="datetime", x_axis_label='Date', y_axis_label='US Dollars')`
## Plotting datas from NumPyArrays
- `np.linspace()` is a function that returns an array of evenly spaced numbers over a specified interval. `np.linspace(0, 10, 5), for example, returns an array of 5 evenly spaced samples calculated over the interval [0, 10].
- `np.cos(x)` calculates the element-wise cosine of some array x.
## Plotting datas from Pandas DataFrames
Exemple de script :
	# Import pandas as pd
	import pandas as pd
	# Read in the CSV file: df
	df = pd.read_csv('auto.csv')

	# Import figure from bokeh.plotting
	from bokeh.plotting import figure 

	# Create the figure: p
	p = figure(x_axis_label='HP', y_axis_label='MPG')

	# Plot mpg vs hp by color
	p.circle(df['hp'],df['mpg'],color=df['color'],size=10)

	# Specify the name of the output file and show the result
	output_file('auto-df.html')
	show(p)
## Bokeh ColumnDataSource << mieux !

	# Import the ColumnDataSource class from bokeh.plotting
	from bokeh.plotting import ColumnDataSource

	# Create a ColumnDataSource: source
	source = ColumnDataSource(df)
	# Add circle glyphs to the figure p
	p.circle(x='Year', y='Time', color='color', size=8, source=source)
	# Specify the name of the output file and show the result
	output_file('sprint.html')
	show(p)

## Customizing glyphs
### Hover glyphs

	# import the HoverTool
	from bokeh.models import HoverTool
	# Add circle glyphs to figure p
	p.circle(x, y, size=10,
         fill_color='grey', alpha=0.1, line_color=None,
         hover_fill_color='firebrick', hover_alpha=0.5,
         hover_line_color='white')
	  # Create a HoverTool: hover
	  hover = HoverTool(tooltips=None,mode='vline')
	  # Add the hover tool to the figure p
	  p.add_tools(hover)
	  # Specify the name of the output file and show the result
	  output_file('hover_glyph.html')
	  show(p)

### Colormapping

```
 #Import CategoricalColorMapper from bokeh.models
 from bokeh.models import CategoricalColorMapper
 # Convert df to a ColumnDataSource: source
 source = ColumnDataSource(df)
 # Make a CategoricalColorMapper object: color_mapper
 color_mapper = CategoricalColorMapper(factors=['Europe', 'Asia', 'US'],
                                      palette=['red', 'green', 'blue'])
 # Add a circle glyph to the figure p
 p.circle('weight', 'mpg', source=source,
            color=dict(field='origin',transform=color_mapper),
            legend='origin')
 # Specify the name of the output file and show the result
output_file('colormap.html')
show(p)
```
